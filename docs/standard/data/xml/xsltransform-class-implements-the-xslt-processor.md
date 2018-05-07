---
title: XSLT işlemci çok sınıfı uygular
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fd0a72ab0274fe6ccc2016d90739a5fda876826
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>XSLT işlemci çok sınıfı uygular
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 <xref:System.Xml.Xsl.XslTransform> XSL Dönüşümleri (XSLT) sürüm 1.0 öneri uygulama XSLT işlemci bir sınıftır. <xref:System.Xml.Xsl.XslTransform.Load%2A> Yöntemi bulur ve stil sayfaları, okur ve <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, belirtilen kaynak belge dönüştürür. Uygulayan deposu <xref:System.Xml.XPath.IXPathNavigable> arabirimi, kaynak belge için kullanılabilir <xref:System.Xml.Xsl.XslTransform>. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Şu anda uygulayan <xref:System.Xml.XPath.IXPathNavigable> üzerinde arabirim <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>ve <xref:System.Xml.XPath.XPathDocument>, bunların tümü dönüştürme giriş kaynağı belgeye olarak kullanılabilir.  
  
 <xref:System.Xml.Xsl.XslTransform> Nesnesinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] yalnızca aşağıdaki ad ile tanımlı XSLT 1.0 belirtimi destekler:  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 Kullanarak stil sayfası yüklenebilir <xref:System.Xml.Xsl.XslTransform.Load%2A> aşağıdaki sınıflar birinden yöntemi:  
  
-   XPathNavigator  
  
-   XmlReader  
  
-   Bir URL temsil eden bir dize  
  
 Var. farklı bir <xref:System.Xml.Xsl.XslTransform.Load%2A> yukarıdaki Giriş sınıfların her biri için yöntem. Bu sınıfların birinin bir arada bazı yöntemler alın ve <xref:System.Xml.XmlResolver> bağımsız değişken olarak sınıfı. <xref:System.Xml.XmlResolver> Tarafından başvurulan kaynaklar bulur `<xsl:import>` veya `<xsl:include>` stil sayfanızda bulundu. Aşağıdaki yöntemlerden bir dize olması <xref:System.Xml.XmlReader>, veya <xref:System.Xml.XPath.XPathNavigator> giriş olarak.  
  
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
  
 Çoğu <xref:System.Xml.Xsl.XslTransform.Load%2A> Al gösterilen yöntemleri bir <xref:System.Xml.XmlResolver> bir parametre olarak. <xref:System.Xml.XmlResolver> Stil sayfası ve import ve xsl başvuruda bulunulan tüm stil sayfalar yüklemek için kullanılan: öğeler içerir.  
  
 Çoğu <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemleri de kanıt bir parametre olarak alın. Kanıt parametresi <xref:System.Security.Policy.Evidence> stil sayfası ile ilişkili. Stil sayfası güvenlik düzeyini başvurduğu tüm sonraki kaynakları güvenlik düzeyini etkiler, komut dosyası gibi içerdiği, herhangi bir `document()` işlevleri kullanır ve herhangi bir uzantı nesne tarafından kullanılan <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Stil sayfası kullanarak yüklü ise bir <xref:System.Xml.Xsl.XslTransform.Load%2A> bir URL parametresi ve kanıt içeren yöntemi sağlanır, stil sayfası kanıtı kendi site ve bölge verilen URL'nin birleştirerek hesaplanır.  
  
 Herhangi bir URI veya kanıt sağlanırsa, stil sayfası ayarlamak kanıt tam güvenilir. Stil sayfaları güvenilmeyen kaynaklardan yüklenemedi, veya güvenilmeyen uzantı nesneleri eklemek <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Güvenlik düzeyleri ve kanıt ve komut dosyası nasıl etkilediği hakkında daha fazla bilgi için bkz: [XSLT stil sayfası komut dosyası kullanarak \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md). Güvenlik düzeyleri ve kanıt ve uzantısı nesnelerinin nasıl etkilediği hakkında daha fazla bilgi için bkz: [XsltArgumentList stil sayfası parametreleri ve uzantı nesneleri için](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).  
  
 Güvenlik düzeyleri ve kanıt ve nasıl etkilediği hakkında bilgi için `document()` işlev, bkz: [çözme dış XSLT stil sayfaları ve belgeleri](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).  
  
 Stil sayfası girdi parametresi sayısı ile sağlanabilir. Stil sayfası aynı zamanda uzantısı nesnelerde işlevleri çağırabilir. Parametreleri ve uzantı nesneleri sağlanacak olan stil sayfası kullanılarak <xref:System.Xml.Xsl.XsltArgumentList> sınıfı. Hakkında daha fazla bilgi için <xref:System.Xml.Xsl.XsltArgumentList>, bkz: <xref:System.Xml.Xsl.XsltArgumentList>.  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a>Önerilen güvenli kullanımı çok sınıfı  
 Stil sayfası, güvenlik ayrıcalıklarını sağlanan kanıt üzerinde bağlıdır. Aşağıdaki tabloda, stil sayfası konumunu özetler ve ne tür bir kanıt sağlamak için bir açıklama sağlar.  
  
-   XSLT stil sayfası dış başvuru içermiyorsa veya güvendiğiniz bir kod taban stil sayfası gelir.  
  
    -   Derleme kanıt:  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   XSLT stil sayfası bir dış kaynaktan geliyor. Kaynak kökeni bilinen ve doğrulanabilen bir URI yok.  
  
    -   URI'ı kullanarak kanıt oluşturur.  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   XSLT stil sayfası bir dış kaynaktan geliyor. Kaynak kaynağı bilinmiyor.  
  
    -   Kümesine kanıt `null`. Komut dosyası blokları işlenmedi, XSLT `document()` işlevi desteklenmiyor ve ayrıcalıklı uzantısı nesnelerinin izin verilmiyor.  
  
         Ayrıca, aynı zamanda ayarlayabileceğiniz `resolver` parametresi `null` bu sağlar `xsl:import` ve `xsl:include` öğeleri işlenmedi.  
  
