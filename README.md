Download Link: https://assignmentchef.com/product/solved-mm621-tma937-project-1-nonlinear-optimization
<br>
In this project we want to study the gas network that was used in Belgium in the 1990s and see if there are ways to improve it by maintaining requirements meanwhile lowering costs. Since Belgium does not have any internal gas resources within the country they rely on importing gas from other countries, specifically the countries Algeria and Norway during this time. A relevant question was how much gas they should buy from respective country so that they fullfilled all of its demand in respective town in terms of having an interval of minimal and maximum requirement of gas imported to each town. We also need to consider additional requirements such as having a specific gas pressure, and we also wish to find out more concretely how much gas should be sent from which towns.

We make a distinction between supply, demand and intermediate towns or nodes. Supply nodes are simply the ones where the gas is bought from either Algeria or Norway and sent to other towns. Demand nodes requires a certain amount of gas which will be used and intermediate nodes are simply the towns where the gas will pass through. We also make a dinstiction between active and passive edges, where in passive edges, i.e the pipes between towns, gas can be transported both ways whereas active edges specify a direction. A relevant map of the direction of the gas flow and the types of towns (supply, demand or intermediate) is shown in Fig. 1.




Figure 1: Figure of the gas flow of the towns. Orange, pink and blue nodes correspond to intermediate, demand and supply towns, respectively. The arrows show the direction of the gas flow.

<h1><a name="_Toc12320"></a>1           Model description</h1>

We start with defining the <strong>sets </strong>for our model:

<em>I </em>= {All towns represented by Table 1}

<em>P </em>= {All passive edges defined in Table 2}

<em>A </em>= {All active edges defined in Table 3}

<em>E </em>= {All edges} = {<em>P </em>∪ <em>A</em>}

And the <strong>parameters </strong>of our model

<em>L<sub>ij </sub></em>= ”Length in km of the pipe between town i and town <em>j</em>. Found in Table 2 and Table 3”

<em>D<sub>ij </sub></em>= ”Interior diameter of the pipe in mm between town <em>i </em>and town <em>j</em>. Found in Table 2 and Table 3”

= ”Minimum quantity of 10<sup>6</sup><em>m</em><sup>3 </sup>gas / day to town <em>j</em>. Found in Table 1”

= ”Maximum quantity of 10<sup>6</sup><em>m</em><sup>3 </sup>gas / day to town <em>j</em>. Found in Table 1”

= ”Minimum pressure in bar in town <em>j</em>. Found in Table 1”

= ”Maximum pressure in bar in town <em>j</em>. Found in Table 1” <em>c<sub>j </sub></em>= ”Cost in [$<em>/m</em><sup>3</sup>] to buy to town <em>j </em>defined in Table 1”

<em>K </em>= ”Constant to convert BTU to <em>m</em><sup>3</sup>”

<em>z </em>= ”Gas compressibility factor”

Lastly the <strong>variables </strong>for our model will be

<em>f<sub>ij </sub></em>= ”Flow of gas from town i to town j” <em>x<sub>j </sub></em>= ”Net result of gas in 10<sup>6</sup><em>m</em><sup>3 </sup>/ day to town j” <em>p<sub>j </sub></em>= ”Pressure of gas in bar in town j”

And the following numerical constants:

(1)

Now we are ready to define our actual model to solve the problem introduced in Section 1. We start with the obvious which is that our objective is to minimize the cost. We know that the only places where it is possible to buy is to two towns, which is illustrated in Table 1 as the cost equal zero where gas cannot be purchased. This objective corresponds to:

minimize <sup>X</sup><em>Kc<sub>j</sub>x<sub>j             </sub></em>(2) <em>x</em>∈<em>I j</em>∈<em>I</em>

where K is simply a constant the converts the price to <em>m</em><sup>3</sup>.

We also realize that depending on the town is a supply, demand or intermediate node the net result of the gas flow will change. If it is a supply town then gas will be flowing out from this town which we count as a positive net result of gas flow. Conversely, a demand node will take in more gas than it leaves, resulting in a net negative gas flow from a demand node. Lastly, the net in/out flow from an intermediate node will simply be zero. This is all shown in Table 1. For example, in intermediate nodes the minimum and maximum quantity are both zero, signifying that the gas quantity that enters the town also goes out. We let the relation of how much gas goes out subtracted from how much gas goes in to a specific town j (i.e the net result) be defined by

