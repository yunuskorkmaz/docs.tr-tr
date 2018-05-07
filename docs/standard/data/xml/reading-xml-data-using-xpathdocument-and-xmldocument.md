---
title: XPathDocument ve XmlDocument kullanarak XML verilerini okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc8e1b85543fca0281b6433dd5c87c28b37818db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>XPathDocument ve XmlDocument kullanarak XML verilerini okuma
XML belgesi olarak okumak için iki yolla <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı. Salt okunur kullanarak bir XML belgesi okumak için biridir <xref:System.Xml.XPath.XPathDocument> sınıfı ve diğer olan düzenlenebilir kullanarak bir XML belgesi okumak için <xref:System.Xml.XmlDocument> sınıfını <xref:System.Xml?displayProperty=nameWithType> ad alanı.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Okuma XML belgelerini XPathDocument sınıfını kullanma  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı XPath veri modelini kullanarak bir XML belgesi hızlı, salt okunur, bellek içi bir gösterimini sağlar. Örneklerini <xref:System.Xml.XPath.XPathDocument> sınıfı altı oluşturucular biri kullanılarak oluşturulur. Bu oluşturucu kullanılarak bir XML belgesi okuma izin bir <xref:System.IO.Stream>, <xref:System.IO.TextReader>, veya <xref:System.Xml.XmlReader> nesnesi yanı sıra `string` bir XML dosyasının yolu.  
  
 Aşağıdaki örnek kullanarak gösterilmektedir <xref:System.Xml.XPath.XPathDocument> sınıfının `string` bir XML belgesi okumak için Oluşturucusu.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>XmlDocument sınıfını kullanarak XML belgeleri okuma  
 <xref:System.Xml.XmlDocument> W3C belge nesne modeli (DOM) Düzey 1 çekirdek ve çekirdek DOM Düzey 2 uygulayan bir XML belgesi düzenlenebilir bir bellek içi temsili bir sınıftır. Örneklerini <xref:System.Xml.XmlDocument> sınıfı, üç oluşturucular biri kullanılarak oluşturulur. Yeni, boş oluşturabilirsiniz <xref:System.Xml.XmlDocument> çağırarak nesne <xref:System.Xml.XmlDocument> hiçbir parametre sınıfı oluşturucusu. Oluşturucusu çağrıldıktan sonra kullanın <xref:System.Xml.XmlDocument.Load%2A> metodu XML verilerini yeni içine yüklemek için <xref:System.Xml.XmlDocument> nesnesinin bir <xref:System.IO.Stream>, <xref:System.IO.TextReader>, veya <xref:System.Xml.XmlReader> nesnesi yanı sıra `string` bir XML dosyasının yolu.  
  
 Kullanarak aşağıdaki örnekte gösterilmiştir <xref:System.Xml.XmlDocument> hiçbir parametre sınıfı oluşturucusu ve <xref:System.Xml.XmlDocument.Load%2A> bir XML belgesi okumak için yöntem.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Bir XML belgesi kodlama belirleme  
 Bir <xref:System.Xml.XmlReader> nesne bir XML belgesi okuyun ve oluşturmak için kullanılabilir <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XmlDocument> nesneleri önceki bölümlerde gösterildiği gibi. Ancak, bir <xref:System.Xml.XmlReader> nesnesi kodlanmamış ve sonuç olarak herhangi bir kodlama bilgi sağlamaz veri okuma.  
  
 <xref:System.Xml.XmlTextReader> Sınıfının devraldığı <xref:System.Xml.XmlReader> sınıfı, kodlama bilgileri kullanarak sağlar, <xref:System.Xml.XmlTextReader.Encoding%2A> özelliği ve oluşturmak için kullanılan bir <xref:System.Xml.XPath.XPathDocument> nesne veya <xref:System.Xml.XmlDocument> nesnesi.  
  
 Tarafından sağlanan kodlama bilgileri hakkında daha fazla bilgi için <xref:System.Xml.XmlTextReader> sınıfı için bkz: <xref:System.Xml.XmlTextReader.Encoding%2A> özelliğinde <xref:System.Xml.XmlTextReader> sınıf başvurusu belgelerinde.  
  
## <a name="creating-xpathnavigator-objects"></a>XPathNavigator nesneleri oluşturma  
 Ya da bir XML belgesi okuduktan sonra bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne oluşturabileceğiniz bir <xref:System.Xml.XPath.XPathNavigator> nesneyi seçin, değerlendirmek, sayfasına gidin ve bazı durumlarda, temel alınan XML verilerini düzenleyin.  
  
 Hem <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XmlDocument> , ayrıca için sınıfları <xref:System.Xml.XmlNode> sınıfı, uygulama <xref:System.Xml.XPath.IXPathNavigable> arabiriminin <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı. Sonuç olarak, tüm üç sınıf sağlayan bir <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> döndüren yöntemi bir <xref:System.Xml.XPath.XPathNavigator> nesnesi.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>XML belgeleri XPathNavigator sınıfı kullanarak düzenleme  
 Seçerek, değerlendirme ve XML veri gezinme yanı sıra <xref:System.Xml.XPath.XPathNavigator> sınıfı, bazı durumlarda, oluşturulduğu nesnesini temel alan bir XML belgesi düzenlemek için kullanılabilir.  
  
 <xref:System.Xml.XPath.XPathDocument> Sınıftır salt okunur sırasında <xref:System.Xml.XmlDocument> sınıftır düzenlenebilir ve sonuç olarak, <xref:System.Xml.XPath.XPathNavigator> oluşturulan nesneleri bir <xref:System.Xml.XPath.XPathDocument> nesnesi, bir XML belgesi olanlar oluşturulduğu sırasında düzenlemek için kullanılamaz bir <xref:System.Xml.XmlDocument> nesne olabilir. <xref:System.Xml.XPath.XPathDocument> Sınıfı, bir XML belgesi yalnızca okumak için kullanılmalıdır. Gereken bir XML belgesi düzenlemek ya da tarafından sağlanan ek işlevsellik erişim gerektiren durumlarda <xref:System.Xml.XmlDocument> olay işleme gibi sınıfı <xref:System.Xml.XmlDocument> sınıfı kullanılmalıdır.  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı belirtirse bir <xref:System.Xml.XPath.XPathNavigator> nesneyi XML verileri düzenleme.  
  
 Aşağıdaki tabloda değerini açıklanmaktadır <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> her sınıf özelliği.  
  
|<xref:System.Xml.XPath.IXPathNavigable> Uygulama|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Değer|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak XML Verilerini Düzenleme](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak Şema Doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
