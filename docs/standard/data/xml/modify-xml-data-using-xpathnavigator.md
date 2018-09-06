---
title: XPathNavigator kullanarak XML verilerini değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 219327d246416cfb3d76919680aa74a58bae5fb3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884992"
---
# <a name="modify-xml-data-using-xpathnavigator"></a>XPathNavigator kullanarak XML verilerini değiştirme
<xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümleri ve bir XML belgesi değerleri değiştirmek için kullanılan yöntemler kümesi sağlar. Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesne olmalıdır düzenlenemez, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. <xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesnelerin <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunurdur ve tüm düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> nesnesi tarafından oluşturulan bir <xref:System.Xml.XPath.XPathDocument> nesne sonucunda bir <xref:System.NotSupportedException>.  
  
 Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML verileri okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Düğümleri değiştirme  
 Bir düğümün değerini değiştirmek için basit bir yöntem kullanmaktır <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
 Aşağıdaki tabloda, farklı bir düğüme türlerinin bu yöntemlerin efektleri listeler.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Değiştirilen veriler|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Desteklenmez.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Öğe içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Öznitelik değeri.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Metin içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Hedef hariç içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|İçerik açıklaması.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Desteklenmiyor.|  
  
> [!NOTE]
>  Düzenleme <xref:System.Xml.XPath.XPathNodeType.Namespace> düğümleri veya <xref:System.Xml.XPath.XPathNodeType.Root> düğümü desteklenmiyor.  
  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı ekleyin ve düğümleri kaldırma için kullanılan yöntemler kümesi sağlar. Ekleme ve bir XML belgesinden düğümleri kaldırma hakkında daha fazla bilgi için bkz. [Ekle XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) ve [kaldırmak XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) konuları.  
  
### <a name="modifying-untyped-values"></a>Yazılmamış değerlerini değiştirme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler yazılmamış `string` düğümün değeri olarak bir parametre olarak geçirilen değer <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda. Değer, her türlü olmadan veya şema bilgileri kullanılabilir durumdaysa, yeni değer düğüm türüne göre geçerli olduğu doğrulanıyor olmadan eklenir.  
  
 Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> tümünü güncelleştirmek için kullanılan yöntemi `price` öğelerinde `contosoBooks.xml` dosya.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Girilen değerleri değiştirme  
 Bir düğüm türü basit bir W3C XML Şeması olduğunda tür, tarafından eklenen yeni değer <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi değeri ayarlanmadan önce basit türe ilişkin modelleri karşı denetlenir. Yeni değer düğüm türüne göre geçerli değilse (örneğin, bir değeri ayarlamak `-1` türü olan bir öğede `xs:positiveInteger`), bir özel durum oluşur.  
  
 Aşağıdaki örnek, değerini değiştirme girişiminde `price` ilk öğenin `book` öğesinde `contosoBooks.xml` dosyasını bir <xref:System.DateTime> değeri. XML şema türü olduğundan `price` öğesi olarak tanımlanmış olan `xs:decimal` içinde `contosoBooks.xsd` dosyaları, bu sonuçları bir özel durum.  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Kesin türü belirtilmiş XML verilerini düzenleme etkileri  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfını kullanan W3C XML şema temel olarak kesin tür belirtilmiş XML açıklamak için. Öğeler ve öznitelikler W3C XML şema belgesi karşı doğrulama temel türü bilgilerini ile açıklama eklenebilir. Metinsel içeriği yalnızca içerebilir bunlar basit türler olarak adlandırılır ancak diğer öğeler veya öznitelikleri içeren öğelerin karmaşık türler olarak adlandırılır.  
  
