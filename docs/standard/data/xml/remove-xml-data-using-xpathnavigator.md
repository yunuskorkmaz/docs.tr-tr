---
title: XPathNavigator kullanarak XML verilerini kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1827e40256bc4307006ce081cbb6cbc44a89a0bc
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46480714"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>XPathNavigator kullanarak XML verilerini kaldırma
<xref:System.Xml.XPath.XPathNavigator> Sınıf bir XML belgesinden düğümleri ve değerleri kaldırmak için kullanılan yöntemler kümesi sağlar. Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesne olmalıdır düzenlenemez, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. <xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesnelerin <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunurdur ve tüm düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> nesnesi tarafından oluşturulan bir <xref:System.Xml.XPath.XPathDocument> nesne sonuçlanıyor bir <xref:System.NotSupportedException>.  
  
 Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML verileri okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Düğümleri kaldırma  
 <xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi bir XML belgesinden düğümleri kaldırma.  
  
### <a name="removing-a-node"></a>Düğüm kaldırma  
 <xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> geçerli düğüm silmek için yöntemi bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde bir XML belgesinden.  
  
 Kullanarak bir düğümü silindikten sonra <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi, artık kökünden erişilebilir <xref:System.Xml.XmlDocument> nesne. Bir düğüm silindikten sonra <xref:System.Xml.XPath.XPathNavigator> Silinen düğümün üst düğümde konumlandırılır.  
  
 Bir silme işlemi herhangi bir konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> silinen düğüm üzerinde konumlandırılmış bir nesne. Bunlar <xref:System.Xml.XPath.XPathNavigator> nesnelerdir silinmiş alt ağacı içinde geçebilirsiniz ancak ana düğüm ağacı kullanarak normal bir düğüm kümesi gezinme yöntemlerinden biri taşınamaz anlamda geçerli <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı, bunları taşımak için kullanılabilir <xref:System.Xml.XPath.XPathNavigator> nesneler, silinen alt ağacı için ana düğüm ağaca veya ana düğüm ağacı geri.  
  
 Aşağıdaki örnekte, `price` ilk öğenin `book` öğesinin `contosoBooks.xml` dosyası kullanarak silinir <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi. Konumunu <xref:System.Xml.XPath.XPathNavigator> sonra nesne `price` silinir üzerinde üst `book` öğesi.  
  
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
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Bir öznitelik düğümü kaldırma  
 Öznitelik düğümleri kullanarak bir XML belgesi kaldırılır <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi.  
  
 Bir öznitelik düğümü silindikten sonra artık ' kök düğümünden erişilebilir değil bir <xref:System.Xml.XmlDocument> nesne ve <xref:System.Xml.XPath.XPathNavigator> nesnenin üst öğede konumlanan.  
  
#### <a name="default-attributes"></a>Varsayılan öznitelikler  
 Öznitelikleri kaldırmak için kullanılan yöntem ne olursa olsun DTD'nin veya XML Şeması XML belgesi için varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırma hakkında özel sınırlamalar vardır. Ayrıca ait oldukları öğesi kaldırılmadığı sürece, varsayılan öznitelikler kaldırılamaz. Varsayılan öznitelikleri her zaman bildirilen, sonuç olarak, varsayılan öznitelik sonuçları öğesine eklenen bir değiştirme özniteliğinde silme ve bildirilen varsayılan değeri olarak başlatılan varsayılan öznitelikleri olan öğeler için yok.  
  
## <a name="removing-values"></a>Değerleri kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> kaldırmak için yöntemleri türsüz ve yazılan değerleri bir XML belgesi.  
  
### <a name="removing-untyped-values"></a>Yazılmamış değerleri kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler yazılmamış `string` düğümün değeri olarak bir parametre olarak geçirilen değer <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda. Boş dize olarak geçirerek <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi değeri geçerli düğümün kaldırır.  
  
 Aşağıdaki örnek, değeri kaldırır `price` ilk öğenin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi.  
  
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
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Yazılan değerleri kaldırılıyor  
 Bir düğüm türü basit bir W3C XML Şeması olduğunda tür, tarafından eklenen yeni değer <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi değeri ayarlanmadan önce basit türe ilişkin modelleri karşı denetlenir. Yeni değer düğüm türüne göre geçerli değilse (örneğin, bir değeri ayarlamak `-1` türü olan bir öğede `xs:positiveInteger`), bir özel durum oluşur. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Yöntemi de geçirilemez `null` bir parametre olarak. Sonuç olarak belirlenmiş bir düğümün değerini kaldırma, düğüm şema türü ile uyumlu olmalıdır.  
  
 Aşağıdaki örnek, değeri kaldırır `price` ilk öğenin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değeri ayarlanarak yöntemi `0`. Bir düğümün değerini kaldırılmaz, ancak kendi veri türüne göre fiyat kitabın kaldırıldı `xs:decimal`.  
  
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
  
## <a name="namespace-nodes"></a>Namespace düğümleri  
 Namespace düğümleri, gelen silinemiyor bir <xref:System.Xml.XmlDocument> nesne. Ad alanı düğümleri kullanarak silmeyi dener <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi bir özel durum oluşur.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Sınıfının InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfını değiştirin XML işaretlemesini düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde belirli XML ayrıştırılmış içeriğiyle `string`. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde geçerli düğüm yanı sıra kendisini.  
  
 Bu konuda, açıklanan yöntemlerin yanı sıra <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, bir XML belgesinden düğümleri ve değerleri kaldırmak için kullanılabilir. Kullanma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> düğümleri değiştirilecek özellikleri görmek [değiştirme XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.  
  
## <a name="saving-an-xml-document"></a>Bir XML belgesi kaydediliyor  
 Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan yöntemlerden sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı. Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne, bkz: [kaydetme ve belge yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [XPathNavigator Kullanarak XML Verileri Ekleme](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak XML Verilerini Değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
