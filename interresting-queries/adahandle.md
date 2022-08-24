Quickly draws a table with all adahandles.

handle | fingerprint | address_owner | account_owner

```WITH handles AS (
         SELECT encode(ma.name::bytea, 'escape'::text) AS name,
            ma.fingerprint,
            txo.address,
            sa.view AS stake,
            ( SELECT min(txo_1.id) AS min
                   FROM ma_tx_out mto
                     JOIN tx_out txo_1 ON txo_1.id = mto.tx_out_id
                  WHERE mto.id = ma.id) AS mtx
           FROM multi_asset ma
             LEFT JOIN tx_out txo ON txo.id = (( SELECT max(ma_tx_out.tx_out_id) AS max
                   FROM ma_tx_out
                  WHERE ma_tx_out.ident = ma.id))
             LEFT JOIN stake_address sa ON sa.id = txo.stake_address_id
          WHERE ma.policy::bytea = '\xf0ff48bbb7bbe9d59a40f1ce90e9e9d0ff5002ec48f232b49ca0fb9a'
        )
 SELECT handles.name,
    handles.fingerprint,
    handles.address,
    handles.stake
   FROM handles;
   ```