<em>x</em><em>j </em>= X<em>f</em><em>ji </em>− X<em>f</em><em>ij, </em>∀<em>j </em>∈ <em>I                                                                                           </em>(3)

<em>i</em>∈<em>I                      i</em>∈<em>I</em>

Next we know that <em>x<sub>j </sub></em>should be between a minimum and a maximum quantity, and similarly for the pressure of the gas <em>p<sub>j</sub></em>.

Depending if the edge is passive or active we have different restrictions on the flow, most noticeably is that the flow can only go one direction in an active edge. The flow from a town <em>i </em>to <em>j </em>also depends on the pressure of the gas in both of these towns as well as specifics of the pipe measurements (Table 2 and Table 3. With the most important details covered we present the entire model.

<table width="123">

 <tbody>

  <tr>

   <td width="66">minimize <em>x</em>∈<em>I </em>s.t.</td>

   <td width="57">X<em>Kc</em><em>jx</em><em>j</em><em>j</em>∈<em>I</em></td>

  </tr>

 </tbody>

</table>

<em>I</em>

<em>i</em>∈<em>I                     i</em>∈

<em>x</em><em>j                     </em>≥                   <em>q</em><em>jmin, </em>∀<em>j </em>∈

<em>p</em><em>j                     </em>≥                 <em>p</em><em>minj   , </em>∀<em>j </em>∈

<em>P</em>

<table width="236">

 <tbody>

  <tr>

   <td width="67">|<em>f</em><em>ij</em>| · <em>f</em><em>ij</em></td>

   <td width="24">≥</td>

   <td width="146"><em>C<sub>ij</sub></em><sup>2 </sup>(<em>p</em><sup>2</sup><em><sub>i </sub></em>− <em>p</em><sup>2</sup><em><sub>j</sub></em>)<em>, </em>∀ (<em>i,j</em>) ∈ <em>A</em></td>

  </tr>

  <tr>

   <td width="67"><em>f</em><em>ij</em></td>

   <td width="24">≥</td>

   <td width="146">0<em>, </em>(<em>i,j</em>) ∈ <em>A</em></td>

  </tr>

  <tr>

   <td width="67"><em>f</em><em>ij</em></td>

   <td width="24">=</td>

   <td width="146">0<em>, </em>(<em>i,j</em>) 6∈ <em>E</em></td>

  </tr>

 </tbody>

</table>

<h1><a name="_Toc12321"></a>2           Appendix</h1>

Table 1: Table of constants for town <em>j </em>in set <em>I</em>

<table width="394">

 <tbody>

  <tr>

   <td width="65"><em>Town j</em></td>

   <td width="93"><strong>Town name</strong></td>

   <td width="53"><em>q</em><em>jmin</em></td>

   <td width="53"><em>q</em><em>jmax</em></td>

   <td width="44"><em>p</em><em>min</em><em><sub>j</sub></em></td>

   <td width="45"><em>p</em><em>max</em><em><sub>j</sub></em></td>

   <td width="40"><em>c<sub>j</sub></em></td>

  </tr>

  <tr>

   <td width="65">1</td>

   <td width="93">Zeebrugge</td>

   <td width="53">8.870</td>

   <td width="53">11.594</td>

   <td width="44">0</td>

   <td width="45">77</td>

   <td width="40">2.28</td>

  </tr>

  <tr>

   <td width="65">2</td>

   <td width="93">Brugge</td>

   <td width="53">−∞</td>

   <td width="53">-3.918</td>

   <td width="44">30</td>

   <td width="45">80</td>

   <td width="40">0</td>

  </tr>

  <tr>

   <td width="65">3</td>

   <td width="93">Zomergem</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="44">0</td>

   <td width="45">80</td>

   <td width="40">0</td>

  </tr>

  <tr>

   <td width="65">4</td>

   <td width="93">Antwerpen</td>

   <td width="53">−∞</td>

   <td width="53">-4.034</td>

   <td width="44">30</td>

   <td width="45">80</td>

   <td width="40">0</td>

  </tr>

  <tr>

   <td width="65">5</td>

   <td width="93">Gent</td>

   <td width="53">−∞</td>

   <td width="53">-5.256</td>

   <td width="44">30</td>

   <td width="45">80</td>

   <td width="40">0</td>

  </tr>

  <tr>

   <td width="65">6</td>

   <td width="93">Voeren</td>

   <td width="53">20.344</td>

   <td width="53">22.012</td>

   <td width="44">50</td>

   <td width="45">66.2</td>

   <td width="40">1.68</td>

  </tr>

  <tr>

   <td width="65">7</td>

   <td width="93">Li`ege</td>

   <td width="53">−∞</td>

   <td width="53">-6.365</td>

   <td width="44">30</td>

   <td width="45">66.2</td>

   <td width="40">0</td>

  </tr>

  <tr>

   <td width="65">8</td>

   <td width="93">Warnant</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="44">0</td>

   <td width="45">66.2</td>

   <td width="40">0</td>

  </tr>

  <tr>

   <td width="65">9</td>

   <td width="93">Namur</td>

   <td width="53">−∞</td>

   <td width="53">-2.120</td>

   <td width="44">0</td>

   <td width="45">66.2</td>

   <td width="40">0</td>

  </tr>

  <tr>

   <td width="65">10</td>

   <td width="93">Mons</td>

   <td width="53">−∞</td>

   <td width="53">-6.848</td>

   <td width="44">0</td>

   <td width="45">66.2</td>

   <td width="40">0</td>

  </tr>

  <tr>

   <td width="65">11</td>

   <td width="93">Sinsin</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="44">0</td>

   <td width="45">63</td>

   <td width="40">0</td>

  </tr>

  <tr>

   <td width="65">12</td>

   <td width="93">Arlon</td>

   <td width="53">−∞</td>

   <td width="53">-0.222</td>

   <td width="44">0</td>

   <td width="45">66.2</td>

   <td width="40">0</td>

  </tr>

 </tbody>

</table>

Table 2: Set of passive edges <em>P</em>

<table width="299">

 <tbody>

  <tr>

   <td width="79"><strong>From</strong></td>

   <td width="77"><strong>To</strong></td>

   <td width="79"><strong>Diameter</strong></td>

   <td width="63"><strong>Length</strong></td>

  </tr>

  <tr>

   <td width="79"><em>Zeebrugge</em></td>

   <td width="77"><em>Brugge</em></td>

   <td width="79">890.0</td>

   <td width="63">12</td>

  </tr>

  <tr>

   <td width="79"><em>Brugge</em></td>

   <td width="77"><em>Zomergem</em></td>

   <td width="79">890.0</td>

   <td width="63">26</td>

  </tr>

  <tr>

   <td width="79"><em>Antwerpen</em></td>

   <td width="77"><em>Gent</em></td>

   <td width="79">590.1</td>

   <td width="63">39</td>

  </tr>

  <tr>

   <td width="79"><em>Gent</em></td>

   <td width="77"><em>Zomergem</em></td>

   <td width="79">590.1</td>

   <td width="63">14</td>

  </tr>

  <tr>

   <td width="79"><em>Zomergem</em></td>

   <td width="77"><em>Mons</em></td>

   <td width="79">890.0</td>

   <td width="63">75</td>

  </tr>

  <tr>

   <td width="79"><em>Mons</em></td>

   <td width="77"><em>Namur</em></td>

   <td width="79">890.0</td>

   <td width="63">55</td>

  </tr>

  <tr>

   <td width="79"><em>Namur</em></td>

   <td width="77"><em>Warnant</em></td>

   <td width="79">890.0</td>

   <td width="63">42</td>

  </tr>

  <tr>

   <td width="79"><em>Voeren</em></td>

   <td width="77"><em>Li`ege</em></td>

   <td width="79">890.0</td>

   <td width="63">22</td>

  </tr>

  <tr>

   <td width="79"><em>Li`ege</em></td>

   <td width="77"><em>Warnant</em></td>

   <td width="79">590.1</td>

   <td width="63">25</td>

  </tr>

  <tr>

   <td width="79"><em>Sinsin</em></td>

   <td width="77"><em>Arlon</em></td>

   <td width="79">315.5</td>

   <td width="63">98</td>

  </tr>

 </tbody>

</table>

Table 3: Set of active edges <em>A</em>

<table width="265">

 <tbody>

  <tr>

   <td width="70"><strong>From</strong></td>

   <td width="53"><strong>To</strong></td>

   <td width="79"><strong>Diameter</strong></td>

   <td width="63"><strong>Length</strong></td>

  </tr>

  <tr>

   <td width="70"><em>Warnant</em></td>

   <td width="53"><em>Sinsin</em></td>

   <td width="79">315.5</td>

   <td width="63">40</td>

  </tr>

 </tbody>

</table>


