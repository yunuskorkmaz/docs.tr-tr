---
title: XPathNavigator Kullanarak XML Verileri Ekleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 1dbe1a709f7c1b527a1754ab943a0a10ff52c6e8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289193"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verileri Ekleme
Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için kullanılan bir yöntemler kümesi sağlar. Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true` .  
  
 <xref:System.Xml.XPath.XPathNavigator>bir XML belgesini düzenleyebilen nesneler, <xref:System.Xml.XmlDocument.CreateNavigator%2A> sınıfının yöntemiyle oluşturulur <xref:System.Xml.XmlDocument> . <xref:System.Xml.XPath.XPathNavigator>sınıfı tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> salt okunurdur ve bir <xref:System.Xml.XPath.XPathNavigator> nesne tarafından oluşturulan nesnenin Editing yöntemlerini kullanma girişimleri <xref:System.Xml.XPath.XPathDocument> bir ile sonuçlanır <xref:System.NotSupportedException> .  
  
 Düzenlenebilir nesneler oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPathDocument ve XMLDOCUMENT kullanarak XML verilerini okuma](reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Düğüm ekleme  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı, BIR XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için yöntemler sağlar. Bu yöntemler, bir nesnenin geçerli konumuyla ilişkili olarak farklı konumlara düğüm ve öznitelik eklemenize olanak sağlar <xref:System.Xml.XPath.XPathNavigator> ve aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="inserting-sibling-nodes"></a>Eşdüzey düğümler ekleme  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı eşdüzey düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Bu yöntemler, bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlanan düğümden önce ve sonra eşdüzey düğümler ekler.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>Ve <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> yöntemleri aşırı yüklenmiş ve `string` <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklenecek eşdüzey düğümü içeren bir, nesne veya nesne kabul eder. Her iki yöntem de <xref:System.Xml.XmlWriter> eşdüzey düğümleri eklemek için kullanılan bir nesne döndürür.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>Ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri, bir nesneden önce ve sonra bir <xref:System.Xml.XPath.XPathNavigator> nesne, ad alanı ön eki, yerel adı, ad alanı URI 'si ve parametre olarak belirtilen değer kullanılarak konumlandırılmış olan bir eşdüzey düğüm ekler.  
  
 Aşağıdaki örnekte, `pages` `price` dosyasındaki ilk öğenin alt öğesinden önce yeni bir öğe eklenir `book` `contosoBooks.xml` .  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 , Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> bkz <xref:System.Xml.XPath.XPathNavigator> . sınıf başvurusu belgeleri.  
  
### <a name="inserting-child-nodes"></a>Alt düğümler ekleniyor  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı alt düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Bu yöntemler, alt düğümleri sonuna ekler ve sonuna eklenmiş olan düğüm alt düğümleri listesinin başlangıcına <xref:System.Xml.XPath.XPathNavigator> eklenir.  
  
 "Eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemleri `string` <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklenecek alt düğümü içeren bir, nesne veya nesne kabul eder. Her iki yöntem de <xref:System.Xml.XmlWriter> alt düğüm eklemek için kullanılan bir nesne döndürür.  
  
 Ayrıca, "eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve yöntemleri, ' <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> nin sonuna tek bir alt düğüm ekler ve bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda ad alanı ön eki, yerel ad, ad alanı URI 'si ve parametre olarak belirtilen değer kullanılarak konumlandırılmış.  
  
 Aşağıdaki örnekte, `pages` dosyasındaki ilk öğenin alt öğeleri listesine yeni bir alt öğe eklenir `book` `contosoBooks.xml` .  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 , Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> bkz <xref:System.Xml.XPath.XPathNavigator> . sınıf başvurusu belgeleri.  
  
### <a name="inserting-attribute-nodes"></a>Öznitelik düğümleri ekleniyor  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı, öznitelik düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Bu yöntemler, bir nesne üzerinde konumlandırılmış olan öğe düğümüne öznitelik düğümleri ekler <xref:System.Xml.XPath.XPathNavigator> . <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>Yöntemi, bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda ad alanı ön eki, yerel ad, ad alanı URI 'si ve parametre olarak belirtilen değer kullanılarak konumlandırılmış olan öğe düğümünde bir öznitelik düğümü oluşturur. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>Yöntemi <xref:System.Xml.XmlWriter> öznitelik düğümleri eklemek için kullanılan bir nesne döndürür.  
  
 Aşağıdaki örnekte, `discount` `currency` `price` `book` `contosoBooks.xml` yönteminden döndürülen nesneyi kullanarak dosyadaki ilk öğenin alt öğesinde yeni ve öznitelikleri oluşturulur <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> .  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> bkz <xref:System.Xml.XPath.XPathNavigator> . sınıf başvurusu belgeleri.  
  
## <a name="copying-nodes"></a>Düğümler kopyalanıyor  
 Belirli durumlarda, bir XML belgesini başka bir XML belgesinden içerik ile doldurmak isteyebilirsiniz. Hem <xref:System.Xml.XPath.XPathNavigator> sınıf hem de <xref:System.Xml.XmlWriter> sınıf, düğümleri varolan bir <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> nesne veya nesneden bir nesneye kopyalayabilir <xref:System.Xml.XPath.XPathNavigator> .  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>Sınıfının, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> yöntemlerinin hepsi bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator> nesne veya <xref:System.Xml.XmlReader> nesneyi parametre olarak kabul edebilecek aşırı yüklemeleridir.  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A>Sınıfının yönteminde,, <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlNode> <xref:System.Xml.XmlReader> veya nesnesini kabul edebilecek aşırı yüklemeler vardır <xref:System.Xml.XPath.XPathNavigator> .  
  
 Aşağıdaki örnek, tüm `book` öğeleri bir belgeden diğerine kopyalar.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a>Değer ekleme  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> bir düğümün değerlerini bir nesnesine eklemek için ve yöntemlerini sağlar <xref:System.Xml.XmlDocument> .  
  
### <a name="inserting-untyped-values"></a>Türsüz değerler ekleme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Yöntemi, `string` bir parametre olarak geçirilen türsüz değeri <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olan düğümün değeri olarak ekler. Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa düğüm türüne göre yeni değerin geçerli olduğunu doğrulamadan eklenir.  
  
 Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi dosyadaki tüm öğeleri güncelleştirmek için kullanılır `price` `contosoBooks.xml` .  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Yazılan değerler ekleniyor  
 Bir düğümün türü bir W3C XML şeması basit türü olduğunda, yöntemi tarafından yerleştirilen yeni değer, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değer ayarlanmadan önce basit türdeki modellerle denetlenir. Yeni değer, düğüm türüne göre geçerli değilse (örneğin, `-1` türü olan bir öğe üzerinde değerini ayarlamak `xs:positiveInteger` ), bir özel durumla sonuçlanır.  
  
 Aşağıdaki örnek, `price` dosyasındaki ilk öğe öğesinin değerini `book` `contosoBooks.xml` bir değere değiştirmeye çalışır <xref:System.DateTime> . Öğesinin XML şeması türü `price` dosyalarda olarak tanımlandığından `xs:decimal` `contosoBooks.xsd` , bu durum bir özel durumla sonuçlanır.  
  
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
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek de `contosoBooks.xsd` bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Sınıfının ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Özellikleri, <xref:System.Xml.XPath.XPathNavigator> bir <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Özelliği, <xref:System.Xml.XPath.XPathNavigator> belirtilen XML 'nin ayrıştırılmış içeriğiyle bir nesne şu anda konumlandırılmış olan alt düğümlerin XML işaretlemesini değiştirir `string` . Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği de bir nesnenin şu anda bulunduğu alt DÜĞÜMLERIN XML işaretlemesini ve <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün kendisini değiştirir.  
  
 Bu konuda açıklanan yöntemlere ek olarak, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> ÖZELLIKLERI bir XML belgesine düğüm ve değer eklemek için kullanılabilir. <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Ve özelliklerini kullanarak düğüm ve değer ekleme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> bkz. [XPathNavigator kullanarak XML verilerini değiştirme](modify-xml-data-using-xpathnavigator.md) konusu.  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespace ve XML: lang çakışmaları  
 Ad alanı ve bildirimlerin kapsamı ile ilgili bazı çakışmalar `xml:lang` <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> , <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator> nesneleri parametre olarak alan sınıfın,, ve yöntemlerini kullanarak XML verileri eklenirken meydana gelebilir <xref:System.Xml.XmlReader> .  
  
 Olası ad alanı çakışmaları aşağıda verilmiştir.  
  
- Nesne bağlamında kapsam içinde bir ad alanı varsa <xref:System.Xml.XmlReader> , ad alanı URI eşlemesinin öneki <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamında değilse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir.  
  
- Aynı ad alanı URI 'SI hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de nesnenin bağlamı içinde kapsam içindeyse <xref:System.Xml.XPath.XPathNavigator> , ancak her iki bağlamda da eşlenmiş farklı bir ön eke sahipse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir, önek ve ad alanı URI 'si <xref:System.Xml.XmlReader> nesneden alınır.  
  
- Aynı ad alanı öneki hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de nesnenin bağlamı içinde kapsam içindeyse <xref:System.Xml.XPath.XPathNavigator> , ancak her iki bağlamda de kendisine eşlenmiş farklı bir ad alanı URI 'si varsa, yeni eklenen düğüme, bu öneki nesnesinden alınan ad alanı URI 'si ile yeniden bildiren yeni bir ad alanı bildirimi eklenir <xref:System.Xml.XmlReader> .  
  
- Hem <xref:System.Xml.XmlReader> nesnenin bağlamında hem de nesnenin bağlamı aynı olan önek ve ad alanı URI 'si <xref:System.Xml.XPath.XPathNavigator> aynıysa, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenmez.  
  
> [!NOTE]
> Yukarıdaki açıklama, bir ön ek olarak boş ad alanı bildirimleri için de geçerlidir `string` (örneğin, varsayılan ad alanı bildirimi).  
  
 Olası `xml:lang` Çakışmalar şunlardır.  
  
- Nesnenin `xml:lang` bağlamı içinde kapsam içinde olmayan bir öznitelik varsa <xref:System.Xml.XmlReader> , ancak nesne <xref:System.Xml.XPath.XPathNavigator> bağlamında, `xml:lang` değeri nesnesinden alınmış olan bir öznitelik <xref:System.Xml.XmlReader> yeni eklenen düğüme eklenir.  
  
- `xml:lang`Hem nesnenin bağlamı hem de nesnenin bağlamı içinde kapsam içinde bir öznitelik varsa <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> , ancak her biri farklı bir değere sahipse, `xml:lang` değeri nesnesinden alınmış olan bir öznitelik <xref:System.Xml.XmlReader> yeni eklenen düğüme eklenir.  
  
- `xml:lang`Hem nesnenin bağlamı hem de nesnenin bağlamı içinde kapsam içinde bir öznitelik varsa <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> , ancak her biri aynı değere sahip ise, yeni `xml:lang` eklenen düğüme yeni bir öznitelik eklenmez.  
  
- `xml:lang`Nesnenin bağlamı içinde kapsam içinde bir öznitelik varsa <xref:System.Xml.XPath.XPathNavigator> ancak <xref:System.Xml.XmlReader> nesnenin bağlamında yok, `xml:lang` yeni eklenen düğüme hiçbir öznitelik eklenmez.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>XmlWriter ile düğüm ekleme  
 "Düğüm ve değer ekleme" bölümünde açıklanan eşdüzey, alt ve öznitelik düğümlerini eklemek için kullanılan yöntemler aşırı yüklenmiştir. <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>Sınıfının, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> , <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> ve yöntemleri, <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlWriter> düğümleri eklemek için kullanılan bir nesne döndürüyor.  
  
### <a name="unsupported-xmlwriter-methods"></a>Desteklenmeyen XmlWriter yöntemleri  
 Sınıf kullanarak bir XML belgesine bilgi yazmak için kullanılan yöntemlerin hepsi, <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator> XPath veri modeli ve belge nesne MODELI (DOM) arasındaki fark nedeniyle sınıfı tarafından desteklenir.  
  
 Aşağıdaki tablo, <xref:System.Xml.XmlWriter> sınıfı tarafından desteklenmeyen sınıf yöntemlerini açıklar <xref:System.Xml.XPath.XPathNavigator> .  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Bir <xref:System.NotSupportedException> özel durum oluşturur.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Kök düzeyinde yok sayılır ve <xref:System.NotSupportedException> XML belgesinde başka bir düzeyde çağrılırsa bir özel durum oluşturur.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<xref:System.Xml.XmlWriter.WriteString%2A>Eşdeğer karakter veya karakterler için yönteme çağrı olarak kabul edilir.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<xref:System.Xml.XmlWriter.WriteString%2A>Eşdeğer karakter veya karakterler için yönteme çağrı olarak kabul edilir.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<xref:System.Xml.XmlWriter.WriteString%2A>Eşdeğer karakter veya karakterler için yönteme çağrı olarak kabul edilir.|  
  
 Sınıfı hakkında daha fazla bilgi için <xref:System.Xml.XmlWriter> bkz <xref:System.Xml.XmlWriter> . sınıf başvurusu belgeleri.  
  
### <a name="multiple-xmlwriter-objects"></a>Birden çok XmlWriter nesnesi  
 <xref:System.Xml.XPath.XPathNavigator>Bir veya daha fazla açık nesne içeren BIR XML belgesinin farklı bölümlerine işaret eden birden çok nesne olması mümkündür <xref:System.Xml.XmlWriter> . Birden çok <xref:System.Xml.XmlWriter> nesneye izin verilir ve tek iş parçacıklı senaryolarda desteklenir.  
  
 Birden çok nesne kullanırken göz önünde bulundurmanız gereken önemli notlar aşağıda verilmiştir <xref:System.Xml.XmlWriter> .  
  
- Nesneleri tarafından yazılan XML parçaları, <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlWriter.Close%2A> her bir nesnenin YÖNTEMI çağrıldığında XML belgesine eklenir <xref:System.Xml.XmlWriter> . Bu noktaya kadar, <xref:System.Xml.XmlWriter> nesne bağlantısı kesik bir parça yazıyor. XML belgesinde bir işlem gerçekleştirilirse, kullanılmadan önce bir nesne tarafından yazılan tüm parçalar <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlWriter.Close%2A> etkilenmez.  
  
- <xref:System.Xml.XmlWriter>Belirli BIR XML alt ağacı üzerinde açık bir nesne varsa ve bu alt ağaç silinirse, <xref:System.Xml.XmlWriter> nesne hala alt ağaca eklenebilir. Alt ağaç yalnızca silinmiş bir parça haline gelir.  
  
- <xref:System.Xml.XmlWriter>XML belgesinde aynı noktada birden çok nesne açılırsa, XML belgesine, <xref:System.Xml.XmlWriter> nesneleri açıldığı sırada değil, bunların kapandıkları sırada eklenir.  
  
 Aşağıdaki örnek bir nesnesi oluşturur <xref:System.Xml.XmlDocument> , bir nesnesi oluşturur <xref:System.Xml.XPath.XPathNavigator> ve sonra, <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> dosyadaki ilk kitabın yapısını oluşturmak için yöntemi tarafından döndürülen nesneyi kullanır `books.xml` . Örnek daha sonra dosyayı dosya olarak kaydeder `book.xml` .  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a>XML belgesi kaydetme  
 <xref:System.Xml.XmlDocument>Bu konuda açıklanan yöntemlerin sonucu olarak bir nesne üzerinde yapılan değişikliklerin kaydedilmesi, sınıfının yöntemleri kullanılarak gerçekleştirilir <xref:System.Xml.XmlDocument> . Bir nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için <xref:System.Xml.XmlDocument> bkz. [belgeyi kaydetme ve yazma](saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verilerini Değiştirme](modify-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Kaldırma](remove-xml-data-using-xpathnavigator.md)
