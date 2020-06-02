---
title: XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: 61957ff88ef57703aff1861238ee10b23c2f16ff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291610"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme
XPath 2,0 veri modelinin bir örneği olarak, <xref:System.Xml.XPath.XPathNavigator> sınıfı ortak dil çalışma zamanı (CLR) türleriyle eşleşen kesin tür belirtilmiş verileri içerebilir. XPath 2,0 veri modeline göre yalnızca öğeler ve öznitelikler kesin türü belirtilmiş veri içerebilir. Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> veya nesnesi içindeki verilere, türü <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> kesin belirlenmiş verilerin yanı sıra bir veri türünden diğerine dönüştürmeye yönelik mekanizmalar sağlar.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>XPathNavigator tarafından sunulan tür bilgileri  
 XML 1,0 verileri, bir DTD, XML şeması tanım dili (XSD) şeması veya başka bir mekanizmasıyla işlenmediği sürece Teknik olarak tür olmadan yapılır. Bir XML öğesi veya özniteliği ile ilişkilendirilebilen tür bilgileri kategorileri vardır.  
  
- Basit CLR türleri: XML şema dillerinin hiçbiri doğrudan ortak dil çalışma zamanı (CLR) türlerini desteklemez. En uygun CLR türü olarak basit öğe ve öznitelik içeriğini görüntüleyebilmek yararlı olduğundan, tüm basit içerikler, <xref:System.String> eklenen herhangi bir şema bilgileriyle şema bilgileri yokluğunda olarak yazılabilir ve bu içeriği daha uygun bir türe göre iyileştiriyor. Özelliğini kullanarak, basit öğe ve öznitelik içeriğinin en iyi eşleşen CLR türünü bulabilirsiniz <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> . Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).  
  
- Basit (CLR) türleri listeleri: basit içeriğe sahip bir öğe veya öznitelik, boşluk ile ayrılmış bir değerler listesi içerebilir. Değerler bir XML şeması tarafından bir "liste türü" olarak belirtilir. XML şeması yokluğunda, bu gibi basit içerik tek bir metin düğümü olarak değerlendirilir. Bir XML şeması kullanılabilir olduğunda, bu basit içerik her biri bir CLR nesneleri koleksiyonuyla eşleşen basit bir türe sahip bir dizi Atomik değer olarak gösterilebilir. Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).  
  
- Yazılan değer: şema tarafından doğrulanan bir öznitelik veya basit bir türe sahip öğe türü belirtilmiş bir değer içeriyor. Bu değer, sayısal, dize veya tarih türü gibi temel bir türdür. XSD içindeki yerleşik basit türler, bir düğümün değerine yalnızca gibi daha uygun bir tür olarak erişim sağlayan CLR türleriyle eşleştirilebilir <xref:System.String> . Öznitelikleri veya öğe alt öğesi olan bir öğe karmaşık bir tür olarak kabul edilir. Basit içeriğe sahip bir karmaşık türün türü belirlenmiş değeri (yalnızca alt öğe olarak metin düğümleri), içeriğinin basit türü ile aynıdır. Karmaşık içerik (bir veya daha fazla alt öğesi) olan bir karmaşık türün tür değeri, bir olarak döndürülen tüm alt metin düğümlerinin birleştirilmesiyle ilgili dize değeridir <xref:System.String> . Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).  
  
- Şema diline özgü tür adı: çoğu durumda, bir dış şema uygulamanın yan etkisi olarak ayarlanan CLR türleri, bir düğümün değerine erişim sağlamak için kullanılır. Ancak, bir XML belgesine uygulanan belirli bir şema ile ilişkili türü incelemek isteyebileceğiniz durumlar olabilir. Örneğin, ekli bir şemaya göre "PurchaseOrder" türünde içeriğe sahip olacak şekilde belirlenen tüm öğeleri ayıklayarak bir XML belgesinde arama yapmak isteyebilirsiniz. Bu tür bilgiler yalnızca şema doğrulamasının sonucu olarak ayarlanabilir ve bu bilgilere <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> sınıfının ve özellikleri aracılığıyla erişilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> . Daha fazla bilgi için aşağıdaki şema doğrulama bilgi kümesi (PSVı) bölümüne bakın.  
  
- Şemaya özgü tür yansıtma: başka durumlarda, bir XML belgesine uygulanan şemaya özgü türün daha ayrıntılı ayrıntılarını elde etmek isteyebilirsiniz. Örneğin, bir XML dosyası okurken, `maxOccurs` bazı özel hesaplamalar gerçekleştirmek IÇIN XML belgesindeki her bir geçerli düğüm için özniteliğini ayıklamak isteyebilirsiniz. Bu bilgiler yalnızca şema doğrulaması aracılığıyla ayarlandığından, <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> sınıfının özelliği aracılığıyla erişilir <xref:System.Xml.XPath.XPathNavigator> . Daha fazla bilgi için aşağıdaki şema doğrulama bilgi kümesi (PSVı) bölümüne bakın.  
  
