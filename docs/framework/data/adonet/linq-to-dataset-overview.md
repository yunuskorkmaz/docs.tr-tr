---
title: LINQ to DataSet Genel Bakış
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: 20d9be052ba2567c16718b4b1c1019427c9b5df1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634826"
---
# <a name="linq-to-dataset-overview"></a>LINQ to DataSet Genel Bakış
<xref:System.Data.DataSet>, ADO.NET 'in daha yaygın olarak kullanılan bileşenlerinden biridir. Bu, ADO.NET tarafından kullanılan, bağlantısı kesilen programlama modelinin temel öğesidir ve farklı veri kaynaklarından gelen verileri açıkça önbelleğe almanıza olanak sağlar. Sunum katmanı için <xref:System.Data.DataSet>, veri bağlama için GUI denetimleriyle sıkı bir şekilde tümleşiktir. Orta katman için, verilerin ilişkisel şeklini koruyan bir önbellek sağlar ve hızlı basit sorgu ve hiyerarşi gezinti hizmetlerini içerir. Bir veritabanındaki isteklerin sayısını azaltmak için kullanılan yaygın bir teknik, Orta katmanda önbelleğe alma için <xref:System.Data.DataSet> kullanmaktır. Örneğin, veri odaklı bir ASP.NET Web uygulaması düşünün. Genellikle, uygulama verilerinin önemli bir kısmı sık değişmez ve oturumlarda veya kullanıcılar arasında ortaktır. Bu veriler Web sunucusunda bellekte tutulabilir, bu da veritabanına yönelik istek sayısını azaltır ve kullanıcı etkileşimlerini hızlanır. <xref:System.Data.DataSet> bir diğer faydalı yönü, uygulamanın bir veya daha fazla veri kaynağından veri alt kümelerini uygulama alanına almasına izin verir. Uygulama daha sonra ilişkisel şeklini korurken verileri bellek içinde işleyebilir.  
  
 Bu da <xref:System.Data.DataSet>, sınırlı sayıda sorgu özelliğine sahip olmasına rağmen. <xref:System.Data.DataTable.Select%2A> yöntemi filtreleme ve sıralama için kullanılabilir ve <xref:System.Data.DataRow.GetChildRows%2A> ve <xref:System.Data.DataRow.GetParentRow%2A> yöntemleri hiyerarşi gezintisi için kullanılabilir. Ancak, daha karmaşık bir şey için, geliştiricinin özel bir sorgu yazması gerekir. Bu, kötü bir şekilde gerçekleştiren ve bakım zor olan uygulamaların oluşmasına neden olabilir.  
  
 LINQ to DataSet, bir <xref:System.Data.DataSet> nesnesinde önbelleğe alınan verilerin sorgulanmasını kolaylaştırır ve daha hızlı hale getirir. Bu sorgular, uygulama kodunda gömülü dize sabit değerleri yerine programlama dilinde ifade edilir. Bu, geliştiricilerin ayrı bir sorgu dili öğrenmelerine sahip olmadığı anlamına gelir. Ayrıca, LINQ to DataSet Visual Studio geliştiricilerin daha üretken bir şekilde çalışmasını sağlar çünkü Visual Studio IDE, derleme zamanı sözdizimi denetimi, statik yazma ve LINQ için IntelliSense desteği sağlar. LINQ to DataSet, bir veya daha fazla veri kaynağından birleştirilmiş verileri sorgulamak için de kullanılabilir. Bu, verilerin nasıl temsil edildiği ve işlendiği konusunda esneklik gerektiren birçok senaryoya izin vermez. Özellikle, genel raporlama, analiz ve iş zekası uygulamaları için bu işleme yöntemi gerekir.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>LINQ to DataSet kullanarak veri kümelerini sorgulama  
 LINQ to DataSet kullanarak bir <xref:System.Data.DataSet> nesnesini sorgulamaya başlayabilmeniz için önce <xref:System.Data.DataSet>doldurmanız gerekir. <xref:System.Data.Common.DataAdapter> sınıfını veya [LINQ to SQL](./sql/linq/index.md)kullanma gibi <xref:System.Data.DataSet>veri yüklemek için birkaç yol vardır. Veriler bir <xref:System.Data.DataSet> nesnesine yüklendikten sonra sorgulama işlemine başlayabilirsiniz. LINQ to DataSet kullanarak sorguları formüle eklemek, diğer LINQ özellikli veri kaynaklarına karşı dil ile tümleşik sorgu (LINQ) kullanılmasına benzerdir. LINQ sorguları, <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> standart sorgu işleçleri kullanılarak <xref:System.Data.DataSet> tek tablolara karşı veya birden fazla tabloya karşı gerçekleştirilebilir.  
  
 LINQ sorguları hem yazılan hem de untyped <xref:System.Data.DataSet> nesneleri için desteklenir. <xref:System.Data.DataSet> şeması uygulama tasarım zamanında biliniyorsa, yazılan bir <xref:System.Data.DataSet> önerilir. Türü belirtilmiş bir <xref:System.Data.DataSet>, tablolar ve satırlar her bir sütun için, sorguları daha basit ve daha okunaklı hale getiren üyelere sahiptir.  
  
 System. Core. dll ' de uygulanan standart sorgu işleçlerine ek olarak LINQ to DataSet, <xref:System.Data.DataRow> nesne kümesi üzerinde sorgu yapmayı kolaylaştıran birkaç <xref:System.Data.DataSet>özel uzantı ekler. Bu <xref:System.Data.DataSet>özgü uzantılar, satır dizilerini karşılaştırmak için İşleçleri ve bir <xref:System.Data.DataRow>sütun değerlerine erişim sağlayan yöntemleri içerir.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N katmanlı uygulamalar ve LINQ to DataSet  
 N katmanlı veri uygulamaları, birden çok mantıksal katmana (veya katmana) ayrılan veri merkezli uygulamalardır. Tipik N katmanlı bir uygulama, bir sunum katmanı, orta katman ve veri katmanı içerir. Uygulama bileşenlerini ayrı katmanlara ayırmak, uygulamanın bakım ve ölçeklenebilirlik düzeyini artırır. N katmanlı veri uygulamaları hakkında daha fazla bilgi için, bkz. [n katmanlı uygulamalarda veri kümeleriyle çalışma](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 N katmanlı uygulamalarda <xref:System.Data.DataSet>, genellikle bir Web uygulamasının bilgilerini önbelleğe almak için Orta katmanda kullanılır. LINQ to DataSet sorgulama işlevselliği, uzantı yöntemleri aracılığıyla uygulanır ve var olan ADO.NET 2,0 <xref:System.Data.DataSet>genişletir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’leri Sorgulama](querying-datasets-linq-to-dataset.md)
- [Dil ile tümleşik sorgu (LINQ)-C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Dil ile tümleşik sorgu (LINQ)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
