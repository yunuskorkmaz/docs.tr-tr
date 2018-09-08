---
title: XslTransform sınıfı XSLT işlemcisini uygular
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81d0ce4f697935908b8ad7084560bd1adacbdf2d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44222733"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>XslTransform sınıfı XSLT işlemcisini uygular
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 <xref:System.Xml.Xsl.XslTransform> XSLT Dönüşümleri (XSLT) sürüm 1.0 öneri uygulayan bir XSLT işlemci bir sınıftır. <xref:System.Xml.Xsl.XslTransform.Load%2A> Yöntemi bulur ve stil sayfalarını okur ve <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, belirtilen kaynak belge dönüştürür. Uygulayan herhangi bir depolama <xref:System.Xml.XPath.IXPathNavigable> arabirimi, kaynak belge için kullanılabilir <xref:System.Xml.Xsl.XslTransform>. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Şu anda uygulayan <xref:System.Xml.XPath.IXPathNavigable> üzerinde arabirim <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>ve <xref:System.Xml.XPath.XPathDocument>, bunların tümü, bir dönüştürme için giriş kaynağı belge olarak kullanılabilir.  
  
 <xref:System.Xml.Xsl.XslTransform> Nesnesine [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aşağıdaki ad alanıyla tanımlı XSLT 1.0 belirtimi yalnızca destekler:  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 Stil sayfası, yüklenebiliyor <xref:System.Xml.Xsl.XslTransform.Load%2A> aşağıdaki sınıflarının birinden yöntemi:  
  
-   XPathNavigator  
  
-   XmlReader  
  
-   URL'yi temsil eden bir dize  
  
 Var. farklı bir <xref:System.Xml.Xsl.XslTransform.Load%2A> yukarıdaki Giriş sınıflarının her biri için yöntemi. Bu sınıfların birinin bir arada bazı yöntemleri alır ve <xref:System.Xml.XmlResolver> bağımsız değişkenler olarak sınıf. <xref:System.Xml.XmlResolver> Tarafından başvurulan kaynakları bulur `<xsl:import>` veya `<xsl:include>` stil sayfası içinde bulunamadı. Aşağıdaki yöntemlerden bir dize olması <xref:System.Xml.XmlReader>, veya <xref:System.Xml.XPath.XPathNavigator> giriş olarak.  
  
```vb  
Overloads Public Sub Load(String)  
```  
  
```csharp  
public void Load(string);  
```  
  
```vb  
Overloads Public Sub Load(String, XmlResolver)  
```  
  
```csharp  
public void Load(string, XmlResolver);  
```  
  
```vb  
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XmlReader, XmlResolver, Evidence);  
```  
  
```vb  
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XPathNavigator, XmlResolver, Evidence);  
```  
  
 Çoğu <xref:System.Xml.Xsl.XslTransform.Load%2A> Al gösterilen yöntemleri bir <xref:System.Xml.XmlResolver> bir parametre olarak. <xref:System.Xml.XmlResolver> Stil sayfası ve import ve xsl başvuruda bulunulan tüm stil sayfaları kaldırılsın yüklemek için kullanılır: öğelerini içerir.  
  
 Çoğu <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemleri de kanıt bir parametre olarak alır. Kanıt parametresi <xref:System.Security.Policy.Evidence> stil sayfası ile ilişkili. Stil sayfası güvenlik düzeyini ona başvuran tüm sonraki kaynakları güvenlik düzeyini etkiler, betik gibi içerdiği herhangi `document()` işlevleri kullanır ve herhangi bir uzantı nesnesi tarafından kullanılan <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Stil sayfası kullanılarak yüklenmişse bir <xref:System.Xml.Xsl.XslTransform.Load%2A> bir URL parametresi ve kanıt içeren yöntemi sağlanır, stil sayfası kanıt, site ve bölge verilen URL'nin birleştirerek hesaplanır.  
  
 URI ya da bir kanıt sağlanırsa, stil sayfası kümesi kanıt tam olarak güvenilir. Stil sayfaları güvenilmeyen kaynaklardan yüklenemedi, veya güvenilir olmayan uzantı nesneleri eklemek <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Güvenlik düzeyleri ve kanıt ve betik oluşturma nasıl etkilediği hakkında daha fazla bilgi için bkz. [XSLT stil sayfası komut dosyalarını kullanarak \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md). Güvenlik düzeyleri ve kanıt ve genişletme nesneleri nasıl etkilediği hakkında daha fazla bilgi için bkz: [stil sayfası parametreleri ve genişletme nesneleri için XsltArgumentList](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).  
  
 Güvenlik düzeyleri ve kanıt ve nasıl etkilediği hakkında bilgi için `document()` çalışması için bkz: [çözme dış XSLT stil sayfaları ile belgelerini](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).  
  
 Bir stil sayfası, giriş parametreleri sayısıyla sağlanabilir. Stil sayfası, uzantı nesneler üzerinde işlevler de çağırabilirsiniz. Hem parametreleri hem de genişletme nesneleri sağlanacak olan stil sayfası kullanılarak <xref:System.Xml.Xsl.XsltArgumentList> sınıfı. Hakkında daha fazla bilgi için <xref:System.Xml.Xsl.XsltArgumentList>, bkz: <xref:System.Xml.Xsl.XsltArgumentList>.  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a>XslTransform sınıfı önerilen güvenli kullanımı  
 Stil sayfası güvenlik ayrıcalıkları sağlanan kanıta göre değişir. Aşağıdaki tabloda, stil sayfası konumunu özetler ve ne tür bir kanıt sağlamak için bir açıklama sağlar.  
  
-   XSLT stil sayfası boş dış başvuru veya stil sayfası güvendiğiniz bir kod tabanından gelir.  
  
    -   Kanıt, derleme:  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   XSLT stil sayfası, dış bir kaynaktan geliyor. Kaynak dosyanın kaynağını bilinen ve doğrulanabilir bir URI yoktur.  
  
    -   URI'yi kullanarak kanıt oluşturur.  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   XSLT stil sayfası, dış bir kaynaktan geliyor. Kaynak kaynağı bilinmiyor.  
  
    -   Kümesine kanıt `null`. Komut dosyası blokları işlenmedi, XSLT `document()` işlevi desteklenmiyor ve ayrıcalıklı genişletme nesneleri izin verilmiyor.  
  
         Buna ek olarak da ayarlayabilirsiniz `resolver` parametresi `null` bu sağlar `xsl:import` ve `xsl:include` öğeleri işlenmedi.  
  
-   XSLT stil sayfası, dış bir kaynaktan geliyor. Kaynak kaynağı bilinmiyor ancak betik desteği gerektirir.  
  
    -   Kanıt çağrıyı yapandan isteyin.  
  
## <a name="transformation-of-xml-data"></a>XML veri dönüştürme  
 Bir stil sayfası yüklendikten sonra Dönüşüm, aşağıdakilerden birini çağırarak başlar <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemleri ve bir giriş kaynağı belge sağlama. <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntemi aşırı yüklüdür farklı dönüştürme çıkışları sağlamak için. Aşağıdaki çıktı biçimlerde dönüşümü neden olabilir:  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   Dosya dize URL'si  
  
 URL'de bulunan bir giriş belge dönüştürme, yaygın olarak kullanılan bir senaryo için bu son biçimi dizesi URL sağlar ve belge yazma çıkış URL'si. Bu <xref:System.Xml.Xsl.XslTransform.Transform%2A> bir XML belgesi bir dosyadan yüklemek, XSLT dönüşümü gerçekleştirme ve çıktıyı bir dosyaya yazmak için bir kolaylık yöntemi bir yöntemdir. Bu oluşturmak ve giriş kaynak belge yüklemek zorunda kalmasını önler ve ardından bir dosya akışına yazar. Aşağıdaki kod örneği bu kullanımı gösterir <xref:System.Xml.Xsl.XslTransform.Transform%2A> girdi ve çıktı olarak dize URL'yi kullanarak yöntemi:  
  
```vb  
Dim xsltransform As XslTransform = New XslTransform()  
xsltransform.Load("favorite.xsl")  
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)  
```  
  
```csharp  
XslTransform xsltransform = new XslTransform();  
xsltransform.Load("favorite.xsl");  
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);  
```  
  
## <a name="transforming-a-section-of-an-xml-document"></a>Bir XML belgesi bir bölümünü dönüştürme  
 Dönüşümler belgenin bir bütün olarak uygular. Belge kök düğümü dışındaki bir düğümde geçirirseniz, diğer bir deyişle, bu dönüştürme süreci yüklenen belgedeki tüm düğümleri erişmesini engellemez. Sonuç ağacı parçası dönüştürmek için oluşturmalısınız bir <xref:System.Xml.XmlDocument> içeren yalnızca sonuç ağacı parçası ve, geçirmek <xref:System.Xml.XmlDocument> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi. Aşağıdaki örnek bir sonuç ağacı parçası üzerinde bir dönüştürme gerçekleştirir.  
  
```vb  
Dim xslt As New XslTransform()  
xslt.Load("print_root.xsl")  
Dim doc As New XmlDocument()  
doc.Load("library.xml")  
' Create a new document containing just the result tree fragment.  
Dim testNode As XmlNode = doc.DocumentElement.FirstChild  
Dim tmpDoc As New XmlDocument()  
tmpDoc.LoadXml(testNode.OuterXml)  
' Pass the document containing the result tree fragment   
' to the Transform method.  
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))  
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)  
```  
  
```csharp  
XslTransform xslt = new XslTransform();       
xslt.Load("print_root.xsl");  
XmlDocument doc = new XmlDocument();  
doc.Load("library.xml");  
// Create a new document containing just the result tree fragment.  
XmlNode testNode = doc.DocumentElement.FirstChild;   
XmlDocument tmpDoc = new XmlDocument();   
tmpDoc.LoadXml(testNode.OuterXml);  
// Pass the document containing the result tree fragment   
// to the Transform method.  
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");  
xslt.Transform(tmpDoc, null, Console.Out, null);  
```  
  
 Örnek library.xml kullanır ve print_root.xsl giriş olarak dosyaları ve aşağıdakileri konsola çıkarır.  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 Library.XML  
  
```xml  
<library>  
  <book genre='novel' ISBN='1-861001-57-5'>  
     <title>Pride And Prejudice</title>  
  </book>  
  <book genre='novel' ISBN='1-81920-21-2'>  
     <title>Hook</title>  
  </book>  
</library>  
```  
  
 print_root.xsl  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>.NET Framework sürüm 1.1 .NET Framework sürüm 1.0 XSLT geçişi  
 Aşağıdaki tabloda, artık kullanılmayan gösterilmektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 yöntemleri ve yeni [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 yöntemleri <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi. Yeni yöntemleri kanıt belirterek izinleri stil sayfası sınırlamanıza olanak sağlar.  
  
|Eski .NET Framework sürüm 1.0 yük yöntemler|Değiştirme .NET Framework sürüm 1.1 yükleme yöntemleri|  
|------------------------------------------------------|---------------------------------------------------------|  
|(XPathNavigator giriş) yük;<br /><br /> Yük (XPathNavigator giriş, XmlResolver Çözümleyicisi);|Yük (XPathNavigator stil sayfası, XmlResolver Çözümleyici, kanıt kanıt);|  
|(IXPathNavigable stil sayfası) yük;<br /><br /> Yük (IXPathNavigable stil sayfası, XmlResolver Çözümleyicisi);|Yük (IXPathNavigable stil sayfası, XmlResolver Çözümleyici, kanıt kanıt);|  
|(XmlReader stil sayfası) yük;<br /><br /> Yük (XmlReader stil sayfası, XmlResolver Çözümleyicisi);|Yük (XmlReader stil sayfası, XmlResolver Çözümleyici, kanıt kanıt);|  
  
 Aşağıdaki tabloda eski ve yeni yöntemleri gösterilmektedir <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi. Yeni yöntemleri ele bir <xref:System.Xml.XmlResolver> nesne.  
  
|.NET Framework sürüm 1.0 dönüştürme yöntemleri geçersiz|Değiştirme .NET Framework sürüm 1.1 yöntemleri dönüştürme|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|XmlReader Transform(XPathNavigator input, XsltArgumentList args)|XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)|  
|XmlReader Transform(IXPathNavigable input, XsltArgumentList args)|XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)|  
|Void dönüştürme (XPathNavigator giriş, XsltArgumentList args, XmlWriter çıkış)|Void (XPathNavigator giriş, XsltArgumentList args, XmlWriter çıkış, XmlResolver Çözümleyicisi) dönüştürme|  
|Void dönüştürme (IXPathNavigable giriş, XsltArgumentList args, XmlWriter çıkış)|Void (IXPathNavigable giriş, XsltArgumentList args, XmlWriter çıkış, XmlResolver Çözümleyicisi) dönüştürme|  
|Void dönüştürme (XPathNavigator giriş, XsltArgumentList args, TextWriter çıkış)|Void (XPathNavigator giriş, XsltArgumentList args, TextWriter çıkış, XmlResolver Çözümleyicisi) dönüştürme|  
|Void dönüştürme (IXPathNavigable giriş, XsltArgumentList args, TextWriter çıkış)|Void (IXPathNavigable giriş, XsltArgumentList args, TextWriter çıkış, XmlResolver Çözümleyicisi) dönüştürme|  
|Void dönüştürme (XPathNavigator giriş, XsltArgumentList args, Stream çıkış)|Void (XPathNavigator giriş, XsltArgumentList args, Stream çıkış, XmlResolver Çözümleyicisi) dönüştürme|  
|Void dönüştürme (IXPathNavigable giriş, XsltArgumentList args, Stream çıkış)|Void (IXPathNavigable giriş, XsltArgumentList args, Stream çıkış, XmlResolver Çözümleyicisi) dönüştürme|  
|Void dönüştürme (dize giriş, dize çıkış);|Void dönüştürme (dize giriş, dize çıktısı, XmlResolver Çözümleyicisi);|  
  
 <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> İçinde özellik kullanılmıyor [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1. Bunun yerine, yeni kullanın <xref:System.Xml.Xsl.XslTransform.Transform%2A> yeniden yüklemeleri hangi bir <xref:System.Xml.XmlResolver> nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslTransform>  
- [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [XslTransform’a XmlDataDocument Girişi](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
