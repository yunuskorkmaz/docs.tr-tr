---
title: XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
ms.openlocfilehash: da1cb81c819e55f572e9faaabef4dd49ee7397de
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288686"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma
Ad alanındaki bir XML belgesini bulmanın iki yolu vardır <xref:System.Xml.XPath?displayProperty=nameWithType> . Bunlardan biri, salt okunurdur sınıfını kullanarak bir XML belgesini okumalıdır <xref:System.Xml.XPath.XPathDocument> ve diğer ad alanındaki düzenlenebilir sınıfını kullanarak BIR XML belgesini okumalıdır <xref:System.Xml.XmlDocument> <xref:System.Xml?displayProperty=nameWithType> .  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>XPathDocument sınıfını kullanarak XML belgelerini okuma  
 <xref:System.Xml.XPath.XPathDocument>Sınıfı, XPath veri modelini kullanarak BIR XML belgesinin hızlı, Salt okunabilir ve bellek içi gösterimini sağlar. Sınıfının örnekleri, <xref:System.Xml.XPath.XPathDocument> altı oluşturucularından biri kullanılarak oluşturulur. Bu oluşturucular, bir XML belgesinin bir <xref:System.IO.Stream> , <xref:System.IO.TextReader> , veya nesnesi Ile bir <xref:System.Xml.XmlReader> `string` XML dosyasının yolunu kullanarak okumanızı sağlar.  
  
 Aşağıdaki örnek, <xref:System.Xml.XPath.XPathDocument> sınıfının `string` YAPıCıSıNı bir XML belgesi okumak için kullanmayı gösterir.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>XmlDocument sınıfını kullanarak XML belgelerini okuma  
 <xref:System.Xml.XmlDocument>Sınıfı, W3C belge nesne modeli (DOM) düzey 1 Core ve çekırdek DOM düzeyi 2 uygulayan BIR XML belgesinin düzenlenebilir bellek içi gösterimidir. Sınıfının örnekleri, <xref:System.Xml.XmlDocument> üç oluşturucularından biri kullanılarak oluşturulur. <xref:System.Xml.XmlDocument>Sınıf oluşturucusunu parametre olmadan çağırarak yeni, boş bir nesne oluşturabilirsiniz <xref:System.Xml.XmlDocument> . Oluşturucuyu çağırdıktan sonra, <xref:System.Xml.XmlDocument.Load%2A> bir,, veya nesnesinden yeni nesneye XML verisi yüklemek için yöntemini ve <xref:System.Xml.XmlDocument> <xref:System.IO.Stream> <xref:System.IO.TextReader> <xref:System.Xml.XmlReader> `string` bir XML dosyasının yolunu kullanın.  
  
 Aşağıdaki örnek, <xref:System.Xml.XmlDocument> sınıf oluşturucunun parametre olmadan ve <xref:System.Xml.XmlDocument.Load%2A> bir XML belgesini okuma yöntemiyle kullanılması gösterilmektedir.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>XML belgesinin kodlamasını belirleme  
 Bir <xref:System.Xml.XmlReader> nesne, BIR XML belgesini okumak ve <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> önceki bölümlerde gösterildiği gibi oluşturmak ve nesneler oluşturmak için kullanılabilir. Ancak, bir <xref:System.Xml.XmlReader> nesne kodlanmayan verileri okuyabilir ve sonuç olarak herhangi bir kodlama bilgisi sağlamaz.  
  
 <xref:System.Xml.XmlTextReader>Sınıfı sınıfından devralır <xref:System.Xml.XmlReader> , özelliğini kullanarak kodlama bilgilerini sağlar <xref:System.Xml.XmlTextReader.Encoding%2A> ve bir <xref:System.Xml.XPath.XPathDocument> nesne veya nesne oluşturmak için kullanılabilir <xref:System.Xml.XmlDocument> .  
  
 Sınıfı tarafından verilen kodlama bilgileri hakkında daha fazla bilgi için <xref:System.Xml.XmlTextReader> bkz <xref:System.Xml.XmlTextReader.Encoding%2A> <xref:System.Xml.XmlTextReader> . sınıf başvurusu belgelerindeki özelliği.  
  
## <a name="creating-xpathnavigator-objects"></a>XPathNavigator nesneleri oluşturma  
 Bir veya nesnesine bir XML belgesi okuduktan sonra <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> , <xref:System.Xml.XPath.XPathNavigator> seçim yapmak, değerlendirmek, gezinmek ve bazı durumlarda temel alınan XML verilerini düzenlemek için bir nesne oluşturabilirsiniz.  
  
 Hem <xref:System.Xml.XPath.XPathDocument> hem de <xref:System.Xml.XmlDocument> sınıfları sınıfının yanı sıra, <xref:System.Xml.XmlNode> <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanının arabirimini uygular. Sonuç olarak, üç sınıf de bir <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> nesne döndüren bir yöntem sağlar <xref:System.Xml.XPath.XPathNavigator> .  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>XPathNavigator sınıfını kullanarak XML belgelerini Düzenle  
 XML verilerini seçmeye, değerlendirmeye ve gezinmeye ek olarak, <xref:System.Xml.XPath.XPathNavigator> sınıfı, BIR XML belgesini oluşturan nesneye göre bazı durumlarda düzenlemek için kullanılabilir.  
  
 Sınıf <xref:System.Xml.XPath.XPathDocument> düzenlenebilir olsa da, sınıf salt okunurdur ve bir nesneden oluşturulan <xref:System.Xml.XmlDocument> nesneler, bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> NESNEDEN oluşturulan nesneler bir XML belgesini düzenlemek için kullanılamaz <xref:System.Xml.XmlDocument> . <xref:System.Xml.XPath.XPathDocument>Sınıfı yalnızca BIR XML belgesini okumak için kullanılmalıdır. Bir XML belgesini düzenlemeniz veya sınıf tarafından sunulan ve olay işleme gibi ek işlevlere erişmeniz gereken durumlarda, <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> sınıf kullanılmalıdır.  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>Sınıfının özelliği, <xref:System.Xml.XPath.XPathNavigator> BIR <xref:System.Xml.XPath.XPathNavigator> nesnenin XML verilerini düzenleyip düzenleyeolabileceğini belirtir.  
  
 Aşağıdaki tabloda her bir sınıfın özelliğinin değeri açıklanmaktadır <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> .  
  
|<xref:System.Xml.XPath.IXPathNavigable>Paylaşır|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>Deeri|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verilerine Erişme](accessing-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Düzenleme](editing-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Şema Doğrulama](schema-validation-using-xpathnavigator.md)
