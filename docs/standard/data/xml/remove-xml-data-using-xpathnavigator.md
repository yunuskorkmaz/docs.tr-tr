---
title: "XML XPathNavigator kullanarak verileri Kaldır"
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
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4bc7c2de8bec50293a815195416575d20d648706
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="remove-xml-data-using-xpathnavigator"></a>XML XPathNavigator kullanarak verileri Kaldır
<xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümleri ve değerleri bir XML belgesinden kaldırmak için kullanılan yöntemler kümesi sağlar. Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesnesi olmalıdır düzenlenebilir, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> olmalıdır `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator>tarafından oluşturulan bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. <xref:System.Xml.XPath.XPathNavigator>tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunur ve herhangi bir düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesne bir <xref:System.Xml.XPath.XPathDocument> nesne sonuçlanıyor bir <xref:System.NotSupportedException>.  
  
 Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML veri okunurken](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Düğümleri kaldırma  
 <xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> bir XML belgesinden düğümler çıkarmak için yöntem.  
  
### <a name="removing-a-node"></a>Düğüm kaldırma  
 <xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi geçerli düğüm silmek için bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde bir XML belgesinden.  
  
 Kullanarak bir düğümü silindikten sonra <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi, onu artık kökünden ulaşılabilir <xref:System.Xml.XmlDocument> nesnesi. Bir düğüm silindikten sonra <xref:System.Xml.XPath.XPathNavigator> Silinen düğümün üst düğümde konumlandırıldı.  
  
 Bir silme işlemi herhangi konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> silinen düğümde konumlandırılmış nesnesi. Bunlar <xref:System.Xml.XPath.XPathNavigator> nesneler, silinen ağaçtaki taşıyabilir ancak ana düğüm kullanarak ağaç normal düğüm kümesi Gezinti yöntemlerinin taşınamaz anlamda geçerli <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı, bunlar taşımak için kullanılabilir <xref:System.Xml.XPath.XPathNavigator> nesneleri, silinen alt ağacı için ana düğüm ağaca ya da ana düğüm ağacından yedekleyin.  
  
 Aşağıdaki örnekte, `price` ilk öğesinin `book` öğesinin `contosoBooks.xml` dosyası kullanarak silinir <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi. Konumunu <xref:System.Xml.XPath.XPathNavigator> sonra nesne `price` öğesi silinir üzerinde üst `book` öğesi.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Öznitelik düğümü kaldırma  
 Öznitelik düğümleri kullanarak bir XML belgesi kaldırılır <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi.  
  
 Öznitelik düğümü silindikten sonra artık kök düğümden erişilebilir bir <xref:System.Xml.XmlDocument> nesne ve <xref:System.Xml.XPath.XPathNavigator> nesne üst öğede konumlandırılır.  
  
#### <a name="default-attributes"></a>Varsayılan öznitelikleri  
 Öznitelikleri kaldırmak için kullanılan yöntemin bağımsız olarak DTD ya da XML Şeması XML belgesi için varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırma özel sınırlamalar vardır. Ait oldukları öğesi de kaldırılmadığı sürece varsayılan öznitelikleri kaldırılamaz. Varsayılan öznitelikler, her zaman bildirilen, sonuç olarak, varsayılan özniteliği sonuçları öğesine eklenen bir değiştirme özniteliğinde silme ve varsayılan değerin bildirildi başlatıldı varsayılan özniteliklere sahip öğe yok.  
  
## <a name="removing-values"></a>Değerleri kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> kaldırmak için yöntemleri türsüz ve yazılan bir XML belgesi değerleri.  
  
### <a name="removing-untyped-values"></a>Türsüz değerleri kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler türsüz `string` değeri düğümün değeri olarak bir parametre olarak geçirilen <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır. Boş bir dize olarak geçirme <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi geçerli düğüm değerini kaldırır.  
  
 Aşağıdaki örnek değeri kaldırır `price` ilk öğesinin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
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
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Yazılan değerleri kaldırılıyor  
 Bir düğüm türü bir basit W3C XML Şeması olduğunda türü, tarafından eklenen yeni değer <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değer ayarlamadan önce yöntemi basit türe ilişkin modelleri karşı denetlenir. Yeni değer düğüm türüne göre geçerli değilse (örneğin, bir değeri ayarlamak `-1` türü olan bir öğe üzerinde `xs:positiveInteger`), bir özel durum oluşur. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Yöntemi de yapamazsınız bayraklarıdır `null` bir parametre olarak. Sonuç olarak yazılan düğüm değerinin kaldırma düğümünün şema türü ile uyumlu olmalıdır.  
  
 Aşağıdaki örnek değeri kaldırır `price` ilk öğesinin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değeri ayarlayarak yöntemi `0`. Düğümün değerini kaldırılmaz, ancak kitap fiyat veri türüne göre kaldırıldı `xs:decimal`.  
  
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
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
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
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a>Namespace düğümler  
 Namespace düğümleri, gelen silinemez bir <xref:System.Xml.XmlDocument> nesnesi. Ad alanı düğümleri kullanarak silme girişiminde <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi bir özel durum oluşur.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfı düğümlerin XML biçimlendirmesini değiştirme bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde verilen XML ayrıştırılmış içeriğini `string`. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde geçerli düğüm yanı sıra.  
  
 Bu konuda, açıklanan yöntemlerden yanı sıra <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, düğümleri ve değerleri bir XML belgesinden kaldırmak için kullanılabilir. Kullanma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> düğümleri değiştirmek için özellikler bkz [XML XPathNavigator kullanarak verileri değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.  
  
## <a name="saving-an-xml-document"></a>Bir XML belgesi kaydetme  
 Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan yöntemlerden sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı. Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne için bkz: [kaydetme ve bir belgeyi yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator Kullanarak XML Verileri Ekleme](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak XML Verilerini Değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
