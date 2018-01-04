---
title: "XML XPathNavigator kullanarak verileri değiştirme"
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
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cc46aeda6efe9f21bc094a4bc9d211fc282e9b65
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="modify-xml-data-using-xpathnavigator"></a>XML XPathNavigator kullanarak verileri değiştirme
<xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümleri ve bir XML belgesi değerleri değiştirmek için kullanılan yöntemler kümesi sağlar. Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesnesi olmalıdır düzenlenebilir, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> olmalıdır `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator>tarafından oluşturulan bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. <xref:System.Xml.XPath.XPathNavigator>tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunur ve herhangi bir düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesne bir <xref:System.Xml.XPath.XPathDocument> nesne sonucunda bir <xref:System.NotSupportedException>.  
  
 Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML veri okunurken](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Düğümleri değiştirme  
 Bir düğüm değerini değiştirmek için basit bir teknik kullanmaktır <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
 Aşağıdaki tabloda bu yöntemleri etkilerini farklı düğüm türleri listelenmektedir.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Değiştirilen veri|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Desteklenmez.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Öğesinin içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Öznitelik değeri.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Metin içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Hedef hariç içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Açıklama içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Desteklenmiyor.|  
  
> [!NOTE]
>  Düzenleme <xref:System.Xml.XPath.XPathNodeType.Namespace> düğümleri veya <xref:System.Xml.XPath.XPathNodeType.Root> düğümü desteklenmiyor.  
  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı ayrıca takın ve düğüm kaldırmak için kullanılan yöntemler kümesi sağlar. Ekleme ve bir XML belgesinden düğümleri kaldırma hakkında daha fazla bilgi için bkz: [XML XPathNavigator kullanarak veri ekleme](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) ve [XML XPathNavigator kullanarak verileri Kaldır](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) Konular.  
  
### <a name="modifying-untyped-values"></a>Türsüz değerlerini değiştirme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler türsüz `string` değeri düğümün değeri olarak bir parametre olarak geçirilen <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır. Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa, yeni değer düğüm türüne göre geçerli olduğunu doğrulama olmadan eklenir.  
  
 Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi tüm güncelleştirmek için kullanılan `price` öğelerinde `contosoBooks.xml` dosya.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Yazılı değerlerini değiştirme  
 Bir düğüm türü bir basit W3C XML Şeması olduğunda türü, tarafından eklenen yeni değer <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değer ayarlamadan önce yöntemi basit türe ilişkin modelleri karşı denetlenir. Yeni değer düğüm türüne göre geçerli değilse (örneğin, bir değeri ayarlamak `-1` türü olan bir öğe üzerinde `xs:positiveInteger`), bir özel durum oluşur.  
  
 Aşağıdaki örnek değerini değiştirme girişiminde `price` ilk öğesinin `book` öğesinde `contosoBooks.xml` dosyasını bir <xref:System.DateTime> değeri. XML şema türü olduğundan `price` öğesi olarak tanımlanır `xs:decimal` içinde `contosoBooks.xsd` dosyaları, bu sonuçları bir özel durum.  
  
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
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Kesin türü belirtilmiş XML verileri düzenleme etkileri  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfını kullanır W3C XML Şeması temeli olarak kesin türü belirtilmiş XML açıklamak için. Öğeleri ve özniteliklerinin W3C XML şema belgesi doğrulanması temel türü bilgilerle açıklama. Metin içeriği yalnızca içerebilir o basit türler denir sırada diğer öğeleri ya da öznitelikleri içeren öğeler karmaşık türler denir.  
  
> [!NOTE]
>  Özniteliklerin yalnızca basit türler olabilir.  
  
 Öğe veya öznitelik şema türü tanımına belirli kuralları uyuyorsa geçerli olması için kabul edilebilir. Basit tür olan bir öğeyi `xs:int` -2147483648 ve 2147483647 arasında olacak şema geçerli olması için sayısal bir değer içermesi gerekir. Karmaşık türler için öğenin şema geçerlilik şema-geçerliliği kendi alt öğeleri ve özniteliklerinin bağlıdır. Bu nedenle, karmaşık tür tanımına göre bir öğeyi geçerliyse, tüm alt öğeleri ve özniteliklerinin tür tanımlarını karşı geçerlidir. Alt öğeler biri bile veya bir öğenin öznitelikleri tür tanımına göre geçersiz veya bilinmeyen bir geçerlilik yüklüyse, benzer şekilde, öğe ayrıca geçersiz veya Bilinmeyen geçerlilik.  
  
 Öğenin geçerliliğini kendi alt öğelerini ve özniteliklerini geçerliliğini bağımlı olması koşuluyla, değişiklik ya da daha önce geçerli ise, öğenin geçerliliğini değiştirilmesine neden. Alt öğe veya öğenin özniteliklerini eklendiğinde, güncelleştirilmiş, silinmiş veya, özellikle, ardından öğenin geçerliliğini bilinmeyen haline gelir. Bu tarafından temsil edilen <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> öğenin özelliğinin <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği ayarlanıyor <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>. Ayrıca, öğenin üst öğesi (ve kendi üst öğesi vb.) geçerliliğini de bilinmeyen azaldığından Bu etkiyi yukarı yinelemeli olarak XML belgesi aktarılır.  
  
 Şema doğrulama hakkında daha fazla bilgi ve <xref:System.Xml.XPath.XPathNavigator> sınıfı için bkz: [şema XPathNavigator kullanarak doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Özniteliklerini değiştirme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri, türsüz ve yazılı özniteliği düğümlerin yanı sıra "Düğümleri değiştirme" bölümünde listelenen diğer düğüm türleri değiştirmek için kullanılabilir.  
  
 Aşağıdaki örnek değerini değiştirir `genre` ilk öznitelik `book` öğesinde `books.xml` dosya.  
  
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
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri, "Türsüz değerleri değiştirme" ve "Yazdığınız değerleri değiştirme" bölümlerine bakın.  
  
## <a name="innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfı düğümlerin XML biçimlendirmesini değiştirme bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde verilen XML ayrıştırılmış içeriğini `string`. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde geçerli düğüm yanı sıra.  
  
 Aşağıdaki örnek kullanır <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> değerini değiştirmek için özellik `price` öğesi ve yeni bir INSERT `discount` ilk öznitelikte `book` öğesinde `contosoBooks.xml` dosya.  
  
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
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Namespace düğümleri değiştirme  
 Eklenen, güncelleştirilen silinmiş ve yönetilebilen normal öznitelikler varsa gibi belge nesne modeli (DOM)'da, ad alanı bildirimleri kabul edilir. <xref:System.Xml.XPath.XPathNavigator> Sınıfı izin vermiyor bu tür işlemler ad alanı düğümlerde ad alanı düğüm değerinin değiştirilmesi aşağıdaki örnekte gösterildiği gibi öğeleri ve öznitelikleri düğüm ad kapsamında kimliğini değişebileceği için.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, her öğenin ad alanı URI değeri değiştiğinden bu etkin belgedeki her öğe yeniden adlandırır.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 Ad alanı bildirimleri yerleştirildikleri kapsamındaki çakışmadığından ad alanı düğümleri ekleme tarafından verilir <xref:System.Xml.XPath.XPathNavigator> sınıfı. Bu durumda, ad alanı bildirimleri XML belgesi olarak alt kapsamlar adresindeki bildirilmemiş ve aşağıdaki örnekte gösterildiği gibi yeniden adlandırarak sonuçlanmaz.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Yukarıdaki XML örneği aşağıdaki şekilde değiştirdiyseniz, ad alanı bildirimleri düzgün bir ad alanı bildiriminin kapsamını aşağıda XML belgesi arasında yayılır.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 Yukarıdaki, öznitelik XML örnekte `a:parent-id` eklenmesini `parent` öğesinde `http://www.contoso.com/parent-id` ad alanı. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Yöntemi üzerinde konumlandırılmış sırada özniteliğini eklemek için kullanılan `parent` öğesi. `http://www.contoso.com` Ad alanı bildirimi tarafından otomatik olarak eklenir <xref:System.Xml.XPath.XPathNavigator> XML belgenin geri kalanında tutarlılığını korumak için sınıf.  
  
