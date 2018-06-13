---
title: SQL Server Compact ve LINQ-SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 74b8a7a6dfc9a4050dbba9a8c2f6969dba42656c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355792"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact ve LINQ-SQL
SQL Server Compact Visual Studio ile yüklenen varsayılan veritabanıdır. Daha fazla bilgi için bkz: [PAVE üzerinden kullanarak SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).  
  
 Bu konu kullanımı, yapılandırma, özellik kümeleri ve kapsamını temel farklılıkları özetler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>LINQ-SQL ile ilgili SQL Server Compact özellikleri  
 Varsayılan olarak, SQL Server Compact tüm Visual Studio sürümleri için yüklü ve bu nedenle ile kullanmak için geliştirme bilgisayarındaki kullanılabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Ancak, SQL Server Compact kullanan bir uygulama dağıtımını ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , SQL Server uygulaması için farklıdır. SQL Server Compact .NET Framework'ün bir parçası değil ve bu nedenle uygulama ile paketlenmiş veya gerekir ayrı olarak Microsoft sitesinden indirilen.  
  
 Aşağıdaki özelliklere dikkat edin:  
  
-   SQL Server Compact veritabanı dosyalarını (.sdf uzantılı) karşı doğrudan kullanılabilen DLL olarak paketlenir.  
  
-   İstemci uygulaması ile aynı işlemde SQL Server Compact çalışır. SQL Server Compact ile iletişim verimliliğini, bu nedenle SQL Server ile iletişim kurarken daha önemli ölçüde daha yüksek olabilir. Diğer taraftan, SQL Server Compact Katılımcısı maliyetleri yönetilen ve yönetilmeyen kod birlikte çalışabilirliği gerektirir.  
  
-   SQL Server Compact DLL'si boyutu küçüktür. Bu özellik genel uygulama boyutunu azaltır.  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çalışma zamanı ve SQLMetal komut satırı aracı SQL Server Compact destekler.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] SQL Server Compact desteklemiyor.  
  
## <a name="feature-set"></a>Özellik kümesi  
 SQL Server Compact özellik kümesi etkileyebilir aşağıdaki yollarla SQL Server'ın özellik kümesi çok daha kolaydır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar:  
  
-   SQL Server Compact saklı yordamları veya görünümleri desteklemez.  
  
-   SQL Server Compact yalnızca bir alt veri türleri ve SQL işlevleri destekler.  
  
-   SQL Server Compact yalnızca bir alt kümesini SQL yapısını destekler.  
  
-   SQL Server Compact en az bir iyileştirici sağlar. Bazı sorgular zaman aşımı olabilir mümkündür.  
  
-   SQL Server Compact, kısmi güven desteklemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
