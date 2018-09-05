---
title: ADO.NET veri kümeleri
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: e4f2aeca72404379a9cebbfacda77f98a9e85bf3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565100"
---
# <a name="adonet-datasets"></a>ADO.NET veri kümeleri
<xref:System.Data.DataSet> Dağıtılmış veri senaryoları ile bağlantı kesildi, nesne Destek Merkezi [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. **Veri kümesi** bir veri kaynağını bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan veri bellekte gösterimidir. Birden çok ile kullanılabilir ve farklı veri kaynakları, XML verileriyle veya uygulamaya yerel verileri yönetmek için. **Veri kümesi** ilgili tabloları, kısıtlamalar ve tablolar arasındaki ilişkiler dahil eksiksiz bir kümesini temsil eder. Aşağıdaki çizimde gösterildiği **veri kümesi** nesne modeli.  
  
 ![ADO.Net grafik](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Veri kümesi nesne modeli  
  
 Nesneleri ve yöntemleri bir **veri kümesi** ilişkisel veritabanı modeli içinde tutarlıdır.  
  
 **Veri kümesi** ayrıca kalıcı hale getirmek ve XML içeriği ve şeması XML Şeması Tanım Dili (XSD) şemaya olarak yeniden yükleyin. Daha fazla bilgi için [kullanarak bir veri kümesi XML'de](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataRow  
 Bir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **veri kümesi** sıfır veya daha fazla tablo ile temsil edilen bir koleksiyon içeren <xref:System.Data.DataTable> nesneleri. <xref:System.Data.DataTableCollection> Tüm içeren **DataTable** nesneler bir **veri kümesi**.  
  
 A **DataTable** tanımlanan <xref:System.Data> ad alanı ve bellekte verilerin tek bir tabloyu temsil eder. Tarafından temsil edilen sütunlar koleksiyonu içeren bir <xref:System.Data.DataColumnCollection>ve kısıtlamalar tarafından temsil edilen bir <xref:System.Data.ConstraintCollection>, tablonun şeması birlikte tanımlayan. A **DataTable** tarafından temsil edilen bir koleksiyonu içerir <xref:System.Data.DataRowCollection>, tablodaki verileri içerir. Geçerli durumuna yanı sıra bir <xref:System.Data.DataRow> satır içinde depolanan değerleri yapılan değişiklikleri belirlemek için her iki, geçerli ve orijinal sürümler korur.  
  
## <a name="the-dataview-class"></a>DataView sınıfı  
 A <xref:System.Data.DataView> depolanan veriler alanının farklı görünümlerini oluşturmanızı sağlayan bir <xref:System.Data.DataTable>, veri bağlama uygulamalarda sık kullanılan bir özellik. Kullanarak bir <xref:System.Data.DataView>sıralamalar farklı olan bir tabloda verilerini açığa çıkarabilir ve verileri satır durum ya da bir filtre ifadesi temelinde göre filtre uygulayabilirsiniz. Daha fazla bilgi için [DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A **veri kümesi** ilişkileri içeren kendi <xref:System.Data.DataRelationCollection> nesne. Tarafından temsil edilen bir ilişki <xref:System.Data.DataRelation> nesnesi, bir ilişkilendirir satırlarda **DataTable** başka bir satır içeren **DataTable**. Bir ilişki, ilişkisel bir veritabanındaki birincil ve yabancı anahtar sütun arasında mevcut olabilecek bir birleşim yola benzerdir. A **DataRelation** eşleşen sütunları iki tablodaki tanımlayan bir **veri kümesi**.  
  
 İlişkiler başka bir tablodan gezintiyi etkinleştir bir **veri kümesi**. Temel öğelerini bir **DataRelation** ilişki adı, ilişkili tablo adını ve ilgili sütunları her tablo. İlişkiler oluşturulabilen tablo başına birden fazla sütun içeren bir dizi belirterek <xref:System.Data.DataColumn> nesneleri anahtar sütunları olarak. Arasında bir ilişki eklediğinizde <xref:System.Data.DataRelationCollection>, isteğe bağlı olarak ekleyebileceğiniz bir **UniqueKeyConstraint** ve **ForeignKeyConstraint** ilgili sütununa değişiklik yapıldığında bütünlük kısıtlamaları uygulamak için değerler.  
  
 Daha fazla bilgi için [DataRelations ekleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Doldurmak için bir **veri kümesi** bir XML akışı veya belge. XML akışı veya belge için sağlamak için kullanabileceğiniz **veri kümesi** verileri, şema bilgileri veya her ikisi de. XML akışı ya da belge sağlanan bilgilerin mevcut verileriniz veya şema bilgileri zaten var. birleştirilebilir **veri kümesi**. Daha fazla bilgi için [kullanarak bir veri kümesi XML'de](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **Veri kümesi**, **DataTable**, ve **DataColumn** tüm bir **ExtendedProperties** özelliği. **ExtendedProperties** olduğu bir **PropertyCollection** nereye yerleştirmeniz sonuç kümesi oluşturmak için kullanılan bir SELECT deyimi veya verilerin ne zaman oluşturulduğu zaman gibi özel bilgiler. **ExtendedProperties** koleksiyonu için şema bilgileri ile kalıcıdır **veri kümesi**.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bir veri kümesinde depolanan bağlantısı kesilen veriler için dil ile tümleşik sorgulama özellikleri sağlar. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Standart kullanır [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] söz dizimi ve Visual Studio IDE kullanırken, derleme zamanı söz dizimi denetimini, statik yazmaya ve IntelliSense desteğini sağlar.  
  
 Daha fazla bilgi için [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
