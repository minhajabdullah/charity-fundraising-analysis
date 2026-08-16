# Charity Fundraising Analysis
Analyzing a fundraising dataset to evaluate data quality, supporter behaviour, and fundraising performance.<br/><br/>
**Skills:** Data Cleaning, Data Visualization, Data Analysis. <br>
**Tools:** Microsoft Excel, Microsoft Powerpoint.

## Scenario
The fundraising team from an environmental charity would like to understand more about the quality of their data, the supporters they have and their giving behaviour, and the performance of the charity’s fundraising activities. My task is to explore the data, analyse and extract key insights from the data and present my findings.

| Term | Definition & Clarification |
| :- | :- |
| Fund | An allocation of funds to a particular purpose, ie. how that money can be spent by the charity. |
| Campaign | A broad categorisation of fundraising activities. A single Campaign can have multiple Appeals associated with it. |
| Appeal | A more granular categorisation of fundraising activities. Each Appeal is associated with one Campaign. |

> [!NOTE]
> The dataset was provided with limited context, based only on the information outlined in this section.

## Analysis
### 1. Methodology
>_Tools used and their applications_

#### 1.1 Usage of Excel
|  |  |
| :- | :- |
| Why? | <li>Familiarity and comfort over SQL</li><li>Alternatives better suited for other purposes</li> |
| How? | <li>Usage of Power Pivot add-on</li><li>Utilizing Pivot Tables for analysis and visuals’ creation</li><li>Using helper columns and formulas where necessary</li> |
|  |  |

#### 1.2 Data Cleaning
|  |  |
| :- | :- |
| Dates in Transactions[date] not in standardized form | <li>8th Apr 2025</li><li>16th Mar 2025</li> |
| Data Type Conversion from ‘Text’ to ‘Currency’ | <li>Campaigns[goal_amount]</li><li>Appeals[goal_amount]</li><li>Transactions[amount]</li> |
|  |  |

#### 1.3 Relationships between tables
| Table 1 | Cardinality | Filter Direction | Table 2 |
| :- | :- | :- | :- | 
| transactions[appeal_id] | Many to One | << To transactions | appeals[appeal_id] | 
| transactions[campaign_id] | Many to One | << To transactions | campaigns[campaign_id] |
| transactions[fund_id] | Many to One | << To transactions | funds[fund_id] | 
| transactions[supporter_id] | Many to One | << To transactions | supporters[constituent_id] | 

Establishing correct relationships –
* Allows pivot tables to connect and aggregate data seamlessly across multiple tables.
* Ensure data accuracy and consistency in analysis.

---
### 2. Supporter Insights

#### 2.1 Demographics
<img src="images/2.1%20Demographics.png">

#### 2.2 Donor Behaviour
<img src="images/2.2%20Donor%20Behaviour.png">

> [!IMPORTANT]
> Donors with at least two donations, including one in 2024 or later, are considered regular.

#### 2.3 Preferred Payment Methods
<img src="images/2.3%20Preferred%20Payment%20Methods.png">

