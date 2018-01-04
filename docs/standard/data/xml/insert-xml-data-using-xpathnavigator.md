---
title: XML XPathNavigator kullanarak verileri ekleme
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
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 33a1bf08d7a66dd970a3a7207293277021ed46b7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="insert-xml-data-using-xpathnavigator"></a>XML XPathNavigator kullanarak verileri ekleme
<xref:System.Xml.XPath.XPathNavigator> Sınıfı XML belgesinde eş, alt ve öznitelik düğümleri eklemek için kullanılan yöntemler kümesi sağlar. Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesnesi olmalıdır düzenlenebilir, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> olmalıdır `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator>tarafından oluşturulan bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. <xref:System.Xml.XPath.XPathNavigator>tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunur ve herhangi bir düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesne bir <xref:System.Xml.XPath.XPathDocument> nesne sonuçlanıyor bir <xref:System.NotSupportedException>.  
  
 Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML veri okunurken](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Düğümler ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı XML belgesinde eş, alt ve öznitelik düğümleri eklemek için yöntemler sağlar. Bu yöntem, geçerli konumu ile ilgili olarak farklı konumlarda düğümleri ve öznitelikler eklemek izin bir <xref:System.Xml.XPath.XPathNavigator> nesne ve aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="inserting-sibling-nodes"></a>Eşdüzey düğümleri ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı eşdüzey düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Bu yöntemler önce ve sonra düğümün eşdüzey düğümleri Ekle bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> yöntemlerini aşırı yüklenmiş olan iş ve kabul bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklemek için eşdüzey düğüm içeren nesne. Her iki yöntem aynı zamanda sonuç bir <xref:System.Xml.XmlWriter> eşdüzey düğümleri eklemek için kullanılan nesne.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri eklemek tek Eşdüzey Düğüm önce ve sonra düğüm bir <xref:System.Xml.XPath.XPathNavigator> nesne, ad alanı öneki, yerel ad, ad alanı URI'si ve parametre olarak belirtilen değeri kullanarak şu anda konumlandırılır.  
  
 Aşağıdaki örnekte yeni bir `pages` öğesine önce eklenir `price` ilk alt öğesi `book` öğesinde `contosoBooks.xml` dosya.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri bkz <xref:System.Xml.XPath.XPathNavigator> sınıf başvurusu belgelerinde.  
  
### <a name="inserting-child-nodes"></a>Alt düğümler ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı, alt düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Bu yöntemler ekleme ve alt düğümleri sonuna ve düğümün alt öğelerinin listesi başlangıcını başına bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır.  
  
 "Eşdüzey düğümleri ekleme" bölümündeki yöntemleri gibi <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemlerini kabul edecek bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklemek için alt düğümü içeren bir nesne. Her iki yöntem aynı zamanda sonuç bir <xref:System.Xml.XmlWriter> alt düğümleri eklemek için kullanılan nesne.  
  
 Ayrıca, "Eşdüzey düğümleri ekleme" bölümündeki yöntemleri ister <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri sonuna ve düğümün alt öğelerinin listesi başına tek alt düğümü Ekle bir <xref:System.Xml.XPath.XPathNavigator> nesnesi, kullanarak şu anda konumlandırılır ad alanı öneki, yerel ad, ad alanı URI'si ve parametre olarak belirtilen değeri.  
  
 Aşağıdaki örnekte, yeni bir `pages` alt öğesi ilk alt öğelerinin listesine eklenen `book` öğesinde `contosoBooks.xml` dosya.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri bkz <xref:System.Xml.XPath.XPathNavigator> sınıf başvurusu belgelerinde.  
  
### <a name="inserting-attribute-nodes"></a>Öznitelik düğümleri ekleme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı, öznitelik düğümleri eklemek için aşağıdaki yöntemleri sağlar.  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Bu yöntemler öğesi düğümde öznitelik düğümleri Ekle bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Yöntemi oluşturur öznitelik düğümü öğesi düğümde bir <xref:System.Xml.XPath.XPathNavigator> nesne, ad alanı öneki, yerel ad, ad alanı URI'si ve parametre olarak belirtilen değeri kullanarak şu anda konumlandırılır. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Yöntemi döndürür bir <xref:System.Xml.XmlWriter> öznitelik düğümleri eklemek için kullanılan nesne.  
  
 Aşağıdaki örnekte, yeni `discount` ve `currency` öznitelikleri üzerinde oluşturulan `price` ilk alt öğesi `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XmlWriter> döndürülen nesne <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntem.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> ve <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemleri bkz <xref:System.Xml.XPath.XPathNavigator> sınıf başvurusu belgelerinde.  
  
