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
<xref:System.Xml.XPath?displayProperty=nameWithType> Ad ALANıNDAKI bir XML belgesini bulmanın iki yolu vardır. Bunlardan biri, salt okunurdur <xref:System.Xml.XPath.XPathDocument> sınıfını kullanarak bir XML belgesini okumalıdır ve diğer <xref:System.Xml.XmlDocument> <xref:System.Xml?displayProperty=nameWithType> ad alanındaki düzenlenebilir sınıfını kullanarak bir XML belgesini okumalıdır.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>XPathDocument sınıfını kullanarak XML belgelerini okuma  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı, XPath veri modelini kullanarak bir XML belgesinin hızlı, Salt okunabilir ve bellek içi gösterimini sağlar. <xref:System.Xml.XPath.XPathDocument> Sınıfının örnekleri, altı oluşturucularından biri kullanılarak oluşturulur. Bu oluşturucular, bir XML belgesinin <xref:System.IO.Stream>bir, <xref:System.IO.TextReader>, veya <xref:System.Xml.XmlReader> nesnesi ile bir XML dosyasının `string` yolunu kullanarak okumanızı sağlar.  
  
 Aşağıdaki örnek, <xref:System.Xml.XPath.XPathDocument> sınıfının `string` yapıcısını bir XML belgesi okumak için kullanmayı gösterir.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>XmlDocument sınıfını kullanarak XML belgelerini okuma  
 <xref:System.Xml.XmlDocument> Sınıfı, W3C belge nesne MODELI (DOM) düzey 1 Core ve çekirdek DOM düzeyi 2 uygulayan bir XML belgesinin düzenlenebilir bellek içi gösterimidir. <xref:System.Xml.XmlDocument> Sınıfının örnekleri, üç oluşturucularından biri kullanılarak oluşturulur. Sınıf oluşturucusunu parametre olmadan çağırarak yeni, <xref:System.Xml.XmlDocument> boş bir nesne oluşturabilirsiniz. <xref:System.Xml.XmlDocument> Oluşturucuyu <xref:System.Xml.XmlDocument.Load%2A> çağırdıktan sonra, bir <xref:System.Xml.XmlDocument> <xref:System.IO.Stream>, <xref:System.IO.TextReader>, veya <xref:System.Xml.XmlReader> nesnesinden yeni nesneye XML verisi yüklemek için yöntemini ve bir XML dosyasının `string` yolunu kullanın.  
  
 Aşağıdaki örnek, <xref:System.Xml.XmlDocument> sınıf oluşturucunun parametre olmadan ve bir XML belgesini okuma <xref:System.Xml.XmlDocument.Load%2A> yöntemiyle kullanılması gösterilmektedir.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>XML belgesinin kodlamasını belirleme  
 Bir <xref:System.Xml.XmlReader> nesne, bir XML belgesini okumak ve önceki bölümlerde gösterildiği gibi oluşturmak <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XmlDocument> nesneler oluşturmak için kullanılabilir. Ancak, bir <xref:System.Xml.XmlReader> nesne kodlanmayan verileri okuyabilir ve sonuç olarak herhangi bir kodlama bilgisi sağlamaz.  
  
 <xref:System.Xml.XmlTextReader> <xref:System.Xml.XmlReader> Sınıfı sınıfından devralır <xref:System.Xml.XmlTextReader.Encoding%2A> , özelliğini kullanarak kodlama bilgilerini sağlar ve bir <xref:System.Xml.XPath.XPathDocument> nesne veya <xref:System.Xml.XmlDocument> nesne oluşturmak için kullanılabilir.  
  
 <xref:System.Xml.XmlTextReader> Sınıfı tarafından verilen kodlama bilgileri hakkında daha fazla bilgi için bkz. <xref:System.Xml.XmlTextReader> sınıf başvurusu <xref:System.Xml.XmlTextReader.Encoding%2A> belgelerindeki özelliği.  
  
## <a name="creating-xpathnavigator-objects"></a>XPathNavigator nesneleri oluşturma  
 Bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesine bir XML belgesi okuduktan sonra, seçim yapmak, değerlendirmek, gezinmek ve bazı <xref:System.Xml.XPath.XPathNavigator> durumlarda temel alınan XML verilerini düzenlemek için bir nesne oluşturabilirsiniz.  
  
 <xref:System.Xml.XPath.XPathDocument> Hem <xref:System.Xml.XmlDocument> hem de <xref:System.Xml.XmlNode> sınıfları sınıfının yanı sıra, <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanının arabirimini uygular. Sonuç olarak, üç sınıf de bir <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> <xref:System.Xml.XPath.XPathNavigator> nesne döndüren bir yöntem sağlar.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>XPathNavigator sınıfını kullanarak XML belgelerini Düzenle  
 XML verilerini seçmeye, değerlendirmeye ve gezinmeye ek olarak, <xref:System.Xml.XPath.XPathNavigator> sınıfı, bir XML belgesini oluşturan nesneye göre bazı durumlarda düzenlemek için kullanılabilir.  
  
 Sınıf <xref:System.Xml.XPath.XPathDocument> düzenlenebilir olsa <xref:System.Xml.XmlDocument> da, sınıf salt okunurdur ve bir nesneden oluşturulan nesneler, <xref:System.Xml.XPath.XPathNavigator> bir <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> nesneden oluşturulan nesneler bir XML belgesini düzenlemek için kullanılamaz. <xref:System.Xml.XPath.XPathDocument> Sınıfı yalnızca bir XML belgesini okumak için kullanılmalıdır. Bir XML belgesini düzenlemeniz veya <xref:System.Xml.XmlDocument> sınıf tarafından sunulan ve olay işleme gibi ek işlevlere erişmeniz gereken durumlarda, <xref:System.Xml.XmlDocument> sınıf kullanılmalıdır.  
  
 Sınıfının özelliği, <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> BIR <xref:System.Xml.XPath.XPathNavigator> nesnenin XML verilerini düzenleyip düzenleyeolabileceğini belirtir. <xref:System.Xml.XPath.XPathNavigator>  
  
 Aşağıdaki tabloda her bir sınıfın <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliğinin değeri açıklanmaktadır.  
  
|<xref:System.Xml.XPath.IXPathNavigable>Paylaşır|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>Deeri|  
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
