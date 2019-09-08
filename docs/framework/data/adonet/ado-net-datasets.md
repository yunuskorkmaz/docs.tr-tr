---
title: ADO.NET Veri Kümeleri
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: acbe5a549539a77d63332687486cbe8744592f8b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786979"
---
# <a name="adonet-datasets"></a>ADO.NET Veri Kümeleri
<xref:System.Data.DataSet> Nesnesi, ADO.NET ile bağlı olmayan, dağıtılmış veri senaryolarını desteklemek için merkezi bir merkezidir. Veri **kümesi** , veri kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir. Bu, birden çok ve farklı veri kaynaklarıyla, XML verileriyle birlikte kullanılabilir veya uygulamadaki verileri yerel olarak yönetebilir. Veri **kümesi** , ilişkili tablolar, kısıtlamalar ve tablolar arasındaki ilişkiler dahil olmak üzere bir bütün veri kümesini temsil eder. Aşağıdaki çizimde **veri kümesi** nesne modeli gösterilmektedir.  
  
 ![ADO.net grafiği](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Veri kümesi nesne modeli  
  
 Bir **veri kümesindeki** Yöntemler ve nesneler, ilişkisel veritabanı modelindeki olanlarla tutarlıdır.  
  
 **Veri kümesi** Ayrıca içeriğini XML olarak ve şeması XML şeması tanım DILI (xsd) şeması olarak kalıcı olarak yeniden yükleyebilir. Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 Bir ADO.net **veri kümesi** , <xref:System.Data.DataTable> nesnelerle temsil edilen sıfır veya daha fazla tablo koleksiyonunu içerir. , <xref:System.Data.DataTableCollection> Bir **veri kümesindeki**tüm **DataTable** nesnelerini içerir.  
  
 <xref:System.Data> Ad alanında bir **DataTable** tanımlanmıştır ve bellekte yerleşik verilerin tek bir tablosunu temsil eder. Bir <xref:System.Data.DataColumnCollection>ile temsil edilen bir sütun koleksiyonu ve ile temsil edilen <xref:System.Data.ConstraintCollection>kısıtlamalar içerir, birlikte tablo şemasını tanımlar. **DataTable** , tablodaki verileri içeren ile <xref:System.Data.DataRowCollection>temsil edilen satırların bir koleksiyonunu da içerir. Geçerli durumuyla birlikte, bir <xref:System.Data.DataRow> , satırda depolanan değerlerde yapılan değişiklikleri belirlemek için hem geçerli hem de orijinal sürümlerini korur.  
  
## <a name="the-dataview-class"></a>DataView sınıfı  
 , Genellikle veri bağlama uygulamalarında kullanılan bir özellik olan, <xref:System.Data.DataView> içinde depolanan verilerin farklı görünümlerini <xref:System.Data.DataTable>oluşturmanızı sağlar. <xref:System.Data.DataView>Kullanarak, verileri farklı sıralama siparişleriyle bir tabloda kullanıma sunabilirsiniz ve verileri satır durumuna göre veya bir filtre ifadesine göre filtreleyebilirsiniz. Daha fazla bilgi için bkz. [DataView](./dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 Bir **veri kümesi** kendi <xref:System.Data.DataRelationCollection> nesnesinde ilişkiler içerir. <xref:System.Data.DataRelation> Nesneyle temsil edilen bir ilişki, bir **DataTable** içindeki satırları başka bir **DataTable**'daki satırlarla ilişkilendirir. İlişki, ilişkisel bir veritabanındaki birincil ve yabancı anahtar sütunları arasında mevcut olabilecek bir JOIN yoluna benzer. Bir **DataRelation** , eşleşen sütunları bir **veri kümesinin**iki tablosu içinde tanımlar.  
  
 İlişkiler bir **veri kümesindeki**bir tablodan diğerine gezinmeyi etkinleştirir. Bir **DataRelation** 'ın temel öğeleri ilişkinin adı, ilişkili tabloların adı ve her tablodaki ilgili sütunlar ' tır. İlişkiler, bir <xref:System.Data.DataColumn> nesne dizisini anahtar sütunları olarak belirterek tablo başına birden fazla sütunla oluşturulabilir. Öğesine <xref:System.Data.DataRelationCollection>bir ilişki eklediğinizde, ilgili sütun değerlerinde değişiklik yapıldığında bütünlük kısıtlamalarını zorlamak için isteğe bağlı olarak **UniqueKeyConstraint** ve **ForeignKeyConstraint** ekleyebilirsiniz.  
  
 Daha fazla bilgi için bkz. [DataRelation 'ı ekleme](./dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Bir **veri kümesini** bir XML akışından veya belgesinden doldurabilirsiniz. Veri **kümesine** verileri, şema bilgilerini veya her ikisini de sağlamak için XML Stream veya Document kullanabilirsiniz. XML akışından veya belgesinden sağlanan bilgiler, **veri kümesinde**zaten mevcut olan mevcut verilerle veya şema bilgileriyle birleştirilebilir. Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **DataSet**, **DataTable**ve **DataColumn** All 'un **ExtendedProperties** özelliği vardır. **ExtendedProperties** , sonuç kümesini oluşturmak IÇIN kullanılan Select açıklaması veya verilerin oluşturulduğu zaman gibi özel bilgileri yerleştirebileceğiniz bir **PropertyCollection** . **ExtendedProperties** koleksiyonu, **veri kümesinin**şema bilgileriyle kalıcı hale getirilir.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 LINQ to DataSet, veri kümesinde depolanan, bağlantısı kesilen veriler için dil ile tümleşik sorgulama özellikleri sağlar. LINQ to DataSet, standart [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sözdizimini kullanır ve Visual Studio IDE 'yi kullanırken derleme zamanı sözdizimi denetimi, statik yazma ve IntelliSense desteği sağlar.  
  
 Daha fazla bilgi için [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)
- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
