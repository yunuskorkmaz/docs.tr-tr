---
title: XPathNavigator kullanarak XML verilerini Ekle
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b9eedfab68dc6aeacf9ed51ffc7205b73c062ca
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44338720"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>XPathNavigator kullanarak XML verilerini Ekle
<xref:System.Xml.XPath.XPathNavigator> Sınıf bir XML belgesinde eşdüzey, alt öğe ve öznitelik düğümleri eklemek için kullanılan yöntemler kümesi sağlar. Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesne olmalıdır düzenlenemez, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. <xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesnelerin <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunurdur ve tüm düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> nesnesi tarafından oluşturulan bir <xref:System.Xml.XPath.XPathDocument> nesne sonuçlanıyor bir <xref:System.NotSupportedException>.  
  
 Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML verileri okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Düğümler ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı eşdüzey, alt öğe ve öznitelik düğümleri bir XML belgesinde eklemek için yöntemler sağlar. Geçerli konumu ile ilgili farklı konumlarda düğümleri ve öznitelikler eklemek bu yöntemleri izin bir <xref:System.Xml.XPath.XPathNavigator> nesne ve aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="inserting-sibling-nodes"></a>Eşdüzey düğümler ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı eşdüzey düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Bu yöntemler eşdüzey düğümleri önceki ve sonraki düğümü Ekle bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> yöntemleri aşırı ve kabul bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklenecek eşdüzey düğüm içeren nesne. Her iki yöntem aynı zamanda sonuç bir <xref:System.Xml.XmlWriter> eşdüzey düğümleri eklemek için kullanılan nesne.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri eklemek tek Eşdüzey Düğüm önce ve sonra düğümü bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır ad alanı öneki, yerel ad, ad alanı URI ve parametre olarak belirtilen değeri kullanarak.  
  
 Aşağıdaki örnekte yeni bir `pages` önce eklenen öğe `price` ilk alt öğenin `book` öğesinde `contosoBooks.xml` dosya.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri bkz <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.  
  
### <a name="inserting-child-nodes"></a>Alt düğümler ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı alt düğümler eklemek için aşağıdaki yöntemleri sağlar.  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Bu yöntemler ekleme ve sonuna ve düğümünün alt düğümleri listesini başına alt düğümler başına bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.  
  
 "Eşdüzey düğümleri ekleme" bölümünde, yöntemler gibi <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemleri kabul bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklenecek alt düğüm içeren nesne. Her iki yöntem aynı zamanda sonuç bir <xref:System.Xml.XmlWriter> alt düğümler eklemek için kullanılan nesne.  
  
 Ayrıca, "Eşdüzey düğümleri ekleme" bölümündeki yöntemleri ister <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri sonuna ve düğümünün alt düğümleri listesini başına tek bir alt düğümü ekleme bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır kullanarak ad alanı öneki, yerel ad, ad alanı URI ve parametre olarak belirtilen değeri.  
  
 Aşağıdaki örnekte, yeni bir `pages` alt öğesi ilk alt öğelerini listesine eklenmiş `book` öğesinde `contosoBooks.xml` dosya.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri bkz <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.  
  
### <a name="inserting-attribute-nodes"></a>Öznitelik düğümleri ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı, öznitelik düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Bu yöntemleri öznitelik düğümleri üzerinde öğe düğümü Ekle bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Yöntemi öğesi düğümde bir öznitelik düğümü oluşturur bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır ad alanı öneki, yerel ad, ad alanı URI ve parametre olarak belirtilen değeri kullanarak. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Yöntemi döndürür bir <xref:System.Xml.XmlWriter> öznitelik düğümleri eklemek için kullanılan nesne.  
  
 Aşağıdaki örnekte, yeni `discount` ve `currency` öznitelikleri üzerinde oluşturulan `price` ilk alt öğenin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XmlWriter> döndürülen nesne <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntem.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> ve <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemleri bkz <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.  
  
## <a name="copying-nodes"></a>Düğümleri kopyalama  
 Bazı durumlarda içeriği başka bir XML belgesi bir XML belgesi doldurmak isteyebilirsiniz. Her iki <xref:System.Xml.XPath.XPathNavigator> sınıfı ve <xref:System.Xml.XmlWriter> sınıfı düğümlerine kopyalayabilir bir <xref:System.Xml.XmlDocument> mevcut bir nesne <xref:System.Xml.XmlReader> nesne veya <xref:System.Xml.XPath.XPathNavigator> nesne.  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> tümü, kabul eden aşırı yüklemeler sahip sınıf bir <xref:System.Xml.XPath.XPathNavigator> nesnesi veya bir <xref:System.Xml.XmlReader> bir parametre olarak nesne.  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A> Yöntemi <xref:System.Xml.XmlWriter> sınıfında, kabul eden aşırı yüklemeler bir <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, veya <xref:System.Xml.XPath.XPathNavigator> nesne.  
  
 Aşağıdaki örnekte tüm kopyalar `book` bir belgeden öğelerine.  
  
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
  
