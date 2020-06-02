---
title: XML’den DataSet Yükleme
description: XML 'den bir ADO.NET veri kümesine içerik eklemeyi öğrenin. .NET Framework, yükleme ve veri kümesinin yapısına yönelik esneklik sunar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 8c81e6e29678fe2e30af7c15d8d6e90f23dd0762
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286889"
---
# <a name="loading-a-dataset-from-xml"></a>XML’den DataSet Yükleme
Bir ADO.NET içeriği <xref:System.Data.DataSet> BIR XML akışından veya belgesinden oluşturulabilir. Ayrıca .NET Framework, XML 'den hangi bilgilerin yüklendiği ve şema ya da ilişkisel yapısının nasıl oluşturulduğuna ilişkin büyük bir esnekliğe sahip olursunuz <xref:System.Data.DataSet> .  
  
 <xref:System.Data.DataSet>XML 'deki verileri bir ile doldurmanız için nesnenin **ReadXml** yöntemini kullanın <xref:System.Data.DataSet> . **ReadXml** yöntemi bir dosyadan, akıştan veya bir **XmlReader**'dan yararlanır ve XML kaynağı Ile Isteğe bağlı bir **XmlReadMode** bağımsız değişkeni olarak bağımsız değişken alır. **XmlReader**hakkında daha fazla bilgi için bkz. [XML verilerini XmlTextReader ile okuma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). **ReadXml** YÖNTEMI, XML akışı veya belgesinin içeriğini okur ve <xref:System.Data.DataSet> ile verileri yükler. Ayrıca, <xref:System.Data.DataSet> belirtilen **XmlReadMode** öğesine ve ilişkisel bir şemanın zaten mevcut olup olmadığına bağlı olarak ilişkisel şeması da oluşturur.  
  
 Aşağıdaki tabloda **XmlReadMode** bağımsız değişkeninin seçenekleri açıklanmaktadır.  
  
|Seçenek|Description|  
|------------|-----------------|  
|**Otomatik**|Bu varsayılandır. XML 'i inceler ve aşağıdaki sırada en uygun seçeneği seçer:<br /><br /> -XML bir DiffGram ise, **DiffGram** kullanılır.<br />- <xref:System.Data.DataSet> Bir şema içeriyorsa veya XML bir satır içi şema Içeriyorsa **ReadSchema** kullanılır.<br />- <xref:System.Data.DataSet> Bir şema içermiyorsa ve XML bir satır içi şema içermiyorsa, **ınseschema** kullanılır.<br /><br /> Okunan XML 'nin biçimini biliyorsanız, en iyi performans için **Otomatik** varsayılanı kabul etmek yerine açık bir **XmlReadMode**ayarlamanız önerilir.|  
|**ReadSchema**|Herhangi bir satır içi şemayı okur ve verileri ve şemayı yükler.<br /><br /> <xref:System.Data.DataSet>Zaten bir şema içeriyorsa, yeni tablolar satır içi şemadan içindeki mevcut şemaya eklenir <xref:System.Data.DataSet> . Satır içi şemadaki herhangi bir tablo ' de zaten mevcutsa <xref:System.Data.DataSet> , bir özel durum oluşturulur. **XmlReadMode. ReadSchema**kullanarak var olan bir tablonun şemasını değiştiremeyeceksiniz.<br /><br /> <xref:System.Data.DataSet>Bir şema içermiyorsa ve satır içi şema yoksa, hiçbir veri okunamaz.<br /><br /> Satır içi şema, XML şeması tanım dili (XSD) şeması kullanılarak tanımlanabilir. Satır içi şemayı XML şeması olarak yazma hakkında daha fazla bilgi için bkz. [xml şemasından (xsd) DataSet Ilişkisel yapısını türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Herhangi bir satır içi şemayı yoksayar ve verileri var olan <xref:System.Data.DataSet> şemaya yükler. Varolan şemayla eşleşmeyen tüm veriler atılır. İçinde hiçbir şema yoksa <xref:System.Data.DataSet> , hiçbir veri yüklenmez.<br /><br /> Veriler bir DiffGram ise, **ıgnoreschema** **DiffGram** ile aynı işlevselliğe sahiptir *.*|  
|**Inseschema**|Satır içi şemayı yoksayar ve XML verilerinin yapısına göre şemayı algılar, ardından verileri yükler.<br /><br /> <xref:System.Data.DataSet>Zaten bir şema içeriyorsa, geçerli şema varolan tablolara sütun eklenerek genişletilir. Mevcut tablolar yoksa ek tablolar eklenmez. Başka bir ad alanı olan çıkartılan bir tablo zaten varsa veya herhangi bir çıkarılan sütun varolan sütunlarla çakışıyorsa, bir özel durum oluşturulur.<br /><br /> **ReadXmlSchema** 'ın bir XML belgesinden bir şemayı nasıl kullandığını öğrenmek için bkz. [XML 'Den veri kümesi ilişkisel yapısını](inferring-dataset-relational-structure-from-xml.md)anlamak.|  
|**Içeriyor**|Bir DiffGram okur ve verileri geçerli şemaya ekler. **DiffGram** , benzersiz tanımlayıcı değerlerinin eşleştiği varolan satırlarla yeni satırları birleştirir. Bu konunun sonundaki "XML 'den veri birleştirme" konusuna bakın. DiffGram hakkında daha fazla bilgi için bkz. [DiffGram](diffgrams.md).|  
|**Parça**|Akışın sonuna ulaşılana kadar birden çok XML parçasının okunmasına devam eder. Şemayla eşleşen parçalar <xref:System.Data.DataSet> ilgili tablolara eklenir. Şemayla eşleşmeyen parçalar <xref:System.Data.DataSet> atılır.|  
  
