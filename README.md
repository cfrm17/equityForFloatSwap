# Equity for Float Swap Valuation

An equity-for-float swap is an agreement between two counterparties to exchange the dividends and capital gains realized on an equity portfolio for a floating rate of interest.  When the reset dates for the equity leg and for the floating leg are different, a new dividend payment option is now available, where the user can specify that dividends be paid according to the floating payment dates.

The notations:

 - The time corresponding to the payment date associated with the kth floating reset period;
 - The time corresponding to the end of the kth floating reset period;
 - The time corresponding to the end of the final floating reset period;
 - The time corresponding to the ex-dividend date for the jth dividend;
 - The notional amount of the equity portfolio;
 - The notional amount of the floating leg.

Let us consider a single underlying stock for now.  Assume that the stock price S follows a geometric Brownian motion in the risk-neutral world Q such that if the given stock pay no dividends before T, then
					 .							(1)
More generally, suppose the stock is a claim to a cumulative dividend process D. (That is,   is the cumulative dividends paid by the stock up through time t.)  In this case, according to [1], we have

	 .	(2)

If we do not consider the dynamics of the interest rate, (2) becomes

	 .	(3)

Assume  , we then obtain from (3)

	 .	
		(4)
The left hand side of equation (4) is the present value (always refer to time t hereinafter) of the capital return of the stock for the period  .  In case of discrete dividends and assume that the amount and timing of the dividends during   can be predicted with certainty, the right hand of equation (4) can be written as

	 .	(5)

It can be seen from equations (4) and (5) that the present value of the capital return of the stock can be broken into two parts, one without considering dividends, and the other comprising discrete dividends only.  The latter can be regarded as the “cost of dividend”, as the stock price will fall on the ex-dividend date.  The former can also be derived as if the stock does not pay any dividends, and in this case,

	 

noting that the expected price of the stock at a future time is the forward price of the stock.  Following the derivation of equation (6) and again without considering dividends, we can derive an expected return on the underlying stock when   as follows.  By applying Ito’s Lemma on equation (1) and performing a little algebra, we have

	 .	(7)

We then obtain the expectation and variance of   from (7) and in turn obtain

	 

Therefore the present value of the capital return of the stock for the period  , where  , is

	 ,	(9)

where  ’s are the dividends going ex-dividend during the period  .

For our equity-for-float swap, two swap values are calculated: economic and replacement.  The economic value is the value of the swap to one party, while the replacement value is the dollars received/paid to offset the swap to a third party.

When we say selling a swap, we pay the return on equity and receive Libor plus a spread.  The economic value of the swap is decomposed into 4 parts: current equity (CE), future equity (FE), current interest rate (CI), and future interest rate (FI).  The value of CE is the present value of the capital gains and dividends of the underlying stock portfolio between the beginning of the first equity reset date   and the end of the first equity reset date  .  Based on the derivations above, we have

	 

where

 .	(11)

The first term in equation (11) captures the benefit of the dividend to the owner of the swap.  If the dividends are paid according to the floating reset dates,   is the dividend paid to the swap counterparty at the nearest future floating reset date that is in the period between the time t and the first equity reset period  .  In the second term of equation (11),   is the dividend for which the underlying equity will trade ex-dividend between time t and the first equity reset period  .  

The value for the future equity is

	 ,	(12)

where the summation begins at  .

The economic value of the current interest rate payment is

	 .	(13)

It is a general practice that when a particular accrual period is not specified, we use two adjoining floating payment dates for calculation of day count fraction.

The economic value of the future interest payments is obtained using the Libor curve (see https://finpricing.com/lib/IrCurve.html) and the original spread.  The forward Libor is interpolated using the adjoining floating payment dates.  The following formula is obtained

	 .	(14)

Finally, the economic value of the swap to one party is

	 .	(15)

Here we assume all the notionals are positive.

For the replacement value of an equity-for-float swap, we need use the Libor rate plus the current swap spread to replace the corresponding interest rate in above equations.  Specially, substitute   for  .  But this should be carried out on every relevant reset period.  For example, when we replace  ,  , we should use

	 .	(16)


