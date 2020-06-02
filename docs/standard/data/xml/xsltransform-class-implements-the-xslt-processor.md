---
title: XslTransform Sınıfı XSLT İşlemcisini Uygular
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
ms.openlocfilehash: eec5d6588d907e2d12b588ab3bfe743d6d1eaff9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281615"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>XslTransform Sınıfı XSLT İşlemcisini Uygular

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .

<xref:System.Xml.Xsl.XslTransform>Sınıfı, XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi uygulayan BIR XSLT işlemcisidir. <xref:System.Xml.Xsl.XslTransform.Load%2A>Yöntemi, stil sayfalarını bulur ve okur ve <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntemi verilen kaynak belgeyi dönüştürür. Arabirimini uygulayan herhangi bir mağaza <xref:System.Xml.XPath.IXPathNavigable> , için kaynak belge olarak kullanılabilir <xref:System.Xml.Xsl.XslTransform> . .NET Framework şu anda arabirimini,, ve ' de uygular, <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDataDocument> <xref:System.Xml.XPath.XPathDocument> Bu nedenle tüm bunlar bir dönüşüme giriş kaynak belgesi olarak kullanılabilir.

<xref:System.Xml.Xsl.XslTransform>.NET Framework nesne yalnızca aşağıdaki ad alanıyla tanımlanan XSLT 1,0 belirtimini destekler:

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

Stil sayfası, <xref:System.Xml.Xsl.XslTransform.Load%2A> aşağıdaki sınıflardan birinden yöntemi kullanılarak yüklenebilir:

- XPathNavigator

- Değerine

- URL 'YI temsil eden bir dize

<xref:System.Xml.Xsl.XslTransform.Load%2A>Yukarıdaki giriş sınıflarının her biri için farklı bir yöntem vardır. Bazı yöntemler, bu sınıflardan birinin ve <xref:System.Xml.XmlResolver> sınıfından bağımsız değişken olarak bir birleşimini alır. <xref:System.Xml.XmlResolver>Tarafından başvurulan `<xsl:import>` veya `<xsl:include>` stil sayfasında bulunan kaynakları bulur. Aşağıdaki yöntemler bir String, <xref:System.Xml.XmlReader> veya <xref:System.Xml.XPath.XPathNavigator> girdi olarak alır.

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

<xref:System.Xml.Xsl.XslTransform.Load%2A>Yukarıda gösterilen yöntemlerin çoğu bir <xref:System.Xml.XmlResolver> parametre olarak alır. , <xref:System.Xml.XmlResolver> Stil sayfasını ve xsl: import ve xsl: include öğelerinde başvurulan stil sayfaları yüklemek için kullanılır.

<xref:System.Xml.Xsl.XslTransform.Load%2A>Yöntemlerin çoğu ayrıca bir parametre olarak kanıt alır. Kanıt parametresi, <xref:System.Security.Policy.Evidence> Stil sayfasıyla ilişkili olan ' dır. Stil sayfasının güvenlik düzeyi, başvurduğu komut dosyası, `document()` kullandığı tüm işlevler ve tarafından kullanılan tüm uzantı nesneleri gibi referans yaptığı sonraki kaynakların güvenlik düzeyini etkiler <xref:System.Xml.Xsl.XsltArgumentList> .

Stil sayfası <xref:System.Xml.Xsl.XslTransform.Load%2A> BIR URL parametresi içeren bir yöntem kullanılarak yüklenirse ve kanıt sağlanmazsa, stil sayfasının kanıtı, VERILEN URL 'nin sitesi ve bölgesi ile birleştirilerek hesaplanır.

URI veya kanıt sağlanmazsa, stil sayfası için kanıt kümesi tam olarak güvenilirdir. Güvenilmeyen kaynaklardan stil sayfaları yüklemeyin veya uygulamasına güvenilmeyen uzantı nesneleri eklemeyin <xref:System.Xml.Xsl.XsltArgumentList> .

Güvenlik düzeyleri ve kanıt hakkında daha fazla bilgi ve komut dosyasını nasıl etkilediği hakkında daha fazla bilgi için bkz. [XSLT stil sayfası betiği \<msxsl:script> ](xslt-stylesheet-scripting-using-msxsl-script.md) Güvenlik düzeyleri ve kanıt ve uzantı nesnelerini nasıl etkilediği hakkında bilgi için bkz. [stil sayfası parametreleri ve uzantı nesneleri Için XsltArgumentList](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).

