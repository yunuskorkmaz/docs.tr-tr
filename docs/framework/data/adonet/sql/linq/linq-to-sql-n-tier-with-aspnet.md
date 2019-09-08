---
title: ASP.NET ile LINQ to SQL N Katmanı
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1770d84053b57e05d1a4e41919a3eb4122dc73a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793024"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="47aa4-102">ASP.NET ile LINQ to SQL N Katmanı</span><span class="sxs-lookup"><span data-stu-id="47aa4-102">LINQ to SQL N-Tier with ASP.NET</span></span>
<span data-ttu-id="47aa4-103">Kullanan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ASP.NET uygulamalarında, <xref:System.Web.UI.WebControls.LinqDataSource> Web sunucusu denetimini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="47aa4-103">In ASP.NET applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="47aa4-104">Denetim, sorgulamak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]için gereken mantığın çoğunu işler, verileri tarayıcıya geçirin, alın ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> daha sonra veritabanını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="47aa4-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="47aa4-105">Biçimlendirmeyi yalnızca biçimlendirme içinde yapılandırdığınızda, denetim ve tarayıcı arasındaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tüm veri aktarımını işler.</span><span class="sxs-lookup"><span data-stu-id="47aa4-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="47aa4-106">Denetim, sunu katmanıyla etkileşimi işletiğinden ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri katmanıyla iletişimi işletiğinden, ana odağınız ASP.net çok katmanlı uygulamalarında özel iş mantığınızı yazmaya yönelik olur.</span><span class="sxs-lookup"><span data-stu-id="47aa4-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in ASP.NET multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="47aa4-107">Hakkında `LINQDataSource`daha fazla bilgi için bkz. [LinqDataSource Web sunucusu denetimine genel bakış](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="47aa4-107">For more information about `LINQDataSource`, see [LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47aa4-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47aa4-108">See also</span></span>

- [<span data-ttu-id="47aa4-109">LINQ to SQL ile N Katmanı ve Uzak Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="47aa4-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
