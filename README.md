# Source: https://blog.bitmex.com/a-brief-history-of-stablecoins-part-1/

# Tasklist:

- [ ] Modify content for accuracy (do not change article structure)
  - [ ] Ensure content reflects "BTS Token" rather than "bitshares"
  - [ ] Describe the process for BTS Token holder to create (short) bitUSD into the smart contract (collateral ratio, etc.)
  - [ ] Describe the process for the smart contract to sell the bitUSD within the DEX market
  - [ ] Describe the process for a DEX user to purchase bitUSD from the market
  - [ ] Correct the sentiment that the "Block Producers" may influence the market and somehow benefit, rather the smart contract does this
  - [ ] Correct he omission of fact that Block Producers provide oracle price feed data from external sources, used by the smart contract
  - [ ] Describe the mechanics of the smart contract using the median feed price for various events
- [ ] Other?

# Content:

<article id="post-10813" class="post-10813 post type-post status-publish format-standard hentry category-research language-en_us">
	<header class="entry-header">
		<h1 class="entry-title">A brief history of Stablecoins (Part 1)</h1>
		<div class="entry-meta">
			<span class="posted-on"><a href="https://blog.bitmex.com/a-brief-history-of-stablecoins-part-1/" rel="bookmark"><time class="entry-date published" datetime="2018-07-02T09:17:48+00:00">2 July 2018</time><time class="updated" datetime="2018-07-08T10:14:18+00:00">8 July 2018</time></a></span><span class="byline"> <span class="author vcard"><a class="url fn n" href="https://blog.bitmex.com/author/bitmex-research/">BitMEX Research</a></span></span>		</div><!-- .entry-meta -->
	</header><!-- .entry-header -->

	<div class="entry-content">
		
		<p><b>Abstract: </b><span style="font-weight: 400">In this piece we look over the history of distributed stablecoins, focusing on two case studies, Bitshares (BitUSD) and MakerDAO (Dai). We examine the efficacy of various design choices, such as the inclusion of price oracles and pooled collateral. We conclude that while a successful stablecoin is likely to represent the holy grail of financial technology, none of the systems we have examined so far appear robust enough to scale in a meaningful way. The coins we have looked at seem to rely on “why would it trade at any other price?” type logic, to enforce price stability to some extent, although dependence on this reasoning is decreasing as technology improves.</span></p>