## <a name="inserting-values"></a>Değerleri ekleniyor  
 <xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değerleri için bir düğüm eklemek için yöntemleri bir <xref:System.Xml.XmlDocument> nesne.  
  
### <a name="inserting-untyped-values"></a>Yazılmamış değerler ekleme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler yazılmamış `string` düğümün değeri olarak bir parametre olarak geçirilen değer <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda. Değer, her türlü olmadan veya şema bilgileri kullanılabilir durumdaysa, yeni değer düğüm türüne göre geçerli olduğu doğrulanıyor olmadan eklenir.  
  
 Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> tümünü güncelleştirmek için kullanılan yöntemi `price` öğelerinde `contosoBooks.xml` dosya.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Yazılan değerleri ekleniyor  
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
  
## <a name="the-innerxml-and-outerxml-properties"></a>Sınıfının InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfını değiştirin XML işaretlemesini düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde belirli XML ayrıştırılmış içeriğiyle `string`. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde geçerli düğüm yanı sıra kendisini.  
  
 Bu konuda, açıklanan yöntemlerin yanı sıra <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikler XML belgesinde düğümleri ve değerler eklemek için kullanılabilir. Kullanma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> düğümleri ve değerler eklemek için özellikleri görmek [değiştirme XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespace ve XML: lang çakışmaları  
 Ad alanı kapsamına ilgili belirli çakışma ve `xml:lang` bildirimleri eklerken kullanarak XML verilerini oluşabilir <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> elesınıfı<xref:System.Xml.XmlReader>parametre olarak nesne.  
  
 Olası ad çakışmalarını aşağıda verilmiştir.  
  
-   Bir ad alanı kapsamındaki içinde ise <xref:System.Xml.XmlReader> nerede önek için ad alanı URI eşlemesi içinde değil, nesnenin bağlam <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, yeni bir ad alanı bildirimi yeni eklenen düğümüne eklenir.  
  
-   Kapsamdaki aynı ad URI ise, her ikisi içinde <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak her iki içerikte eşlenmiş farklı bir önek varsa, yeni bir ad alanı bildirimi, ön eki yeni eklenen düğümüne eklenir ve ad alanı URI alınan <xref:System.Xml.XmlReader> nesne.  
  
-   Kapsamdaki aynı ad alanı öneki ise öğesinde hem de <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak sahip farklı bir ad alanı URI eşlenmesi için her iki içerikte yeni bir ad alanı bildirimi yeni eklenen düğümüne eklenir, Bu ad alanı URI alınan önekiyle yeniden bildirir <xref:System.Xml.XmlReader> nesne.  
  
-   Varsa ön ek olarak, hem de ad alanı URI <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin içeriği aynı olduğundan, hiçbir yeni ad alanı bildirimi yeni eklenen düğümüne eklenir.  
  
> [!NOTE]
>  Yukarıdaki açıklamada ile boş ad alanı bildirimi için de geçerlidir. `string` bir önek (örneğin, varsayılan ad alanı bildirimi) olarak.  
  
 Aşağıdaki yapılabilen `xml:lang` çakışıyor.  
  
-   Varsa bir `xml:lang` kapsam içinde öznitelik <xref:System.Xml.XmlReader> nesnenin bağlam de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı bir `xml:lang` değeri alınan öznitelik <xref:System.Xml.XmlReader> nesne yeni eklenen düğümüne eklenir.  
  
-   Varsa bir `xml:lang` kapsamındaki her ikisi içinde öznitelik <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak her farklı bir değere sahip bir `xml:lang` değeri alınan öznitelik <xref:System.Xml.XmlReader> eklenir Yeni eklenen düğüm.  
  
-   Varsa bir `xml:lang` kapsamındaki her ikisi içinde öznitelik <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak her yeni aynı değere sahip `xml:lang` özniteliği, yeni eklenen düğümüne eklenir.  
  
-   Varsa bir `xml:lang` kapsam içinde öznitelik <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak hiçbiri varolan <xref:System.Xml.XmlReader> nesnenin bağlamı, Hayır `xml:lang` özniteliği, yeni eklenen düğümüne eklenir.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>XmlWriter ile düğüm ekleme  
 "Düğümleri ve değerler ekleme" bölümünde açıklanan eşdüzey, alt öğe ve öznitelik düğümleri eklemek için kullanılan yöntemler aşırı yüklenmesi sebebiyledir. <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> Ve <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfı döndürülecek bir <xref:System.Xml.XmlWriter> düğümleri eklemek için kullanılan nesne.  
  
### <a name="unsupported-xmlwriter-methods"></a>Desteklenmeyen XmlWriter yöntemleri  
 Tüm bilgileri kullanarak bir XML belgesi yazmak için kullanılan yöntemleri <xref:System.Xml.XmlWriter> sınıfı tarafından desteklenen <xref:System.Xml.XPath.XPathNavigator> XPath veri modelini ve belge nesne modeli (DOM) arasındaki farkı nedeniyle sınıfı.  
  
 Aşağıdaki tabloda açıklanmıştır <xref:System.Xml.XmlWriter> sınıfı yöntemleri tarafından desteklenmeyen <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Oluşturur bir <xref:System.NotSupportedException> özel durum.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Oluşturur ve kök düzeyiyle göz ardı bir <xref:System.NotSupportedException> herhangi bir düzeyde XML belgesi olarak adlandırılan özel durum.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Bir çağrı olarak kabul <xref:System.Xml.XmlWriter.WriteString%2A> eşdeğer karakter veya karakterler için yöntemi.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Bir çağrı olarak kabul <xref:System.Xml.XmlWriter.WriteString%2A> eşdeğer karakter veya karakterler için yöntemi.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Bir çağrı olarak kabul <xref:System.Xml.XmlWriter.WriteString%2A> eşdeğer karakter veya karakterler için yöntemi.|  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XmlWriter> sınıfı <xref:System.Xml.XmlWriter> sınıfı başvuru belgeleri.  
  
### <a name="multiple-xmlwriter-objects"></a>Birden çok XmlWriter nesnesi  
 Birden çok olması mümkündür <xref:System.Xml.XPath.XPathNavigator> nesneleri işaret eden bir XML farklı bölümlerine bir veya daha fazla açık belge <xref:System.Xml.XmlWriter> nesneleri. Birden çok <xref:System.Xml.XmlWriter> nesneleri izin verilen ve tek iş parçacıklı senaryolarında desteklenir.  
  
 Birden çok kullanırken dikkate alınması gereken önemli notlar şunlardır <xref:System.Xml.XmlWriter> nesneleri.  
  
-   XML parçaları tarafından yazılan <xref:System.Xml.XmlWriter> nesneleri XML'e eklenen zaman belge <xref:System.Xml.XmlWriter.Close%2A> yöntemi her <xref:System.Xml.XmlWriter> nesne çağrılır. O noktaya kadar <xref:System.Xml.XmlWriter> nesnesi bağlantısı kesilmiş bir parça yazma. Bir işlem tarafından yazılan tüm parçaları bir XML belgesi üzerinde gerçekleştirilirse bir <xref:System.Xml.XmlWriter> önce nesne <xref:System.Xml.XmlWriter.Close%2A> çağrıldı, etkilenmez.  
  
-   Açık ise <xref:System.Xml.XmlWriter> belirli bir XML alt ağaç ve bu alt ağaç nesnesi silindiğinde <xref:System.Xml.XmlWriter> nesne alt ağacı için yine de ekleyebilir. Alt ağacı, yalnızca silinen bir parçası haline gelir.  
  
-   Birden çok <xref:System.Xml.XmlWriter> nesneleri, XML belgesi içindeki aynı noktada açıldığında, sırayı XML belgesinde eklenen <xref:System.Xml.XmlWriter> nesneleri kapatılır, bunlar açık sırasına göre değil.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Xml.XmlDocument> nesne, oluşturur bir <xref:System.Xml.XPath.XPathNavigator> nesne ve kullandığı <xref:System.Xml.XmlWriter> tarafından döndürülen nesne <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> ilk kitap yapısını oluşturmak için gereken yöntemini `books.xml` dosya. Örnek olarak sonra kaydeder `book.xml` dosya.  
  
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
  
## <a name="saving-an-xml-document"></a>Bir XML belgesi kaydediliyor  
 Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan yöntemlerden sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı. Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne, bkz: [kaydetme ve belge yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [XPathNavigator Kullanarak XML Verilerini Değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak XML Verilerini Kaldırma](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
