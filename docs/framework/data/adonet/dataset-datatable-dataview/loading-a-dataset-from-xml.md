---
title: XML'den DataSet yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 3a781f17ac3cabebce17955b9a7e2edda4d4fd4b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746854"
---
# <a name="loading-a-dataset-from-xml"></a>XML'den DataSet yükleme
Bir ADO.NET içeriğini <xref:System.Data.DataSet> bir XML akışı veya bir belgeden oluşturulabilir. Ayrıca, .NET Framework ile büyük esneklik hangi bilgilerin, XML'den yüklenen sahip olduğunuz ve nasıl önceden şema veya ilişkisel yapısını <xref:System.Data.DataSet> oluşturulur.  
  
 Doldurmak için bir <xref:System.Data.DataSet> XML verileri ile kullanma **ReadXml** yöntemi <xref:System.Data.DataSet> nesne. **ReadXml** yöntemi bir akışa bir dosyadan okur ya da bir **XmlReader**ve kaynak XML ek olarak isteğe bağlı bağımsız değişkenleri alan **XmlReadMode** bağımsız değişken. (Hakkında daha fazla bilgi için **XmlReader**, bkz: [NIB: XmlTextReader ile XML verileri okuma](https://msdn.microsoft.com/library/762c069b-b50c-41b8-936e-39eacfb0d540).) **ReadXml** yöntemi XML akışı veya belge ve yükleri içeriğini okur <xref:System.Data.DataSet> verilerle. İlişkisel şemasını oluşturacak <xref:System.Data.DataSet> bağlı olarak **XmlReadMode** belirtilen ve olup olmadığı bir ilişkisel şema zaten mevcut.  
  
 Aşağıdaki tablo için seçenekleri açıklar **XmlReadMode** bağımsız değişken.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Auto**|Bu varsayılandır. XML inceler ve en uygun seçeneği şu sırayla seçer:<br /><br /> -Bir DiffGram XML olup olmadığını **DiffGram** kullanılır.<br />-Eğer <xref:System.Data.DataSet> bir şema içeriyor veya bir satır içi şema XML içeriyor **ReadSchema** kullanılır.<br />-Eğer <xref:System.Data.DataSet> bir şema içermiyor ve bir satır içi şema XML içermiyor **InferSchema** kullanılır.<br /><br /> Okunan XML biçimini biliyorsanız, en iyi performans için açık bir ayarladığınız önerilir **XmlReadMode**yerine kabul daha **otomatik** varsayılan.|  
|**ReadSchema**|Herhangi bir satır içi şema okur ve verileri hem de şemayı yükler.<br /><br /> Varsa <xref:System.Data.DataSet> zaten bir şema mevcut şemayla eklenen yeni tablolar satır içi şema içeriyor. <xref:System.Data.DataSet>. Herhangi bir tablo satır içi şema zaten mevcut değilse <xref:System.Data.DataSet>, bir özel durum oluşturulur. Mevcut bir tabloyu kullanarak şemayı değiştirmek mümkün olmayacaktır **gt;XmlReadMode.ReadSchema**.<br /><br /> Varsa <xref:System.Data.DataSet> bir şema içermiyor ve satır içi şema yok, hiçbir veri okuyun.<br /><br /> Satır içi şema XML Şeması Tanım Dili (XSD) şemaya kullanılarak tanımlanabilir. Satır içi şema XML şema olarak yazma hakkında daha fazla ayrıntı için bkz. [türetme DataSet ilişkisel yapısını XML Şeması (XSD) öğesinden](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Herhangi bir satır içi şema yoksayar ve mevcut verileri yükler <xref:System.Data.DataSet> şema. Varolan şema eşleşmeyen herhangi bir veri göz ardı edilir. Şema varsa <xref:System.Data.DataSet>, hiç veri yüklenmedi.<br /><br /> Veriler bir DiffGram ise **IgnoreSchema** ile aynı işlevlere sahip **DiffGram** *.*|  
|**InferSchema**|Herhangi bir satır içi şema yoksayar ve XML veri yapısını başına şemayı algılar ve ardından verileri yükler.<br /><br /> Varsa <xref:System.Data.DataSet> zaten bir şema içeriyor. Geçerli şema varolan tablolarda sütunlar ekleyerek genişletilir. Ek tablolar değil varsa tablolar eklenmeden bırakılır. Farklı bir ad alanı ile gösterilen bir tablo zaten varsa veya çıkarsanan sütun mevcut sütunları arasında çakışma varsa, bir özel durum oluşturulur.<br /><br /> Hakkında ayrıntılar için **ReadXmlSchema** bir şema çıkarsar bir XML belgesinden bkz [DataSet ilişkisel yapısını çıkarma XML'den](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).|  
|**DiffGram**|Bir DiffGram okur ve verileri geçerli şemaya ekler. **DiffGram** yeni varolan satırları benzersiz tanımlayıcı değerlerinin eşleştiği satırları birleştirir. "Birleştirme veri gelen XML" Bu konu sonuna bakın. DiffGrams hakkında daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
|**Parça**|Birden çok XML parçası okuma, akışın sonuna ulaşılana kadar devam eder. Parçacık eşleşen <xref:System.Data.DataSet> şema uygun tablolarına eklenir. Eşleşmeyen parçaları <xref:System.Data.DataSet> şema atılır.|  
  
> [!NOTE]
>  Geçirirseniz bir **XmlReader** için **ReadXml** konumlandırılmış parçası olan bir XML belgesine biçimini **ReadXml** sonraki öğe düğümü için okur ve, temeli olarak değerlendirilecektir. öğe, öğe düğümü yalnızca sonuna kadar okumak. Belirtirseniz bu uygulanmaz **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>DTD'nin varlıkları  
 Yüklemeye çalışırsanız, XML belge türü tanımı (DTD'nin) şemasında tanımlanan varlıklarını içeriyorsa, bir özel durum oluşturulur bir <xref:System.Data.DataSet> bir dosyaya geçirerek adı, akış veya yapmayan **XmlReader** için  **ReadXml**. Bunun yerine, oluşturmalısınız bir **XmlValidatingReader**, ile **EntityHandling** kümesine **EntityHandling.ExpandEntities**, geçirin,  **XmlValidatingReader** için **ReadXml**. **XmlValidatingReader** varlıklar tarafından okunan önce genişletilir <xref:System.Data.DataSet>.  
  
 Aşağıdaki kod örneğinde nasıl yükleneceğini gösterir. bir <xref:System.Data.DataSet> bir XML Akışı'ndan. İlk örnek, gönderilmiş bir dosya adı gösterir **ReadXml** yöntemi. İkinci örnek XML durdurulmasını kullanarak yüklenen içeren bir dize gösterir bir <xref:System.IO.StringReader>.  
  
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
>  Eğer **ReadXml** çok büyük bir dosya yüklemek için yavaş performansla karşılaşabilirsiniz. İçin en iyi performansı elde etmek için **ReadXml**, büyük bir dosya arama <xref:System.Data.DataTable.BeginLoadData%2A> yöntemi her tablo için <xref:System.Data.DataSet>ve sonra çağrı **ReadXml**. Son olarak, çağrı <xref:System.Data.DataTable.EndLoadData%2A> her tablo için <xref:System.Data.DataSet>, aşağıdaki örnekte gösterildiği gibi.  
  
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
>  XSD şeması, <xref:System.Data.DataSet> içeren bir **targetNamespace**veri olmayan okunabilir ve çağrılırken özel durum, karşılaşabileceğiniz **ReadXml** yüklemek için <xref:System.Data.DataSet> barındıran XML ile ad alanı içermeyen öğeler. Bu durumda, nitelenmemiş öğeleri okumak için ayarlanmış **elementFormDefault** , XSD şema "nitelenmiş" değerine eşit. Örneğin:  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>XML verilerini birleştirme  
 Varsa <xref:System.Data.DataSet> zaten veri içeriyor. XML yeni verileri zaten mevcut verilere eklenir <xref:System.Data.DataSet>. **ReadXml** XML'den birleştirmez <xref:System.Data.DataSet> herhangi bir satır birincil anahtarları eşleşen bilgileri. Var olan satır bilgileri XML alınan yeni bilgilerle üzerine yazmak için kullanmak **ReadXml** yeni bir <xref:System.Data.DataSet>, ardından <xref:System.Data.DataSet.Merge%2A> yeni <xref:System.Data.DataSet> varolan içine <xref:System.Data.DataSet>. Bu kullanarak DiffGram yüklenirken Not **ReadXML** ile bir **XmlReadMode** , **DiffGram** aynı benzersiz tanımlayıcıya sahip satırları birleştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
