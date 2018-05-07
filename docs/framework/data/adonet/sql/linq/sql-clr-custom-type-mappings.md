---
title: SQL CLR özel türü eşlemeleri
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: ebbbaf4b90c289d4230bada210d3031a87ac4f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="sql-clr-custom-type-mappings"></a>SQL CLR özel türü eşlemeleri
SQLMetal komut satırı aracı, Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) kullandığınızda, SQL Server ve ortak dil çalışma zamanı (CLR) arasında tür eşlemesi otomatik olarak belirtilir.  
  
 Özelleştirilmiş eşleme gerçekleştirildiğinde, bu araçları varsayılan türü eşlemeleri açıklandığı gibi atama [SQL CLR türü eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md). Bu varsayılan ayarından farklı bir şekilde eşlemeleri yazmak istiyorsanız, bazı türü eşlemelerini özelleştirme yapmanız gerekir.  
  
 Tür eşlemeleri özelleştirirken, önerilen bir ara DBML dosyasında değişiklik yaklaşımdır. Daha sonra kodu ve eşleme dosyaları SQLMetal veya O/R Tasarımcısı ile oluşturduğunuz özelleştirilmiş DBML dosyanızda kullanılmalıdır.  
  
 Örneği sonra <xref:System.Data.Linq.DataContext> eşleme dosyaları ve kod nesnesinden <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi, belirtilen türü eşlemeleri dayalı bir veritabanı oluşturur. Hiçbir CLR varsa `type` öznitelikleri varsayılan türü eşlemeleri kullanılacak eşlemesinde belirtilen.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>SQLMetal veya O/R Tasarımcısı ile özelleştirme  
 SQLMetal ve O/R Tasarımcısı ile otomatik olarak veya kod dosyası dışındaki türü eşleme bilgilerini içeren bir nesne modeli oluşturabilirsiniz. Bu dosyalar SQLMetal veya O/R tasarımcısı tarafından üzerine yazılır olduğundan, eşlemeleri yeniden her zaman özel tür eşlemeleri belirtme önerilen DBML dosyasını özelleştirmek için yaklaşımdır.  
  
 SQLMetal veya O/R Tasarımcısı ile türü eşlemeleri özelleştirmek için önce bir DBML dosyası oluşturun. Ardından, eşleme dosyasını ve kod dosyası oluşturmadan önce istenen türe eşlemeleri tanımlamak için DBML dosyasını değiştirin. El ile değiştirmek zorunda SQLMetal ile `Type` ve `DbType` türünüz eşleme özelleştirmeler için DBML dosyasındaki öznitelikleri. O/R Tasarımcısı ile Tasarımcısı'nda yaptığınız değişiklikleri yapabilirsiniz. O/R Tasarımcısı'nı kullanma hakkında daha fazla bilgi için bkz: [LINQ-SQL Visual Studio Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
>  Bazı türü eşlemeleri taşması veya veri kaybı durumlar için veya veritabanından çevrilirken neden olabilir. Çalışma zamanı türü Eşleme davranışı matrisinde dikkatlice inceleyin [SQL CLR türü eşleme](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) özelleştirmeler yapmadan önce.  
  
 SQLMetal veya O/R tasarımcısı tarafından kabul edilecek türü eşleme özelleştirmelerinizi kod dosyası veya dış eşleme dosyası oluşturduğunuzda bu araçları özel DBML dosyanızın yolu ile birlikte verilen emin olmak gerekir. Tür eşlemesi özelleştirme için gerekli değildir, ancak her zaman kodu dosyanızdan türü eşleme bilgilerinizi ayırın ve ek dış türü eşleme dosyası oluşturmak önerilir. Bunun yapılması, bazı esneklik kod dosyası derlenmesi isteyerek değil bırakır.  
  
## <a name="incorporating-database-changes"></a>Veritabanı değişikliklerini ekleme  
 Ne zaman veritabanı değişikliklerinizi DBML dosyanızı konusu değişiklikleri yansıtacak şekilde güncelleştirmeniz gerekir. Yapmanın bir yolu otomatik olarak yeni bir DBML dosyası oluşturmak için budur ve tür eşlemesi özelleştirmelerinizi yeniden yapın. Alternatif olarak, yeni DBML dosyanızı ve özelleştirilmiş DBML dosyanızda arasındaki farklar karşılaştırın ve özel DBML dosyanızı el ile veritabanı değişikliği yansıtacak şekilde güncelleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [LINQ to SQL’de Kod Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
