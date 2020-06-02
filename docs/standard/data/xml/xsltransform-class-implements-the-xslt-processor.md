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
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="abc1c-102">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="abc1c-102">XslTransform Class Implements the XSLT Processor</span></span>

> [!NOTE]
> <span data-ttu-id="abc1c-103"><xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="abc1c-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="abc1c-104">Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="abc1c-105">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="abc1c-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="abc1c-106"><xref:System.Xml.Xsl.XslTransform>Sınıfı, XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi uygulayan BIR XSLT işlemcisidir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="abc1c-107"><xref:System.Xml.Xsl.XslTransform.Load%2A>Yöntemi, stil sayfalarını bulur ve okur ve <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntemi verilen kaynak belgeyi dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="abc1c-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="abc1c-108">Arabirimini uygulayan herhangi bir mağaza <xref:System.Xml.XPath.IXPathNavigable> , için kaynak belge olarak kullanılabilir <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="abc1c-109">.NET Framework şu anda arabirimini,, ve ' de uygular, <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDataDocument> <xref:System.Xml.XPath.XPathDocument> Bu nedenle tüm bunlar bir dönüşüme giriş kaynak belgesi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-109">The .NET Framework currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>

<span data-ttu-id="abc1c-110"><xref:System.Xml.Xsl.XslTransform>.NET Framework nesne yalnızca aşağıdaki ad alanıyla tanımlanan XSLT 1,0 belirtimini destekler:</span><span class="sxs-lookup"><span data-stu-id="abc1c-110">The <xref:System.Xml.Xsl.XslTransform> object in the .NET Framework only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

<span data-ttu-id="abc1c-111">Stil sayfası, <xref:System.Xml.Xsl.XslTransform.Load%2A> aşağıdaki sınıflardan birinden yöntemi kullanılarak yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="abc1c-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>

- <span data-ttu-id="abc1c-112">XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="abc1c-112">XPathNavigator</span></span>

- <span data-ttu-id="abc1c-113">Değerine</span><span class="sxs-lookup"><span data-stu-id="abc1c-113">XmlReader</span></span>

- <span data-ttu-id="abc1c-114">URL 'YI temsil eden bir dize</span><span class="sxs-lookup"><span data-stu-id="abc1c-114">A string representing a URL</span></span>

<span data-ttu-id="abc1c-115"><xref:System.Xml.Xsl.XslTransform.Load%2A>Yukarıdaki giriş sınıflarının her biri için farklı bir yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="abc1c-116">Bazı yöntemler, bu sınıflardan birinin ve <xref:System.Xml.XmlResolver> sınıfından bağımsız değişken olarak bir birleşimini alır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="abc1c-117"><xref:System.Xml.XmlResolver>Tarafından başvurulan `<xsl:import>` veya `<xsl:include>` stil sayfasında bulunan kaynakları bulur.</span><span class="sxs-lookup"><span data-stu-id="abc1c-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="abc1c-118">Aşağıdaki yöntemler bir String, <xref:System.Xml.XmlReader> veya <xref:System.Xml.XPath.XPathNavigator> girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>

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

<span data-ttu-id="abc1c-119"><xref:System.Xml.Xsl.XslTransform.Load%2A>Yukarıda gösterilen yöntemlerin çoğu bir <xref:System.Xml.XmlResolver> parametre olarak alır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="abc1c-120">, <xref:System.Xml.XmlResolver> Stil sayfasını ve xsl: import ve xsl: include öğelerinde başvurulan stil sayfaları yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>

