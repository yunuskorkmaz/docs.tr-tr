---
title: "Bir veri kümesini XML dosyası şuradan yükleniyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ebbe1addf47bc76903e362cfb353ade359a1c8ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="loading-a-dataset-from-xml"></a>Bir veri kümesini XML dosyası şuradan yükleniyor
Bir ADO.NET içeriğini <xref:System.Data.DataSet> bir XML akışı veya belge oluşturulabilir. Ayrıca, .NET Framework ile büyük esneklik hangi bilgilerin, XML'den yüklenen elinizde ve nasıl şema veya ilişkisel yapısını <xref:System.Data.DataSet> oluşturulur.  
  
 Doldurmak için bir <xref:System.Data.DataSet> ile verileri XML kullanarak **ReadXml** yöntemi <xref:System.Data.DataSet> nesnesi. **ReadXml** yöntemi bir dosyadan bir akış okur veya bir **XmlReader**ve kaynak XML ve isteğe bağlı bir bağımsız değişken olarak alan **XmlReadMode** bağımsız değişkeni. (Hakkında daha fazla bilgi için **XmlReader**, bkz: [NIB: Okuma XML XmlTextReader verileriyle](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) **ReadXml** yöntemi XML akışı veya belge ve yükleri içeriğini okur <xref:System.Data.DataSet> verilerle. İlişkisel şeması oluşturacak <xref:System.Data.DataSet> bağlı olarak **XmlReadMode** belirtilen ve desteklemediğini ilişkisel şema zaten mevcut.  
  
 Aşağıdaki tabloda ilgili seçenekleri açıklar **XmlReadMode** bağımsız değişkeni.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Auto**|Bu varsayılandır. XML inceler ve aşağıdaki sırayla en uygun seçeneği seçer:<br /><br /> -Bir DiffGram XML olup olmadığını **DiffGram** kullanılır.<br />-İf <xref:System.Data.DataSet> bir şema içeriyor veya bir satır içi şema XML içeriyor **ReadSchema** kullanılır.<br />-İf <xref:System.Data.DataSet> bir şema içermiyor ve XML bir satır içi şema içermediğinden **InferSchema** kullanılır.<br /><br /> Okunan XML biçimi biliyorsanız, en iyi performans için açık bir ayarlamanız önerilir **XmlReadMode**, bunun yerine kabul daha **otomatik** varsayılan.|  
|**ReadSchema**|Herhangi bir satır içi şema okur ve veri ve şema yükler.<br /><br /> Varsa <xref:System.Data.DataSet> zaten varolan şemayla eklenen yeni tablolar satır içi şema bir şema içeriyor <xref:System.Data.DataSet>. Satır içi şema herhangi bir tablo zaten içinde olup olmadığını <xref:System.Data.DataSet>, bir özel durum. Kullanarak varolan bir tablo için şemayı mümkün olmaz **XmlReadMode.ReadSchema**.<br /><br /> Varsa <xref:System.Data.DataSet> bir şema içermiyor ve satır içi şema yok, hiçbir veri okuma.<br /><br /> Satır içi şema XML Şeması Tanım Dili (XSD) şeması kullanılarak tanımlanabilir. Satır içi şeması XML şeması olarak yazma hakkında daha fazla bilgi için bkz [türetme DataSet ilişkisel yapısı XML Şeması'ndan (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Herhangi bir satır içi şema yoksayar ve mevcut verileri yükler <xref:System.Data.DataSet> şema. Varolan şema eşleşmiyor herhangi bir veri göz ardı edilir. Hiçbir şema varsa <xref:System.Data.DataSet>, hiçbir veri yüklendi.<br /><br /> Verileri bir DiffGram ise **IgnoreSchema** aynı işlevselliğe sahip **DiffGram** *.*|  
|**InferSchema**|Herhangi bir satır içi şema yoksayar, şemanın XML veri yapısı başına oluşturur ve sonra verileri yükler.<br /><br /> Varsa <xref:System.Data.DataSet> zaten bir şema içeriyor geçerli şema var olan tablolara sütunlar ekleyerek genişletilir. Değil varsa tabloları ek tablolar eklenmez. Farklı bir ad alanı ile oluşturulursa bir tablo zaten varsa veya çıkarsanan sütun varolan sütunlarla çakışırsa özel durum oluşur.<br /><br /> Hakkında ayrıntılar için **ReadXmlSchema** bir şema oluşturur bir XML belgesinden bkz [çıkarımını yapma DataSet ilişkisel yapısından XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).|  
|**DiffGram**|Bir DiffGram okur ve verileri geçerli şemaya ekler. **DiffGram** yeni satırların benzersiz tanımlayıcı değerlerini eşleştiği varolan satırları ile birleştirir. "Birleştirme veri gelen XML" Bu konunun sonundaki bakın. DiffGrams hakkında daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
|**Parça**|Akışın sonuna ulaşılana kadar birden çok XML parçaları okuma devam eder. Parça eşleşen <xref:System.Data.DataSet> şema uygun tablolara eklenir. Eşleşmeyen parçaları <xref:System.Data.DataSet> şema atılır.|  
  
> [!NOTE]
>  Geçirirseniz bir **XmlReader** için **ReadXml** konumlandırılmış parçası olan bir XML belgesi içine yolu **ReadXml** sonraki öğe düğüme okuma yapacak ve kök olarak kabul eder öğesi, yalnızca öğe düğümü sonuna kadar okumak. Belirtirseniz bu uygulanmaz **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>DTD varlıklar  
 Yüklemeye çalışırsanız, XML belge türü tanımı (DTD) şemada tanımlanan varlıklar içeriyorsa, bir özel durum oluşturulur bir <xref:System.Data.DataSet> geçirerek bir dosya adı, akış veya yapmayan **XmlReader** için  **ReadXml**. Bunun yerine, oluşturmalısınız bir **XmlValidatingReader**, ile **EntityHandling** kümesine **EntityHandling.ExpandEntities**ve geçirmek,  **XmlValidatingReader** için **ReadXml**. **XmlValidatingReader** tarafından okunan önce varlıkları genişletecek <xref:System.Data.DataSet>.  
  
 Aşağıdaki kodu nasıl yükleneceğini örnekler bir <xref:System.Data.DataSet> bir XML akışından. İlk örnek için geçirilen bir dosya adı gösterir **ReadXml** yöntemi. İkinci örnek XML olma kullanarak yüklenen içeren bir dize gösterir bir <xref:System.IO.StringReader>.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
>  Çağırırsanız **ReadXml** çok büyük bir dosya yüklemek için yavaş performans karşılaşabilirsiniz. İçin en iyi performansı elde etmek için **ReadXml**, büyük boyutlu bir dosyayı çağrısı <xref:System.Data.DataTable.BeginLoadData%2A> yöntemi her tablo için <xref:System.Data.DataSet>ve ardından arama **ReadXml**. Son olarak, arama <xref:System.Data.DataTable.EndLoadData%2A> her tablo için <xref:System.Data.DataSet>, aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
>  Varsa XSD şeması, <xref:System.Data.DataSet> içeren bir **targetNamespace**veri okunamadığı ve çağrılırken özel durumlar, karşılaşabileceğiniz **ReadXml** yüklemek için <xref:System.Data.DataSet> içeren XML ile öğeleri ile belirleme ad alanı yok. Bu durumda nitelenmemiş öğelerini okumak için **elementFormDefault** eşit "tam" XSD şemasında. Örneğin:  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>XML verileri birleştirme  
 Varsa <xref:System.Data.DataSet> zaten verilerini içeren XML yeni verileri zaten mevcut verilere eklenir <xref:System.Data.DataSet>. **ReadXml** XML'den birleştirmez <xref:System.Data.DataSet> herhangi bir satır eşleşen birincil anahtarlarla bilgi. Var olan satır bilgilerini XML yeni bilgilerle üzerine yazmak için kullanın **ReadXml** yeni <xref:System.Data.DataSet>ve ardından <xref:System.Data.DataSet.Merge%2A> yeni <xref:System.Data.DataSet> varolan içine <xref:System.Data.DataSet>. Bu DiffGram kullanarak yükleme Not **ReadXML** ile bir **XmlReadMode** , **DiffGram** aynı benzersiz tanımlayıcısına sahip satırları birleştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
