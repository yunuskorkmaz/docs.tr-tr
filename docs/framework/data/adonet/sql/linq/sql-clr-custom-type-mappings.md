---
title: SQL-CLR özel tür eşlemeleri
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: 36763be3cd4845fbbd027b448098d0dafb9e448a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622523"
---
# <a name="sql-clr-custom-type-mappings"></a>SQL-CLR özel tür eşlemeleri
SQLMetal komut satırı aracı, Object Relational Designer (O/R Tasarımcısı) kullandığınızda, ortak dil çalışma zamanı (CLR) ile SQL Server arasında eşleme türü otomatik olarak belirtilir.  
  
 Özelleştirilmiş hiçbir eşleme gerçekleştirildiğinde, bu araçlar varsayılan türü eşlemeleri açıklandığı atama [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md). Bu varsayılan alanından farklı eşlemeleri yazmak istiyorsanız, bazı türü eşlemelerini özelleştirme yapmanız gerekir.  
  
 Türü eşlemelerini özelleştirme, önerilen yaklaşım, bir aracı DBML dosyasına değişiklikler olmasını sağlamaktır. Ardından, kod ve eşleme dosyalarını SQLMetal veya O/R Tasarımcısı ile oluşturduğunuz özelleştirilmiş DBML dosyanızı kullanılmalıdır.  
  
 Örneği sonra <xref:System.Data.Linq.DataContext> kod ve eşleme dosyalarını nesneden <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi belirtilen türü eşlemeleri tabanlı bir veritabanı oluşturur. Hiçbir CLR varsa `type` öznitelikleri belirtildiğinde eşlemeleri varsayılan türü eşlemeleri kullanılır.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>SQLMetal veya O/R Tasarımcısı ile özelleştirme  
 SQLMetal ve O/R Tasarımcısı ile içinde veya kod dosyası dışında türü eşleme bilgilerini içeren bir nesne modeli otomatik olarak oluşturabilirsiniz. Bu dosyalar SQLMetal veya O/R tasarımcısı tarafından üzerine yazılır olduğundan, eşlemeleri yeniden her zaman özel tür eşlemeleri belirtme önerilen DBML dosyasını özelleştirmek için yaklaşımdır.  
  
 SQLMetal veya O/R Tasarımcısı türü eşlemeleri özelleştirmek için öncelikle DBML dosyasını oluşturur. Ardından, kod dosyası veya eşleme dosyası oluşturmadan önce istenen türde eşlemeler tanımlamak için DBML dosyasını değiştirin. SQLMetal ile el ile değiştirmeniz gerekir. `Type` ve `DbType` türünüz eşleme özelleştirmeler için DBML dosyasına öznitelikleri. O/R Tasarımcısı ile Tasarımcı içinde yaptığınız değişiklikleri yapabilirsiniz. O/R Tasarımcısı kullanma hakkında daha fazla bilgi için bkz. [LINQ to SQL araçlarını Visual Studio'da](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
>  Bazı tür eşlemeleri için veya veritabanından çevrilirken taşması veya veri kaybı durumlar neden olabilir. Eşleme türü çalışma zamanı davranışı matriste dikkatle inceleyin [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) özelleştirmeler yapmadan önce.  
  
 SQLMetal veya O/R tasarımcısı tarafından tanınması tür eşlemesi özelleştirmelerinizi kod dosyası veya dış eşleme dosyası oluşturduğunuzda bu araçlar, özel bir DBML dosyasının yolu ile sağlanan emin olmanız gerekir. Tür eşlemesi özelleştirme için gerekli değildir, ancak her zaman, kod dosyasından türü eşleme bilgilerinizi ayırın ve ek dış tür eşleme dosyası üretmek önerilir. Bunun yapılması, kod dosyasının yeniden derlenmesi gerektirmeyen bazı esneklik bırakır.  
  
## <a name="incorporating-database-changes"></a>Veritabanı değişikliklerini ekleme  
 Ne zaman veritabanı değişikliklerinizi DBML dosyanızı o değişiklikleri yansıtacak şekilde güncelleştirmeniz gerekir. Yapmanın bir yolu otomatik olarak yeni bir DBML dosyasının oluşturulacağı budur ve tür eşlemesi özelleştirmelerinizi yeniden yapın. Alternatif olarak, yeni DBML dosyasını ve özelleştirilmiş DBML dosyanızı arasındaki farkları karşılaştırmak ve özel DBML dosyanızı el ile veritabanı değişikliği yansıtacak şekilde güncelleştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [LINQ to SQL’de Kod Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
