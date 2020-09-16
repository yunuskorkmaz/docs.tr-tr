---
title: ASP.NET ile LINQ to SQL N Katmanı
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1af7f0d78f16e25c1ae7bf563c6abfb3b77f6183
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559232"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>ASP.NET ile LINQ to SQL N Katmanı
Kullanan ASP.NET uygulamalarında [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , <xref:System.Web.UI.WebControls.LinqDataSource> Web sunucusu denetimini kullanırsınız. Denetim, sorgulamak için gereken mantığın çoğunu işler, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] verileri tarayıcıya geçirin, alın ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> daha sonra veritabanını güncelleştirir. Biçimlendirmeyi yalnızca biçimlendirme içinde yapılandırdığınızda, denetim ve tarayıcı arasındaki tüm veri aktarımını işler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Denetim, sunu katmanıyla etkileşimi işletiğinden ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri katmanıyla iletişimi işletiğinden, ana odağınız ASP.net çok katmanlı uygulamalarında özel iş mantığınızı yazmaya yönelik olur.  
  
 Hakkında daha fazla bilgi için `LINQDataSource` bkz. [LinqDataSource Web sunucusu denetimine genel bakış](/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](n-tier-and-remote-applications-with-linq-to-sql.md)
