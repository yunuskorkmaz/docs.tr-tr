---
title: ASP.NET ile LINQ to SQL N Katmanı
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 85ead36d1d927084c11dca1bd73a192b16e4ab7b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880760"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>ASP.NET ile LINQ to SQL N Katmanı
ASP.NET uygulamalarında kullanmak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], kullandığınız <xref:System.Web.UI.WebControls.LinqDataSource> Web sunucu denetimi. Denetim olmalıdır mantıksal çoğunu işleme sorgulamanın yapılacağı [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], verilerin tarayıcıya geçirmek, alma ve kendisine göndermek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> daha sonra veritabanını güncelleştirir. Yalnızca denetim işaretlemede yapılandırın ve tüm veri aktarımı arasında denetim işleme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve tarayıcı. Denetim sunu katmanı etkileşim gerçekleştirdiğinden ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] odaklandığı ASP.NET çok katmanlı uygulamalarda veri katmanıyla iletişimidir özel iş mantığınızı yazmaya işler.  
  
 Hakkında daha fazla bilgi için `LINQDataSource`, bkz: [LinqDataSource Web sunucusu denetimine genel bakış](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
