---
title: "LINQ-SQL N katmanlı ASP.NET ile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9b71113ca76eec5888aed2123ec9c55ad66a72bf
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="716eb-102">LINQ-SQL N katmanlı ASP.NET ile</span><span class="sxs-lookup"><span data-stu-id="716eb-102">LINQ to SQL N-Tier with ASP.NET</span></span>
<span data-ttu-id="716eb-103">İçinde [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] kullanan uygulamalar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], kullandığınız <xref:System.Web.UI.WebControls.LinqDataSource> Web sunucusu denetimi.</span><span class="sxs-lookup"><span data-stu-id="716eb-103">In [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="716eb-104">Çoğu gerekir mantığı denetim işleme sorgusu için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], tarayıcıya veri iletmek, bunu almak ve göndermek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> , daha sonra veritabanını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="716eb-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="716eb-105">Biçimlendirme içinde yalnızca denetimini yapılandırmak ve tüm veri aktarımı arasında denetim işleme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve tarayıcı.</span><span class="sxs-lookup"><span data-stu-id="716eb-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="716eb-106">Sunu katmanı ile etkileşim denetim işleme olduğundan ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ana odağınız veri katmanı ile iletişimi işleme [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] çok katmanlı uygulamaları olduğundan, özel iş mantığı yazma.</span><span class="sxs-lookup"><span data-stu-id="716eb-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="716eb-107">Hakkında daha fazla bilgi için `LINQDataSource`, bkz: [NIB: LinqDataSource Web sunucusu denetimine genel bakış](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span><span class="sxs-lookup"><span data-stu-id="716eb-107">For more information about `LINQDataSource`, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716eb-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="716eb-108">See Also</span></span>  
 [<span data-ttu-id="716eb-109">LINQ to SQL ile N Katmanı ve Uzak Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="716eb-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
