---
title: Veri Kümeleri
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: 86c14f516ff82e4d9acf7cc3078e04590971a8a1
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980307"
---
# <a name="adonet-datasets"></a>ADO.NET Veri Kümeleri
<xref:System.Data.DataSet> nesnesi, ADO.NET ile bağlı olmayan, dağıtılmış veri senaryolarını desteklemek için merkezi bir merkezidir. Veri **kümesi** , veri kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir. Bu, birden çok ve farklı veri kaynaklarıyla, XML verileriyle birlikte kullanılabilir veya uygulamadaki verileri yerel olarak yönetebilir. Veri **kümesi** , ilişkili tablolar, kısıtlamalar ve tablolar arasındaki ilişkiler dahil olmak üzere bir bütün veri kümesini temsil eder. Aşağıdaki çizimde **veri kümesi** nesne modeli gösterilmektedir.  
  
 ![ADO.Net grafiği](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Veri kümesi nesne modeli  
  
 Bir **veri kümesindeki** Yöntemler ve nesneler, ilişkisel veritabanı modelindeki olanlarla tutarlıdır.  
  
 **Veri kümesi** Ayrıca içeriğini XML olarak ve şeması XML şeması tanım DILI (xsd) şeması olarak kalıcı olarak yeniden yükleyebilir. Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 Bir ADO.NET **veri kümesi** <xref:System.Data.DataTable> nesneleriyle temsil edilen sıfır veya daha fazla tablo koleksiyonunu içerir. <xref:System.Data.DataTableCollection>, bir **veri kümesindeki**tüm **DataTable** nesnelerini içerir.  
  
 <xref:System.Data> ad alanında bir **DataTable** tanımlanmıştır ve bellekte yerleşik verilerin tek bir tablosunu temsil eder. Bir <xref:System.Data.DataColumnCollection>temsil eden bir sütun koleksiyonu ve bir <xref:System.Data.ConstraintCollection>tarafından temsil edilen ve bir arada tablo şemasını tanımlayan kısıtlamalar içerir. **DataTable** Ayrıca, tablodaki verileri içeren <xref:System.Data.DataRowCollection>temsil edilen satırların bir koleksiyonunu içerir. Geçerli durumu ile birlikte <xref:System.Data.DataRow>, satırda depolanan değerlerde yapılan değişiklikleri belirlemek için hem geçerli hem de orijinal sürümlerini korur.  
  
## <a name="the-dataview-class"></a>DataView sınıfı  
 <xref:System.Data.DataView>, genellikle veri bağlama uygulamalarında kullanılan bir özellik olan bir <xref:System.Data.DataTable>depolanan verilerin farklı görünümlerini oluşturmanızı sağlar. <xref:System.Data.DataView>kullanarak verileri farklı sıralama siparişleriyle bir tabloda kullanıma sunabilirsiniz ve verileri satır durumuna göre veya bir filtre ifadesine göre filtreleyebilirsiniz. Daha fazla bilgi için bkz. [DataView](./dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 Bir **veri kümesi** , <xref:System.Data.DataRelationCollection> nesnesinde ilişkiler içerir. <xref:System.Data.DataRelation> nesnesi tarafından temsil edilen bir ilişki, bir **DataTable** içindeki satırları başka bir **DataTable**içindeki satırlarla ilişkilendirir. İlişki, ilişkisel bir veritabanındaki birincil ve yabancı anahtar sütunları arasında mevcut olabilecek bir JOIN yoluna benzer. Bir **DataRelation** , eşleşen sütunları bir **veri kümesinin**iki tablosu içinde tanımlar.  
  
 İlişkiler bir **veri kümesindeki**bir tablodan diğerine gezinmeyi etkinleştirir. Bir **DataRelation** 'ın temel öğeleri ilişkinin adı, ilişkili tabloların adı ve her tablodaki ilgili sütunlar ' tır. İlişkiler, anahtar sütunları olarak bir dizi <xref:System.Data.DataColumn> nesneleri belirterek tablo başına birden fazla sütunla oluşturulabilir. <xref:System.Data.DataRelationCollection>bir ilişki eklediğinizde, ilgili sütun değerlerinde değişiklik yapıldığında bütünlük kısıtlamalarını zorlamak için isteğe bağlı olarak bir **UniqueKeyConstraint** ve **ForeignKeyConstraint** ekleyebilirsiniz.  
  
 Daha fazla bilgi için bkz. [DataRelation 'ı ekleme](./dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>{1&gt;XML&lt;1}  
 Bir **veri kümesini** bir XML akışından veya belgesinden doldurabilirsiniz. Veri **kümesine** verileri, şema bilgilerini veya her ikisini de sağlamak için XML Stream veya Document kullanabilirsiniz. XML akışından veya belgesinden sağlanan bilgiler, **veri kümesinde**zaten mevcut olan mevcut verilerle veya şema bilgileriyle birleştirilebilir. Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **DataSet**, **DataTable**ve **DataColumn** All 'un **ExtendedProperties** özelliği vardır. **ExtendedProperties** , sonuç kümesini oluşturmak IÇIN kullanılan Select açıklaması veya verilerin oluşturulduğu zaman gibi özel bilgileri yerleştirebileceğiniz bir **PropertyCollection** . **ExtendedProperties** koleksiyonu, **veri kümesinin**şema bilgileriyle kalıcı hale getirilir.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 LINQ to DataSet, veri kümesinde depolanan, bağlantısı kesilen veriler için dil ile tümleşik sorgulama özellikleri sağlar. LINQ to DataSet, standart LINQ söz dizimini kullanır ve Visual Studio IDE 'yi kullanırken derleme zamanı sözdizimi denetimi, statik yazma ve IntelliSense desteği sağlar.  
  
 Daha fazla bilgi için [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)
- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
