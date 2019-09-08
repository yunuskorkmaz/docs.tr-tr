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
# <a name="linq-to-sql-n-tier-with-aspnet"></a>ASP.NET ile LINQ to SQL N Katmanı
Kullanan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ASP.NET uygulamalarında, <xref:System.Web.UI.WebControls.LinqDataSource> Web sunucusu denetimini kullanırsınız. Denetim, sorgulamak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]için gereken mantığın çoğunu işler, verileri tarayıcıya geçirin, alın ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> daha sonra veritabanını güncelleştirir. Biçimlendirmeyi yalnızca biçimlendirme içinde yapılandırdığınızda, denetim ve tarayıcı arasındaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tüm veri aktarımını işler. Denetim, sunu katmanıyla etkileşimi işletiğinden ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri katmanıyla iletişimi işletiğinden, ana odağınız ASP.net çok katmanlı uygulamalarında özel iş mantığınızı yazmaya yönelik olur.  
  
 Hakkında `LINQDataSource`daha fazla bilgi için bkz. [LinqDataSource Web sunucusu denetimine genel bakış](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](n-tier-and-remote-applications-with-linq-to-sql.md)
