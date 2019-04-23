---
title: XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1905e9f1d80931bd15cff5f3d0a92ceee29435ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319891"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme
XPath 2.0 veri modeli, bir örneği olarak <xref:System.Xml.XPath.XPathNavigator> sınıfı, ortak dil çalışma zamanı (CLR) türleri ile eşleştirir, kesin türü belirtilmiş veri içerebilir. XPath 2.0 veri modeline göre yalnızca öğeler ve öznitelikler kesin türü belirtilmiş veri içerebilir. <xref:System.Xml.XPath.XPathNavigator> Sınıf içindeki verilerine erişmek için bir mekanizma sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> başka bir veri türünden dönüştürme mekanizmaları yanı sıra, kesin türü belirtilmiş veri nesnesi.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>XPathNavigator tarafından kullanıma sunulan tür bilgileri  
 XML 1.0 verilerdir teknik türü sürece işlenen bir DTD'nin XML Şeması Tanım Dili (XSD) şemaya veya başka bir mekanizma. Bir XML öğesi veya özniteliği ile ilişkilendirilebilen türü bilgi kategorilerde vardır.  
  
-   Basit CLR türleri: XML şema diller hiçbiri doğrudan ortak dil çalışma zamanı (CLR) türlerini destekler. Olarak basit bir öğe ve öznitelik içeriği en uygun CLR türü olarak görüntülemek yararlı olur çünkü tüm basit içerik yazılabilir <xref:System.String> tüm şema bilgileri olmadığında bu içerik için büyük olasılıkla iyileştirme şema bilgileri eklendi daha uygun bir tür. CLR basit öğe ve öznitelik içerik türünü kullanarak eşleştirme en iyi bulabilirsiniz <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> özelliği. Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Basit (CLR) türleri listeler: Bir öğe veya öznitelik basit içeriğe sahip boşluk tarafından ayrılmış değerlerin bir listesini içerebilir. Bir "listesi türü." bir XML şeması tarafından belirtilen değerler Bir XML Şeması olmaması durumunda tür basit içerik tek bir metin düğümü olarak kabul edilir. Bir XML Şeması kullanılabilir olduğunda, bir dizi atomik her CLR nesnelerin bir koleksiyona eşler basit bir tür olan değerleri gibi bu basit içerik sunulabilir. Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Belirtilen değer: Bir şema doğrulanmış öznitelik veya öğenin basit bir tür ile yazılan bir değeri var. Bu değer bir sayı, dize veya tarih türü gibi basit bir türdür. CLR türleri, daha uygun bir tür yerine yalnızca bir düğümün değerini erişim sağlamak için tüm yerleşik basit türler XSD eşleştirilmiş olarak bir <xref:System.String>. Öznitelikleri veya alt öğesi olan bir öğe, bir karmaşık tür olarak kabul edilir. Basit içerik (yalnızca alt öğeleri olarak metin düğümleri) sahip bir karmaşık türü belirlenmiş değerini, kendi içerik basit türü aynıdır. Karmaşık içerik (bir veya daha fazla alt öğe) sahip bir karmaşık türü belirlenmiş değerini birleştirme, tüm alt metin düğümleri olarak döndürülen dize değeridir bir <xref:System.String>. Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Dil şeması belirli tür adı: Çoğu durumda, bir yan dış şeması uygulama etkisi olarak ayarlanır, CLR türleri, bir düğümün değerini erişim sağlamak için kullanılır. Bununla birlikte, burada bir XML belgeye uygulanan belirli bir şema ile ilişkili tür incelemek isteyebilirsiniz durumlar olabilir. Örneğin, bir XML belgesi arama "PurchaseOrder" eklenmiş bir şemaya göre içerik türü için belirlenen tüm öğeleri ayıklama isteyebilirsiniz. Bu tür bilgileri yalnızca şema doğrulama sonucu olarak ayarlanabilir ve bu bilgileri aracılığıyla erişilir <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> ve <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfı. Daha fazla bilgi için aşağıdaki sonrası Schema doğrulama bilgi kümesi (PSVI) bölümüne bakın.  
  
-   Dil şeması belirli tür yansıma: Diğer durumlarda, daha fazla bir XML belgeye uygulanan şema özgü türü ayrıntılarını almak isteyebilirsiniz. Örneğin, bir XML dosyası okunurken ayıklamak istediğiniz `maxOccurs` öznitelik XML belgesindeki özel bir hesaplama gerçekleştirmek için geçerli her düğüm için. Bu bilgiler yalnızca şema doğrulaması ayarlandığından aracılığıyla erişilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı. Daha fazla bilgi için aşağıdaki sonrası Schema doğrulama bilgi kümesi (PSVI) bölümüne bakın.  
  
