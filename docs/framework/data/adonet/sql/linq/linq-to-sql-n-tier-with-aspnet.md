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
# <a name="linq-to-sql-n-tier-with-aspnet"></a>ASP.NET ile LINQ to SQL N Katmanı

Kullanan ASP.NET uygulamalarında [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , <xref:System.Web.UI.WebControls.LinqDataSource> Web sunucusu denetimini kullanırsınız. Denetim, sorgulamak için gereken mantığın çoğunu işler, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] verileri tarayıcıya geçirin, alın ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> daha sonra veritabanını güncelleştirir. Biçimlendirmeyi yalnızca biçimlendirme içinde yapılandırdığınızda, denetim ve tarayıcı arasındaki tüm veri aktarımını işler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Denetim, sunu katmanıyla etkileşimi işletiğinden ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri katmanıyla iletişimi işletiğinden, ana odağınız ASP.net çok katmanlı uygulamalarında özel iş mantığınızı yazmaya yönelik olur.  
  
 Hakkında daha fazla bilgi için `LINQDataSource` bkz. [LinqDataSource Web sunucusu denetimine genel bakış](/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](n-tier-and-remote-applications-with-linq-to-sql.md)