<p><img class="alignnone size-full wp-image-10816" src="https://blog.bitmex.com/wp-content/uploads/2018/07/Cover.jpg" alt="" width="567" height="340" srcset="https://blog.bitmex.com/wp-content/uploads/2018/07/Cover.jpg 567w, https://blog.bitmex.com/wp-content/uploads/2018/07/Cover-300x180.jpg 300w, https://blog.bitmex.com/wp-content/uploads/2018/07/Cover-210x126.jpg 210w" sizes="(max-width: 567px) 100vw, 567px"></p>
<p><b>Overview</b></p>
<p><span style="font-weight: 400">Distributed stablecoins aim to achieve both the characteristics of crypto-coins like Bitcoin (censorship resistant digital transactions) and the price stability of traditional financial assets, such as the US Dollar or gold. These systems are distinct from tokens such as </span><a href="https://blog.bitmex.com/tether/"><span style="font-weight: 400">Tether</span></a><span style="font-weight: 400">, where one entity controls a pool of US Dollar collateral, ultimately making the system centralised and thus susceptible to being shut down by the authorities. </span></p>
<p><span style="font-weight: 400">Along with the somewhat related idea of distributed exchanges, distributed stablecoins have been referred to as the “holy grail” of financial technology, due to their very strong potential benefits. In our view the transformative nature of such a technology on society would be immense, perhaps far more significant than Bitcoin or Ethereum tokens with their floating exchange rates.</p>
<p>Distributed stablecoins could have the <a href="https://blog.bitmex.com/value_proposition/">advantages of Bitcoin</a> (censorship resistance combined with the ability to transact electronically), without the difficulties of a volatile exchange rate and the challenge of encouraging users and merchants to adopt a new unknown token. Such a system is likely to be very successful and therefore it is no surprise that so many people have attempted to launch such projects:</span></p>
<p><b>List of stablecoin projects </b></p>
<table style="width: 651px">
<tbody>
<tr bgcolor="#526482">
<td width="25%"><span style="color: white"><b>Name</b></span></td>
<td width="25%"><span style="color: white"><b>Type</b></span></td>
<td width="25%"><span style="color: white"><b>Launch Date</b></span></td>
<td width="25%"><span style="color: white"><b>White paper link</b></span></td>
</tr>
<tr>
<td style="width: 173px">Bitshares (BitUSD)</td>
<td style="width: 166px"><span style="font-weight: 400">Crypto-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">21 July 2014</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/173481633-Bitshares-White-Paper.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr bgcolor="#F2F7FF">
<td style="width: 173px">Nu (NuBits)</td>
<td style="width: 166px"><span style="font-weight: 400">Crypto-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">24 Sept 2014</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/NuWhitepaper.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr>
<td style="width: 173px">Steem (SteemUSD)</td>
<td style="width: 166px"><span style="font-weight: 400">Crypto-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">19 April 2016</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/steem-whitepaper.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr bgcolor="#F2F7FF">
<td style="width: 173px">Corion</td>
<td style="width: 166px"><span style="font-weight: 400">Non-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">14 Oct 2017</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/cor.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr>
<td style="width: 173px">MakerDAO (Dai)</td>
<td style="width: 166px"><span style="font-weight: 400">Crypto-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">27 Dec 2017</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/DAI.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr bgcolor="#F2F7FF">
<td style="width: 173px">Alchemint</td>
<td style="width: 166px"><span style="font-weight: 400">Crypto-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">Sept 2018</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/AlchemintWhitePaper_EN-v0.9.2.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr>
<td style="width: 173px">BitBay</td>
<td style="width: 166px"><span style="font-weight: 400">Non-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">Sept 2018</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/bitbay-whitepaper.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr bgcolor="#F2F7FF">
<td style="width: 173px">Carbon</td>
<td style="width: 166px"><span style="font-weight: 400">Non-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">n/a</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/carbonwhitepaper.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr>
<td style="width: 173px">Basis</td>
<td style="width: 166px"><span style="font-weight: 400">Non-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">n/a</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/basis_whitepaper_en.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr bgcolor="#F2F7FF">
<td style="width: 173px">Havven</td>
<td style="width: 166px"><span style="font-weight: 400">Crypto-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">n/a</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/havven_whitepaper.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
<tr>
<td style="width: 173px">Seignoriage Shares</td>
<td style="width: 166px"><span style="font-weight: 400">Non-collateralized</span></td>
<td style="width: 161px"><span style="font-weight: 400">n/a</span></td>
<td style="width: 151px"><a href="https://blog.bitmex.com/wp-content/uploads/2018/06/A-Note-on-Cryptocurrency-Stabilisation-Seigniorage-Shares.pdf"><span style="font-weight: 400">White paper</span></a></td>
</tr>
</tbody>
</table>
<p><span style="font-weight: 400">The technical challenges involved in creating such systems are often underestimated. Indeed constructing a distributed stablecoin system, which is robust enough to withstand cycles or the turbulence and volatility linked to financial markets may be almost impossible. For instance perhaps most forms of fiat money, even the US Dollar itself, have not even achieved that, with credit cycles putting US Dollar bank deposits at risk. A stablecoin system which builds on top of the US Dollar is therefore never going to be more reliable than traditional banking, in our view.</span></p>
<p><span style="font-weight: 400">In economics there is a concept of money supply, with risk and the potential inflationary impact increasing as the number of layers increase. One could add this stablecoin systems on top, as a new high risk layer:</span></p>
<ul>
<li style="font-weight: 400"><span style="font-weight: 400">M0 – Notes &amp; coins plus deposits at the central banks </span></li>
<li style="font-weight: 400"><span style="font-weight: 400">M1 – Money on deposit in a bank current account (including M0)</span></li>
<li style="font-weight: 400"><span style="font-weight: 400">M2 – Money on deposit in a bank savings account (including M1)</span></li>
<li style="font-weight: 400"><span style="font-weight: 400">M3 – Money in a money market account (including M2)</span></li>
<li style="font-weight: 400"><span style="font-weight: 400">MZM – Money in all financial assets redeemable on demand (including M3)</span></li>
<li style="font-weight: 400"><span style="font-weight: 400">MSC (Synthetic Crypto Money) – Money inside synthetic crypto stablecoin systems &nbsp;(including MZM)</span></li>
</ul>
<p><span style="font-weight: 400">However advanced or sophisticated the distributed stablecoin technology is, we believe the token is likely to be less robust than the layers above it in the money supply tree.</span></p>
<p><span style="font-weight: 400">In this piece we review some of the most prominent and interesting attempts at building these synthetic US Dollar type systems. BitUSD in 2014 and then a more recent project, MakerDAO (Dai).</span></p>
<p>&nbsp;</p>
<p style="text-align: center"><span style="text-decoration: underline"><b>Case study 1: Bitshares (BitUSD) – 2014</b></span></p>
<table>
<tbody>
<tr bgcolor="#526482">
<td width="40%"><span style="color: white"><b>Factbox</b></span></td>
<td width="60%"></td>
</tr>
<tr>
<td><span style="font-weight: 400">Coin Name</span></td>
<td><span style="font-weight: 400">BitUSD</span></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">Launch Date</span></td>
<td><span style="font-weight: 400">21 July 2014 </span></td>
</tr>
<tr>
<td><span style="font-weight: 400">Crypto collateral</span></td>
<td><span style="font-weight: 400">Yes</span></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">Price feed publishers</span></td>
<td><span style="font-weight: 400">Yes</span></td>
</tr>
</tbody>
</table>
<p><span style="font-weight: 400">We'll first discuss BitUSD which is one of many available stablecoins (<a href="http://docs.bitshares.org/bitshares/user/mpa.html#collateralized-tokens">Market Pegged Assets</a>) which operate on-top of the Bitshares platform.</span> Bitshares is a Delegated-Proof-of-Stake (DPOS) blockchain based decentralized exchange (DEX) which offers next generation trading performance and the tools for anyone to create their own User Issued Assets (<a href="http://docs.bitshares.org/bitshares/user/uia.html">UIAs</a>), Market Pegged Assets (like <a href="http://open-explorer.io/#/assets/USD">bitUSD</a>, <a href="http://open-explorer.io/#/assets/CNY">bitCNY</a>, <a href="http://open-explorer.io/#/assets/HERO">HERO</a>, etc..), prediction markets and a large reserve pool of Bitshares available to workers and witnesses given sufficient network consensus.</p>
<p><span style="text-decoration: underline"><span style="font-weight: 400">BitUSD System dynamics</span></span></p>
<table>
<tbody>
<tr bgcolor="#526482">
<td width="30%"><span style="color: white"><b>Pools of Funds</b></span></td>
<td width="70%"><span style="color: white"><b>Description</b></span></td>
</tr>
<tr>
<td><span style="font-weight: 400">Bitshares</span></td>
<td><span style="font-weight: 400">The native currency of the Bitshares platform</span></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">Bitshares held as collateral</span></td>
<td><span style="font-weight: 400">Separate pools of Bitshares held as stablecoin backing collateral.</span></td>
</tr>
<tr>
<td><span style="font-weight: 400">BitUSD</span></td>
<td><span style="font-weight: 400">The stable token, designed to track the value of the US Dollar</span></td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<table>
<tbody>
<tr bgcolor="#526482">
<td width="30%"><span style="color: white"><b>Groups of Participants</b></span></td>
<td width="70%"><span style="color: white"><b>Description</b></span></td>
</tr>
<tr>
<td><span style="font-weight: 400">BitUSD holders</span></td>
<td><span style="font-weight: 400">Investors and users of the BitUSD stable coin. Holders of BitUSD are able to redeem the tokens for the Bitshares held in collateral.</span></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">BitUSD creators</span></td>
<td><span style="font-weight: 400">Those that create new BitUSD, by selling it into the market (creating new loans), by posting Bitshares as collateral. This loan may be for a small period of time, after which it needs to be rolled over or have its collateral topped up to the initial margin level.</span></td>
</tr>
<tr>
<td><span style="font-weight: 400">Traders</span></td>
<td><span style="font-weight: 400">Those trading bitUSD for any asset issued on the BTS DEX, and vica versa. There are no trading pair limitations for bitUSD.</span></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">Block producers</span></td>
<td><span style="font-weight: 400">Bitshares block producers have no influence over the <a href="http://docs.bitshares.org/bitshares/user/mpa.html#collateralized-tokens">Market Pegged Asset</a> smart contract. The smart contract enforces the minimum backing collateral and will force settle under collateralized short positions (below 175%) after a short delay. Similarly, the smart contract handles the exchange of settled bitUSD in return for backing BTS tokens.</span></td>
</tr>
<tr>
<td><span style="font-weight: 400">Price feed publishers</span></td>
<td><span style="font-weight: 400">All active <a href="http://docs.bitshares.org/bitshares/user/mpa.html#collateralized-tokens">MPA</a> on the BTS DEX have price feed publishers who frequently publish the latest asset value in the backing collateral asset's value. These publishers can be the Bitshares committee members, the Bitshares witnesses or 25 private price feed publishers for private MPA.</span></td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<table>
<tbody>
<tr bgcolor="#526482">
<td width="25%"><span style="color: white"><b>Price Stability Mechanisms</b></span></td>
<td width="25%"><span style="color: white"><b>Price Direction</b></span></td>
<td width="50%"><span style="color: white"><b>Description</b></span></td>
</tr>
<tr>
<td><span style="font-weight: 400">Price feeds</span></td>
<td><span style="font-weight: 400">Both directions</span></td>
<td><span style="font-weight: 400">Bitshares MPA have a price feed mechanism which uses the median published price feed (from a set of many price feed publishers) as the feed price. There are approx 27 price feed publishers for bitUSD currently.</span></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">BitUSD redemption (indirect)</span></td>
<td><span style="font-weight: 400">Positive</span></td>
<td><span style="font-weight: 400">Should the value of the collateral currency (Bitshares) fall, any BitUSD holder can redeem the BitUSD and obtain $1 worth of Bitshares, assuming the market price of BitUSD is still worth $1 and there is sufficient Bitshares held in collateral.</span><p></p>
<p><span style="font-weight: 400">This stability mechanism protects the integrity of the system only in the event that the value of Bitshares falls and the BitUSD market price remains at $1. It does not directly stabilize the price of BitUSD around $1, in our view. If the price of BitUSD deviates from $1, this mechanism may not help correct the price.</span></p>
<p>In our view, it is important to draw the distinction between a mechanism designed to protect the value of collateral and that of a mechanism which directly causes the price of the stablecoin to converge.</p></td>
</tr>
</tbody>
</table>
<p><span style="text-decoration: underline"><span style="font-weight: 400">Weaknesses</span></span></p>
<p><b>Exposure to a fall in the value of collateral</b><span style="font-weight: 400"> – Bitshares was a new, untested and low value asset, and therefore its value was volatile. If the value of the token falls by 50% sharply, in a period spanned by one of the loans used to create BitUSD, there may be insufficient collateral and the peg could fail.</span></p>

