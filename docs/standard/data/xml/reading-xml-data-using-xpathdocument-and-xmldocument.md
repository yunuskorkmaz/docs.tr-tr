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
ms.openlocfilehash: 68d19784bab8a5d5a1994ea139b5631f56c7c680
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580427"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>XPathDocument ve XmlDocument kullanarak XML verilerini okuma
Bir XML belgesinde okumak için iki yolla <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı. Salt okunur kullanarak bir XML belgesi okumak için biridir <xref:System.Xml.XPath.XPathDocument> sınıfı ve diğer olan düzenlenebilir kullanarak bir XML belgesi okumak için <xref:System.Xml.XmlDocument> sınıfını <xref:System.Xml?displayProperty=nameWithType> ad alanı.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Okuma XML belgeleri XPathDocument sınıfını kullanma  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı XPath veri modelini kullanarak bir XML belgesi hızlı, salt okunur, bellek içi bir gösterimini sağlar. Örneklerini <xref:System.Xml.XPath.XPathDocument> sınıf kendi altı oluşturucular biri kullanılarak oluşturulur. Bu oluşturucular kullanarak bir XML belgesi okumak izin bir <xref:System.IO.Stream>, <xref:System.IO.TextReader>, veya <xref:System.Xml.XmlReader> nesnesi yanı sıra `string` bir XML dosyasının yolu.  
  
 Kullanarak aşağıdaki örnekte gösterildiği <xref:System.Xml.XPath.XPathDocument> sınıfın `string` bir XML belgesi okumak için oluşturucu.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>Okuma XML belgeleri XmlDocument sınıfını kullanma  
 <xref:System.Xml.XmlDocument> Düzenlenebilir bir bellek içi temsili W3C belge nesne modeli (DOM) Düzey 1 çekirdek ve çekirdek DOM Düzey 2 uygulama bir XML belgesi bir sınıftır. Örneklerini <xref:System.Xml.XmlDocument> sınıfı üç kendi oluşturucular biri kullanılarak oluşturulur. Yeni, boş oluşturabilirsiniz <xref:System.Xml.XmlDocument> çağırarak <xref:System.Xml.XmlDocument> sınıf oluşturucusu parametresiz. Oluşturucu çağrıldıktan sonra kullanmak <xref:System.Xml.XmlDocument.Load%2A> yeni XML verilerini yüklemek için gereken yöntemini <xref:System.Xml.XmlDocument> nesnesinden bir <xref:System.IO.Stream>, <xref:System.IO.TextReader>, veya <xref:System.Xml.XmlReader> nesnesi yanı sıra `string` bir XML dosyasının yolu.  
  
 Kullanarak aşağıdaki örnekte gösterildiği <xref:System.Xml.XmlDocument> sınıf oluşturucusu parametresiz ve <xref:System.Xml.XmlDocument.Load%2A> bir XML belgesi okumak için yöntem.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Bir XML belgesi kodlamasıyla belirleme  
 Bir <xref:System.Xml.XmlReader> nesnesi, bir XML belgesi okumak ve oluşturmak için kullanılabilir <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XmlDocument> nesneleri önceki bölümlerde gösterildiği gibi. Ancak, bir <xref:System.Xml.XmlReader> nesne kodlanmamış ve sonuç olarak, kodlama herhangi bir bilgi sağlamaz verileri okuma.  
  
 <xref:System.Xml.XmlTextReader> Sınıfının devraldığı <xref:System.Xml.XmlReader> sınıfı, kodlama bilgileriyle sağlar, <xref:System.Xml.XmlTextReader.Encoding%2A> özelliği ve oluşturmak için kullanılan bir <xref:System.Xml.XPath.XPathDocument> nesne veya <xref:System.Xml.XmlDocument> nesne.  
  
 Tarafından sağlanan kodlama bilgileri hakkında daha fazla bilgi için <xref:System.Xml.XmlTextReader> sınıfı <xref:System.Xml.XmlTextReader.Encoding%2A> özelliğinde <xref:System.Xml.XmlTextReader> sınıfı başvuru belgeleri.  
  
## <a name="creating-xpathnavigator-objects"></a>XPathNavigator nesneleri oluşturma  
 Bir XML belgesi okuduktan sonra bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi oluşturmak için kullanabileceğiniz bir <xref:System.Xml.XPath.XPathNavigator> seçin, değerlendirmek, gidin ve bazı durumlarda, temel alınan XML verileri düzenlemek için nesne.  
  
 Hem <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XmlDocument> ayrıca için sınıfları <xref:System.Xml.XmlNode> sınıfı, uygulama <xref:System.Xml.XPath.IXPathNavigable> arabiriminin <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı. Sonuç olarak, tüm üç sınıfları sağlar bir <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> döndüren yöntem bir <xref:System.Xml.XPath.XPathNavigator> nesne.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>XML belgelerini XPathNavigator sınıfını kullanarak düzenleme  
 Ek olarak seçme, değerlendirme ve XML verilerinde gezinme <xref:System.Xml.XPath.XPathNavigator> sınıfı, bazı durumlarda, oluşturduğu nesneye bağlı bir XML belgesi düzenlemek için kullanılabilir.  
  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı, salt okunur sırasında <xref:System.Xml.XmlDocument> sınıfıdır düzenlenebilir ve sonuç olarak, <xref:System.Xml.XPath.XPathNavigator> oluşturulan nesneleri bir <xref:System.Xml.XPath.XPathDocument> bağlanırken oluşturulan bir XML belgesi düzenlemek için nesne kullanılamaz bir <xref:System.Xml.XmlDocument> nesnesi. <xref:System.Xml.XPath.XPathDocument> Sınıfı, yalnızca bir XML belgesi okumak için kullanılmalıdır. Bir XML belgesi düzenlemek ya da tarafından sağlanan ek işlevsellik erişmesi gerektiğinde burada <xref:System.Xml.XmlDocument> olay işlemede gibi bir sınıf <xref:System.Xml.XmlDocument> sınıfı kullanılmalıdır.  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfını belirtir bir <xref:System.Xml.XPath.XPathNavigator> nesne XML verileri düzenleyebilirsiniz.  
  
 Aşağıdaki tabloda değerinin açıklanmıştır <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> her sınıf için özellik.  
  
|<xref:System.Xml.XPath.IXPathNavigable> Uygulama|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Değer|  
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