<span data-ttu-id="abc1c-121"><xref:System.Xml.Xsl.XslTransform.Load%2A>Yöntemlerin çoğu ayrıca bir parametre olarak kanıt alır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="abc1c-122">Kanıt parametresi, <xref:System.Security.Policy.Evidence> Stil sayfasıyla ilişkili olan ' dır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="abc1c-123">Stil sayfasının güvenlik düzeyi, başvurduğu komut dosyası, `document()` kullandığı tüm işlevler ve tarafından kullanılan tüm uzantı nesneleri gibi referans yaptığı sonraki kaynakların güvenlik düzeyini etkiler <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="abc1c-124">Stil sayfası <xref:System.Xml.Xsl.XslTransform.Load%2A> BIR URL parametresi içeren bir yöntem kullanılarak yüklenirse ve kanıt sağlanmazsa, stil sayfasının kanıtı, VERILEN URL 'nin sitesi ve bölgesi ile birleştirilerek hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>

<span data-ttu-id="abc1c-125">URI veya kanıt sağlanmazsa, stil sayfası için kanıt kümesi tam olarak güvenilirdir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="abc1c-126">Güvenilmeyen kaynaklardan stil sayfaları yüklemeyin veya uygulamasına güvenilmeyen uzantı nesneleri eklemeyin <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="abc1c-127">Güvenlik düzeyleri ve kanıt hakkında daha fazla bilgi ve komut dosyasını nasıl etkilediği hakkında daha fazla bilgi için bkz. [XSLT stil sayfası betiği \<msxsl:script> ](xslt-stylesheet-scripting-using-msxsl-script.md)</span><span class="sxs-lookup"><span data-stu-id="abc1c-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="abc1c-128">Güvenlik düzeyleri ve kanıt ve uzantı nesnelerini nasıl etkilediği hakkında bilgi için bkz. [stil sayfası parametreleri ve uzantı nesneleri Için XsltArgumentList](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="abc1c-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>

