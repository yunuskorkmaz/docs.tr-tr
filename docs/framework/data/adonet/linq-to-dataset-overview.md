---
title: LINQ to DataSet genel bakış
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: 43c3aa081bd934202bd3a7831741054115d7a6d5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739356"
---
# <a name="linq-to-dataset-overview"></a>LINQ to DataSet genel bakış
<xref:System.Data.DataSet> Daha yaygın olarak kullanılan bileşenlerden biri [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Anahtar öğesi bağlantısı kesilmiş olan programlama modeli [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] , temel alır ve onu açıkça bu verileri önbelleğe almak için farklı veri kaynaklarından sağlar. Sunu katmanı için <xref:System.Data.DataSet> GUI denetimleri için veri bağlama ile tümleşiktir. Orta katman için ilişkisel veri şeklini korur ve hızlı Basit Sorgu ve hiyerarşi Gezinti hizmetleri içeren bir önbellek sağlar. Bir veritabanı isteklerinde sayısını azaltmak için kullanılan genel bir tekniktir kullanmaktır <xref:System.Data.DataSet> Orta katmanda önbelleğe alma. Örneğin, veri odaklı düşünün [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması. Genellikle, uygulama verilerinin büyük bir kısmı sık değişmeyen ve oturumlar veya kullanıcılar arasında yaygındır. Bu verileri, veritabanında istek sayısını azaltan ve kullanıcının etkileşim hızlandırır Web sunucusu üzerindeki bellekte tutulabilir. Başka bir kullanışlı yönüyle <xref:System.Data.DataSet> veri kümelerine bir veya daha fazla veri kaynağından uygulama alanına taşıyacak şekilde olanak tanımasıdır. Uygulama, ilişkisel şeklini korurken verileri bellek içinde daha sonra değiştirebilirsiniz.  
  
 Kendi teklifleriyle rağmen <xref:System.Data.DataSet> sorgu özellikleri sınırlıdır. <xref:System.Data.DataTable.Select%2A> Yöntemi, filtreleme ve sıralama için kullanılabilir ve <xref:System.Data.DataRow.GetChildRows%2A> ve <xref:System.Data.DataRow.GetParentRow%2A> yöntemleri hiyerarşi gezinme için kullanılabilir. Geliştirici her şey için daha karmaşık, ancak özel sorgu yazmalısınız. Bu, sonlanmayacağından ve bakımını yapmak zor olan uygulamalarda neden olabilir.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] daha kolay ve hızlı sorgu için verileri önbelleğe üzerinde kolaylaştırır bir <xref:System.Data.DataSet> nesne. Bu sorguları programlama dilinde ifade edilir yerine gibi uygulama koduna katıştırılmış dize sabitleri. Başka bir deyişle, geliştiriciler ayrı sorgu dil öğrenmek gerekmez. Ayrıca, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Visual Studio IDE derleme zamanı söz dizimi denetimini, statik yazmaya ve IntelliSense desteğini sağlar çünkü Visual Studio geliştiricilerinin daha üretken bir şekilde çalışmasını sağlayan [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Ayrıca bir veya daha fazla veri kaynağından birleştirilmiş veriler üzerinde sorgu için. Bu verilerin nasıl temsil edilen ve işlenmiş esneklik gerektiren birçok senaryolar sağlar. Özellikle, bu yöntem işlemlerinde genel raporlama, analiz ve iş zekası uygulamaları gerektirir.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>LINQ to DataSet kullanarak DataSet'leri sorgulama  
 Sorgulama başlamadan önce bir <xref:System.Data.DataSet> kullanarak nesne [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], doldurmanız gerekir <xref:System.Data.DataSet>. Veri yükleme birkaç şekilde bir <xref:System.Data.DataSet>, kullanma gibi <xref:System.Data.Common.DataAdapter> sınıfı veya [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md). Veri uygulamasına yüklendikten sonra bir <xref:System.Data.DataSet> nesne sorgulamanız bunu başlayabilirsiniz. Formulating sorgular kullanarak [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanmaya benzer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] diğer karşı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-veri kaynakları etkin. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgular tek tablolarında karşı gerçekleştirilebilir bir <xref:System.Data.DataSet> veya karşı kullanarak birden fazla tablo <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> standart sorgu işleçleridir.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorguları ve ikisi de karşı yazılan türsüz desteklenir <xref:System.Data.DataSet> nesneleri. Varsa şemasını <xref:System.Data.DataSet> uygulama tasarım zamanında, bir türü belirtilmiş bilinen <xref:System.Data.DataSet> önerilir. İçinde bir türü belirtilmiş <xref:System.Data.DataSet>, tabloları ve satırları her sorguları daha basit ve daha okunabilir hale getirir. sütun olarak belirtilmiş üyeler olmalıdır.  
  
 System.Core.dll içinde uygulanan standart sorgu işleçleri yanı sıra [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] birkaç ekler <xref:System.Data.DataSet>-üzerinde bir dizi sorgu daha kolay hale getirmek belirli uzantılara <xref:System.Data.DataRow> nesneleri. Bunlar <xref:System.Data.DataSet>-sütun değerlerine erişim sağlayan yöntemler yanı sıra satırları dizileri karşılaştırmak için belirli uzantılara işleçleri içeren bir <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N katmanlı uygulamalar ve LINQ to DataSet  
 N katmanlı veri uygulamaları birden çok mantıksal katmanları (veya katmanları) ayrılmış veri merkezli uygulamalardır. Tipik bir N katmanlı uygulamanın sunu katmanı, bir orta katman ve bir veri katmanı içerir. Uygulama bileşenleri ayrı katmanlara ayırmak Bakım ve uygulama'nın ölçeklenebilirliğini artırır. N katmanlı veri uygulamaları hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 N katmanlı uygulamalarda <xref:System.Data.DataSet> genellikle Orta katmanda bilgiyi önbelleğe bir Web uygulaması için kullanılır. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] İşlevi sorgulanırken genişletme yöntemleri uygulanır ve mevcut ADO.NET 2.0 genişletir <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [LINQ (dil ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