Güvenlik düzeyleri ve kanıtları ve işlevi nasıl etkilediği hakkında bilgi için `document()` bkz. [dış XSLT stil sayfalarını ve belgelerini çözümleme](resolving-external-xslt-style-sheets-and-documents.md).

Bir stil sayfası, bir dizi giriş parametresiyle sağlanabilir. Stil sayfası, uzantı nesnelerindeki işlevleri de çağırabilir. Hem parametreler hem de uzantı nesneleri, sınıfını kullanarak stil sayfasına sağlanır <xref:System.Xml.Xsl.XsltArgumentList> . Hakkında daha fazla bilgi için <xref:System.Xml.Xsl.XsltArgumentList> bkz <xref:System.Xml.Xsl.XsltArgumentList> ..

## <a name="recommended-secure-use-of-xsltransform-class"></a>XslTransform sınıfının önerilen güvenli kullanımı

Stil sayfasının güvenlik ayrıcalıkları, belirtilen kanıta bağımlıdır. Aşağıdaki tabloda stil sayfasının konumu özetlenmektedir ve ne tür bir kanıt verilecek olduğuna ilişkin bir açıklama verilir.

- XSLT stil sayfasının dış başvuruları yoktur veya stil sayfası güvendiğiniz bir kod tabanından gelir.

  - Derlemeinizden kanıt sağlayın:

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- XSLT stil sayfası bir dış kaynaktan gelir. Kaynağın kaynağı bilinirdi ve doğrulanabilir bir URI vardır.

  - URI kullanarak kanıt oluşturun.

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- XSLT stil sayfası bir dış kaynaktan gelir. Kaynağın kaynağı bilinmiyor.

  - Kanıtları olarak ayarlayın `null` . Betik blokları işlenmiyor, XSLT `document()` işlevi desteklenmiyor ve ayrıcalıklı uzantı nesnelerine izin verilmiyor.

    Ayrıca, parametresini de ayarlayabilirsiniz `resolver` `null` `xsl:import` ve `xsl:include` öğelerin işlenmemesini sağlar.

- XSLT stil sayfası bir dış kaynaktan gelir. Kaynağın kaynağı bilinmiyor, ancak betik desteğine ihtiyacınız vardır.

  - Çağırandan kanıt iste.

## <a name="transformation-of-xml-data"></a>XML verilerinin dönüştürülmesi

Bir stil sayfası yüklendikten sonra, dönüştürme yöntemlerinden birini çağırarak <xref:System.Xml.Xsl.XslTransform.Transform%2A> ve bir giriş kaynak belgesi sağlayarak başlar. <xref:System.Xml.Xsl.XslTransform.Transform%2A>Yöntemi, farklı dönüştürme çıktıları sağlamak için aşırı yüklendi. Dönüştürme, aşağıdaki çıkış biçimlerine neden olabilir:

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- Dosyanın dize URL 'SI

Bu son biçim olan dize URL 'si, URL 'de bulunan bir giriş belgesini dönüştürme ve belgeyi çıkış URL 'sine yazma konusunda yaygın olarak kullanılan bir senaryo sağlar. Bu <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntem, bir dosyadan XML belgesi yüklemek, XSLT dönüşümünü gerçekleştirmek ve çıktıyı bir dosyaya yazmak için kullanışlı bir yöntemdir. Bu, giriş kaynak belgesi oluşturup yüklemeyi ve ardından bir dosya akışına yazmanızı önler. Aşağıdaki kod örneğinde, <xref:System.Xml.Xsl.XslTransform.Transform%2A> giriş ve çıkış olarak dize URL 'si kullanılarak yönteminin bu kullanımı gösterilmektedir:

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

## <a name="transforming-a-section-of-an-xml-document"></a>XML belgesinin bir bölümünü dönüştürme

Dönüşümler belgeye bir bütün olarak uygulanır. Diğer bir deyişle, belge kök düğümü dışında bir düğüm geçirirseniz, bu, dönüşüm işleminin yüklenen belgedeki tüm düğümlere erişmesini engellemez. Bir sonuç ağacı parçasını dönüştürmek için, <xref:System.Xml.XmlDocument> yalnızca sonuç ağacı parçasını içeren bir oluşturmanız ve bunu metoduna geçirmeniz gerekir <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslTransform.Transform%2A> . Aşağıdaki örnek, bir sonuç ağacı parçasında bir dönüştürme gerçekleştirir.

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

