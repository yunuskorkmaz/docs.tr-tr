---
title: LINQ to DataSet Genel Bakış
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: de49febdc81eaf4f487423c5804d1e5cc897cdce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794969"
---
# <a name="linq-to-dataset-overview"></a>LINQ to DataSet Genel Bakış
, <xref:System.Data.DataSet> ADO.net 'in daha yaygın olarak kullanılan bileşenlerinden biridir. Bu, ADO.NET tarafından kullanılan, bağlantısı kesilen programlama modelinin temel öğesidir ve farklı veri kaynaklarından gelen verileri açıkça önbelleğe almanıza olanak sağlar. Sunum katmanı <xref:System.Data.DataSet> için, veri bağlama için GUI denetimleriyle sıkı bir şekilde tümleşiktir. Orta katman için, verilerin ilişkisel şeklini koruyan bir önbellek sağlar ve hızlı basit sorgu ve hiyerarşi gezinti hizmetlerini içerir. Bir veritabanındaki isteklerin sayısını azaltmak için kullanılan yaygın bir teknik, <xref:System.Data.DataSet> Orta katmanda önbelleğe alma için kullanılır. Örneğin, veri odaklı bir ASP.NET Web uygulaması düşünün. Genellikle, uygulama verilerinin önemli bir kısmı sık değişmez ve oturumlarda veya kullanıcılar arasında ortaktır. Bu veriler Web sunucusunda bellekte tutulabilir, bu da veritabanına yönelik istek sayısını azaltır ve kullanıcı etkileşimlerini hızlanır. Uygulamasının diğer yararlı bir yönü <xref:System.Data.DataSet> , bir uygulamanın bir veya daha fazla veri kaynağından veri alt kümelerini uygulama alanına almasına izin verir. Uygulama daha sonra ilişkisel şeklini korurken verileri bellek içinde işleyebilir.  
  
 Bunun göze çarbuna <xref:System.Data.DataSet> rağmen sınırlı sayıda sorgu özelliği vardır. Yöntemi filtreleme ve sıralama için kullanılabilir <xref:System.Data.DataRow.GetChildRows%2A> ve ve <xref:System.Data.DataRow.GetParentRow%2A> yöntemleri hiyerarşi gezintisi için kullanılabilir. <xref:System.Data.DataTable.Select%2A> Ancak, daha karmaşık bir şey için, geliştiricinin özel bir sorgu yazması gerekir. Bu, kötü bir şekilde gerçekleştiren ve bakım zor olan uygulamaların oluşmasına neden olabilir.  
  
 LINQ to DataSet, bir <xref:System.Data.DataSet> nesnede önbelleğe alınan verilerin sorgulanmasını kolaylaştırır ve daha hızlı hale getirir. Bu sorgular, uygulama kodunda gömülü dize sabit değerleri yerine programlama dilinde ifade edilir. Bu, geliştiricilerin ayrı bir sorgu dili öğrenmelerine sahip olmadığı anlamına gelir. Ayrıca, LINQ to DataSet Visual Studio geliştiricilerin daha üretken bir şekilde çalışmasını sağlar çünkü Visual Studio IDE, derleme zamanı sözdizimi denetimi, statik yazma ve IntelliSense desteği [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]sağlar. LINQ to DataSet, bir veya daha fazla veri kaynağından birleştirilmiş verileri sorgulamak için de kullanılabilir. Bu, verilerin nasıl temsil edildiği ve işlendiği konusunda esneklik gerektiren birçok senaryoya izin vermez. Özellikle, genel raporlama, analiz ve iş zekası uygulamaları için bu işleme yöntemi gerekir.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>LINQ to DataSet kullanarak veri kümelerini sorgulama  
 LINQ to DataSet kullanarak bir <xref:System.Data.DataSet> nesneyi sorgulamaya başlayabilmeniz için <xref:System.Data.DataSet>önce öğesini doldurmanız gerekir. ' <xref:System.Data.DataSet> A<xref:System.Data.Common.DataAdapter> veya [LINQ to SQL](./sql/linq/index.md)gibi bir veri yüklemek için birkaç yol vardır. Veriler bir <xref:System.Data.DataSet> nesneye yüklendikten sonra sorgu oluşturmaya başlayabilirsiniz. LINQ to DataSet kullanarak sorguları formüle eklemek, diğer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]etkin veri kaynaklarında kullanılmasına benzer. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]sorgular, <xref:System.Data.DataSet> <xref:System.Linq.Enumerable.Join%2A> ve Standartsorguişleçlerinikullanarakbirveyabirdenfazlatabloyakarşıtektablolarakarşıgerçekleştirilebilir.<xref:System.Linq.Enumerable.GroupJoin%2A>  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]sorgular hem yazılan hem de türsüz <xref:System.Data.DataSet> nesneler için desteklenir. Şeması <xref:System.Data.DataSet> uygulama tasarım zamanında biliniyorsa, bir türü <xref:System.Data.DataSet> önerilir. Bir tür <xref:System.Data.DataSet>içinde tablolar ve satırlar, her bir sütun için, sorguları daha basit ve daha okunaklı hale getiren bir üye türdedir.  
  
 System. Core. dll ' de uygulanan standart sorgu işleçlerine ek olarak LINQ to DataSet bir <xref:System.Data.DataSet> <xref:System.Data.DataRow> nesne kümesi üzerinde sorgu yapmayı kolaylaştıran birkaç özel uzantı ekler. Bu <xref:System.Data.DataSet>özel uzantılar, satır dizilerini karşılaştırmak için İşleçleri ve ' <xref:System.Data.DataRow>ın sütun değerlerine erişim sağlayan yöntemleri içerir.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N katmanlı uygulamalar ve LINQ to DataSet  
 N katmanlı veri uygulamaları, birden çok mantıksal katmana (veya katmana) ayrılan veri merkezli uygulamalardır. Tipik N katmanlı bir uygulama, bir sunum katmanı, orta katman ve veri katmanı içerir. Uygulama bileşenlerini ayrı katmanlara ayırmak, uygulamanın bakım ve ölçeklenebilirlik düzeyini artırır. N katmanlı veri uygulamaları hakkında daha fazla bilgi için, bkz. [n katmanlı uygulamalarda veri kümeleriyle çalışma](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 N katmanlı uygulamalarda <xref:System.Data.DataSet> , genellikle bir Web uygulamasının bilgilerini önbelleğe almak için Orta katmanda kullanılır. LINQ to DataSet sorgulama işlevselliği, uzantı yöntemleri aracılığıyla uygulanır ve var olan ADO.NET 2,0 <xref:System.Data.DataSet>' i genişletir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’leri Sorgulama](querying-datasets-linq-to-dataset.md)
- [Dil ile tümleşik sorgu (LINQ)-C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Dil ile tümleşik sorgu (LINQ)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
