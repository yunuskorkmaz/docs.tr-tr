---
title: SQL-CLR Özel Tür Eşlemeleri
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: 5aff9a78349cbf9443c5b663a41d7c13a109e625
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945054"
---
# <a name="sql-clr-custom-type-mappings"></a>SQL-CLR Özel Tür Eşlemeleri
SQL Server ile ortak dil çalışma zamanı (CLR) arasında tür eşlemesi Nesne İlişkisel Tasarımcısı, SQLMetal komut satırı aracını (O/R Designer) kullandığınızda otomatik olarak belirtilir.  
  
 Özelleştirilmiş eşleme gerçekleştirilmeyen bu araçlar, [SQL-CLR türü eşlemesinde](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)açıklandığı gibi varsayılan tür eşlemelerini atar. Eşlemeleri bu varsayılandan farklı şekilde yazmak istiyorsanız, tür eşlemelerini özelleştirme yapmanız gerekir.  
  
 Tür eşlemelerini özelleştirirken, bir ara DBML dosyasında değişiklik yapmak önerilen yaklaşım olur. Daha sonra, kod oluşturduğunuzda ve dosyaları SQLMetal veya O/R Tasarımcısı ile eşleştirdikten sonra özelleştirilmiş DBML dosyanız kullanılmalıdır.  
  
 Koddan ve eşleme dosyalarından <xref:System.Data.Linq.DataContext> nesneyi örnekledikten sonra <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> , yöntemi belirtilen tür eşlemelerini temel alan bir veritabanı oluşturur. Eşlemelerde hiçbir CLR `type` özniteliği belirtilmemişse, varsayılan tür eşlemeleri kullanılacaktır.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>SQLMetal veya O/R Tasarımcısı ile özelleştirme  
 SQLMetal ve O/R Tasarımcısı ile, kod dosyasının içindeki veya dışındaki tür eşleme bilgilerini içeren bir nesne modeli otomatik olarak oluşturabilirsiniz. Bu dosyalar SQLMetal veya O/R Tasarımcısı tarafından üzerine yazıldığı için, eşlemelerinizi her yeniden oluşturduğunuzda özel tür eşlemelerini belirtmeye yönelik önerilen yaklaşım bir DBML dosyasını özelleştirmektir.  
  
 Tür eşlemelerini SQLMetal veya O/R Tasarımcısı ile özelleştirmek için önce bir DBML dosyası oluşturun. Ardından, kod dosyası veya eşleme dosyası oluşturmadan önce, istenen tür eşlemelerini belirlemek için DBML dosyasını değiştirin. SqlMetal ile, tür eşleme özelleştirmelerinizi yapmak için DBML `DbType` dosyasındaki `Type` ve özniteliklerini el ile değiştirmeniz gerekir. O/R Tasarımcısı ile değişikliklerinizi tasarımcı içinde yapabilirsiniz. O/R tasarımcısını kullanma hakkında daha fazla bilgi için bkz. [Visual Studio 'da LINQ to SQL araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
> Bazı tür eşlemelerde veya veritabanına çevrilirken taşma veya veri kaybı özel durumları oluşabilir. Herhangi bir özelleştirme yapmadan önce [SQL-CLR tür eşlemesindeki](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) tür eşleme çalışma zamanı davranış matrisini dikkatle gözden geçirin.  
  
 Tür eşleme özelleştirmelerinizin SQLMetal veya O/R Tasarımcısı tarafından tanınması için, kod dosyanızı veya dış eşleme dosyanızı oluştururken özel DBML dosyanızın yoluyla bu araçların sağlandığından emin olmanız gerekir. Tür eşleme özelleştirmesi için gerekli olmasa da, kod dosyanızdaki tür eşleme bilgilerinizi her zaman ayırmanız ve ek dış tür eşleme dosyasını oluşturmanız önerilir. Bunun yapılması, kod dosyasının yeniden derlenmesi gerekmeden bazı esneklikten ayrılacaktır.  
  
## <a name="incorporating-database-changes"></a>Veritabanı değişikliklerini ekleme  
 Veritabanınız değiştiğinde DBML dosyanızı bu değişiklikleri yansıtacak şekilde güncelleştirmeniz gerekir. Bunu yapmanın bir yolu, otomatik olarak yeni bir DBML dosyası oluşturmak ve ardından tür eşleme özelleştirmelerinizi yeniden oluşturmaktır. Alternatif olarak, yeni DBML dosyanız ile özelleştirilmiş DBML dosyanız arasındaki farklılıkları karşılaştırabilir ve özel DBML dosyanızı, veritabanı değişikliğini yansıtacak şekilde el ile güncelleştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [LINQ to SQL’de Kod Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
