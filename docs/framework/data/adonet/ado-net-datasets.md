---
title: Veri Kümeleri
description: ADO.NET içindeki veri kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan, bellekte yerleşik bir veri temsili olan veri kümesi hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: d78918773c3cc88d8a925788d81cdafdc0a2db27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153592"
---
# <a name="adonet-datasets"></a>ADO.NET Veri Kümeleri

<xref:System.Data.DataSet>Nesnesi, ADO.NET ile bağlı olmayan, dağıtılmış veri senaryolarını desteklemek için merkezi bir merkezidir. Veri **kümesi** , veri kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir. Bu, birden çok ve farklı veri kaynaklarıyla, XML verileriyle birlikte kullanılabilir veya uygulamadaki verileri yerel olarak yönetebilir. Veri **kümesi** , ilişkili tablolar, kısıtlamalar ve tablolar arasındaki ilişkiler dahil olmak üzere bir bütün veri kümesini temsil eder. Aşağıdaki çizimde **veri kümesi** nesne modeli gösterilmektedir.  
  
 ![ADO.Net grafiği](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Veri kümesi nesne modeli  
  
 Bir **veri kümesindeki** Yöntemler ve nesneler, ilişkisel veritabanı modelindeki olanlarla tutarlıdır.  
  
 **Veri kümesi** Ayrıca içeriğini XML olarak ve şeması XML şeması tanım DILI (xsd) şeması olarak kalıcı olarak yeniden yükleyebilir. Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  

 Bir ADO.NET **veri kümesi** , nesnelerle temsil edilen sıfır veya daha fazla tablo koleksiyonunu içerir <xref:System.Data.DataTable> . , <xref:System.Data.DataTableCollection> Bir **veri kümesindeki**tüm **DataTable** nesnelerini içerir.  
  
 Ad alanında bir **DataTable** tanımlanmıştır <xref:System.Data> ve bellekte yerleşik verilerin tek bir tablosunu temsil eder. Bir ile temsil edilen bir sütun koleksiyonu ve ile <xref:System.Data.DataColumnCollection> temsil edilen kısıtlamalar içerir <xref:System.Data.ConstraintCollection> , birlikte tablo şemasını tanımlar. **DataTable** , tablodaki verileri içeren ile temsil edilen satırların bir koleksiyonunu da içerir <xref:System.Data.DataRowCollection> . Geçerli durumuyla birlikte, bir, <xref:System.Data.DataRow> satırda depolanan değerlerde yapılan değişiklikleri belirlemek için hem geçerli hem de orijinal sürümlerini korur.  
  
## <a name="the-dataview-class"></a>DataView sınıfı  

 <xref:System.Data.DataView> <xref:System.Data.DataTable> , Genellikle veri bağlama uygulamalarında kullanılan bir özellik olan, içinde depolanan verilerin farklı görünümlerini oluşturmanızı sağlar. Kullanarak <xref:System.Data.DataView> , verileri farklı sıralama siparişleriyle bir tabloda kullanıma sunabilirsiniz ve verileri satır durumuna göre veya bir filtre ifadesine göre filtreleyebilirsiniz. Daha fazla bilgi için bkz. [DataView](./dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  

 Bir **veri kümesi** kendi nesnesinde ilişkiler içerir <xref:System.Data.DataRelationCollection> . Nesneyle temsil edilen bir ilişki, bir <xref:System.Data.DataRelation> **DataTable** içindeki satırları başka bir **DataTable**'daki satırlarla ilişkilendirir. İlişki, ilişkisel bir veritabanındaki birincil ve yabancı anahtar sütunları arasında mevcut olabilecek bir JOIN yoluna benzer. Bir **DataRelation** , eşleşen sütunları bir **veri kümesinin**iki tablosu içinde tanımlar.  
  
 İlişkiler bir **veri kümesindeki**bir tablodan diğerine gezinmeyi etkinleştirir. Bir **DataRelation** 'ın temel öğeleri ilişkinin adı, ilişkili tabloların adı ve her tablodaki ilgili sütunlar ' tır. İlişkiler <xref:System.Data.DataColumn> , bir nesne dizisini anahtar sütunları olarak belirterek tablo başına birden fazla sütunla oluşturulabilir. Öğesine bir ilişki eklediğinizde <xref:System.Data.DataRelationCollection> , ilgili sütun değerlerinde değişiklik yapıldığında bütünlük kısıtlamalarını zorlamak için isteğe bağlı olarak **UniqueKeyConstraint** ve **ForeignKeyConstraint** ekleyebilirsiniz.  
  
 Daha fazla bilgi için bkz. [DataRelation 'ı ekleme](./dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  

 Bir **veri kümesini** bir XML akışından veya belgesinden doldurabilirsiniz. Veri **kümesine** verileri, şema bilgilerini veya her ikisini de sağlamak için XML Stream veya Document kullanabilirsiniz. XML akışından veya belgesinden sağlanan bilgiler, **veri kümesinde**zaten mevcut olan mevcut verilerle veya şema bilgileriyle birleştirilebilir. Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  

 **DataSet**, **DataTable**ve **DataColumn** All 'un **ExtendedProperties** özelliği vardır. **ExtendedProperties** , sonuç kümesini oluşturmak IÇIN kullanılan Select açıklaması veya verilerin oluşturulduğu zaman gibi özel bilgileri yerleştirebileceğiniz bir **PropertyCollection** . **ExtendedProperties** koleksiyonu, **veri kümesinin**şema bilgileriyle kalıcı hale getirilir.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  

 LINQ to DataSet, veri kümesinde depolanan, bağlantısı kesilen veriler için dil ile tümleşik sorgulama özellikleri sağlar. LINQ to DataSet, standart LINQ söz dizimini kullanır ve Visual Studio IDE 'yi kullanırken derleme zamanı sözdizimi denetimi, statik yazma ve IntelliSense desteği sağlar.  
  
 Daha fazla bilgi için bkz. [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)
- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
