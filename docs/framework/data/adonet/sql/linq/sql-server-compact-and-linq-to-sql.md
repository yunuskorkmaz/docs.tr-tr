---
title: SQL Server Compact ve LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792539"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact ve LINQ to SQL
SQL Server Compact, Visual Studio ile yüklenen varsayılan veritabanıdır. Daha fazla bilgi için bkz. [SQL Server Compact kullanma (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).  
  
 Bu konuda kullanım, yapılandırma, özellik kümeleri ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destek kapsamındaki önemli farklılıklar özetlenmektedir.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>LINQ to SQL göre SQL Server Compact özellikleri  
 Varsayılan olarak, tüm Visual Studio sürümleri için SQL Server Compact yüklenir ve bu nedenle geliştirme bilgisayarında ile [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kullanım için kullanılabilir. Ancak SQL Server Compact kullanan ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server bir uygulama için bundan farklı bir uygulama dağıtımı. SQL Server Compact, .NET Framework bir parçası değildir ve bu nedenle uygulamayla paketlenmesi veya Microsoft sitesinden ayrı olarak indirilmelidir.  
  
 Aşağıdaki özelliklere göz önünde edin:  
  
- SQL Server Compact, veritabanı dosyalarında (. sdf uzantısı) doğrudan kullanılabilecek bir DLL olarak paketlenmiştir.  
  
- SQL Server Compact, istemci uygulamasıyla aynı işlemde çalışır. SQL Server Compact ile iletişimin verimliliği, SQL Server iletişim kurmaktan önemli ölçüde yüksek olabilir. Diğer yandan SQL Server Compact, yönetilen ve yönetilmeyen kod arasında ortak maliyetleriyle birlikte çalışabilirlik gerektirir.  
  
- SQL Server Compact DLL boyutu küçüktür. Bu özellik, uygulamanın boyutunun tamamını azaltır.  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çalışma zamanı ve SQLMetal komut satırı aracı SQL Server Compact destekler.  
  
- Nesne İlişkisel Tasarımcısı SQL Server Compact desteklemez.  
  
## <a name="feature-set"></a>Özellik kümesi  
 SQL Server Compact özellik kümesi, uygulamaları etkileyebilecek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki yollarla SQL Server Özellik kümesinden çok daha basittir:  
  
- SQL Server Compact, saklı yordamları veya görünümleri desteklemez.  
  
- SQL Server Compact, veri türleri ve SQL işlevlerinin yalnızca bir alt kümesini destekler.  
  
- SQL Server Compact, SQL yapılarının yalnızca bir alt kümesini destekler.  
  
- SQL Server Compact yalnızca en az bir iyileştirici sağlar. Bazı sorgular zaman aşımına uğrar.  
  
- SQL Server Compact kısmi güveni desteklemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](reference.md)
