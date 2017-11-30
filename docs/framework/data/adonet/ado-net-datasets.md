---
title: "ADO.NET veri kümeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dce5f5ae2d672349c21a89bb35a56da0b11f864a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="adonet-datasets"></a>ADO.NET veri kümeleri
<xref:System.Data.DataSet> Dağıtılmış veri senaryoları ile bağlantısı kesildi, Destek Merkezi nesnesidir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. **DataSet** bir veri kaynağı bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlar veri bellekte gösterimidir. Birden fazla ile kullanılabilir ve farklı veri kaynakları, XML verileriyle ya da uygulamaya yerel verileri yönetmek için. **DataSet** ilişkili tabloları, kısıtlamalar ve tablolar arasında ilişkiler gibi veriler, eksiksiz bir kümesini temsil eder. Aşağıdaki çizimde gösterildiği **DataSet** nesne modeli.  
  
 ![ADO.Net grafiği](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Veri kümesi nesne modeli  
  
 Nesneler ve yöntemler bir **DataSet** ilişkisel veritabanı modeli de tutarlıdır.  
  
 **DataSet** da kalır ve içeriğinin XML olarak ve kendi şeması XML Şeması Tanım Dili (XSD) şeması olarak yeniden yükleyin. Daha fazla bilgi için bkz: [XML kullanarak bir veri kümesinde](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataRow  
 Bir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **DataSet** tarafından temsil edilen sıfır veya daha fazla tablo oluşan bir koleksiyon içeren <xref:System.Data.DataTable> nesneleri. <xref:System.Data.DataTableCollection> Tüm içeren **DataTable** nesnelerini bir **DataSet**.  
  
 A **DataTable** tanımlanan <xref:System.Data> ad alanı ve bellekte verilerin tek bir tabloyu temsil eder. Tarafından temsil edilen sütunlar oluşan bir koleksiyon içeren bir <xref:System.Data.DataColumnCollection>ve kısıtlamalar tarafından temsil edilen bir <xref:System.Data.ConstraintCollection>, tablonun şeması birlikte tanımlayan. A **DataTable** de tarafından temsil edilen bir koleksiyon içeren <xref:System.Data.DataRowCollection>, tablodaki verileri içerir. Geçerli durumuna birlikte bir <xref:System.Data.DataRow> satır içinde depolanan değerleri değişiklikleri belirlemek için her iki kendi geçerli ve özgün sürümü korur.  
  
## <a name="the-dataview-class"></a>DataView sınıfı  
 A <xref:System.Data.DataView> depolanan verilerin farklı görünümlerini oluşturmanızı sağlayan bir <xref:System.Data.DataTable>, veri bağlama uygulamalarında sık kullanılan bir özellik. Kullanarak bir <xref:System.Data.DataView>farklı sıralamalar olan bir tabloda veri getirebilir ve veri satırı durum ya da bir filtre ifadesi göre göre filtre uygulayabilirsiniz. Daha fazla bilgi için bkz: [DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A **DataSet** ilişkilerde içeren kendi <xref:System.Data.DataRelationCollection> nesnesi. Tarafından temsil edilen bir ilişki <xref:System.Data.DataRelation> nesnesi, bir ilişkilendirilmiş bir satır **DataTable** başka bir satır ile **DataTable**. Bir ilişki ilişkisel bir veritabanındaki birincil ve yabancı anahtar sütunları arasında mevcut olabilecek bir birleşim yola benzerdir. A **DataRelation** iki tablodaki eşleşen sütunları tanımlayan bir **DataSet**.  
  
 İlişkileri etkinleştir başka bir tablodan gezinme bir **DataSet**. Temel öğelerini bir **DataRelation** ilişkinin adını, ilişkili tabloları adını ve ilişkili sütunların her tabloda. İlişkileri oluşturulabilen tablo başına birden fazla sütun içeren bir dizi belirterek <xref:System.Data.DataColumn> nesneleri anahtar sütunları olarak. Bir ilişki eklediğinizde <xref:System.Data.DataRelationCollection>, isteğe bağlı olarak ekleyebilirsiniz bir **UniqueKeyConstraint** ve **ForeignKeyConstraint** ilgili sütununa değişiklik yapıldığında bütünlük kısıtlamaları zorlamak için değerler.  
  
 Daha fazla bilgi için bkz: [ekleme DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Doldurmak için bir **DataSet** bir XML akışı veya belge. XML akışı veya belge için sağlamak için kullanabileceğiniz **DataSet** verileri, şema bilgileri veya her ikisi de. Varolan veriler veya şema bilgileri zaten var XML akışı veya belge sağlanan bilgileri birleştirilebilir **DataSet**. Daha fazla bilgi için bkz: [XML kullanarak bir veri kümesinde](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>extendedProperties  
 **DataSet**, **DataTable**, ve **DataColumn** tümüne sahip bir **ExtendedProperties** özelliği. **ExtendedProperties** olan bir **PropertyCollection** burada yerleştirebileceğiniz sonuç kümesi oluşturmak için kullanılan SELECT deyimi veya verilerin ne zaman oluşturulduğu saat gibi özel bilgiler. **ExtendedProperties** koleksiyonu için şema bilgileri olarak kalıcı **DataSet**.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]bir veri kümesinde depolanan bağlantısı kesilen veriler için dil ile tümleşik sorgulama özellikleri sağlar. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]Standart kullanan [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sözdizimi ve kullanırken derleme zamanı sözdizimi denetimi ve statik yazarak IntelliSense desteği sağlar ve [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE.  
  
 Daha fazla bilgi için bkz: [LINQ-DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET genel bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Veri kümeleri, DataTable ve DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Alma ve ADO.NET veri değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
