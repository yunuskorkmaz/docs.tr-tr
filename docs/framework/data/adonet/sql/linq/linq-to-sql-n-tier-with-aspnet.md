---
title: ASP.NET ile LINQ to SQL N Katmanı
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: a184c9dcb29e7994aefa4062be2b30484539c4e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175323"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="271db-102">ASP.NET ile LINQ to SQL N Katmanı</span><span class="sxs-lookup"><span data-stu-id="271db-102">LINQ to SQL N-Tier with ASP.NET</span></span>

<span data-ttu-id="271db-103">Kullanan ASP.NET uygulamalarında [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , <xref:System.Web.UI.WebControls.LinqDataSource> Web sunucusu denetimini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="271db-103">In ASP.NET applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="271db-104">Denetim, sorgulamak için gereken mantığın çoğunu işler, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] verileri tarayıcıya geçirin, alın ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> daha sonra veritabanını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="271db-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="271db-105">Biçimlendirmeyi yalnızca biçimlendirme içinde yapılandırdığınızda, denetim ve tarayıcı arasındaki tüm veri aktarımını işler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="271db-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="271db-106">Denetim, sunu katmanıyla etkileşimi işletiğinden ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri katmanıyla iletişimi işletiğinden, ana odağınız ASP.net çok katmanlı uygulamalarında özel iş mantığınızı yazmaya yönelik olur.</span><span class="sxs-lookup"><span data-stu-id="271db-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in ASP.NET multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="271db-107">Hakkında daha fazla bilgi için `LINQDataSource` bkz. [LinqDataSource Web sunucusu denetimine genel bakış](/previous-versions/aspnet/bb547113(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="271db-107">For more information about `LINQDataSource`, see [LinqDataSource Web Server Control Overview](/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="271db-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="271db-108">See also</span></span>

- [<span data-ttu-id="271db-109">LINQ to SQL ile N Katmanı ve Uzak Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="271db-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
