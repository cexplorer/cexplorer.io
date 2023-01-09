# Ranking formula

			$rank = 
			(
				(
					500 
					+ min($test['roa_lifetime'],6) * 10
					+ min($test['roa_short'],6) * 12 
					+ (min($test['pledge'],$test['pledge_active'],100000000000)/15000000000)
					+ min(40,$test['blocks_est_epoch']) / 3
					+ min(7000,$test['delegators']) / 250
					+ min(5000,$test['blocks_lifetime']) / 300
					+ $test['stake'] / 500000000000
				)
			- 
				(
					(max($test['tax_ratio'],0.03)*100 * 10) + max($test['tax_fix'],340000000)/50000000
					+ (1-$test['extended']) * 100 
					+ (1-min(1,$test['user_id'])) * 200 
					+ ((20000000000-min(20000000000,$test['pledge']))/200000000)
					+ ((max(0.95,($test['stake']/1000000)/($xd['circ']/$xd['epoch_param']['optimal_pool_count']))*100)-95)*50
				)
			)
						
			;
