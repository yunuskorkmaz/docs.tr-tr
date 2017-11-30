---
title: "XML verilerini XPathNavigator kullanarak yazılan kesinlikle erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61c78adff541ac2ba261d31776478a0468e21d4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>XML verilerini XPathNavigator kullanarak yazılan kesinlikle erişme
XPath 2.0 veri modeli örneği olarak <xref:System.Xml.XPath.XPathNavigator> sınıfı, ortak dil çalışma zamanı (CLR) türleri ile eşleştirir kesin türü belirtilmiş veri içerebilir. XPath 2.0 veri modeline göre yalnızca öğeleri ve özniteliklerinin kesin türü belirtilmiş veri içerebilir. <xref:System.Xml.XPath.XPathNavigator> Sınıfı içindeki verilere erişilirken mekanizmalar sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne bir veri türünden diğerine dönüştürme mekanizmalar yanı sıra kesin türü belirtilmiş veri olarak.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>XPathNavigator tarafından kullanıma sunulan tür bilgileri  
 XML 1.0 veri türüdür teknik, DTD, XML işlenen sürece şema tanım dili (XSD) şeması ya da başka bir mekanizma. Bir XML öğesi veya özniteliği ile ilişkili olabileceği türü bilgi kategorileri arasında mevcuttur.  
  