#### 2.4 Top Supporters
<table>
  <tr>
    <th>Top 5 Individual Supporters</th>
    <th>Top 5 Organization Supporters</th>
  </tr>
  <tr>
    <td>
      <table>
        <tr>
          <th>ID</th>
          <th>Full Name</th>
          <th>Avg Donation Amount</th>
        </tr>
        <tr>
          <td>2749</td>
          <td>Richard Thompson</td>
          <td>£112,717.24</td>
        </tr>
        <tr>
          <td>2243</td>
          <td>Angela Kelly</td>
          <td>£83,817.38</td>
        </tr>
        <tr>
          <td>1980</td>
          <td>Sandra Stewart</td>
          <td>£71,852.93</td>
        </tr>
        <tr>
          <td>4169</td>
          <td>Jessica Gilmore</td>
          <td>£70,051.86</td>
        </tr>
        <tr>
          <td>3905</td>
          <td>William Chang</td>
          <td>£67,543.65</td>
        </tr>
      </table>
    </td>
    <td>
      <table>
        <tr>
          <th>ID</th>
          <th>Organization Name</th>
          <th>Avg Donation Amount</th>
        </tr>
        <tr>
          <td>433</td>
          <td>Whitaker PLC</td>
          <td>£636,840.54</td>
        </tr>
        <tr>
          <td>465</td>
          <td>Lane, Brooks and Wagner</td>
          <td>£274,361.61</td>
        </tr>
        <tr>
          <td>480</td>
          <td>Rodriguez Inc</td>
          <td>£260,868.75</td>
        </tr>
        <tr>
          <td>203</td>
          <td>Garcia-Novak</td>
          <td>£250,337.06</td>
        </tr>
        <tr>
          <td>434</td>
          <td>Chambers-Strickland</td>
          <td>£244,459.82</td>
        </tr>
      </table>
    </td>
  </tr>
</table>

---
### 3. Fundraising Performance

#### 3.1 Campaign-level Performance
| Campaign Name | Total Appeals |
| :- | :-: |
| Earth Protectors Annual Fund | 3 |
| Wildlands Corridor Acquisition | 4 |
| Forest Fire Recovery | 3 |
| Ocean Plastics Initiative | 2 |
| Endangered Species Protection | 2 |
| Youth Environmental Leadership | 3 |
| Native Plant Restoration | 2 |
| Clean Water Action | 4 |
| Conservation Science Center | 2 |
| Year-End Sustainability Drive | 3 |
| Community Garden Network | 5 |
| Renewable Energy Transition | 2 |
| Green Gala Annual Dinner | 3 |
| Trail Blazer 5K Run/Walk | 3 |
| Hike-a-Thon: Miles for Wildlife | 4 |
| Eco Film Festival | 2 |
| River Cleanup Day | 3 |
| Sustainable Living Expo | 2 |
| Polar Plunge for Climate Action | 2 |
| Cycling for Conservation | 4 |
| Moonlight Paddle Fundraiser | 3 |
| Bird-a-Thon Counting Challenge | 2 |
| Tree Planting Day | 4 |
| Nature Photography Auction | 2 |

<img src="images/3.1%20Campaign-level%20Performance.png">

##### 3.1.1 Funds Raised Outside Timeframe
| Within campaign timeframe? | Total Transactions | Funds Raised |
| :-: | :-: | :-: |
| No | 34 | £195,740.68 |
| Yes | 44706 | £197,368,871.80 |

Funds raised outside of campaign date range all came from –
* Year-End Sustainability Drive (Campaign ID 10)
* Green Gala Annual Dinner (Campaign ID 13)

#### 3.2 Appeal Performance
Out of 70 appeals, 59 (~84%) appeals reached their goal amount. The following eleven appeals not only failed to reach their goals, they did not receive a single donation -
| Appeal Name | Financial Year | Goal Amount |
| :- | :-: | :-: |
| Board Giving - Wildlands Corridor Acquisition | 2024/25 | £10,000.00 |
| Peer to Peer - Hike-a-Thon: Miles for Wildlife | 2024/25 | £25,000.00 |
| Peer to Peer - Eco Film Festival | 2021/22 | £5,000.00 |
| Peer to Peer - River Cleanup Day (Appeal ID 49) | 2024/25 | £5,000.00 |
| Peer to Peer - River Cleanup Day (Appeal ID 50) | 2024/25 | £5,000.00 |
| Peer to Peer - Sustainable Living Expo | 2023/24 | £5,000.00 |
| Peer to Peer - Cycling for Conservation | 2024/25 | £50,000.00 |
| Peer to Peer - Cycling for Conservation | 2021/22 | £25,000.00 |
| Peer to Peer - Bird-a-Thon Counting Challenge | 2021/22 | £5,000.00 |
| Peer to Peer - Tree Planting Day | 2022/23 | £25,000.00 |
| Peer to Peer - Tree Planting Day | 2023/24 | £5,000.00 |

