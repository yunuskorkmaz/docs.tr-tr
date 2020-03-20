---
title: XML’den DataSet Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151071"
---
# <a name="loading-a-dataset-from-xml"></a>XML’den DataSet Yükleme
Bir ADO.NET <xref:System.Data.DataSet> içeriği bir XML akışından veya belgeden oluşturulabilir. Buna ek olarak, .NET Framework ile XML'den hangi bilgilerin yüklendiği ve şema veya ilişkisel yapının <xref:System.Data.DataSet> nasıl oluşturulduğu konusunda büyük bir esnekliğe sahipsiniz.  
  
 XML'den gelen <xref:System.Data.DataSet> verilerle doldurmak için nesnenin <xref:System.Data.DataSet> **ReadXml** yöntemini kullanın. **ReadXml** yöntemi bir dosya, bir akış veya **XmlReader**okur ve bağımsız değişkenler XML artı isteğe bağlı **XmlReadMode** bağımsız değişken kaynağı olarak alır. **XmlReader**hakkında daha fazla bilgi için, [XmlTextReader ile XML Veri Okuma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100))bakın. **ReadXml** yöntemi XML akışının veya belgenin içeriğini <xref:System.Data.DataSet> okur ve verileri yükler. Ayrıca <xref:System.Data.DataSet> **xmlReadMode** belirtilen bağlı olarak ilişkisel şema yaratacak ve bir ilişkisel şema zaten var olup olmadığını.  
  
 Aşağıdaki tabloda **XmlReadMode** bağımsız değişkeni için seçenekler açıklanmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Otomatik**|Bu varsayılandır. XML'i inceler ve aşağıdaki sırada en uygun seçeneği seçer:<br /><br /> - XML diffgram ise **DiffGram** kullanılır.<br />- Bir <xref:System.Data.DataSet> şema içeriyorsa veya XML satır içi şema içeriyorsa, **ReadSchema** kullanılır.<br />- Şema <xref:System.Data.DataSet> içermiyorsa ve XML satır içi şema içermiyorsa, **InferSchema** kullanılır.<br /><br /> XML'in okunan biçimini biliyorsanız, en iyi performans için **Otomatik** varsayılanı kabul etmek yerine açık bir **XmlReadMode**ayarlamanız önerilir.|  
|**Okuma Skeci**|Herhangi bir satır lı şema okur ve veri ve şema yükler.<br /><br /> <xref:System.Data.DataSet> Zaten bir şema içeriyorsa, satır satır şemasından varolan şemaya yeni <xref:System.Data.DataSet>tablolar eklenir. Satır satırşeşemasında herhangi bir tablo zaten <xref:System.Data.DataSet>varsa, bir özel durum atılır. **XmlReadMode.ReadSchema**kullanarak varolan bir tablonun şemasını değiştiremeyeceksiniz.<br /><br /> Şema <xref:System.Data.DataSet> içermiyorsa ve satır satır şeması yoksa, veri okunmaz.<br /><br /> Satır çizgisi şema XML Şema tanım dili (XSD) şeması kullanılarak tanımlanabilir. XML Şema olarak satır içinde şema yazma hakkında ayrıntılı bilgi için, [XML Schema (XSD) gelen Veri Seti İlişkisel Yapısı Türetilmesi](deriving-dataset-relational-structure-from-xml-schema-xsd.md)bölümüne bakın.|  
|**Schema'yı Yok Sayma**|Herhangi bir satır dışı şema yoksa <xref:System.Data.DataSet> ve verileri varolan şema içine yükler. Varolan şemaya uymayan tüm veriler atılır. Hiçbir şema <xref:System.Data.DataSet>varsa, hiçbir veri yüklenir.<br /><br /> Veriler Bir DiffGram ise, **YokSaysşek** **DiffGram** ile aynı işlevsellik *vardır.*|  
|**ınferschema**|Herhangi bir satır dışı şema yoksave XML verilerinin yapısına göre şema çıkar, sonra verileri yükler.<br /><br /> <xref:System.Data.DataSet> Zaten bir şema içeriyorsa, geçerli şema varolan tablolara sütunlar eklenerek genişletilir. Varolan tablolar yoksa ek tablolar eklenmez. Çıkarılan bir tablo zaten farklı bir ad alanıyla varsa veya çıkarılan sütunlar varolan sütunlarla çakışmışsa bir özel durum atılır.<br /><br /> **ReadXmlSchema'nın** bir XML belgesinden bir şema çıkartması hakkında ayrıntılı bilgi [için](inferring-dataset-relational-structure-from-xml.md)bkz.|  
|**Diffgram**|DiffGram okur ve verileri geçerli şemaya ekler. **DiffGram,** benzersiz tanımlayıcı değerlerinin eşleştiği varolan satırlarla yeni satırları birleştirir. Bu konunun sonundaki "XML'den Verileri Birleştirme" bölümüne bakın. DiffGrams hakkında daha fazla bilgi için [Bkz.](diffgrams.md)|  
|**Parça**|Akışın sonuna ulaşana kadar birden çok XML parçasını okumaya devam eder. <xref:System.Data.DataSet> Şemaya uyan parçalar uygun tablolara eklenir. <xref:System.Data.DataSet> Şemaya uymayan parçalar atılır.|  
  
