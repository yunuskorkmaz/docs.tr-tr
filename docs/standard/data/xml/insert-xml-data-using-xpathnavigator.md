---
title: XPathNavigator Kullanarak XML Verileri Ekleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 68c003467d837fe79d5e275968e47fa5dc3490cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710732"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verileri Ekleme
<xref:System.Xml.XPath.XPathNavigator> Sınıfı, bir XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için kullanılan bir yöntemler kümesi sağlar. Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır. `true`  
  
 <xref:System.Xml.XPath.XPathNavigator>bir XML belgesini düzenleyebilen nesneler, <xref:System.Xml.XmlDocument.CreateNavigator%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemiyle oluşturulur. <xref:System.Xml.XPath.XPathNavigator>sınıfı tarafından oluşturulan nesneler salt okunurdur ve bir <xref:System.Xml.XPath.XPathDocument> nesne tarafından oluşturulan <xref:System.NotSupportedException> <xref:System.Xml.XPath.XPathNavigator> nesnenin Editing yöntemlerini kullanma girişimleri bir ile sonuçlanır. <xref:System.Xml.XPath.XPathDocument>  
  
 Düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneler oluşturma hakkında daha fazla bilgi için bkz. [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Düğüm ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı, bir XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için yöntemler sağlar. Bu yöntemler, bir <xref:System.Xml.XPath.XPathNavigator> nesnenin geçerli konumuyla ilişkili olarak farklı konumlara düğüm ve öznitelik eklemenize olanak sağlar ve aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="inserting-sibling-nodes"></a>Eşdüzey düğümler ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı eşdüzey düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Bu yöntemler, bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlanan düğümden önce ve sonra eşdüzey düğümler ekler.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> Ve yöntemleri aşırı yüklenmiş ve parametre olarak eklenecek `string`eşdüzey <xref:System.Xml.XmlReader> düğümü içeren bir <xref:System.Xml.XPath.XPathNavigator> , nesne veya nesne kabul eder. Her iki yöntem de eşdüzey <xref:System.Xml.XmlWriter> düğümleri eklemek için kullanılan bir nesne döndürür.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri, bir <xref:System.Xml.XPath.XPathNavigator> nesneden önce ve sonra bir nesne, ad alanı ön eki, yerel adı, ad alanı URI 'si ve parametre olarak belirtilen değer kullanılarak konumlandırılmış olan bir eşdüzey düğüm ekler.  
  
 Aşağıdaki `pages` örnekte, `price` `book` `contosoBooks.xml` dosyasındaki ilk öğenin alt öğesinden önce yeni bir öğe eklenir.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.Xml.XPath.XPathNavigator> sınıf başvurusu belgeleri.  
  
### <a name="inserting-child-nodes"></a>Alt düğümler ekleniyor  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı alt düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Bu yöntemler, alt düğümleri sonuna ekler ve sonuna eklenmiş olan düğüm <xref:System.Xml.XPath.XPathNavigator> alt düğümleri listesinin başlangıcına eklenir.  
  
 " <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> Eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi, ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemleri parametre olarak eklenecek alt düğümü içeren `string`bir <xref:System.Xml.XmlReader> , nesne veya <xref:System.Xml.XPath.XPathNavigator> nesne kabul eder. Her iki yöntem de alt <xref:System.Xml.XmlWriter> düğüm eklemek için kullanılan bir nesne döndürür.  
  
 Ayrıca, "eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri, ' nin sonuna tek bir alt düğüm ekler ve bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda ad alanı ön eki, yerel ad, ad alanı URI 'si ve parametre olarak belirtilen değer kullanılarak konumlandırılmış.  
  
 Aşağıdaki örnekte, `pages` `book` `contosoBooks.xml` dosyasındaki ilk öğenin alt öğeleri listesine yeni bir alt öğe eklenir.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> Ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.Xml.XPath.XPathNavigator> sınıf başvurusu belgeleri.  
  
### <a name="inserting-attribute-nodes"></a>Öznitelik düğümleri ekleniyor  
 Sınıfı <xref:System.Xml.XPath.XPathNavigator> , öznitelik düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Bu yöntemler, bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış olan öğe düğümüne öznitelik düğümleri ekler. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Yöntemi, bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda ad alanı ön eki, yerel ad, ad alanı URI 'si ve parametre olarak belirtilen değer kullanılarak konumlandırılmış olan öğe düğümünde bir öznitelik düğümü oluşturur. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Yöntemi öznitelik düğümleri eklemek <xref:System.Xml.XmlWriter> için kullanılan bir nesne döndürür.  
  
 Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yönteminden döndürülen `book` `contosoBooks.xml` <xref:System.Xml.XmlWriter> nesneyi `discount` kullanarak `currency` dosyadaki ilk öğenin `price` alt öğesinde yeni ve öznitelikleri oluşturulur.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Ve yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.Xml.XPath.XPathNavigator> sınıf başvurusu belgeleri. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
## <a name="copying-nodes"></a>Düğümler kopyalanıyor  
 Belirli durumlarda, bir XML belgesini başka bir XML belgesinden içerik ile doldurmak isteyebilirsiniz. Hem sınıf <xref:System.Xml.XPath.XPathNavigator> hem de <xref:System.Xml.XmlWriter> sınıf, düğümleri varolan <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> bir nesne veya <xref:System.Xml.XPath.XPathNavigator> nesneden bir nesneye kopyalayabilir.  
  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfının <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> yöntemlerinin hepsi bir <xref:System.Xml.XPath.XPathNavigator> nesne veya <xref:System.Xml.XmlReader> nesneyi parametre olarak kabul edebilecek aşırı yüklemeleridir.  
  
 <xref:System.Xml.XmlWriter> Sınıfının <xref:System.Xml.XmlWriter.WriteNode%2A> yönteminde <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, veya <xref:System.Xml.XPath.XPathNavigator> nesnesini kabul edebilecek aşırı yüklemeler vardır.  
  
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
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> , bir düğümün değerlerini <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> bir <xref:System.Xml.XmlDocument> nesnesine eklemek için ve yöntemlerini sağlar.  
  
### <a name="inserting-untyped-values"></a>Türsüz değerler ekleme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi, bir parametre olarak geçirilen `string` türsüz değeri <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olan düğümün değeri olarak ekler. Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa düğüm türüne göre yeni değerin geçerli olduğunu doğrulamadan eklenir.  
  
 Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi `price` `contosoBooks.xml` dosyadaki tüm öğeleri güncelleştirmek için kullanılır.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Yazılan değerler ekleniyor  
 Bir düğümün türü bir W3C XML şeması basit türü olduğunda, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi tarafından yerleştirilen yeni değer, değer ayarlanmadan önce basit türdeki modellerle denetlenir. Yeni değer, düğüm türüne göre geçerli değilse (örneğin, türü olan bir öğe `-1` üzerinde değerini ayarlamak `xs:positiveInteger`), bir özel durumla sonuçlanır.  
  
 Aşağıdaki `price` örnek, `book` `contosoBooks.xml` dosyasındaki ilk öğe öğesinin değerini bir <xref:System.DateTime> değere değiştirmeye çalışır. `price` Öğesinin XML şeması türü `xs:decimal` `contosoBooks.xsd` dosyalarda olarak tanımlandığından, bu durum bir özel durumla sonuçlanır.  
  
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
  
 Örnek de bir giriş `contosoBooks.xsd` olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 Sınıfının ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> bir <xref:System.Xml.XPath.XPathNavigator> NESNENIN Şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir. <xref:System.Xml.XPath.XPathNavigator>  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliği, belirtilen XML `string`'nin ayrıştırılmış içeriğiyle bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılmış olan alt düğümlerin XML işaretlemesini değiştirir. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği de bir <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda bulunduğu alt düğümlerin XML işaretlemesini ve geçerli düğümün kendisini değiştirir.  
  
 Bu konuda açıklanan yöntemlere ek olarak, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri bir XML belgesine düğüm ve değer eklemek için kullanılabilir. Ve özelliklerini kullanarak düğüm ve değer ekleme hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak XML verilerini değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konusu. <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespace ve XML: lang çakışmaları  
 Ad alanı ve `xml:lang` bildirimlerin kapsamı ile ilgili <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>bazı çakışmalar, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlReader> nesneleri parametre olarak alan sınıfın,, ve yöntemlerini kullanarak XML verileri eklenirken meydana gelebilir.  
  
 Olası ad alanı çakışmaları aşağıda verilmiştir.  
  
- <xref:System.Xml.XmlReader> Nesne bağlamında kapsam içinde bir ad alanı varsa, ad alanı URI eşlemesinin öneki <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamında değilse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir.  
  
- Aynı ad alanı URI 'SI hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı içinde kapsam içindeyse, ancak her iki bağlamda da eşlenmiş farklı bir ön eke sahipse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir, önek ve ad alanı URI 'si <xref:System.Xml.XmlReader> nesneden alınır.  
  
- Aynı ad alanı öneki hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı içinde kapsam içindeyse, ancak her iki bağlamda de kendisine eşlenmiş farklı bir ad alanı URI 'si varsa, yeni eklenen düğüme, bu öneki <xref:System.Xml.XmlReader> nesnesinden alınan ad alanı URI 'si ile yeniden bildiren yeni bir ad alanı bildirimi eklenir.  
  
- Hem <xref:System.Xml.XmlReader> nesnenin bağlamında hem de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı aynı olan önek ve ad alanı URI 'si aynıysa, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenmez.  
  
> [!NOTE]
> Yukarıdaki açıklama, bir ön ek olarak boş `string` ad alanı bildirimleri için de geçerlidir (örneğin, varsayılan ad alanı bildirimi).  
  
 Olası `xml:lang` çakışmalar şunlardır.  
  
- Nesnenin bağlamı içinde kapsam `xml:lang` <xref:System.Xml.XmlReader> içinde olmayan <xref:System.Xml.XPath.XPathNavigator> bir öznitelik varsa, ancak nesne bağlamında, değeri `xml:lang` <xref:System.Xml.XmlReader> nesnesinden alınmış olan bir öznitelik yeni eklenen düğüme eklenir.  
  
- `xml:lang` Hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı içinde kapsam içinde bir öznitelik varsa, ancak her biri farklı bir değere sahipse, değeri `xml:lang` <xref:System.Xml.XmlReader> nesnesinden alınmış olan bir öznitelik yeni eklenen düğüme eklenir.  
  
- Hem `xml:lang` <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı içinde kapsam içinde bir öznitelik varsa, ancak her biri aynı değere sahip ise, yeni eklenen düğüme yeni `xml:lang` bir öznitelik eklenmez.  
  
- Nesnenin bağlamı içinde kapsam `xml:lang` içinde bir öznitelik varsa ancak <xref:System.Xml.XmlReader> nesnenin bağlamında yok, yeni eklenen düğüme hiçbir `xml:lang` öznitelik eklenmez. <xref:System.Xml.XPath.XPathNavigator>  
  
## <a name="inserting-nodes-with-xmlwriter"></a>XmlWriter ile düğüm ekleme  
 "Düğüm ve değer ekleme" bölümünde açıklanan eşdüzey, alt ve öznitelik düğümlerini eklemek için kullanılan yöntemler aşırı yüklenmiştir. <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Sınıfının,, ve yöntemleri, düğümleri eklemek için kullanılan bir <xref:System.Xml.XmlWriter> nesne döndürüyor. <xref:System.Xml.XPath.XPathNavigator>  
  
### <a name="unsupported-xmlwriter-methods"></a>Desteklenmeyen XmlWriter yöntemleri  
 <xref:System.Xml.XmlWriter> Sınıf kullanarak bir XML belgesine bilgi yazmak için kullanılan yöntemlerin hepsi, XPath veri modeli ve belge nesne MODELI (DOM) <xref:System.Xml.XPath.XPathNavigator> arasındaki fark nedeniyle sınıfı tarafından desteklenir.  
  
 Aşağıdaki tablo, <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından <xref:System.Xml.XmlWriter> desteklenmeyen sınıf yöntemlerini açıklar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Bir <xref:System.NotSupportedException> özel durum oluşturur.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Kök düzeyinde yok sayılır ve XML belgesinde başka <xref:System.NotSupportedException> bir düzeyde çağrılırsa bir özel durum oluşturur.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Eşdeğer karakter veya karakterler için <xref:System.Xml.XmlWriter.WriteString%2A> yönteme çağrı olarak kabul edilir.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Eşdeğer karakter veya karakterler için <xref:System.Xml.XmlWriter.WriteString%2A> yönteme çağrı olarak kabul edilir.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Eşdeğer karakter veya karakterler için <xref:System.Xml.XmlWriter.WriteString%2A> yönteme çağrı olarak kabul edilir.|  
  
 <xref:System.Xml.XmlWriter> Sınıfı hakkında daha fazla bilgi için bkz. <xref:System.Xml.XmlWriter> sınıf başvurusu belgeleri.  
  
### <a name="multiple-xmlwriter-objects"></a>Birden çok XmlWriter nesnesi  
 Bir veya daha fazla açık <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlWriter> nesne içeren bir XML belgesinin farklı bölümlerine işaret eden birden çok nesne olması mümkündür. Birden <xref:System.Xml.XmlWriter> çok nesneye izin verilir ve tek iş parçacıklı senaryolarda desteklenir.  
  
 Birden çok <xref:System.Xml.XmlWriter> nesne kullanırken göz önünde bulundurmanız gereken önemli notlar aşağıda verilmiştir.  
  
- Nesneleri tarafından <xref:System.Xml.XmlWriter> yazılan XML parçaları, her <xref:System.Xml.XmlWriter.Close%2A> <xref:System.Xml.XmlWriter> bir nesnenin yöntemi çağrıldığında XML belgesine eklenir. Bu noktaya kadar, <xref:System.Xml.XmlWriter> nesne bağlantısı kesik bir parça yazıyor. XML belgesinde bir işlem gerçekleştirilirse, kullanılmadan önce <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlWriter.Close%2A> bir nesne tarafından yazılan tüm parçalar etkilenmez.  
  
- Belirli bir XML alt ağacı <xref:System.Xml.XmlWriter> üzerinde açık bir nesne varsa ve bu alt ağaç silinirse, <xref:System.Xml.XmlWriter> nesne hala alt ağaca eklenebilir. Alt ağaç yalnızca silinmiş bir parça haline gelir.  
  
- XML belgesinde <xref:System.Xml.XmlWriter> aynı noktada birden çok nesne AÇıLıRSA, XML belgesine, <xref:System.Xml.XmlWriter> nesneleri açıldığı sırada değil, bunların kapandıkları sırada eklenir.  
  
 Aşağıdaki örnek bir <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathNavigator> nesnesi oluşturur, bir nesnesi oluşturur ve sonra, <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> `books.xml` dosyadaki ilk kitabın yapısını oluşturmak için yöntemi tarafından döndürülen nesneyi kullanır. Örnek daha sonra `book.xml` dosyayı dosya olarak kaydeder.  
  
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
 Bu konuda açıklanan yöntemlerin sonucu <xref:System.Xml.XmlDocument> olarak bir nesne üzerinde yapılan değişikliklerin kaydedilmesi, <xref:System.Xml.XmlDocument> sınıfının yöntemleri kullanılarak gerçekleştirilir. Bir <xref:System.Xml.XmlDocument> nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bkz. [belgeyi kaydetme ve yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verilerini Değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Kaldırma](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