> [!NOTE]
> Bir XML belgesine yolunun bir parçası **olarak konumlandırılmış** bir XmlReader öğesine bir **XmlReader** geçirirseniz, **ReadXml** sonraki öğe düğümüne okur ve bunu yalnızca öğe düğümünün sonuna kadar okuyan kök öğe olarak değerlendirir. **XmlReadMode. Fragment**belirtirseniz bu uygulanmaz.  
  
## <a name="dtd-entities"></a>DTD varlıkları  
 XML 'niz bir belge türü tanımı (DTD) şemasında tanımlanan varlıklar içeriyorsa, bir <xref:System.Data.DataSet> dosya adı, akış veya doğrulama olmayan **XmlReader** öğesini **ReadXml**öğesine geçirerek yüklemeyi denerseniz bir özel durum oluşturulur. Bunun yerine, **EntityHandling** 'U **EntityHandling. ExpandEntities**olarak ayarlayıp bir **XmlValidatingReader**oluşturmanız ve **XmlValidatingReader** 'ı **ReadXml**'e geçirmeniz gerekir. **XmlValidatingReader** , tarafından okunmadan önce varlıkları genişletir <xref:System.Data.DataSet> .  
  
 Aşağıdaki kod örnekleri, bir XML akışından nasıl yükleneceğini göstermektedir <xref:System.Data.DataSet> . İlk örnekte, **ReadXml** yöntemine geçirilmiş bir dosya adı gösterilmektedir. İkinci örnek, kullanılarak yüklenen XML içeren bir dize gösterir <xref:System.IO.StringReader> .  
  
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
> Çok büyük bir dosyayı yüklemek için **ReadXml** çağrısı yaparsanız, yavaş performansla karşılaşabilirsiniz. **ReadXml**için en iyi performansı sağlamak üzere, büyük bir dosyada, <xref:System.Data.DataTable.BeginLoadData%2A> içindeki her tablo için yöntemini çağırın <xref:System.Data.DataSet> ve ardından **ReadXml**öğesini çağırın. Son olarak, <xref:System.Data.DataTable.EndLoadData%2A> Aşağıdaki örnekte gösterildiği gibi, içindeki her tablo için öğesini çağırın <xref:System.Data.DataSet> .  
  
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
> İçin XSD şeması <xref:System.Data.DataSet> bir **targetNamespace**içeriyorsa, veriler okunmayabilir ve uygun bir **ReadXml** <xref:System.Data.DataSet> ad alanı olmayan öğeleri içeren XML ile yüklemek için ReadXml çağrılırken özel durumlarla karşılaşabilirsiniz. Bu durumda nitelenmemiş öğeleri okumak için, XSD şemanızda **elementFormDefault** eşittir "Qualified" olarak ayarlayın. Örneğin:  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>XML 'den veri birleştirme  
 <xref:System.Data.DataSet>Zaten veri içeriyorsa, XML 'deki yeni veriler, içinde zaten mevcut olan verilere eklenir <xref:System.Data.DataSet> . **ReadXml** , XML 'den <xref:System.Data.DataSet> eşleşen birincil anahtarlarla satır bilgileriyle birleştirme yapmaz. XML 'deki yeni bilgilerle mevcut satır bilgilerinin üzerine yazmak için, **ReadXml** kullanarak yeni bir ve yeni bir oluşturma <xref:System.Data.DataSet> yapın <xref:System.Data.DataSet.Merge%2A> <xref:System.Data.DataSet> <xref:System.Data.DataSet> . **DiffGram bir** **XmlReadMode** Ile **ReadXml** kullanarak bir DiffGram yüklemenin aynı benzersiz tanımlayıcıya sahip satırları birleştirdiğini unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