<p><span style="text-decoration: underline"><span style="font-weight: 400">Conclusion</span></span></p>
<p><span style="font-weight: 400">The supply of bitUSD is significantly lower than that available in Tether, and at times of high volatility the market has traded slightly above|below the price feed rate rather than hold the true $1.00 peg. There are endless possibilities for new MPA on the BTS DEX, so keep an eye on future Bitshares community developments.</span></p></p>

<p style="text-align: center"><span style="text-decoration: underline"><span style="font-size: 11pt"><b>Case Study 2: MakerDAO (Dai) – 2017</b></span></span></p>
<table>
<tbody>
<tr bgcolor="#526482">
<td width="40%"><span style="color: white"><b>Factbox</b></span></td>
<td width="60%"></td>
</tr>
<tr>
<td><span style="font-weight: 400">Coin Name</span></td>
<td><span style="font-weight: 400">Dai</span></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">Launch Date</span></td>
<td><span style="font-weight: 400">27 Dec 2017</span></td>
</tr>
<tr>
<td><span style="font-weight: 400">Crypto Collateralized</span></td>
<td><span style="font-weight: 400">Yes</span></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">Price Oracles</span></td>
<td><span style="font-weight: 400">Yes (indirect)</span></td>
</tr>
</tbody>
</table>
<p>The next stablecoin we look at is Dai, which exists on the Ethereum platform. This system is highly complex, with four relevant pools of funds and six possible stability mechanisms. There are currently around <a href="https://dai.makerdao.com/">$50 million</a> worth of Dai in issuance and the peg seems to be holding up reasonably well.</p>
<p><span style="text-decoration: underline"><span style="font-weight: 400">System dynamics</span></span></p>
<table style="height: 305px">
<tbody>
<tr style="height: 20px" bgcolor="#526482">
<td style="height: 20px" width="30%"><span style="color: white"><b>Pools of Funds</b></span></td>
<td style="height: 20px" width="70%"><span style="color: white"><b>Description</b></span></td>
</tr>
<tr style="height: 40px">
<td style="height: 40px"><span style="font-weight: 400">Ethereum</span></td>
<td style="height: 40px"><span style="font-weight: 400">Ethereum is the native token of the Blockchain platform used for Maker &amp; Dai</span></td>
</tr>
<tr style="height: 61px" bgcolor="#F2F7FF">
<td style="height: 61px"><span style="font-weight: 400">Pooled Ethereum</span></td>
<td style="height: 61px"><span style="font-weight: 400">Ethereum is placed in pools used as collateral for issuance of the Dai token. These are often referred to a collateralized debt positions (CDPs)</span></td>
</tr>
<tr style="height: 61px">
<td style="height: 61px"><span style="font-weight: 400">Dai</span></td>
<td style="height: 61px"><span style="font-weight: 400">Dai is an ERC-20 token that is generated by collateralizing pooled Ether. Dai is the stablecoin token, designed to be valued at $1.</span></td>
</tr>
<tr style="height: 123px" bgcolor="#F2F7FF">
<td style="height: 123px"><span style="font-weight: 400">Maker</span></td>
<td style="height: 123px"><span style="font-weight: 400">The Maker token is MakerDAO’s governance token. It is used to vote on various initiatives that pertain to the stability of the ecosystem. It is also mandatory to possess during the collateral unlocking process. During such a process, a stability fee is garnered from the user, where payment is accepted exclusively in Maker. Maker is also an ERC-20 token.</span></td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<table style="height: 552px">
<tbody>
<tr style="height: 20px" bgcolor="#526482">
<td style="height: 20px" width="30%"><span style="color: white"><b>Groups of Participants</b></span></td>
<td style="height: 20px" width="70%"><span style="color: white"><b>Description</b></span></td>
</tr>
<tr style="height: 61px">
<td style="height: 61px"><span style="font-weight: 400">Dai Creators</span></td>
<td style="height: 61px"><span style="font-weight: 400">An individual who sends Ethereum to a smart contract, locking up Ethereum in exchange for Dai. These people are also known as CDP owners.</span></td>
</tr>
<tr style="height: 40px" bgcolor="#F2F7FF">
<td style="height: 40px"><span style="font-weight: 400">Dai Holder/User</span></td>
<td style="height: 40px"><span style="font-weight: 400">A Dai holder may or may not be a Dai creator. They may invest in or use the Dai stablecoin token.</span></td>
</tr>
<tr style="height: 82px">
<td style="height: 82px"><span style="font-weight: 400">Maker Token Holders</span></td>
<td style="height: 82px"><span style="font-weight: 400">Maker token holders vote on several functions and parameters of the MakerDAO system. They manage aspects such as stability fees and liquidation ratios, as well as having responsibility to nominate other groups.</span></td>
</tr>
<tr style="height: 61px" bgcolor="#F2F7FF">
<td style="height: 61px"><span style="font-weight: 400">Keepers</span></td>
<td style="height: 61px"><span style="font-weight: 400">These traders monitor the Dai collateral and if it falls to an insufficient level, purchase the collateral in an open auction, by spending Dai.</span></td>
</tr>
<tr style="height: 227px">
<td style="height: 227px"><span style="font-weight: 400">Oracles</span></td>
<td style="height: 227px"><span style="font-weight: 400">Price feed producers submit price information that is aggregated and used to select a given price for both Maker and Ethereum (but not Dai itself). These agents are nominated by MakerDAO token holders.</span><p></p>
<p><span style="font-weight: 400">In order to prevent manipulation, there is a one hour lag between the price publication and when it impacts the system. In addition to this a median type mechanism is used to select the price, which involves ignoring the highest and lowest prices. In our view this may not prove to be robust enough if the oracles have a conflict of interest and try to engage in manipulation.</span></p></td>
</tr>
<tr style="height: 61px" bgcolor="#F2F7FF">
<td style="height: 61px"><span style="font-weight: 400">Global settlers</span></td>
<td style="height: 61px"><span style="font-weight: 400">This is another group nominated by the MakerDAO token holders. This group can unwind the entire Dai system, by giving Dai holders the right to redeem their collateral at a fixed price.</span></td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<table>
<tbody>
<tr bgcolor="#526482">
<td width="25%"><span style="color: white"><b>Price Adjustment Mechanics</b></span></td>
<td width="25%"><span style="color: white"><b>Price Direction</b></span></td>
<td width="50%"><span style="color: white"><b>Description</b></span></td>
</tr>
<tr>
<td><span style="font-weight: 400">Dai Redemption</span></td>
<td><span style="font-weight: 400">Positive</span></td>
<td><span style="font-weight: 400">The primary stability mechanism is the ability, in theory, to redeem Dai for $1 worth of Ethereum. Redemption can only be conducted by CDP owners (unless there is insufficient collateral). If the price of Dai falls, CDP owners need to either use Dai they currently hold or buy it in the market, and then they can redeem/delete Dai for $1 worth of Ethereum based on the price feed provided by the price oracles.</span></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">Dai Creation</span></td>
<td><span style="font-weight: 400">Negative</span></td>
<td><span style="font-weight: 400">To complement the Dai redemption process, the mechanism to prevent the price of Dai climbing too high, is the ability of Ethereum holders to create new Dai, by placing Ethereum inside of CDPs.</span></td>
</tr>
<tr>
<td><span style="font-weight: 400">Target rate (Not active)</span></td>
<td><span style="font-weight: 400">Both directions</span></td>
<td><span style="font-weight: 400">There is a “Target Rate Feedback Mechanism” (TRFM), which appears to be another price stability mechanism in the system. However, it is not yet active nor have several specifications of the mechanism been worked out yet.</span><p></p>
<p><span style="font-weight: 400">The the idea is that a target rate is set by the MakerDAO token holders. The target rate is essentially a spread which applies to the creation or redemption of Dai, designed to correct the price.</span></p></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">CDP liquidation (indirect)</span></td>
<td><span style="font-weight: 400">Positive</span></td>
<td><span style="font-weight: 400">There is a mechanism by which traders/keepers can redeem the Ethereum collateral held by another CDP. This can only occur if the value of this collateral falls to an insufficient level to backup the Dai, in this case 150% of the value of Dai. This should incentivise CDP owners to keep topping up their CDPs to ensure there is a large buffer of Ethereum.</span><p></p>
<p><span style="font-weight: 400">This is a necessary mechanism to ensure the integrity of the system and ensure the value of the collateral is always sufficient. However it is not clear if this directly keeps the value of Dai at $1. This mechanism can be thought of as a building block on the stability mechanism, which merely ensures the level of collateral is sufficient. Other redemption systems are needed to make this meaningful, in our view.</span></p></td>
</tr>
<tr>
<td><span style="font-weight: 400">Global Settlement</span></td>
<td><span style="font-weight: 400">Positive</span></td>
<td><span style="font-weight: 400">This mechanism can be triggered at any time. The triggering essentially gives all Dai holders an option to convert back to a fixed value of Ethereum, worth $1 according to the oracle price feed, at the time of the triggering (or whatever price is possible given the total level of collateral in the system). The difference between this and normal redemption, is that the price is fixed and its open to all Dai token holders and not paired to a particular CDP.</span><p></p>
<p><span style="font-weight: 400">The idea is that this mechanism can be used as a threat against CDP holders, to ensure they keep redeeming Dai in the event the price falls, rather than holding out for an even lower price.</span></p>
<p><span style="font-weight: 400">Global settlement can also be used in the event of bugs or other emergencies.</span></p></td>
</tr>
<tr bgcolor="#F2F7FF">
<td><span style="font-weight: 400">MakerDAO token issuance (indirect)</span></td>
<td><span style="font-weight: 400">Positive</span></td>
<td><span style="font-weight: 400">MakerDAO token holders act as the buyer of last resort. If the collateral (pooled Ethereum) in the system were to drop below 100% collateralization, MakerDAO is automatically created and auctioned on the open market to raise additional funds to collateralize the system. Hence, if the system becomes undercollateralized, Maker holders absorb the damage.</span><p></p>
<p>Again this mechanism protects the value of collateral, but does not directly help the price of Dai converge to $1, in our view.</p></td>
</tr>
</tbody>
</table>
<p><span style="text-decoration: underline"><span style="font-weight: 400">Analysis of the core stability mechanism – Dai redemption</span></span></p>
<p><span style="font-weight: 400">The primary stability mechanisms appear to be the ability of CDP owners to redeem if the price of Dai is too low and for people to create new Dai if the price is too high. For example if the price of Dai falls to 80 cent, CDP owners could purchase Dai in the market and redeem it, unlocking $1 worth of Ethereum and making a nice profit. This is how the system should work under normal circumstances.</span></p>
<p><span style="font-weight: 400">The above appears to be a robust stability mechanism which should keep the price of Dai at or near $1. However, the theory may only work if CDP owners expect the price of Dai to correct back to $1. If the price of Dai has fallen to 80 cent, CDP owners may be reluctant to redeem if they expect the Dai price to fall further to 60 cent, as such a price would enable them to make even more profit. There is no guarantee that once the price reaches 80 cent, it won’t continue to fall.</span></p>
<p><span style="font-weight: 400">Therefore the stability mechanism could depend somewhat on the power dynamics between two groups, Dai owners and CDP owners. These two groups are essentially trading against each other in the market, Dai owners are selling of Dai and CDP owners are the potential buyers. If the power balance shifts towards CDP owners, such that they are well capitalised, patient, collaborative and determined, this group could outmaneuver the Dai token holders, drive the price down, and then buy it back and make a large profit. This may seem unlikely, but in our view the stability mechanism may not work in all market scenarios. Although we consider Dai as superior to BitUSD, in some limited ways, the Dai peg relies on market psychology and investor expectations, in the same way as BitUSD. Therefore the Dai peg is also weak and unlikely to scale.</span></p>
<p><span style="font-weight: 400">The global settlement system can mitigate the above risk. If CDP owners are successfully manipulating the price of Dai down too far, this could trigger global settlement. Dai holders would then get around $1 of Ethereum back. Therefore the threat of global settlement may keep the price of Dai up. However again the effectiveness of this threat depends on the determination of the various groups, the CDP owners, MakerDAO token holders and global settlement activators.</span></p>
<p><span style="text-decoration: underline">Conclusion</span></p>
<p>We consider Dai to be one of the most sophisticated and advanced stablecoins systems which has been produced so far. In our view, when digging into Dai’s stability mechanisms, there is no one powerful mechanism which ensures stability. Instead we have a complex network of systems, which to some extent reference each other and use circular logic.&nbsp;&nbsp;One could claim this complexity was created to obfuscate the lack of a strong and clear stability mechanism, but it is more likely to be an indication of an experimental trial and error type approach to the design of the system.</p>
<p>Therefore the system is still reliant on investor expectations and psychology, although to a lesser extent than the BitUSD. While&nbsp;the stability systems in place could work, at least for a while, we think they are not robust enough to withstand market turmoil or some types of power imbalances between Dai holders and CDP owners. Therefore, the search for the holy grail continues.</p>
<p><img class="alignnone size-full wp-image-10820" src="https://blog.bitmex.com/wp-content/uploads/2018/07/dai.png" alt="" width="812" height="400" srcset="https://blog.bitmex.com/wp-content/uploads/2018/07/dai.png 812w, https://blog.bitmex.com/wp-content/uploads/2018/07/dai-300x148.png 300w, https://blog.bitmex.com/wp-content/uploads/2018/07/dai-768x378.png 768w, https://blog.bitmex.com/wp-content/uploads/2018/07/dai-210x103.png 210w" sizes="(max-width: 812px) 100vw, 812px"></p>
<p>&nbsp;</p>
			</div><!-- .entry-content -->

	<footer class="entry-footer">
		<span class="update">Updated: <a href="https://blog.bitmex.com/a-brief-history-of-stablecoins-part-1/" rel="bookmark"><time class="published updated" datetime="2018-07-08T10:14:18+00:00">8 July 2018</time></a></span><br><span class="cat-links">Categories: <a href="https://blog.bitmex.com/category/research/?lang=en_us" title="View all posts in Research" rel="category tag">Research</a></span>	</footer><!-- .entry-footer -->
</article>