> [!NOTE]
> Bir XML belgesine yolun bir parçası konumlandırılmış **ReadXml** bir Xml için bir **XmlReader** geçerseniz, **ReadXml** sonraki öğe düğümü ne okuyacak ve kök öğesi olarak, yalnızca öğe düğümü sonuna kadar okuma olarak ele alacaktır. **XmlReadMode.Fragment**belirtirseniz bu geçerli değildir.  
  
## <a name="dtd-entities"></a>DTD Varlıklar  
 XML'iniz belge türü tanımında (DTD) şemada tanımlanan varlıklar içeriyorsa, bir <xref:System.Data.DataSet> dosya adını, akışı veya **XmlReader'ı** **ReadXml'e**doğrulamayarak yüklemeyi denerseniz bir özel durum atılır. Bunun yerine, **EntityHandling.ExpandEntities**için **EntityHandling** ayarlanmış bir **XmlValidatingReader**oluşturmanız ve **ReadXml**için **XmlValidatingReader** geçmek gerekir. **XmlValidatingReader** tarafından okunmadan önce varlıkları <xref:System.Data.DataSet>genişletecektir.  
  
 Aşağıdaki kod örnekleri, XML <xref:System.Data.DataSet> akışından nasıl yüklenirgösteriz. İlk örnek, **ReadXml** yöntemine geçirilen bir dosya adını gösterir. İkinci örnek, XML'nin bir <xref:System.IO.StringReader>.  
  
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
> **ReadXml'i** çok büyük bir dosyayüklemek için ararsanız, yavaş performansla karşılaşabilirsiniz. **ReadXml**için en iyi performansı sağlamak için, <xref:System.Data.DataTable.BeginLoadData%2A> büyük bir dosyada, her tablo için yöntemi arayın <xref:System.Data.DataSet>, ve sonra **ReadXml**arayın. Son olarak, aşağıdaki örnekte gösterildiği <xref:System.Data.DataTable.EndLoadData%2A> <xref:System.Data.DataSet>gibi, her tablo için çağrı.  
  
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
> Sizin <xref:System.Data.DataSet> için XSD şema bir **targetNamespace**içeriyorsa, veri okunmayabilir ve özel durumlar karşılaşabilirsiniz, <xref:System.Data.DataSet> **ReadXml'i** arayarak uygun ad alanı olmayan öğeler içeren XML'yi yükleyebilirsiniz. Bu durumda niteliksiz öğeleri okumak için, XSD şemanızda "nitelikli" **öğesiFormDefault'ı** eşit olarak ayarlayın. Örnek:  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>XML'den Veri Birleştirme  
 <xref:System.Data.DataSet> Zaten veri içeriyorsa, XML'den gelen yeni veriler, 'de mevcut olan verilere <xref:System.Data.DataSet>eklenir. **ReadXml,** XML'den eşleşen <xref:System.Data.DataSet> birincil anahtarlarla herhangi bir satır bilgisine birleşmez. XML'den gelen yeni bilgilerle varolan satır bilgilerinin üzerine <xref:System.Data.DataSet>yazmak <xref:System.Data.DataSet.Merge%2A> için <xref:System.Data.DataSet> <xref:System.Data.DataSet> **ReadXml'i** kullanarak yeni bir ve sonra varolana yeni bir tane oluşturun. **ReadXML** kullanarak **DiffGram'ı** **XmlReadMode** of DiffGram ile yüklemenin, aynı benzersiz tanımlayıcıya sahip satırları birleştireceğini unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
