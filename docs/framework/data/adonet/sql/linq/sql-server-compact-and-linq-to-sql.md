---
title: SQL Server Compact ve LINQ-SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9409c17065b0421ec32a61352f9c0b975095ab44
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact ve LINQ-SQL
SQL Server Compact Visual Studio ile yüklenen varsayılan veritabanıdır. Daha fazla bilgi için bkz: [PAVE üzerinden kullanarak SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).  
  
 Bu konu kullanımı, yapılandırma, özellik kümeleri ve kapsamını temel farklılıkları özetler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>LINQ-SQL ile ilgili SQL Server Compact özellikleri  
 Varsayılan olarak, SQL Server Compact tüm yüklü [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] sürümleri ve bu nedenle ile kullanmak için geliştirme bilgisayarındaki kullanılabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Ancak, SQL Server Compact kullanan bir uygulama dağıtımını ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için farklı bir [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] uygulama. SQL Server Compact .NET Framework'ün bir parçası değil ve bu nedenle uygulama ile paketlenmiş veya gerekir ayrı olarak Microsoft sitesinden indirilen.  
  
 Aşağıdaki özelliklere dikkat edin:  
  
-   SQL Server Compact veritabanı dosyalarını (.sdf uzantılı) karşı doğrudan kullanılabilen DLL olarak paketlenir.  
  
-   İstemci uygulaması ile aynı işlemde SQL Server Compact çalışır. SQL Server Compact ile iletişim verimliliğini bu nedenle kurduğu daha önemli ölçüde daha yüksek olabilir [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]. Diğer taraftan, SQL Server Compact Katılımcısı maliyetleri yönetilen ve yönetilmeyen kod birlikte çalışabilirliği gerektirir.  
  
-   SQL Server Compact DLL'si boyutu küçüktür. Bu özellik genel uygulama boyutunu azaltır.  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çalışma zamanı ve SQLMetal komut satırı aracı SQL Server Compact destekler.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] SQL Server Compact desteklemiyor.  
  
## <a name="feature-set"></a>Özellik kümesi  
 SQL Server Compact özellik kümesi özellik kümesini çok daha kolaydır [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] etkileyebilir aşağıdaki yollarla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar:  
  
-   SQL Server Compact saklı yordamları veya görünümleri desteklemez.  
  
-   SQL Server Compact yalnızca bir alt veri türleri ve SQL işlevleri destekler.  
  
-   SQL Server Compact yalnızca bir alt kümesini SQL yapısını destekler.  
  
-   SQL Server Compact en az bir iyileştirici sağlar. Bazı sorgular zaman aşımı olabilir mümkündür.  
  
-   SQL Server Compact, kısmi güven desteklemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