## <a name="xpathnavigator-typed-accessors"></a>XPathNavigator türü erişimciler  
 Aşağıdaki tabloda, <xref:System.Xml.XPath.XPathNavigator> bir düğümle ilgili tür bilgilerine erişmek için kullanılabilecek sınıfının çeşitli özellikleri ve yöntemleri gösterilmektedir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Bu, geçerli olduğunda düğüm için XML Şeması tür bilgilerini içerir.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Bu, doğrulamadan sonra eklenen düğümün şema doğrulama doğrulaması bilgi kümesini içerir. Bu, XML şema türü bilgilerinin yanı sıra geçerlilik bilgilerini de içerir.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Düğümün türü belirlenmiş değeri CLR türü.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Düğümün içeriği, bir veya daha fazla CLR değeri olarak türü, düğümün XML şema türüyle en yakın eşleşme olan.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<xref:System.String>Geçerli düğümün değeri <xref:System.Boolean> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xs:boolean` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<xref:System.String>Geçerli düğümün değeri <xref:System.DateTime> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xs:datetime` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<xref:System.String>Geçerli düğümün değeri <xref:System.Double> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xsd:double` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<xref:System.String>Geçerli düğümün değeri <xref:System.Int32> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xs:integer` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<xref:System.String>Geçerli düğümün değeri <xref:System.Int64> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xs:integer` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Düğüm içeriği, XPath 2,0 atama kurallarına göre hedef türüne atama yapılır.|  
  
 Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Şema sonrası doğrulama bilgi kümesi (PSVı)  
 Bir XML şeması işlemcisi, girdi olarak bir XML Infoset 'i kabul eder ve şema doğrulama bilgisi kümesine (PSVı) dönüştürür. PSVı, yeni bilgi öğeleri eklenen ve mevcut bilgi öğelerine eklenen yeni özellikler içeren özgün giriş XML bilgi kümesidir. Tarafından sunulan PSVı içindeki XML Infoset 'e eklenen üç geniş bilgi sınıfı vardır <xref:System.Xml.XPath.XPathNavigator> .  
  
1. Doğrulama sonuçları: bir öğe veya özniteliğin başarıyla doğrulanıp doğrulanmayacağı hakkında bilgi. Bu, <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> sınıfının özelliğinin özelliği tarafından gösterilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> .  
  
2. Varsayılan bilgiler: öğe veya öznitelik değerinin şemada belirtilen varsayılan değerlerle elde edilip edilmeyeceğini belirtir. Bu, <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> sınıfının özelliğinin özelliği tarafından gösterilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> .  
  
3. Tür açıklamaları: tür tanımları veya öğe ve öznitelik bildirimleri olabilecek şema bileşenlerine başvurular. <xref:System.Xml.XPath.XPathNavigator.XmlType%2A>Öğesinin özelliği, <xref:System.Xml.XPath.XPathNavigator> geçerli ise düğümün belirli tür bilgilerini içerir. Bir düğümün geçerliliği bilinmiyorsa (örneğin, doğrulanıp daha sonra düzenlendiğinde). sonra <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özellik olarak ayarlanır, `null` ancak sınıf özelliğinin farklı özelliklerinden tür bilgisi hala kullanılabilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> .  
  
 Aşağıdaki örnek, tarafından kullanıma sunulan gönderi şeması doğrulama bilgi kümesindeki bilgilerin kullanımını gösterir <xref:System.Xml.XPath.XPathNavigator> .  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 Örnek, `books.xml` dosyayı giriş olarak alır.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Örnek ayrıca `books.xsd` Şemayı giriş olarak alır.  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"
attributeFormDefault="unqualified" elementFormDefault="qualified"
targetNamespace="http://www.contoso.com/books"
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a>ValueAs özelliklerini kullanarak yazılan değerleri Al  
 Bir düğümün yazılan değeri <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> öğesinin özelliğine erişerek alınabilir <xref:System.Xml.XPath.XPathNavigator> . Belirli durumlarda, bir düğümün türü belirlenmiş değerini farklı bir türe dönüştürmek isteyebilirsiniz. Ortak bir örnek, bir XML düğümünden sayısal bir değer almaya yönelik bir örnektir. Örneğin, aşağıdaki doğrulanmamış ve türsüz XML belgesini göz önünde bulundurun.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Öğesi üzerinde konumlandırılmışsa, özelliği olur, özelliği olur <xref:System.Xml.XPath.XPathNavigator> `price` <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> `null` <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> <xref:System.String> ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özellik dize olur `10.00` .  
  
 Ancak,,,, <xref:System.Xml.XPath.XPathItem.ValueAs%2A> <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A> <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> veya <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> yöntemini ve özelliklerini kullanarak değeri sayısal bir değer olarak ayıklamak yine de mümkündür. Aşağıdaki örnek, yöntemini kullanarak böyle bir tür dönüştürme işlemini gösterir <xref:System.Xml.XPath.XPathItem.ValueAs%2A> .  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [System.Xml Sınıflarında Tür Desteği](type-support-in-the-system-xml-classes.md)
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](node-set-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Ayıklama](extract-xml-data-using-xpathnavigator.md)
