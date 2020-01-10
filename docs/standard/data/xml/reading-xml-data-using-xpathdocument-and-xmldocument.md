---
title: XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
ms.openlocfilehash: 87ae96944f9a9f2bbcefb54c343f429c75c3022d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710394"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma
<xref:System.Xml.XPath?displayProperty=nameWithType> ad alanındaki bir XML belgesini bulmanın iki yolu vardır. Bunlardan biri salt okunurdur <xref:System.Xml.XPath.XPathDocument> sınıfını kullanarak bir XML belgesini okumak ve diğeri ise <xref:System.Xml?displayProperty=nameWithType> ad alanındaki düzenlenebilir <xref:System.Xml.XmlDocument> sınıfını kullanarak bir XML belgesini okumalıdır.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>XPathDocument sınıfını kullanarak XML belgelerini okuma  
 <xref:System.Xml.XPath.XPathDocument> sınıfı, XPath veri modelini kullanarak bir XML belgesinin hızlı, Salt okunabilir ve bellek içi gösterimini sağlar. <xref:System.Xml.XPath.XPathDocument> sınıfının örnekleri, altı oluşturucularından biri kullanılarak oluşturulur. Bu oluşturucular, bir <xref:System.IO.Stream>, <xref:System.IO.TextReader>veya <xref:System.Xml.XmlReader> nesne ve bir XML dosyasının `string` yolunu kullanarak bir XML belgesini okumanızı sağlar.  
  
 Aşağıdaki örnekte, bir XML belgesini okumak için <xref:System.Xml.XPath.XPathDocument> sınıfının `string` oluşturucusunun kullanımı gösterilmektedir.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>XmlDocument sınıfını kullanarak XML belgelerini okuma  
 <xref:System.Xml.XmlDocument> sınıfı, W3C Belge Nesne Modeli (DOM) düzey 1 Core ve çekirdek DOM düzeyi 2 uygulayan bir XML belgesinin düzenlenebilir bellek içi gösterimidir. <xref:System.Xml.XmlDocument> sınıfının örnekleri, üç oluşturucularından biri kullanılarak oluşturulur. <xref:System.Xml.XmlDocument> sınıf oluşturucusunu parametresiz çağırarak yeni, boş <xref:System.Xml.XmlDocument> bir nesne oluşturabilirsiniz. Oluşturucuyu çağırdıktan sonra, XML verilerini bir <xref:System.IO.Stream>, <xref:System.IO.TextReader>veya <xref:System.Xml.XmlReader> nesnesinden yeni <xref:System.Xml.XmlDocument> nesnesine yüklemek için <xref:System.Xml.XmlDocument.Load%2A> yöntemini ve bir XML dosyasının `string` yolunu kullanın.  
  
 Aşağıdaki örnek, bir XML belgesini okumak için parametresiz <xref:System.Xml.XmlDocument> sınıf oluşturucuyu ve <xref:System.Xml.XmlDocument.Load%2A> metodunu kullanmayı gösterir.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>XML belgesinin kodlamasını belirleme  
 Bir <xref:System.Xml.XmlReader> nesnesi, bir XML belgesini okumak ve önceki bölümlerde gösterildiği gibi <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XmlDocument> nesneleri oluşturmak için kullanılabilir. Ancak, <xref:System.Xml.XmlReader> bir nesne kodlanmamış verileri okuyabilir ve sonuç olarak herhangi bir kodlama bilgisi sağlamaz.  
  
 <xref:System.Xml.XmlTextReader> sınıfı <xref:System.Xml.XmlReader> sınıfından devralınır, <xref:System.Xml.XmlTextReader.Encoding%2A> özelliğini kullanarak kodlama bilgileri sağlar ve bir <xref:System.Xml.XPath.XPathDocument> nesnesi veya <xref:System.Xml.XmlDocument> nesnesi oluşturmak için kullanılabilir.  
  
 <xref:System.Xml.XmlTextReader> sınıfı tarafından verilen kodlama bilgileri hakkında daha fazla bilgi için <xref:System.Xml.XmlTextReader> sınıfı başvuru belgelerindeki <xref:System.Xml.XmlTextReader.Encoding%2A> özelliğine bakın.  
  
## <a name="creating-xpathnavigator-objects"></a>XPathNavigator nesneleri oluşturma  
 Bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesine bir XML belgesi okuduktan sonra, belirli durumlarda, temel alınan XML verilerini düzenlemek, değerlendirmek, gezinmek ve bazı durumlarda bir <xref:System.Xml.XPath.XPathNavigator> nesnesi oluşturabilirsiniz.  
  
 Hem <xref:System.Xml.XPath.XPathDocument> hem de <xref:System.Xml.XmlDocument> sınıfları <xref:System.Xml.XmlNode> sınıfına ek olarak <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanının <xref:System.Xml.XPath.IXPathNavigable> arabirimini uygular. Sonuç olarak, üç sınıf de bir <xref:System.Xml.XPath.XPathNavigator> nesnesi döndüren <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> yöntemi sağlar.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>XPathNavigator sınıfını kullanarak XML belgelerini Düzenle  
 XML verilerinin seçilmesi, değerlendirilmesi ve gezinmesinin yanı sıra, bir XML belgesini oluşturan nesneye göre bazı durumlarda düzenlemek için <xref:System.Xml.XPath.XPathNavigator> sınıfı kullanılabilir.  
  
 <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunurdur, <xref:System.Xml.XmlDocument> sınıfı düzenlenebilir ancak sonuç olarak, bir <xref:System.Xml.XPath.XPathDocument> nesnesinden oluşturulan <xref:System.Xml.XPath.XPathNavigator> nesneleri bir <xref:System.Xml.XmlDocument> nesnesinden oluşturulan bir XML belgesini düzenlemek için kullanılamaz. <xref:System.Xml.XPath.XPathDocument> sınıfı yalnızca bir XML belgesini okumak için kullanılmalıdır. Bir XML belgesini düzenlemeniz veya olay işleme gibi <xref:System.Xml.XmlDocument> sınıfı tarafından sunulan ek işlevlere erişmeniz gerekiyorsa, <xref:System.Xml.XmlDocument> sınıfının kullanılması gerekir.  
  
 <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği, bir <xref:System.Xml.XPath.XPathNavigator> nesnesinin XML verilerini düzenleyip düzenleyeolabileceğini belirtir.  
  
 Aşağıdaki tabloda her bir sınıf için <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliğinin değeri açıklanmaktadır.  
  
|<xref:System.Xml.XPath.IXPathNavigable> uygulama|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> değeri|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Düzenleme](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Şema Doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