## <a name="modifying-entity-reference-nodes"></a>Varlık başvurusu düğümleri değiştirme  
 Varlık başvurusu düğümler bir <xref:System.Xml.XmlDocument> nesne salt okunur ve ya da kullanarak düzenlenemez <xref:System.Xml.XPath.XPathNavigator> veya <xref:System.Xml.XmlNode> sınıfları. Bir varlık referans düğümün değiştirmek için her türlü girişim sonuçlanıyor bir <xref:System.InvalidOperationException>.  
  
## <a name="modifying-xsinil-nodes"></a>Xsi: nil düğümleri değiştirme  
 W3C XML Şeması öneri bırakılabilir olan bir öğeyi kavramını sunmaktadır. Bir öğe bırakılabilir olduğunda, öğenin içeriği olmamasına ve hala geçerli olması mümkündür. Bir nesne kurulduğunu kavramına bırakılabilir edilen bir öğenin kavram benzer `null`. Ana fark bir `null` nesne olamaz herhangi bir şekilde erişilen, ancak bir `xsi:nil` öğesi hala erişilebilir, ancak içeriği (alt öğeler veya metin) yok öznitelikleri gibi özellikler içeriyor. Varlığını `xsi:nil` öznitelik değerini `true` bir öğede bir XML belgesi öğenin içeriği yok göstermek için kullanılır.  
  
 Varsa bir <xref:System.Xml.XPath.XPathNavigator> nesne geçerli bir öğesi ile içerik eklemek için kullanılan bir `xsi:nil` öznitelik değerini `true`, değerini kendi `xsi:nil` özniteliği olarak ayarlanmış `false`.  
  
> [!NOTE]
>  Varsa bir öğesiyle içeriğini bir `xsi:nil` özniteliğini `false` olduğu silinmiş, öznitelik değeri için değiştirilmez `true`.  
  
## <a name="saving-an-xml-document"></a>Bir XML belgesi kaydetme  
 Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan düzenleme yöntemleri sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı. Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne için bkz: [kaydetme ve bir belgeyi yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator Kullanarak XML Verileri Ekleme](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak XML Verilerini Kaldırma](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