<span data-ttu-id="abc1c-129">Güvenlik düzeyleri ve kanıtları ve işlevi nasıl etkilediği hakkında bilgi için `document()` bkz. [dış XSLT stil sayfalarını ve belgelerini çözümleme](resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="abc1c-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](resolving-external-xslt-style-sheets-and-documents.md).</span></span>

<span data-ttu-id="abc1c-130">Bir stil sayfası, bir dizi giriş parametresiyle sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="abc1c-131">Stil sayfası, uzantı nesnelerindeki işlevleri de çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="abc1c-132">Hem parametreler hem de uzantı nesneleri, sınıfını kullanarak stil sayfasına sağlanır <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="abc1c-133">Hakkında daha fazla bilgi için <xref:System.Xml.Xsl.XsltArgumentList> bkz <xref:System.Xml.Xsl.XsltArgumentList> ..</span><span class="sxs-lookup"><span data-stu-id="abc1c-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="abc1c-134">XslTransform sınıfının önerilen güvenli kullanımı</span><span class="sxs-lookup"><span data-stu-id="abc1c-134">Recommended Secure Use of XslTransform Class</span></span>

<span data-ttu-id="abc1c-135">Stil sayfasının güvenlik ayrıcalıkları, belirtilen kanıta bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="abc1c-136">Aşağıdaki tabloda stil sayfasının konumu özetlenmektedir ve ne tür bir kanıt verilecek olduğuna ilişkin bir açıklama verilir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>

- <span data-ttu-id="abc1c-137">XSLT stil sayfasının dış başvuruları yoktur veya stil sayfası güvendiğiniz bir kod tabanından gelir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>

  - <span data-ttu-id="abc1c-138">Derlemeinizden kanıt sağlayın:</span><span class="sxs-lookup"><span data-stu-id="abc1c-138">Provide the evidence from your assembly:</span></span>

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- <span data-ttu-id="abc1c-139">XSLT stil sayfası bir dış kaynaktan gelir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="abc1c-140">Kaynağın kaynağı bilinirdi ve doğrulanabilir bir URI vardır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-140">The origin of the source is known and there is a verifiable URI.</span></span>

  - <span data-ttu-id="abc1c-141">URI kullanarak kanıt oluşturun.</span><span class="sxs-lookup"><span data-stu-id="abc1c-141">Create evidence using the URI.</span></span>

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- <span data-ttu-id="abc1c-142">XSLT stil sayfası bir dış kaynaktan gelir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="abc1c-143">Kaynağın kaynağı bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="abc1c-143">The origin of the source is not known.</span></span>

  - <span data-ttu-id="abc1c-144">Kanıtları olarak ayarlayın `null` .</span><span class="sxs-lookup"><span data-stu-id="abc1c-144">Set evidence to `null`.</span></span> <span data-ttu-id="abc1c-145">Betik blokları işlenmiyor, XSLT `document()` işlevi desteklenmiyor ve ayrıcalıklı uzantı nesnelerine izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="abc1c-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>

    <span data-ttu-id="abc1c-146">Ayrıca, parametresini de ayarlayabilirsiniz `resolver` `null` `xsl:import` ve `xsl:include` öğelerin işlenmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc1c-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>

- <span data-ttu-id="abc1c-147">XSLT stil sayfası bir dış kaynaktan gelir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="abc1c-148">Kaynağın kaynağı bilinmiyor, ancak betik desteğine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-148">The origin of the source is not known, but you require script support.</span></span>

  - <span data-ttu-id="abc1c-149">Çağırandan kanıt iste.</span><span class="sxs-lookup"><span data-stu-id="abc1c-149">Request evidence from the caller.</span></span>

## <a name="transformation-of-xml-data"></a><span data-ttu-id="abc1c-150">XML verilerinin dönüştürülmesi</span><span class="sxs-lookup"><span data-stu-id="abc1c-150">Transformation of XML Data</span></span>

<span data-ttu-id="abc1c-151">Bir stil sayfası yüklendikten sonra, dönüştürme yöntemlerinden birini çağırarak <xref:System.Xml.Xsl.XslTransform.Transform%2A> ve bir giriş kaynak belgesi sağlayarak başlar.</span><span class="sxs-lookup"><span data-stu-id="abc1c-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="abc1c-152"><xref:System.Xml.Xsl.XslTransform.Transform%2A>Yöntemi, farklı dönüştürme çıktıları sağlamak için aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="abc1c-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="abc1c-153">Dönüştürme, aşağıdaki çıkış biçimlerine neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="abc1c-153">The transformation can result in the following output formats:</span></span>

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- <span data-ttu-id="abc1c-154">Dosyanın dize URL 'SI</span><span class="sxs-lookup"><span data-stu-id="abc1c-154">String URL of file</span></span>

<span data-ttu-id="abc1c-155">Bu son biçim olan dize URL 'si, URL 'de bulunan bir giriş belgesini dönüştürme ve belgeyi çıkış URL 'sine yazma konusunda yaygın olarak kullanılan bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc1c-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="abc1c-156">Bu <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntem, bir dosyadan XML belgesi yüklemek, XSLT dönüşümünü gerçekleştirmek ve çıktıyı bir dosyaya yazmak için kullanışlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="abc1c-157">Bu, giriş kaynak belgesi oluşturup yüklemeyi ve ardından bir dosya akışına yazmanızı önler.</span><span class="sxs-lookup"><span data-stu-id="abc1c-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="abc1c-158">Aşağıdaki kod örneğinde, <xref:System.Xml.Xsl.XslTransform.Transform%2A> giriş ve çıkış olarak dize URL 'si kullanılarak yönteminin bu kullanımı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="abc1c-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>

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

## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="abc1c-159">XML belgesinin bir bölümünü dönüştürme</span><span class="sxs-lookup"><span data-stu-id="abc1c-159">Transforming a Section of an XML Document</span></span>

<span data-ttu-id="abc1c-160">Dönüşümler belgeye bir bütün olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="abc1c-161">Diğer bir deyişle, belge kök düğümü dışında bir düğüm geçirirseniz, bu, dönüşüm işleminin yüklenen belgedeki tüm düğümlere erişmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="abc1c-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="abc1c-162">Bir sonuç ağacı parçasını dönüştürmek için, <xref:System.Xml.XmlDocument> yalnızca sonuç ağacı parçasını içeren bir oluşturmanız ve bunu metoduna geçirmeniz gerekir <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="abc1c-163">Aşağıdaki örnek, bir sonuç ağacı parçasında bir dönüştürme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="abc1c-163">The following example performs a transformation on a result tree fragment.</span></span>

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

<span data-ttu-id="abc1c-164">Örnek, input olarak Library. xml ve print_root. xsl dosyalarını kullanır ve aşağıdakileri konsola verir:</span><span class="sxs-lookup"><span data-stu-id="abc1c-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console:</span></span>

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

<span data-ttu-id="abc1c-165">Library. xml</span><span class="sxs-lookup"><span data-stu-id="abc1c-165">library.xml</span></span>

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

<span data-ttu-id="abc1c-166">print_root. Xsl</span><span class="sxs-lookup"><span data-stu-id="abc1c-166">print_root.xsl</span></span>

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="abc1c-167">XSLT 'nin .NET Framework sürüm 1,0 ' den .NET Framework sürümüne geçişi 1,1</span><span class="sxs-lookup"><span data-stu-id="abc1c-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>

<span data-ttu-id="abc1c-168">Aşağıdaki tabloda, yöntemi için eski .NET Framework sürüm 1,0 yöntemleri ve yeni .NET Framework sürüm 1,1 yöntemleri gösterilmektedir <xref:System.Xml.Xsl.XslTransform.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-168">The following table shows the obsolete .NET Framework version 1.0 methods and new .NET Framework version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="abc1c-169">Yeni yöntemler, kanıt belirterek stil sayfasının izinlerini sınırlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="abc1c-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>

|<span data-ttu-id="abc1c-170">Eski .NET Framework sürüm 1,0 yükleme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="abc1c-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="abc1c-171">Değiştirme .NET Framework sürüm 1,1 yükleme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="abc1c-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|
|------------------------------------------------------|---------------------------------------------------------|
|<span data-ttu-id="abc1c-172">Load (XPathNavigator girişi);</span><span class="sxs-lookup"><span data-stu-id="abc1c-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="abc1c-173">Load (XPathNavigator girişi, XmlResolver Çözümleyicisi);</span><span class="sxs-lookup"><span data-stu-id="abc1c-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="abc1c-174">Load (XPathNavigator stil sayfası, XmlResolver Çözümleyicisi, kanıt kanıtı);</span><span class="sxs-lookup"><span data-stu-id="abc1c-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="abc1c-175">Load (ıxpathgezinebilir stil sayfası);</span><span class="sxs-lookup"><span data-stu-id="abc1c-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="abc1c-176">Load (ıxpathgezinilebilir stil sayfası, XmlResolver Çözümleyicisi);</span><span class="sxs-lookup"><span data-stu-id="abc1c-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="abc1c-177">Load (ıxpathgezinilebilir stil sayfası, XmlResolver Çözümleyicisi, kanıt kanıtı);</span><span class="sxs-lookup"><span data-stu-id="abc1c-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="abc1c-178">Load (XmlReader stil sayfası);</span><span class="sxs-lookup"><span data-stu-id="abc1c-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="abc1c-179">Load (XmlReader stil sayfası, XmlResolver Çözümleyicisi);</span><span class="sxs-lookup"><span data-stu-id="abc1c-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="abc1c-180">Load (XmlReader stil sayfası, XmlResolver Çözümleyicisi, kanıt kanıtı);</span><span class="sxs-lookup"><span data-stu-id="abc1c-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|

<span data-ttu-id="abc1c-181">Aşağıdaki tabloda, yöntemi için eski ve yeni yöntemler gösterilmektedir <xref:System.Xml.Xsl.XslTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="abc1c-182">Yeni yöntemler bir nesnesi alır <xref:System.Xml.XmlResolver> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>

|<span data-ttu-id="abc1c-183">Kullanımdan kalktı .NET Framework sürüm 1,0 dönüştürme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="abc1c-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="abc1c-184">Değiştirme .NET Framework sürüm dönüştürme 1,1 yöntemleri</span><span class="sxs-lookup"><span data-stu-id="abc1c-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|
|-----------------------------------------------------------|--------------------------------------------------------------|
|<span data-ttu-id="abc1c-185">XmlReader dönüşümü (XPathNavigator girişi, XsltArgumentList bağımsız değişkenleri)</span><span class="sxs-lookup"><span data-stu-id="abc1c-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="abc1c-186">XmlReader Transform (XPathNavigator girişi, XsltArgumentList args, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="abc1c-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="abc1c-187">XmlReader Transform (ıxpathgezinebilir girişi, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="abc1c-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="abc1c-188">XmlReader Transform (ıxpathgezinebilir Input, XsltArgumentList args, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="abc1c-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="abc1c-189">Void Transform (XPathNavigator girişi, XsltArgumentList args, XmlWriter çıktısı)</span><span class="sxs-lookup"><span data-stu-id="abc1c-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="abc1c-190">Void Transform (XPathNavigator girişi, XsltArgumentList args, XmlWriter çıktısı, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="abc1c-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="abc1c-191">Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, XmlWriter output)</span><span class="sxs-lookup"><span data-stu-id="abc1c-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="abc1c-192">Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, XmlWriter Output, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="abc1c-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="abc1c-193">Void Transform (XPathNavigator girişi, XsltArgumentList args, TextWriter çıkışı)</span><span class="sxs-lookup"><span data-stu-id="abc1c-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="abc1c-194">Void Transform (XPathNavigator girişi, XsltArgumentList args, TextWriter çıktısı, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="abc1c-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="abc1c-195">Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, TextWriter output)</span><span class="sxs-lookup"><span data-stu-id="abc1c-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="abc1c-196">Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, TextWriter Output, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="abc1c-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="abc1c-197">Void Transform (XPathNavigator girişi, XsltArgumentList args, akış çıkışı)</span><span class="sxs-lookup"><span data-stu-id="abc1c-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="abc1c-198">Void Transform (XPathNavigator girişi, XsltArgumentList args, Stream çıktısı, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="abc1c-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="abc1c-199">Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, stream output)</span><span class="sxs-lookup"><span data-stu-id="abc1c-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="abc1c-200">Void Transform (ıxpathgezinebilir Input, XsltArgumentList args, Stream Output, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="abc1c-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="abc1c-201">Void Transform (dize girişi, dize çıktısı);</span><span class="sxs-lookup"><span data-stu-id="abc1c-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="abc1c-202">Void Transform (dize girişi, dize çıkışı, XmlResolver Çözümleyicisi);</span><span class="sxs-lookup"><span data-stu-id="abc1c-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|

<span data-ttu-id="abc1c-203"><xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType>Özellik .NET Framework sürüm 1,1 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="abc1c-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in .NET Framework version 1.1.</span></span> <span data-ttu-id="abc1c-204">Bunun yerine, <xref:System.Xml.Xsl.XslTransform.Transform%2A> bir nesneyi almak için yeni aşırı yüklemeleri kullanın <xref:System.Xml.XmlResolver> .</span><span class="sxs-lookup"><span data-stu-id="abc1c-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>

## <a name="see-also"></a><span data-ttu-id="abc1c-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abc1c-205">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="abc1c-206">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="abc1c-206">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="abc1c-207">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="abc1c-207">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="abc1c-208">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="abc1c-208">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="abc1c-209">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="abc1c-209">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="abc1c-210">XslTransform’a XmlDataDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="abc1c-210">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="abc1c-211">XslTransform’a XmlDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="abc1c-211">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