## <a name="xpathnavigator-typed-accessors"></a>XPathNavigator türü belirtilmiş erişimcileri  
 Aşağıdaki tabloda, çeşitli özellikleri ve yöntemleri gösterilmektedir <xref:System.Xml.XPath.XPathNavigator> bir düğüm türü bilgilerini erişmek için kullanılan sınıf.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Geçerli ise bu düğüm için XML şema türü bilgisi içerir.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Bu doğrulamadan sonra eklenen düğümünün Post şema doğrulama bilgi kümesi içerir. Bu, geçerlilik bilgi yanı sıra XML şema türü bilgisi içerir.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Türü belirtilmiş bir düğümün değerini CLR türü.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Bir veya birden çok CLR türü değerleri gibi düğümünün düğüm XML şema türü için en yakın eşleşme içeriktir.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.Boolean> XPath 2.0 atama kurallarına göre bir değer `xs:boolean`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.DateTime> XPath 2.0 atama kurallarına göre bir değer `xs:datetime`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.Double> XPath 2.0 atama kurallarına göre bir değer `xsd:double`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.Int32> XPath 2.0 atama kurallarına göre bir değer `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.Int64> XPath 2.0 atama kurallarına göre bir değer `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|XPath 2.0 atama kurallara göre hedef türüne cast düğüm içeriği.|  
  
 Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Sonrası Schema doğrulama bilgi kümesi (PSVI)  
 Bir XML Şeması işlemci bir XML bilgi kümesi girdi olarak kabul eder ve bir sonrası Schema doğrulama bilgi kümesi (PSVI) içine dönüştürür. Bir PSVI yeni eklenen bilgi öğeleri ve bilgi öğelere eklenen yeni özellikleri özgün giriş XML bilgi kümesi olur. XML bilgi kümesi tarafından kullanıma sunulan PSVI içinde eklenen bilgilerin geniş üç sınıfı vardır <xref:System.Xml.XPath.XPathNavigator>.  
  
1. Doğrulama sonuçları: Olup bir öğe veya öznitelik başarıyla veya doğrulandı dair bilgiler. Tarafından sunulan bu <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> özelliği <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
2. Varsayılan bilgileri: Göstergelerden eklenebilir olup varsayılan değerleri veya şemasında belirtilen öğe veya öznitelik değeri alındı. Tarafından sunulan bu <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> özelliği <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
3. Tür ek açıklamaları: Tür tanımları veya öğe ve öznitelik bildirimleri şema bileşenleri başvurular. <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> geçerli olup olmadığını düğümünün belirli tür bilgilerini içerir. Geçerlilik düğümünün, ne zaman, ardından daha sonra doğrulandı gibi bilinmiyorsa düzenlendi. ardından <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özelliği `null` ancak tür bilgileri çeşitli özelliklerini hala kullanılabilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
 Sonrası Schema doğrulama bilgi tarafından kullanıma sunulan kümesi içindeki bilgileri kullanarak aşağıdaki örnekte gösterilmiştir <xref:System.Xml.XPath.XPathNavigator>.  
  
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
  
 Örnek alan `books.xml` dosya giriş olarak.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Bu örnek ayrıca alır `books.xsd` giriş olarak şema.  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a>Değerlerini özellikleri kullanılarak yazılan değerler elde  
 Türü belirtilmiş bir düğümün değerini erişerek alınabilir <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özelliği <xref:System.Xml.XPath.XPathNavigator>. Bazı durumlarda, belirlenmiş bir düğümün değerini farklı bir türe dönüştürmek isteyebilirsiniz. Bir XML düğümünü sayısal değer alma yaygın bir örnektir. Örneğin, aşağıdaki doğrulanmamış ve türü belirsiz XML belgesi göz önünde bulundurun.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Varsa <xref:System.Xml.XPath.XPathNavigator> üzerinde konumlandırılmış `price` öğesi <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özelliği olacaktır `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> özellik olacak <xref:System.String>ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özelliği, bir dize olacak `10.00`.  
  
 Ancak, yine de kullanarak bir sayısal değer olarak değerini ayıklamak mümkün <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, veya <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> yöntem ve özellikleri. Aşağıdaki örnekte, böyle bir dönüştürme gerçekleştirme gösterilmektedir <xref:System.Xml.XPath.XPathItem.ValueAs%2A> yöntemi.  
  
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
  
 Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [System.Xml Sınıflarında Tür Desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Ayıklama](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