## <a name="copying-nodes"></a>Düğümleri kopyalama  
 Bazı durumlarda, bir XML belgesi başka bir XML belgesinden içeriğiyle doldurmak isteyebilirsiniz. Her iki <xref:System.Xml.XPath.XPathNavigator> sınıfı ve <xref:System.Xml.XmlWriter> sınıfı düğümlerine Kopyala bir <xref:System.Xml.XmlDocument> varolan bir nesne <xref:System.Xml.XmlReader> nesne veya <xref:System.Xml.XPath.XPathNavigator> nesnesi.  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> tümüne sahip kabul edebilir aşırı sınıf bir <xref:System.Xml.XPath.XPathNavigator> nesnesi veya bir <xref:System.Xml.XmlReader> nesnesini parametre olarak.  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A> Yöntemi <xref:System.Xml.XmlWriter> sınıfına sahip kabul edebilir aşırı bir <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, veya <xref:System.Xml.XPath.XPathNavigator> nesnesi.  
  
 Aşağıdaki örnek, tüm kopyalar `book` bir belgeden öğelerine.  
  
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
 <xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> bir düğüm için değerler eklemek için yöntemleri bir <xref:System.Xml.XmlDocument> nesnesi.  
  
### <a name="inserting-untyped-values"></a>Türsüz değerleri ekleniyor  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler türsüz `string` değeri düğümün değeri olarak bir parametre olarak geçirilen <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır. Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa, yeni değer düğüm türüne göre geçerli olduğunu doğrulama olmadan eklenir.  
  
 Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi tüm güncelleştirmek için kullanılan `price` öğelerinde `contosoBooks.xml` dosya.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Girilen değerleri ekleniyor  
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
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfı düğümlerin XML biçimlendirmesini değiştirme bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde verilen XML ayrıştırılmış içeriğini `string`. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde geçerli düğüm yanı sıra.  
  
 Bu konuda, açıklanan yöntemlerden yanı sıra <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, bir XML belgesi düğümleri ve değerler eklemek için kullanılabilir. Kullanma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> düğümleri ve değerler eklemek için özellikleri görmek [XML XPathNavigator kullanarak verileri değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespace ve XML: lang çakışıyor  
 İlgili ad alanı kapsamını belirli çakışma ve `xml:lang` bildirimleri XML verileri kullanarak eklerken oluşabilir <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> elesınıfı<xref:System.Xml.XmlReader>parametre olarak nesneleri.  
  
 Olası ad alanı çakışmalarını verilmiştir.  
  
-   Bir ad alanı içinde-kapsamı içinde ise <xref:System.Xml.XmlReader> nesnenin bağlamı, burada önek ad alanı URI eşlemesi içinde değil <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, yeni bir ad alanı bildiriminin yeni eklenen düğümüne eklenir.  
  
-   Aynı ad alanı URI'si kapsam içinde ise öğesinde hem de <xref:System.Xml.XmlReader> nesnenin bağlamı ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak her iki bağlamlarda eşlenmiş farklı bir önek vardır, yeni bir ad alanı bildiriminin önekiyle yeni eklenen düğümüne eklenir ve ad alanı URI'si alınan <xref:System.Xml.XmlReader> nesnesi.  
  
-   Aynı ad alanı öneki kapsam içinde ise öğesinde hem de <xref:System.Xml.XmlReader> nesnenin bağlamı ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak sahip farklı bir ad alanı URI eşlenmesi için her iki bağlamlarda yeni bir ad alanı bildiriminin yeni eklenen düğümüne eklenir, Bu ad alanı URI'si alınan önekiyle yeniden bildirir <xref:System.Xml.XmlReader> nesnesi.  
  
-   Hem de ad alanı URI'si yanı sıra önek <xref:System.Xml.XmlReader> nesnenin bağlamı ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlam aynıdır, yeni bir ad alanı bildiriminin yeni eklenen düğümüne eklenir.  
  
> [!NOTE]
>  Yukarıdaki açıklamayı boş olan ad alanı bildirimleri için de geçerlidir. `string` bir önek (örneğin, varsayılan ad alanı bildiriminin) olarak.  
  
 Olası şunlardır `xml:lang` çakışıyor.  
  
-   Varsa bir `xml:lang` içinde kapsamında özniteliği <xref:System.Xml.XmlReader> nesnenin bağlam de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı bir `xml:lang` öznitelik değeri, gelen alınır <xref:System.Xml.XmlReader> nesne yeni eklenen düğümüne eklenir.  
  
-   Varsa bir `xml:lang` içinde-kapsamında hem öznitelik <xref:System.Xml.XmlReader> nesnenin bağlamı ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak her farklı bir değere sahip bir `xml:lang` öznitelik değeri, gelen alınır <xref:System.Xml.XmlReader> nesne eklenir Yeni eklenen düğüm.  
  
-   Varsa bir `xml:lang` içinde-kapsamında hem öznitelik <xref:System.Xml.XmlReader> nesnenin bağlamı ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak her yeni aynı değere sahip `xml:lang` özniteliği yeni eklenen düğümüne eklenir.  
  
-   Varsa bir `xml:lang` içinde kapsamında özniteliği <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlam ancak hiçbiri mevcut <xref:System.Xml.XmlReader> nesnenin bağlamı, Hayır `xml:lang` özniteliği yeni eklenen düğümüne eklenir.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>XmlWriter ile düğüm ekleme  
 "Düğümler ve değerler ekleme" bölümünde açıklanan eşdüzey, alt ve öznitelik düğümleri eklemek için kullanılan yöntemleri aşırı yüklendi. <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> Ve <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfının return bir <xref:System.Xml.XmlWriter> düğümlerini eklemek için kullanılan nesne.  
  
### <a name="unsupported-xmlwriter-methods"></a>Desteklenmeyen XmlWriter yöntemleri  
 Tüm bilgileri kullanarak bir XML belgesi yazmak için kullanılan yöntemleri <xref:System.Xml.XmlWriter> sınıfı tarafından desteklenen <xref:System.Xml.XPath.XPathNavigator> XPath veri modeli ve belge nesne modeli (DOM) arasındaki fark nedeniyle sınıfı.  
  
 Aşağıdaki tabloda açıklanmaktadır <xref:System.Xml.XmlWriter> sınıfı tarafından desteklenmeyen yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Atan bir <xref:System.NotSupportedException> özel durum.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Atar ve kök düzeyiyle göz ardı bir <xref:System.NotSupportedException> XML belgesi diğer düzeyinde çağrıldıklarında özel durum.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Çağrısı olarak kabul <xref:System.Xml.XmlWriter.WriteString%2A> eşdeğer karakter veya karakter yöntemi.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Çağrısı olarak kabul <xref:System.Xml.XmlWriter.WriteString%2A> eşdeğer karakter veya karakter yöntemi.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Çağrısı olarak kabul <xref:System.Xml.XmlWriter.WriteString%2A> eşdeğer karakter veya karakter yöntemi.|  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.XmlWriter> sınıfı için bkz: <xref:System.Xml.XmlWriter> sınıf başvurusu belgelerinde.  
  
### <a name="multiple-xmlwriter-objects"></a>Birden çok XmlWriter nesnesi  
 Birden çok olması mümkündür <xref:System.Xml.XPath.XPathNavigator> nesneleri farklı bir XML bölümlerine işaret eden bir veya daha fazla açıkken belge <xref:System.Xml.XmlWriter> nesneleri. Birden çok <xref:System.Xml.XmlWriter> nesneleri izin verilen ve tek iş parçacıklı senaryolarında desteklenir.  
  
 Birden çok kullanırken dikkate alınması gereken önemli notlar şunlardır <xref:System.Xml.XmlWriter> nesneleri.  
  
-   XML parçaları tarafından yazılan <xref:System.Xml.XmlWriter> nesneleri XML'e eklenen ne zaman belge <xref:System.Xml.XmlWriter.Close%2A> yöntemi her <xref:System.Xml.XmlWriter> nesne çağrılır. O noktaya kadar <xref:System.Xml.XmlWriter> nesne bağlantısı kesilmiş bir parça yazma. Bir işlem tarafından yazılan tüm parçaları XML belgesi üzerinde gerçekleştirilirse bir <xref:System.Xml.XmlWriter> nesnesi, önce <xref:System.Xml.XmlWriter.Close%2A> çağrıldı, etkilenmez.  
  
-   Açık ise <xref:System.Xml.XmlWriter> nesne belirli bir XML alt ağacı ve bu alt ağaç üzerinde silinir, <xref:System.Xml.XmlWriter> nesne alt ağaç hala eklemek. Alt ağaç, yalnızca silinmiş bir parçası haline gelir.  
  
-   Birden çok <xref:System.Xml.XmlWriter> nesneleri XML belgesindeki bir aynı noktada açıldığında, hangi sırayla XML belgesinde eklendikten <xref:System.Xml.XmlWriter> nesneleri kapalı, bunlar açılan sırasını içinde değil.  
  
 Aşağıdaki örnekte bir <xref:System.Xml.XmlDocument> nesne, oluşturur bir <xref:System.Xml.XPath.XPathNavigator> nesne ve kullandığı <xref:System.Xml.XmlWriter> tarafından döndürülen nesne <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> ilk Defteri'nde yapısını oluşturmak için yöntemi `books.xml` dosya. Örnek olarak sonra kaydeder `book.xml` dosya.  
  
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
  
## <a name="saving-an-xml-document"></a>Bir XML belgesi kaydetme  
 Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan yöntemlerden sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı. Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne için bkz: [kaydetme ve bir belgeyi yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator Kullanarak XML Verilerini Değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak XML Verilerini Kaldırma](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
