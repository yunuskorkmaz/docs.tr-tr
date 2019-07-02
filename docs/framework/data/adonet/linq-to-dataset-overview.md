---
title: LINQ to DataSet Genel Bakış
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: f60308b122841421613d8e1f84aa5b9a23cc3315
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504443"
---
# <a name="linq-to-dataset-overview"></a>LINQ to DataSet Genel Bakış
<xref:System.Data.DataSet> ADO.NET daha yaygın olarak kullanılan bileşenlerden biridir. ADO.NET dayanır bağlantısı kesilmiş bir programlama modeli anahtar öğesi olduğundan ve açıkça bu verileri önbelleğe almak için farklı veri kaynaklarından sağlar. Sunu katmanı için <xref:System.Data.DataSet> GUI denetimleri için veri bağlama ile tümleşiktir. Orta katman için ilişkisel veri şeklini korur ve hızlı Basit Sorgu ve hiyerarşi Gezinti hizmetleri içeren bir önbellek sağlar. Bir veritabanı isteklerinde sayısını azaltmak için kullanılan genel bir tekniktir kullanmaktır <xref:System.Data.DataSet> Orta katmanda önbelleğe alma. Örneğin, veri odaklı bir ASP.NET Web uygulamasına göz önünde bulundurun. Genellikle, uygulama verilerinin büyük bir kısmı sık değişmeyen ve oturumlar veya kullanıcılar arasında yaygındır. Bu verileri, veritabanında istek sayısını azaltan ve kullanıcının etkileşim hızlandırır Web sunucusu üzerindeki bellekte tutulabilir. Başka bir kullanışlı yönüyle <xref:System.Data.DataSet> veri kümelerine bir veya daha fazla veri kaynağından uygulama alanına taşıyacak şekilde olanak tanımasıdır. Uygulama, ilişkisel şeklini korurken verileri bellek içinde daha sonra değiştirebilirsiniz.  
  
 Kendi teklifleriyle rağmen <xref:System.Data.DataSet> sorgu özellikleri sınırlıdır. <xref:System.Data.DataTable.Select%2A> Yöntemi, filtreleme ve sıralama için kullanılabilir ve <xref:System.Data.DataRow.GetChildRows%2A> ve <xref:System.Data.DataRow.GetParentRow%2A> yöntemleri hiyerarşi gezinme için kullanılabilir. Geliştirici her şey için daha karmaşık, ancak özel sorgu yazmalısınız. Bu, sonlanmayacağından ve bakımını yapmak zor olan uygulamalarda neden olabilir.  
  
 LINQ to DataSet kolaylaştırır ve veriler üzerinde sorgu için daha hızlı bir şekilde önbelleğe bir <xref:System.Data.DataSet> nesne. Bu sorguları programlama dilinde ifade edilir yerine gibi uygulama koduna katıştırılmış dize sabitleri. Başka bir deyişle, geliştiriciler ayrı sorgu dil öğrenmek gerekmez. Ayrıca, LINQ to DataSet Visual Studio geliştiricilerinin daha üretken bir şekilde çalışmasını sağlayan çünkü Visual Studio IDE, derleme zamanı söz dizimi denetimini, statik yazmaya ve IntelliSense desteğini sağlar [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. LINQ to DataSet de kullanılabilir bir veya daha fazla veri kaynağından birleştirilmiş veriler üzerinde sorgu için. Bu verilerin nasıl temsil edilen ve işlenmiş esneklik gerektiren birçok senaryolar sağlar. Özellikle, bu yöntem işlemlerinde genel raporlama, analiz ve iş zekası uygulamaları gerektirir.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>LINQ to DataSet kullanarak DataSet'leri sorgulama  
 Sorgulama başlamadan önce bir <xref:System.Data.DataSet> LINQ to DataSet kullanarak nesne doldurmanız gerekir <xref:System.Data.DataSet>. Veri yükleme birkaç şekilde bir <xref:System.Data.DataSet>, kullanma gibi <xref:System.Data.Common.DataAdapter> sınıfı veya [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md). Veri uygulamasına yüklendikten sonra bir <xref:System.Data.DataSet> nesne sorgulamanız bunu başlayabilirsiniz. LINQ to DataSet kullanarak sorguları formulating kullanmaya benzer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] diğer karşı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-veri kaynakları etkin. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgular tek tablolarında karşı gerçekleştirilebilir bir <xref:System.Data.DataSet> veya karşı kullanarak birden fazla tablo <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> standart sorgu işleçleridir.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorguları ve ikisi de karşı yazılan türsüz desteklenir <xref:System.Data.DataSet> nesneleri. Varsa şemasını <xref:System.Data.DataSet> uygulama tasarım zamanında, bir türü belirtilmiş bilinen <xref:System.Data.DataSet> önerilir. İçinde bir türü belirtilmiş <xref:System.Data.DataSet>, tabloları ve satırları her sorguları daha basit ve daha okunabilir hale getirir. sütun olarak belirtilmiş üyeler olmalıdır.  
  
 Standart sorgu işleçleri System.Core.dll içinde uygulanan ek LINQ to DataSet birkaç ekler <xref:System.Data.DataSet>-üzerinde bir dizi sorgu daha kolay hale getirmek belirli uzantılara <xref:System.Data.DataRow> nesneleri. Bunlar <xref:System.Data.DataSet>-sütun değerlerine erişim sağlayan yöntemler yanı sıra satırları dizileri karşılaştırmak için belirli uzantılara işleçleri içeren bir <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N katmanlı uygulamalar ve LINQ to DataSet  
 N katmanlı veri uygulamaları birden çok mantıksal katmanları (veya katmanları) ayrılmış veri merkezli uygulamalardır. Tipik bir N katmanlı uygulamanın sunu katmanı, bir orta katman ve bir veri katmanı içerir. Uygulama bileşenleri ayrı katmanlara ayırmak Bakım ve uygulama'nın ölçeklenebilirliğini artırır. N katmanlı veri uygulamaları hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 N katmanlı uygulamalarda <xref:System.Data.DataSet> genellikle Orta katmanda bilgiyi önbelleğe bir Web uygulaması için kullanılır. LINQ to DataSet işlevi sorgulanırken genişletme yöntemleri uygulanır ve mevcut ADO.NET 2.0 genişletir <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Dil ile tümleşik sorgu (LINQ)-C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Dil ile tümleşik sorgu (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