Örnek, input olarak Library. xml ve print_root. xsl dosyalarını kullanır ve aşağıdakileri konsola verir:

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

Library. xml

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

print_root. Xsl

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>XSLT 'nin .NET Framework sürüm 1,0 ' den .NET Framework sürümüne geçişi 1,1

Aşağıdaki tabloda, yöntemi için eski .NET Framework sürüm 1,0 yöntemleri ve yeni .NET Framework sürüm 1,1 yöntemleri gösterilmektedir <xref:System.Xml.Xsl.XslTransform.Load%2A> . Yeni yöntemler, kanıt belirterek stil sayfasının izinlerini sınırlamanıza olanak tanır.

|Eski .NET Framework sürüm 1,0 yükleme yöntemleri|Değiştirme .NET Framework sürüm 1,1 yükleme yöntemleri|
|------------------------------------------------------|---------------------------------------------------------|
|Load (XPathNavigator girişi);<br /><br /> Load (XPathNavigator girişi, XmlResolver Çözümleyicisi);|Load (XPathNavigator stil sayfası, XmlResolver Çözümleyicisi, kanıt kanıtı);|
|Load (ıxpathgezinebilir stil sayfası);<br /><br /> Load (ıxpathgezinilebilir stil sayfası, XmlResolver Çözümleyicisi);|Load (ıxpathgezinilebilir stil sayfası, XmlResolver Çözümleyicisi, kanıt kanıtı);|
|Load (XmlReader stil sayfası);<br /><br /> Load (XmlReader stil sayfası, XmlResolver Çözümleyicisi);|Load (XmlReader stil sayfası, XmlResolver Çözümleyicisi, kanıt kanıtı);|

Aşağıdaki tabloda, yöntemi için eski ve yeni yöntemler gösterilmektedir <xref:System.Xml.Xsl.XslTransform.Transform%2A> . Yeni yöntemler bir nesnesi alır <xref:System.Xml.XmlResolver> .

|Kullanımdan kalktı .NET Framework sürüm 1,0 dönüştürme yöntemleri|Değiştirme .NET Framework sürüm dönüştürme 1,1 yöntemleri|
|-----------------------------------------------------------|--------------------------------------------------------------|
|XmlReader dönüşümü (XPathNavigator girişi, XsltArgumentList bağımsız değişkenleri)|XmlReader Transform (XPathNavigator girişi, XsltArgumentList args, XmlResolver Çözümleyicisi)|
|XmlReader Transform (ıxpathgezinebilir girişi, XsltArgumentList args)|XmlReader Transform (ıxpathgezinebilir Input, XsltArgumentList args, XmlResolver Çözümleyicisi)|
|Void Transform (XPathNavigator girişi, XsltArgumentList args, XmlWriter çıktısı)|Void Transform (XPathNavigator girişi, XsltArgumentList args, XmlWriter çıktısı, XmlResolver Çözümleyicisi)|
|Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, XmlWriter output)|Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, XmlWriter Output, XmlResolver Çözümleyicisi)|
|Void Transform (XPathNavigator girişi, XsltArgumentList args, TextWriter çıkışı)|Void Transform (XPathNavigator girişi, XsltArgumentList args, TextWriter çıktısı, XmlResolver Çözümleyicisi)|
|Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, TextWriter output)|Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, TextWriter Output, XmlResolver Çözümleyicisi)|
|Void Transform (XPathNavigator girişi, XsltArgumentList args, akış çıkışı)|Void Transform (XPathNavigator girişi, XsltArgumentList args, Stream çıktısı, XmlResolver Çözümleyicisi)|
|Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, stream output)|Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, Stream Output, XmlResolver Çözümleyicisi)|
|Void Transform (dize girişi, dize çıktısı);|Void Transform (dize girişi, dize çıkışı, XmlResolver Çözümleyicisi);|

<xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType>Özellik .NET Framework sürüm 1,1 ' de kullanılmıyor. Bunun yerine, <xref:System.Xml.Xsl.XslTransform.Transform%2A> bir nesneyi almak için yeni aşırı yüklemeleri kullanın <xref:System.Xml.XmlResolver> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslTransform>
- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)
- [Dönüşümlerde XPathNavigator](xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](xmldocument-input-to-xsltransform.md)
