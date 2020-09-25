---
title: LINQ to DataSet Genel Bakış
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: f7659d03005df69d7debe604581ce49973f938cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200621"
---
# <a name="linq-to-dataset-overview"></a>LINQ to DataSet Genel Bakış

, <xref:System.Data.DataSet> ADO.net 'in daha yaygın olarak kullanılan bileşenlerinden biridir. Bu, ADO.NET tarafından kullanılan, bağlantısı kesilen programlama modelinin temel öğesidir ve farklı veri kaynaklarından gelen verileri açıkça önbelleğe almanıza olanak sağlar. Sunum katmanı için, <xref:System.Data.DataSet> veri bağlama IÇIN GUI denetimleriyle sıkı bir şekilde tümleşiktir. Orta katman için, verilerin ilişkisel şeklini koruyan bir önbellek sağlar ve hızlı basit sorgu ve hiyerarşi gezinti hizmetlerini içerir. Bir veritabanındaki isteklerin sayısını azaltmak için kullanılan yaygın bir teknik, <xref:System.Data.DataSet> Orta katmanda önbelleğe alma için kullanılır. Örneğin, veri odaklı bir ASP.NET Web uygulaması düşünün. Genellikle, uygulama verilerinin önemli bir kısmı sık değişmez ve oturumlarda veya kullanıcılar arasında ortaktır. Bu veriler Web sunucusunda bellekte tutulabilir, bu da veritabanına yönelik istek sayısını azaltır ve kullanıcı etkileşimlerini hızlanır. Uygulamasının diğer yararlı bir yönü, bir <xref:System.Data.DataSet> uygulamanın bir veya daha fazla veri kaynağından veri alt kümelerini uygulama alanına almasına izin verir. Uygulama daha sonra ilişkisel şeklini korurken verileri bellek içinde işleyebilir.  
  
 Bunun göze çarbuna rağmen <xref:System.Data.DataSet> sınırlı sayıda sorgu özelliği vardır. <xref:System.Data.DataTable.Select%2A>Yöntemi filtreleme ve sıralama için kullanılabilir ve <xref:System.Data.DataRow.GetChildRows%2A> ve <xref:System.Data.DataRow.GetParentRow%2A> yöntemleri hiyerarşi gezintisi için kullanılabilir. Ancak, daha karmaşık bir şey için, geliştiricinin özel bir sorgu yazması gerekir. Bu, kötü bir şekilde gerçekleştiren ve bakım zor olan uygulamaların oluşmasına neden olabilir.  
  
 LINQ to DataSet, bir nesnede önbelleğe alınan verilerin sorgulanmasını kolaylaştırır ve daha hızlı hale getirir <xref:System.Data.DataSet> . Bu sorgular, uygulama kodunda gömülü dize sabit değerleri yerine programlama dilinde ifade edilir. Bu, geliştiricilerin ayrı bir sorgu dili öğrenmelerine sahip olmadığı anlamına gelir. Ayrıca, LINQ to DataSet Visual Studio geliştiricilerin daha üretken bir şekilde çalışmasını sağlar çünkü Visual Studio IDE, derleme zamanı sözdizimi denetimi, statik yazma ve LINQ için IntelliSense desteği sağlar. LINQ to DataSet, bir veya daha fazla veri kaynağından birleştirilmiş verileri sorgulamak için de kullanılabilir. Bu, verilerin nasıl temsil edildiği ve işlendiği konusunda esneklik gerektiren birçok senaryoya izin vermez. Özellikle, genel raporlama, analiz ve iş zekası uygulamaları için bu işleme yöntemi gerekir.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>LINQ to DataSet kullanarak veri kümelerini sorgulama  

 LINQ to DataSet kullanarak bir nesneyi sorgulamaya başlayabilmeniz <xref:System.Data.DataSet> için önce öğesini doldurmanız gerekir <xref:System.Data.DataSet> . <xref:System.Data.DataSet>' A <xref:System.Data.Common.DataAdapter> veya [LINQ to SQL](./sql/linq/index.md)gibi bir veri yüklemek için birkaç yol vardır. Veriler bir nesneye yüklendikten sonra <xref:System.Data.DataSet> sorgu oluşturmaya başlayabilirsiniz. LINQ to DataSet kullanarak sorguları formüle eklemek, diğer LINQ özellikli veri kaynaklarına karşı dil ile tümleşik sorgu (LINQ) kullanılmasına benzerdir. LINQ sorguları <xref:System.Data.DataSet> , <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> Standart sorgu işleçlerini kullanarak bir veya birden fazla tabloya karşı tek tablolara karşı gerçekleştirilebilir.  
  
 LINQ sorguları hem yazılan hem de türsüz nesneler için desteklenir <xref:System.Data.DataSet> . Şeması <xref:System.Data.DataSet> uygulama tasarım zamanında biliniyorsa, bir türü <xref:System.Data.DataSet> önerilir. Bir tür içinde <xref:System.Data.DataSet> Tablolar ve satırlar, her bir sütun için, sorguları daha basit ve daha okunaklı hale getiren bir üye türdedir.  
  
 System.Core.dll uygulanan standart sorgu işleçlerinin yanı sıra, LINQ to DataSet <xref:System.Data.DataSet> bir nesne kümesi üzerinde sorgu yapmayı kolaylaştıran birkaç özel uzantı ekler <xref:System.Data.DataRow> . Bu <xref:System.Data.DataSet> Özel uzantılar, satır dizilerini karşılaştırmak için İşleçleri ve ' ın sütun değerlerine erişim sağlayan yöntemleri içerir <xref:System.Data.DataRow> .  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N katmanlı uygulamalar ve LINQ to DataSet  

 N katmanlı veri uygulamaları, birden çok mantıksal katmana (veya katmana) ayrılan veri merkezli uygulamalardır. Tipik N katmanlı bir uygulama, bir sunum katmanı, orta katman ve veri katmanı içerir. Uygulama bileşenlerini ayrı katmanlara ayırmak, uygulamanın bakım ve ölçeklenebilirlik düzeyini artırır. N katmanlı veri uygulamaları hakkında daha fazla bilgi için, bkz. [n katmanlı uygulamalarda veri kümeleriyle çalışma](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 N katmanlı uygulamalarda, <xref:System.Data.DataSet> genellikle bir Web uygulamasının bilgilerini önbelleğe almak için Orta katmanda kullanılır. LINQ to DataSet sorgulama işlevselliği, uzantı yöntemleri aracılığıyla uygulanır ve var olan ADO.NET 2,0 ' i genişletir <xref:System.Data.DataSet> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’leri Sorgulama](querying-datasets-linq-to-dataset.md)
- [Dil ile tümleşik sorgu (LINQ)-C #](../../../csharp/programming-guide/concepts/linq/index.md)
- [Dil ile tümleşik sorgu (LINQ)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ - SQL](./sql/linq/index.md)