> [!NOTE]
>  Öznitelikleri Basit türler yalnızca olabilir.  
  
 Bir öğe veya öznitelik şema türü tanımına belirli kuralları uyuyorsa geçerli olması için kabul edilebilir. Basit tür olan bir öğeyi `xs:int` -2147483648 ile 2147483647 şema geçerli olması için arasında sayısal bir değer içermesi gerekir. Karmaşık türler için öğenin şema geçerlilik şema-geçerliliğini üzerinde kendi alt öğeler ve öznitelikler bağlıdır. Bu nedenle tüm alt öğeler ve öznitelikler, karmaşık tür tanımına göre bir öğe geçerliyse, tür tanımlarını karşı geçerli. Alt öğeleri bile birini veya bir öğenin öznitelikleri tür tanımına karşı geçersiz veya bilinmeyen bir geçerliliği vardır, benzer şekilde, öğe ayrıca geçersiz veya Bilinmeyen geçerlilik.  
  
 Geçerlilik bir öğe, alt öğeler ve öznitelikler geçerliliğini bağımlı olduğu düşünüldüğünde, daha önce geçerli ise öğe geçerliliğini değiştirme ya da bir değişiklik neden. Bir öğenin öznitelikleri ve alt öğeleri eklenen, güncelleştirilen veya silinen, özellikle daha sonra geçerliliğini öğesinin bilinmeyen olur. Bu tarafından temsil edilen <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> öğenin özelliği <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği olan kümesine <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>. Ayrıca, öğenin üst öğesi (ve kendi üst öğesi vb.) geçerliliğini ayrıca bilinmeyen olur çünkü bu etkiyi yukarı yinelemeli olarak XML belgesi aktarılır.  
  
 Şema doğrulaması hakkında daha fazla bilgi ve <xref:System.Xml.XPath.XPathNavigator> sınıfı [XPathNavigator kullanarak şema doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Öznitelikleri değiştirme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri, türü belirsiz ve yazılmış öznitelik düğümleri ve bunun yanı sıra "Düğümleri değiştirme" bölümünde listelenen diğer düğüm türleri değiştirmek için kullanılabilir.  
  
 Aşağıdaki örnek değiştirir `genre` ilk öznitelik `book` öğesinde `books.xml` dosya.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri "Yazılmamış değerler değiştirme" ve "Yazılan değerleri değiştirme" bölümlere bakın.  
  
## <a name="innerxml-and-outerxml-properties"></a>Sınıfının InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfını değiştirin XML işaretlemesini düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde belirli XML ayrıştırılmış içeriğiyle `string`. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde geçerli düğüm yanı sıra kendisini.  
  
 Aşağıdaki örnekte <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellik değerini değiştirmek için `price` öğesi ve yeni bir ekleme `discount` ilk öznitelik `book` öğesinde `contosoBooks.xml` dosya.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Namespace düğümleri değiştirme  
 Eklenen, güncelleştirilen silindi ve normal öznitelikleri olmaları durumunda gibi belge nesne modeli (DOM)'da, ad alanı bildirimi kabul edilir. <xref:System.Xml.XPath.XPathNavigator> Sınıfı izin vermez ad alanı düğümleri bu işlemleri çünkü bir ad alanı düğümü değerini değiştirerek aşağıdaki örnekte gösterildiği gibi öğeleri ve öznitelikleri ad alanı düğümünü kapsamında kimliğini değiştirebilirsiniz.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, her öğenin ad alanı URI değerini değiştiğinden bu etkili bir şekilde belge içindeki her öğe yeniden adlandırır.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 Ad alanı bildirimi yerleştirildikleri kapsamda ile çakışmadığından ad alanı düğümleri ekleme tarafından verilir <xref:System.Xml.XPath.XPathNavigator> sınıfı. Bu durumda, ad alanı bildirimi XML belgesi alt kapsamlar, bildirilmemiş ve aşağıdaki örnekte gösterildiği gibi yeniden adlandırarak sonuçlanmaz.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, ad alanı bildirimi bir ad alanı bildirimi kapsamını aşağıdaki XML belgesi üzerinde doğru şekilde yayılır.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 Yukarıdaki öznitelik XML örnekte `a:parent-id` eklenmesini `parent` öğesinde `http://www.contoso.com/parent-id` ad alanı. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Konumlandırılıp sırada özniteliğini eklemek için kullanılan yöntemi `parent` öğesi. `http://www.contoso.com` Ad alanı bildirimi tarafından otomatik olarak eklenir <xref:System.Xml.XPath.XPathNavigator> XML belgenin geri kalanında tutarlılığını korumak için sınıf.  
  
## <a name="modifying-entity-reference-nodes"></a>Varlık başvurusu düğümleri değiştirme  
 Varlık başvurusu düğümlerin bir <xref:System.Xml.XmlDocument> nesnesi salt okunurdur ve düzenlenemez kullanarak <xref:System.Xml.XPath.XPathNavigator> veya <xref:System.Xml.XmlNode> sınıfları. Bir varlık referans düğümün değiştirmek için her türlü girişim sonuçlanıyor bir <xref:System.InvalidOperationException>.  
  
## <a name="modifying-xsinil-nodes"></a>Xsi: nil düğümleri değiştirme  
 W3C XML Şeması öneri nillable edilen bir öğenin kavram tanıtılmaktadır. Bir öğe nillable, öğenin içeriği olmamasına ve hala geçerli olması mümkündür. Bir nesne olan kavramı nillable edilen bir öğenin kavram benzerdir `null`. Ana fark bir `null` nesne olamaz herhangi bir yolla erişilen, while bir `xsi:nil` öğesi, hala erişilebilir, ancak içerik (alt öğeleri veya metin) yok öznitelikleri gibi özelliklere sahiptir. Varlığını `xsi:nil` değerine sahip öznitelik `true` bir öğedeki bir XML belge bir öğenin içerik sahip olduğunu göstermek için kullanılır.  
  
 Varsa bir <xref:System.Xml.XPath.XPathNavigator> nesnesi ile geçerli bir öğesi için içerik eklemek için kullanılır bir `xsi:nil` değerine sahip öznitelik `true`, değerini kendi `xsi:nil` özniteliği `false`.  
  
> [!NOTE]
>  Varsa ile bir öğenin içeriğini bir `xsi:nil` özniteliğini `false` olduğu silinmiş, öznitelik değeri için değişmez `true`.  
  
## <a name="saving-an-xml-document"></a>Bir XML belgesi kaydediliyor  
 Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan düzenleme yöntemlerini sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı. Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne, bkz: [kaydetme ve belge yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [XPathNavigator Kullanarak XML Verileri Ekleme](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak XML Verilerini Kaldırma](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
