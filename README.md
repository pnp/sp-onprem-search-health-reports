# SRx Core 
**Download latest release here: https://github.com/pnp/sp-onprem-search-health-reports/releases**

Announcing the Search Health Reports (SRx) for SharePoint Search Diagnostics
============================================================================
*   3 minutes to read

### In this article

1.  [Getting Started](#getting-started)
2.  [Generating Test Results](#generating-test-results)
3.  [Looking Forward…](#looking-forward)

![srxicon](https://msdnshared.blob.core.windows.net/media/2016/02/SRxIcon.png)Brought to you by [SearchEngineers@microsoft.com](mailto:SearchEngineers@microsoft.com), the [**Search Health Reports (SRx)**](https://github.com/pnp/sp-onprem-search-health-reports/releases) is a PowerShell-driven tool for surfacing complex diagnostics for SharePoint Search through new multifaceted reports. The _**SRx**_ includes a battery of tests that leverage a customized SSA object extended with contextual data from many disparate sources.

Our goal with this project is straightforward – empower users to **troubleshoot Search more effectively** so they can focus on solving business problems using Search.

[](#getting-started)Getting Started
-----------------------------------

First, [**download the SRxCore.zip**](https://github.com/pnp/sp-onprem-search-health-reports/releases) to your SharePoint Search Farm and unzip the files on a SharePoint Server. Then, initialize the _**SRx**_ environment by simply running the .\\initSRx.ps1 script (which exists in the root of the unzipped _SRx_ folder) as demonstrated in the screen shot below:

![srxcore-init](https://msdnshared.blob.core.windows.net/media/2016/02/SRxCore-Init.png)

This initialization script loads the custom PowerShell modules and creates a globally scoped $xSSA, an extended Search Service Application object with many custom properties and methods.

Getting Started

**Worth noting:** The SRx does not persist after closing a PowerShell window, so **each time you open a new PowerShell window, start by running .\\initSRx.ps1 to initialize the SRx** and you'll be good to go from there.

[](#generating-test-results)Generating Test Results
---------------------------------------------------

**\[UPDATE 3/25/2016\]**   For a summary on each test, please refer to the following post: [Search Health Reports (SRx) - Summary for each 'Test'](http://blogs.technet.com/b/onsearch/archive/2016/03/25/search-health-reports-srx-documentation-for-each-test.aspx)

From an initialized environment, you can then run a report including all of the tests with the following command:  
New-SRxReport -RunAllTests [![srxhealth-thehappypath](https://msdnshared.blob.core.windows.net/media/2016/02/SRxHealth-TheHappyPath-1024x971.png)](https://msdnshared.blob.core.windows.net/media/2016/02/SRxHealth-TheHappyPath.png)[](https://msdnshared.blob.core.windows.net/media/2016/02/SRxHealth-TheHappyPath.png)

As seen above, this battery of tests verifies that applicable servers can be pinged, component-related processes and services are running, component states are all 'Active', internal Search WCF EndPoints can be browsed, Index components have sufficient space to complete a Master Merges, the Legacy Admin is synchronized with the Admin Component, and more.

When running this set of tests, you can also output more details about the test results by adding the _Details_ flag, such as (and this is also an example of handling when things go bad):  
New-SRxReport -RunAllTests -Details [![SRxHealth-ThingsGoneBad](https://msdnshared.blob.core.windows.net/media/2016/02/SRxHealth-ThingsGoneBad-588x1024.png)](https://msdnshared.blob.core.windows.net/media/2016/02/SRxHealth-ThingsGoneBad.png)

The SRx also extends and replaces my [previously published Indexer Reports](../sharepoint_strategery/sp2013-using-get-spindexreports-to-troubleshoot-failed-master-merge), which you can generate in the SRx using the following:  
$xSSA | Get-SRxIndexReports -DiskReport [![srx-indexreport](https://msdnshared.blob.core.windows.net/media/2016/02/SRx-IndexReport-1024x763.png)](https://msdnshared.blob.core.windows.net/media/2016/02/SRx-IndexReport.png)

\----

[](#looking-forward)Looking Forward…
------------------------------------

As Search PFEs, we are working with several of our dedicated customers to build upon the _SRx Core_ by developing the **Search Health Reports Dashboard (SRx)** , which entails a custom SharePoint hosted site collection for rendering diagnostic gauges, KPIs, and proactive reporting. Over the last few months, this project significantly matured with expanding functionality and robustness – for that **, a giant thank you goes out for the heavy lifting from Brian Pendergrass, Eric Dixon, Brent Groom, and Russ Maxwell**.

Over the coming weeks, expect to see many more _**SRx**_ related posts here ([SharePoint Strategery](../sharepoint_strategery/sp2013-understanding-storage-locations-for-files-gathered-by-the-crawl-component)), on [SharePoint Brew (Russ Maxwell)](https://blogs.msdn.com/b/russmax/), and on [Eric Dixon's Search Blog](../ericdixon/sharepoint-2013-search-people-search-why-are-my-results-so-bad-understanding-relevancy-the-rank-model-full-text-index-fuzzy-matching-and-social-distance) …all of which roll up to [our team blog (On Search)](../onsearch/modeling-the-adventureworks-inventory-database-for-azure-search). In these coming posts, anticipate more details on individual tests, announcements of new functionality, and recordings that demonstrate advanced usage (\*including sneak peeks of the _SRx Dashboard_). Finally, we'll continue to update the [**SRx Core on TechNet Gallery with the latest enhancements**](https://gallery.technet.microsoft.com/SRx-Core-SharePoint-Search-d60113e9) **.**

For any questions or feedback regarding this, please feel free to contact us at:  
[SearchEngineers@microsoft.com](mailto:SearchEngineers@microsoft.com)

...and to learn more about the **Search Health Reports Dashboard (SRx)** , contact your TAM to help get us engaged.

\---  
And the legalese:  
**Disclaimer:** As the "Search Engineers", we are a group of Microsoft PFEs focused primarily on SharePoint Search. We released the Search Health Reports (SRx) to help others get more out of Search, but the SRx should not be considered an official product . ALL information in this blog is provided "AS IS" with no warranties and confers no rights. This blog does not represent the thoughts, intentions, plans or strategies of my employer. All content is solely my opinion and provided with a best effort to be based in reality.

All examples, code samples, demonstrations, or anything resembling a “how-to” are provided "AS IS" without warranty of any kind, either express or implied, including but not limited to the implied warranties of merchantability and/or fitness for a particular purpose. Inappropriate comments will be deleted at the authors discretion. And yes, the spelling of _strategery_ was intentional.