##### 3.2.1 Funds Raised Outside Timeframe
| Within appeal timeframe? | Total Transactions | Funds Raised |
| :-: | :-: | :-: |
| No | 35* | £195,740.68 |
| Yes | 44,705* | £197,368,871.80 |

Most transactions out of appeal date range occurred almost a year after the appeal ended. Majority of outside timeframe transactions occurred for –
* Monthly Giving Program - Year-End Sustainability Drive (Appeal ID 26)
* Social Media Challenge - Green Gala Annual Dinner (Appeal ID 38)

> [!NOTE]
> *Difference in transactions due to ‘Social Media Challenge - Trail Blazer 5K Run/Walk’ appeal (07/03/25 – 18/03/25) not being within the date range of its campaign (07/12/24 – 05/06/25).

#### 3.3 Fund Performance
<img src="images/3.3%20Funds%20Raised.png">

---
### 4. Temporal Analysis
>_Analysis of time-related data_

#### 4.1 Yearly Fundraising Performance
<img src="images/4.1%20Yearly%20Fundraising%20Performance.png">

> [!NOTE]
> 2025/26 financial year started on 1st April 2025

#### 4.2 Fundraising Heatmap
<img src="images/4.2%20Fundraising%20Heatmap.png">

---
### 5. Additional Insights
1\. Negative transaction values found; requires investigation.

| Transaction ID | Date | Financial Year | Financial Period | Amount |
| :-: | :-: | :-: | :-: | :-: |
| 18958 | 19/08/2024 | 2024/25 | P05 | -£540,389.22 |
| 34845 | 29/01/2025 | 2024/25 | P10 | -£358,546.14 |

2\. No strong correlation between appeal timings and whether they reach fundraising goals.

| Appeal Name | F Year | P01 | P02 | P03 | P04 | P05 | P06 | P07 | P08 | P09 | P10 | P11 | P12 |
| :- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| Board Giving - Wildlands Corridor Acquisition | 2024/25 |   |   | X |   |   |   |   |   |   |   |   |   |
| Peer to Peer - Hike-a-Thon: Miles for Wildlife | 2024/25 |   |   |   |   |   | X |   |   |   |   |   |   |
| Peer to Peer - Eco Film Festival | 2021/22 |   |   |   | X |   |   |   |   |   |   |   |   |
| Peer to Peer - River Cleanup Day | 2024/25 |   |   |   |   | X |   |   |   |   |   |   |   |
| Peer to Peer - River Cleanup Day | 2024/25 |   |   |   |   |   |   |   | X |   |   |   |   |
| Peer to Peer - Sustainable Living Expo | 2023/24 |   |   |   |   |   |   |   |   | X |   |   |   |
| Peer to Peer - Cycling for Conservation | 2024/25 |   |   |   |   |   |   |   |   |   |   | X |   |
| Peer to Peer - Cycling for Conservation | 2021/22 |   |   |   |   |   |   | X |   |   |   |   |   |
| Peer to Peer - Bird-a-Thon Counting Challenge | 2021/22 |   |   |   |   |   |   |   |   |   | X |   |   |
| Peer to Peer - Tree Planting Day | 2022/23 |   |   |   |   |   |   |   |   |   |   |   | X |
| Peer to Peer - Tree Planting Day | 2023/24 | X |   |   |   |   |   |   |   |   |   |   |   |
| **Grand Total** |   | **1** | **1** | **1** | **2** | **0** | **1** | **2** | **1** | **1** | **1** | **0** | **1** |

## Analysis Files
[`Excel Workbook`](/Data%20Analysis.xlsx)
[`Presentation Slides`](/Presentation%20Slides.pptx)

> [!WARNING]
> The Excel workbook I did my analysis on is a bit of a mess 😅
