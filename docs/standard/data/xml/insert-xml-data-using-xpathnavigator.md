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
<xref:System.Xml.XPath.XPathNavigator> sınıfı, bir XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için kullanılan bir yöntemler kümesi sağlar. Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği `true`olmalıdır.  
  
 bir XML belgesini düzenleyebilen <xref:System.Xml.XPath.XPathNavigator> nesneleri, <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemiyle oluşturulur. <xref:System.Xml.XPath.XPathDocument> sınıfı tarafından oluşturulan <xref:System.Xml.XPath.XPathNavigator> nesneleri salt okunurdur ve bir <xref:System.Xml.XPath.XPathDocument> nesnesi tarafından oluşturulan <xref:System.Xml.XPath.XPathNavigator> nesnesinin Editing yöntemlerini kullanma girişimleri bir <xref:System.NotSupportedException>sonuçlanır.  
  
 Düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneleri oluşturma hakkında daha fazla bilgi için bkz. [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Düğüm ekleme  
 <xref:System.Xml.XPath.XPathNavigator> sınıfı, bir XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için yöntemler sağlar. Bu yöntemler, bir <xref:System.Xml.XPath.XPathNavigator> nesnesinin geçerli konumuyla ilişkili olarak farklı konumlara düğüm ve öznitelik eklemenize olanak tanır ve aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="inserting-sibling-nodes"></a>Eşdüzey düğümler ekleme  
 <xref:System.Xml.XPath.XPathNavigator> sınıfı eşdüzey düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Bu yöntemler, düğüm bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde konumlandırılmadan önce ve sonra eşdüzey düğümler ekler.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> yöntemleri aşırı yüklendi ve parametre olarak eklemek için eşdüzey düğümü içeren bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> nesnesi kabul eder. Her iki yöntem de eşdüzey düğümleri eklemek için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi döndürür.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri, düğüm bir <xref:System.Xml.XPath.XPathNavigator> nesnesi şu anda ad alanı ön eki, yerel ad, ad alanı URI 'SI ve parametre olarak belirtilen değer kullanılarak konumlandırılmış bir bir eşdüzey düğüm ekler.  
  
 Aşağıdaki örnekte, `contosoBooks.xml` dosyasındaki ilk `book` öğesinin `price` alt öğesinden önce yeni bir `pages` öğesi eklenir.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.  
  
### <a name="inserting-child-nodes"></a>Alt düğümler ekleniyor  
 <xref:System.Xml.XPath.XPathNavigator> sınıfı alt düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Bu yöntemler, alt düğümleri sonuna ekler ve sonuna eklenmiş bir <xref:System.Xml.XPath.XPathNavigator> nesnesi olan düğümün alt düğümlerinin listesinin başlangıcına eklenir.  
  
 "Eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemleri, parametre olarak eklemek için alt düğümü içeren bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> nesnesi kabul eder. Her iki yöntem de alt düğümleri eklemek için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi döndürür.  
  
 Ayrıca, "eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri, bir <xref:System.Xml.XPath.XPathNavigator> nesnesi şu anda ad alanı ön eki, yerel ad, ad alanı URI 'SI ve parametre olarak belirtilen değer kullanılarak konumlandırılmış olan bir nesnesinin sonuna tek bir alt düğüm ekler.  
  
 Aşağıdaki örnekte, yeni bir `pages` alt öğesi, `contosoBooks.xml` dosyasındaki ilk `book` öğesinin alt öğelerinin listesine eklenir.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.  
  
### <a name="inserting-attribute-nodes"></a>Öznitelik düğümleri ekleniyor  
 <xref:System.Xml.XPath.XPathNavigator> sınıfı, öznitelik düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Bu yöntemler, nesne düğümüne öznitelik düğümleri ekler bir <xref:System.Xml.XPath.XPathNavigator> nesnesi şu anda üzerinde konumlanır. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> yöntemi, öğe düğümünde bir öznitelik düğümü oluşturur <xref:System.Xml.XPath.XPathNavigator> nesnesi şu anda ad alanı ön eki, yerel adı, ad alanı URI 'SI ve parametre olarak belirtilen değer kullanılarak konumlandırılmış. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemi öznitelik düğümleri eklemek için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi döndürür.  
  
 Aşağıdaki örnekte, `contosoBooks.xml` yönteminden döndürülen <xref:System.Xml.XmlWriter> nesnesi kullanılarak <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> dosyasındaki ilk `book` öğesinin `price` alt öğesinde yeni `discount` ve `currency` öznitelikleri oluşturulur.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> ve <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> sınıf başvurusu belgelerine bakın.  
  
## <a name="copying-nodes"></a>Düğümler kopyalanıyor  
 Belirli durumlarda, bir XML belgesini başka bir XML belgesinden içerik ile doldurmak isteyebilirsiniz. <xref:System.Xml.XPath.XPathNavigator> sınıfı ve <xref:System.Xml.XmlWriter> sınıfı, düğümleri varolan bir <xref:System.Xml.XmlReader> nesnesinden veya <xref:System.Xml.XPath.XPathNavigator> nesnesinden bir <xref:System.Xml.XmlDocument> nesnesine kopyalayabilir.  
  
 <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> yöntemlerinin hepsi, bir <xref:System.Xml.XPath.XPathNavigator> nesnesini veya bir <xref:System.Xml.XmlReader> nesnesini parametre olarak kabul edebilecek aşırı yüklemeleri vardır.  
  
 <xref:System.Xml.XmlWriter> sınıfının <xref:System.Xml.XmlWriter.WriteNode%2A> yöntemi <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>veya <xref:System.Xml.XPath.XPathNavigator> nesnesini kabul edebilecek aşırı yüklemelerden oluşur.  
  
 Aşağıdaki örnek, tüm `book` öğelerini bir belgeden diğerine kopyalar.  
  
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
 <xref:System.Xml.XPath.XPathNavigator> sınıfı, bir düğümün değerlerini <xref:System.Xml.XmlDocument> nesnesine eklemek için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri sağlar.  
  
### <a name="inserting-untyped-values"></a>Türsüz değerler ekleme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi, bir parametre olarak geçirilen türsüz `string` değerini, <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandığını düğümün değeri olarak ekler. Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa düğüm türüne göre yeni değerin geçerli olduğunu doğrulamadan eklenir.  
  
 Aşağıdaki örnekte, `contosoBooks.xml` dosyasındaki tüm `price` öğelerini güncelleştirmek için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi kullanılır.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Yazılan değerler ekleniyor  
 Bir düğümün türü bir W3C XML şeması basit türü olduğunda, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi tarafından yerleştirilen yeni değer, değer ayarlanmadan önce basit türdeki modellerle denetlenir. Yeni değer düğüm türüne göre geçerli değilse (örneğin, türü `xs:positiveInteger`olan bir öğe üzerinde `-1` değerini ayarlamak), bir özel durumla sonuçlanır.  
  
 Aşağıdaki örnek `contosoBooks.xml` dosyasındaki ilk `book` öğesinin `price` öğesinin değerini bir <xref:System.DateTime> değerine değiştirmeyi dener. `price` öğesinin XML şeması türü `contosoBooks.xsd` dosyalarında `xs:decimal` olarak tanımlandığından, bu durum bir özel durumla sonuçlanır.  
  
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
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek ayrıca `contosoBooks.xsd` giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> özelliği, alt düğümlerin XML işaretlemesini değiştirir <xref:System.Xml.XPath.XPathNavigator> bir nesne şu anda belirtilen XML `string`ayrıştırılmış içeriğiyle konumlandırılmış. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği, alt düğümlerin XML işaretlemesini de değiştirir ve o durumda geçerli düğümün kendisi de şu anda konumlandırılmış olan <xref:System.Xml.XPath.XPathNavigator> bir nesne.  
  
 Bu konuda açıklanan yöntemlere ek olarak, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri bir XML belgesine düğüm ve değer eklemek için kullanılabilir. <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini kullanarak düğüm ve değer ekleme hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak XML verilerini değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konusu.  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespace ve XML: lang çakışmaları  
 Ad alanı ve `xml:lang` bildirimlerinin kapsamı ile ilgili bazı çakışmalar, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> nesneleri parametre olarak alan <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XmlReader> yöntemleri kullanılarak XML verileri eklenirken meydana gelebilir.  
  
 Olası ad alanı çakışmaları aşağıda verilmiştir.  
  
- <xref:System.Xml.XmlReader> nesnenin bağlamı içinde kapsam içinde bir ad alanı varsa, ad alanı URI eşlemesinin öneki <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamında değilse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir.  
  
- Aynı ad alanı URI 'SI hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içindeyse, ancak her iki bağlamda da eşlenmiş farklı bir ön eke sahipse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir ve bu, <xref:System.Xml.XmlReader> nesnesinden alınan önek ve ad alanı URI 'SI olur.  
  
- Aynı ad alanı öneki hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içindeyse, ancak her iki bağlamda de kendisine eşlenmiş farklı bir ad alanı URI 'SI varsa, bu öneki <xref:System.Xml.XmlReader> nesnesinden alınan ad alanı URI 'SI ile yeniden bildiren yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir.  
  
- Hem <xref:System.Xml.XmlReader> nesnenin bağlamında hem de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı aynı olan ad alanı URI 'SI aynıysa, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenmez.  
  
> [!NOTE]
> Yukarıdaki açıklama aynı zamanda bir ön ek olarak boş `string` olan ad alanı bildirimleri için de geçerlidir (örneğin, varsayılan ad alanı bildirimi).  
  
 Olası `xml:lang` çakışmaları aşağıda verilmiştir.  
  
- <xref:System.Xml.XmlReader> nesnenin bağlamı içinde kapsam içinde `xml:lang` bir öznitelik varsa, ancak <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamında, değeri <xref:System.Xml.XmlReader> nesnesinden alınmış bir `xml:lang` özniteliği yeni eklenen düğüme eklenir.  
  
- Hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içinde bir `xml:lang` özniteliği varsa, ancak her biri farklı bir değere sahipse, <xref:System.Xml.XmlReader> nesnesinden değeri alınmış bir `xml:lang` özniteliği yeni eklenen düğüme eklenir.  
  
- Hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içinde bir `xml:lang` özniteliği varsa, ancak her biri aynı değere sahip olan yeni eklenen düğüme yeni bir `xml:lang` özniteliği eklenmez.  
  
- <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içinde bir `xml:lang` özniteliği varsa, ancak <xref:System.Xml.XmlReader> nesnenin bağlamında yok, yeni eklenen düğüme hiçbir `xml:lang` özniteliği eklenmez.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>XmlWriter ile düğüm ekleme  
 "Düğüm ve değer ekleme" bölümünde açıklanan eşdüzey, alt ve öznitelik düğümlerini eklemek için kullanılan yöntemler aşırı yüklenmiştir. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> sınıfının <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> ve <xref:System.Xml.XPath.XPathNavigator> yöntemleri, düğümleri eklemek için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi döndürüyor.  
  
### <a name="unsupported-xmlwriter-methods"></a>Desteklenmeyen XmlWriter yöntemleri  
 <xref:System.Xml.XmlWriter> sınıfını kullanarak bir XML belgesine bilgi yazmak için kullanılan yöntemlerin hepsi, XPath veri modeli ve Belge Nesne Modeli (DOM) arasındaki fark nedeniyle <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından desteklenir.  
  
 Aşağıdaki tabloda, <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından desteklenmeyen <xref:System.Xml.XmlWriter> sınıfı yöntemleri açıklanmaktadır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<xref:System.NotSupportedException> özel durumu oluşturur.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Kök düzeyinde yok sayılır ve XML belgesinde başka bir düzeyde çağrılırsa bir <xref:System.NotSupportedException> özel durumu oluşturur.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Denk karakter veya karakterler için <xref:System.Xml.XmlWriter.WriteString%2A> yöntemine bir çağrı olarak değerlendirilir.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Denk karakter veya karakterler için <xref:System.Xml.XmlWriter.WriteString%2A> yöntemine bir çağrı olarak değerlendirilir.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Denk karakter veya karakterler için <xref:System.Xml.XmlWriter.WriteString%2A> yöntemine bir çağrı olarak değerlendirilir.|  
  
 <xref:System.Xml.XmlWriter> sınıfı hakkında daha fazla bilgi için bkz. <xref:System.Xml.XmlWriter> sınıf başvurusu belgeleri.  
  
### <a name="multiple-xmlwriter-objects"></a>Birden çok XmlWriter nesnesi  
 Bir veya daha fazla açık <xref:System.Xml.XmlWriter> nesnesi olan bir XML belgesinin farklı bölümlerine işaret eden birden çok <xref:System.Xml.XPath.XPathNavigator> nesnesi olması mümkündür. Çoklu <xref:System.Xml.XmlWriter> nesneleri tek iş parçacıklı senaryolarda kullanılabilir ve desteklenir.  
  
 Birden çok <xref:System.Xml.XmlWriter> nesnesi kullanırken göz önünde bulundurmanız gereken önemli notlar aşağıda verilmiştir.  
  
- <xref:System.Xml.XmlWriter> nesneleri tarafından yazılan XML parçaları, her bir <xref:System.Xml.XmlWriter> nesnesinin <xref:System.Xml.XmlWriter.Close%2A> yöntemi çağrıldığında XML belgesine eklenir. Bu noktaya kadar <xref:System.Xml.XmlWriter> nesnesi bağlantısı kesik bir parça yazıyor. XML belgesinde bir işlem gerçekleştirilirse, <xref:System.Xml.XmlWriter.Close%2A> çağrılmadan önce bir <xref:System.Xml.XmlWriter> nesnesi tarafından yazılan parçalar etkilenmez.  
  
- Belirli bir XML alt ağacında açık bir <xref:System.Xml.XmlWriter> nesnesi varsa ve bu alt ağaç silinirse, <xref:System.Xml.XmlWriter> nesnesi yine de alt ağaca eklenebilir. Alt ağaç yalnızca silinmiş bir parça haline gelir.  
  
- Birden çok <xref:System.Xml.XmlWriter> nesnesi, XML belgesinde aynı noktada açılırsa, XML belgesine, açıldıkları sırada değil, <xref:System.Xml.XmlWriter> nesnelerinin kapatıldığı sırada eklenirler.  
  
 Aşağıdaki örnek bir <xref:System.Xml.XmlDocument> nesnesi oluşturur, bir <xref:System.Xml.XPath.XPathNavigator> nesnesi oluşturur ve sonra `books.xml` dosyasındaki ilk kitabın yapısını oluşturmak için <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemi tarafından döndürülen <xref:System.Xml.XmlWriter> nesnesini kullanır. Örnek daha sonra bu dosyayı `book.xml` dosyası olarak kaydeder.  
  
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
 Bu konuda açıklanan yöntemlerin sonucu olarak, bir <xref:System.Xml.XmlDocument> nesnesine yapılan değişiklikler kaydetme, <xref:System.Xml.XmlDocument> sınıfının yöntemleri kullanılarak gerçekleştirilir. <xref:System.Xml.XmlDocument> nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bkz. [bir belge kaydetme ve yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verilerini Değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Kaldırma](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
