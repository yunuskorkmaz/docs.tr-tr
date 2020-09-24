---
title: SQL Server Compact ve LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 7963db9e05eca7a7a148228c6d2fbca0221ca870
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155685"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact ve LINQ to SQL

SQL Server Compact, Visual Studio ile yüklenen varsayılan veritabanıdır. Daha fazla bilgi için bkz. [SQL Server Compact kullanma (Visual Studio)](/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).  
  
 Bu konuda kullanım, yapılandırma, özellik kümeleri ve destek kapsamındaki önemli farklılıklar özetlenmektedir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>LINQ to SQL göre SQL Server Compact özellikleri  

 Varsayılan olarak, tüm Visual Studio sürümleri için SQL Server Compact yüklenir ve bu nedenle geliştirme bilgisayarında ile kullanım için kullanılabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Ancak SQL Server Compact kullanan ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server bir uygulama için bundan farklı bir uygulama dağıtımı. SQL Server Compact, .NET Framework bir parçası değildir ve bu nedenle uygulamayla paketlenmesi veya Microsoft sitesinden ayrı olarak indirilmelidir.  
  
 Aşağıdaki özelliklere göz önünde edin:  
  
- SQL Server Compact, veritabanı dosyalarında (. sdf uzantısı) doğrudan kullanılabilecek bir DLL olarak paketlenmiştir.  
  
- SQL Server Compact, istemci uygulamasıyla aynı işlemde çalışır. SQL Server Compact ile iletişimin verimliliği, SQL Server iletişim kurmaktan önemli ölçüde yüksek olabilir. Diğer yandan SQL Server Compact, yönetilen ve yönetilmeyen kod arasında ortak maliyetleriyle birlikte çalışabilirlik gerektirir.  
  
- SQL Server Compact DLL boyutu küçüktür. Bu özellik, uygulamanın boyutunun tamamını azaltır.  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Çalışma zamanı ve SQLMetal komut satırı aracı SQL Server Compact destekler.  
  
- Nesne İlişkisel Tasarımcısı SQL Server Compact desteklemez.  
  
## <a name="feature-set"></a>Özellik kümesi  

 SQL Server Compact özellik kümesi, uygulamaları etkileyebilecek aşağıdaki yollarla SQL Server Özellik kümesinden çok daha basittir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :  
  
- SQL Server Compact, saklı yordamları veya görünümleri desteklemez.  
  
- SQL Server Compact, veri türleri ve SQL işlevlerinin yalnızca bir alt kümesini destekler.  
  
- SQL Server Compact, SQL yapılarının yalnızca bir alt kümesini destekler.  
  
- SQL Server Compact yalnızca en az bir iyileştirici sağlar. Bazı sorgular zaman aşımına uğrar.  
  
- SQL Server Compact kısmi güveni desteklemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](reference.md)