-   XSLT stil sayfası bir dış kaynaktan geliyor. Kaynak kaynak bilinmiyor, ancak komut dosyası desteği gerektirir.  
  
    -   Kanıt çağrıyı yapandan isteyin.  
  
## <a name="transformation-of-xml-data"></a>XML veri dönüştürme  
 Stil sayfası yüklendikten sonra dönüştürme birini çağırarak başlatır <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemleri ve bir giriş kaynağı belge sağlama. <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntemi aşırı yüklenmiş farklı dönüştürme çıkışları sağlamak için. Dönüştürme, aşağıdaki çıkış biçimlerde neden olabilir:  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   Dosyanın URL'sini dize  
  
 Bir URL'de bulunan bir giriş belge dönüştürme, yaygın olarak kullanılan bir senaryo için bu son biçim dizesi URL sağlar ve çıktı URL'sine belge yazma. Bu <xref:System.Xml.Xsl.XslTransform.Transform%2A> bir dosyadan bir XML belgesi yüklemek, XSLT dönüşümü gerçekleştirmeye ve çıktıyı bir dosyaya yazmak için bir kolaylık yöntem bir yöntemdir. Bu oluşturma ve giriş kaynak belge yükleme zorunluluğunu ortadan kaldırır ve ardından bir dosya akışı yazın. Aşağıdaki kod örneği bu kullanımını göstermektedir <xref:System.Xml.Xsl.XslTransform.Transform%2A> giriş ve çıkış dize URL'yi kullanarak yöntemi:  
  
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
 Dönüşümleri belgeye bir bütün olarak uygulayın. Belge kök düğümü dışında bir düğümünde geçirirseniz, diğer bir deyişle, bu dönüştürme süreci yüklenen belgedeki tüm düğümleri erişmesini engellemez. Sonuç ağacı parçası dönüştürmek için oluşturmalısınız bir <xref:System.Xml.XmlDocument> yalnızca sonuç ağaç içeren parçalara ve, geçirin <xref:System.Xml.XmlDocument> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi. Aşağıdaki örnek, bir sonuç ağaç parçasını dönüştürme gerçekleştirir.  
  
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
  
 Örnek library.xml kullanır ve print_root.xsl giriş olarak dosyaları ve aşağıdaki konsola çıkarır.  
  
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
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>.NET Framework sürüm 1.1 için .NET Framework sürüm 1.0 gelen XSLT geçişi  
 Aşağıdaki tabloda artık kullanılmayan gösterilmektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 yöntemleri ve yeni [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için sürüm 1.1 yöntemleri <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi. Yeni yöntemleri kanıt belirterek stil sayfası izinleri sınırlamak etkinleştirin.  
  
|.NET Framework sürüm 1.0 yükleme yöntemlerini geçersiz|Değiştirme .NET Framework sürüm 1.1 yükleme yöntemleri|  
|------------------------------------------------------|---------------------------------------------------------|  
|(XPathNavigator giriş) yük;<br /><br /> Yük (XPathNavigator giriş, XmlResolver Çözümleyicisi);|Yük (XPathNavigator stil sayfası, XmlResolver Çözümleyici, kanıt kanıt);|  
|(IXPathNavigable stil) yük;<br /><br /> Yük (IXPathNavigable stil sayfası, XmlResolver Çözümleyicisi);|Yük (IXPathNavigable stil sayfası, XmlResolver Çözümleyici, kanıt kanıt);|  
|(XmlReader stil) yük;<br /><br /> Yük (XmlReader stil sayfası, XmlResolver Çözümleyicisi);|Yük (XmlReader stil sayfası, XmlResolver Çözümleyici, kanıt kanıt);|  
  
 Aşağıdaki tabloda eski ve yeni yöntemleri gösterilmektedir <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi. Yeni yöntemler ele bir <xref:System.Xml.XmlResolver> nesnesi.  
  
|.NET Framework sürüm 1.0 dönüştürme yöntemleri geçersiz|Değiştirme .NET Framework sürüm 1.1 yöntemleri dönüştürme|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|XmlReader Transform(XPathNavigator input, XsltArgumentList args)|XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)|  
|XmlReader Transform(IXPathNavigable input, XsltArgumentList args)|XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)|  
|Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, XmlWriter çıktı)|Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, XmlWriter çıktı, XmlResolver Çözümleyicisi)|  
|Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, XmlWriter çıktı)|Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, XmlWriter çıktı, XmlResolver Çözümleyicisi)|  
|Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, TextWriter çıktı)|Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, TextWriter çıktı, XmlResolver Çözümleyicisi)|  
|Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, TextWriter çıktı)|Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, TextWriter çıktı, XmlResolver Çözümleyicisi)|  
|Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, akış çıkışı)|Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, akış çıkışı, XmlResolver Çözümleyicisi)|  
|Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, akış çıkışı)|Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, akış çıkışı, XmlResolver Çözümleyicisi)|  
|Geçersiz kılma (dize giriş, dize çıktı) dönüştürme;|Geçersiz kılma (dize giriş, dize çıktısı, XmlResolver Çözümleyicisi) dönüştürme;|  
  
 <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Özelliği, içinde kullanılmıyor [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1. Bunun yerine, yeni kullanın <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads hangi Al bir <xref:System.Xml.XmlResolver> nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Xsl.XslTransform>  
 [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [XslTransform’a XmlDataDocument Girişi](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