-   Basit CLR türleri: XML şema dilleri hiçbiri ortak dil çalışma zamanı (CLR) türleri doğrudan desteklemez. Olarak basit bir öğe ve öznitelik içeriği en uygun CLR türü olarak görüntülenmesini yararlıdır çünkü tüm basit içerik girilebilen <xref:System.String> herhangi biriyle şema bilgileri olmadığında potansiyel olarak bu içeriği daraltmayı şema bilgileri eklendi daha uygun bir tür. En iyi kullanarak basit öğe ve öznitelik içerik CLR türü eşleşen bulabilirsiniz <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> özelliği. Eşleme Şeması yerleşik türleri CLR türleri hakkında daha fazla bilgi için bkz: [türü desteği System.Xml sınıflardaki](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Basit (CLR) türleri listesi: bir öğe veya öznitelik basit içerikle beyaz boşlukla ayrılmış bir değer listesi içerebilir. Bir "listesi türü." XML şeması tarafından belirtilen değerler Bir XML Şeması olmaması durumunda, basit tür içeriği tek bir metin düğümü olarak kabul. Bir XML Şeması kullanılabilir olduğunda, bu basit içerik her CLR nesnesini bir koleksiyona eşler basit bir türe sahip bir dizi atomik değerleri olarak gösterilebilir. Eşleme Şeması yerleşik türleri CLR türleri hakkında daha fazla bilgi için bkz: [türü desteği System.Xml sınıflardaki](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Yazılan değeri: Şema doğrulanmış öznitelik veya basit bir tür bir öğesiyle belirtilmiş bir değer içeriyor. Bu değer, sayısal, dize veya tarih türü gibi basit bir türüdür. Düğüm değerinin yerine yalnızca daha uygun bir türü olarak erişebilmesi için CLR türleri için yerleşik basit içindeki tüm türler XSD eşlenebilir olarak bir <xref:System.String>. Öznitelikler veya öğenin alt öğeleri olan bir öğe bir karmaşık tür olarak kabul edilir. Karmaşık türü (yalnızca alt öğeleri olarak metin düğümleri) basit içerikle yazılan değeri, içeriği basit tür aynıdır. Karmaşık türü karmaşık içerik (bir veya daha fazla alt öğe) ile yazılan değeri olarak döndürülen tüm alt metin düğümleri birleşimini dize değeri bir <xref:System.String>. Eşleme Şeması yerleşik türleri CLR türleri hakkında daha fazla bilgi için bkz: [türü desteği System.Xml sınıflardaki](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Şema dil belirli türü adı: Çoğu durumda, bir yan-dış şeması uygulama etkisi ayarlanır, CLR Türleri düğüm değerinin erişim sağlamak için kullanılır. Ancak, bir XML belgesi uygulanan belirli bir şema ile ilişkili türü incelemek istediğiniz durumlar olabilir. Örneğin, bir XML belgesi arama "PurchaseOrder" ekli bir şemaya göre içerik türü için belirlenen tüm öğeleri ayıklanıyor isteyebilirsiniz. Böyle türü bilgileri yalnızca şema doğrulaması sonucu olarak ayarlanabilir ve bu bilgileri üzerinden erişilen <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> ve <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfı. Daha fazla bilgi için aşağıdaki Post şema doğrulama bilgi (PSVI) bölümüne bakın.  
  
-   Türü yansıma belirli şema dil: diğer durumlarda, bir XML belgeye uygulanan şema özgü türü daha ayrıntılı bilgi edinmek isteyebilirsiniz. Örneğin, bir XML dosyası okunurken ayıklamak istediğiniz `maxOccurs` XML belgesinde bazı özel bir hesaplama gerçekleştirmek için geçerli her düğüm için öznitelik. Bu bilgiler yalnızca şema doğrulaması ayarlandığından aracılığıyla erişilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı. Daha fazla bilgi için aşağıdaki Post şema doğrulama bilgi (PSVI) bölümüne bakın.  
  
## <a name="xpathnavigator-typed-accessors"></a>XPathNavigator yazılan erişimciler  
 Aşağıdaki tabloda çeşitli özellikleri ve yöntemleri gösteren <xref:System.Xml.XPath.XPathNavigator> bir düğüm türü bilgilerini erişmek için kullanılan sınıf.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Geçerli ise bu düğüm için XML şema türü bilgileri içerir.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Doğrulama sonrasında eklenen düğümün Post şema doğrulama bilgi içerir. Bu, geçerlilik bilgi yanı sıra XML şema türü bilgileri içerir.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Düğümün yazılan değeri CLR türü.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Bir veya birden çok CLR türü değerleri gibi düğümünün düğüm XML şema türü en yakın eşleşmeyi içeriktir.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<xref:System.String> Geçerli düğüm değerini dönüştürmek için bir <xref:System.Boolean> için XPath 2.0 atama kurallarına göre değeri `xs:boolean`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<xref:System.String> Geçerli düğüm değerini dönüştürmek için bir <xref:System.DateTime> için XPath 2.0 atama kurallarına göre değeri `xs:datetime`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<xref:System.String> Geçerli düğüm değerini dönüştürmek için bir <xref:System.Double> için XPath 2.0 atama kurallarına göre değeri `xsd:double`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<xref:System.String> Geçerli düğüm değerini dönüştürmek için bir <xref:System.Int32> için XPath 2.0 atama kurallarına göre değeri `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<xref:System.String> Geçerli düğüm değerini dönüştürmek için bir <xref:System.Int64> için XPath 2.0 atama kurallarına göre değeri `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Hedef türü XPath 2.0 atama kurallarına göre cast düğüm içerikleri.|  
  
 Eşleme Şeması yerleşik türleri CLR türleri hakkında daha fazla bilgi için bkz: [türü desteği System.Xml sınıflardaki](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Post şema doğrulama bilgi (PSVI)  
 Bir XML Şeması işlemci XML bilgi giriş olarak kabul eder ve bir Post şema doğrulama bilgi (PSVI) içine dönüştürür. Bir PSVI yeni eklenen bilgiler öğeleri ve varolan bilgi öğelerine eklenen yeni özellikleri özgün giriş XML bilgi kümesi olur. Üç geniş sınıfları tarafından sunulan PSVI içinde XML bilgi eklenen bilgilerin vardır <xref:System.Xml.XPath.XPathNavigator>.  
  
1.  Doğrulama sonuçlarını: olup bir öğe veya öznitelik başarıyla veya doğrulandı bilgileri. Bu tarafından sunulan <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> özelliği <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
2.  Varsayılan bilgileri: Göstergeleri mi aldığını veya şemasında belirtilen varsayılan değerleri öğe veya öznitelik değeri alındı. Bu tarafından sunulan <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> özelliği <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
3.  Tür ek açıklamaları: Tür tanımları veya öğe ve öznitelik bildirimleri olabilir şema bileşenleri başvurular. <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> geçerli ise düğümün belirli türü bilgileri içerir. Bir düğüm geçerliliğini, ne zaman, ardından daha sonra doğrulandı gibi bilinmiyorsa düzenlenemez. ardından <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özelliği ayarlanmış `null` ancak tür bilgileri çeşitli özelliklerini hala kullanılabilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
 Post şema doğrulama tarafından sunulan bilgi bilgileri kullanarak aşağıdaki örnekte gösterilmiştir <xref:System.Xml.XPath.XPathNavigator>.  
  
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
  
 Örnek alır `books.xml` dosya giriş olarak.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Bu örnek ayrıca alır `books.xsd` şema giriş olarak.  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a>Değerlerini özellikleri kullanılarak yazılan değerlerin alın  
 Düğüm yazılan değerinin erişerek alınabilir <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özelliği <xref:System.Xml.XPath.XPathNavigator>. Belirli durumlarda farklı bir türe düğüm yazılan değerinin dönüştürmek isteyebilirsiniz. Bir XML düğümden sayısal değer alma ortak bir örnektir. Örneğin, aşağıdaki doğrulanmamış ve türü belirsiz XML belgesi göz önünde bulundurun.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Varsa <xref:System.Xml.XPath.XPathNavigator> üzerinde konumlandırılmış `price` öğesi <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özelliği olacaktır `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> özelliği olacaktır <xref:System.String>ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özelliği, dize olacaktır `10.00`.  
  
 Ancak, bu kullanarak bir sayısal değer olarak değerini ayıklayın hala mümkündür <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, veya <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> yöntem ve özellikleri. Aşağıdaki örnekte, bu tür cast kullanarak bir gerçekleştirme gösterilmektedir <xref:System.Xml.XPath.XPathItem.ValueAs%2A> yöntemi.  
  
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
  
 Eşleme Şeması yerleşik türleri CLR türleri hakkında daha fazla bilgi için bkz: [türü desteği System.Xml sınıflardaki](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [System.Xml sınıflardaki türü desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 [XPath veri modelini kullanarak işlem XML verileri](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Düğüm kümesi Gezinti XPathNavigator kullanma](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [Özniteliği ve XPathNavigator kullanarak Namespace düğümü gezinme](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [XPathNavigator kullanarak XML veri ayıklamak](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
