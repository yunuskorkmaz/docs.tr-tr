---
title: "XSLT işlemci çok sınıfı uygular"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f1367268920e4b72f29b77a7f2e96f09a1dce37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="99148-102">XSLT işlemci çok sınıfı uygular</span><span class="sxs-lookup"><span data-stu-id="99148-102">XslTransform Class Implements the XSLT Processor</span></span>
> [!NOTE]
>  <span data-ttu-id="99148-103"><xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99148-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="99148-104">Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="99148-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="99148-105">Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="99148-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="99148-106"><xref:System.Xml.Xsl.XslTransform> XSL Dönüşümleri (XSLT) sürüm 1.0 öneri uygulama XSLT işlemci bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="99148-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="99148-107"><xref:System.Xml.Xsl.XslTransform.Load%2A> Yöntemi bulur ve stil sayfaları, okur ve <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, belirtilen kaynak belge dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="99148-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="99148-108">Uygulayan deposu <xref:System.Xml.XPath.IXPathNavigable> arabirimi, kaynak belge için kullanılabilir <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="99148-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="99148-109">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Şu anda uygulayan <xref:System.Xml.XPath.IXPathNavigable> üzerinde arabirim <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>ve <xref:System.Xml.XPath.XPathDocument>, bunların tümü dönüştürme giriş kaynağı belgeye olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99148-109">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>  
  
 <span data-ttu-id="99148-110"><xref:System.Xml.Xsl.XslTransform> Nesnesinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] yalnızca aşağıdaki ad ile tanımlı XSLT 1.0 belirtimi destekler:</span><span class="sxs-lookup"><span data-stu-id="99148-110">The <xref:System.Xml.Xsl.XslTransform> object in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 <span data-ttu-id="99148-111">Kullanarak stil sayfası yüklenebilir <xref:System.Xml.Xsl.XslTransform.Load%2A> aşağıdaki sınıflar birinden yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99148-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>  
  
-   <span data-ttu-id="99148-112">XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="99148-112">XPathNavigator</span></span>  
  
-   <span data-ttu-id="99148-113">XmlReader</span><span class="sxs-lookup"><span data-stu-id="99148-113">XmlReader</span></span>  
  
-   <span data-ttu-id="99148-114">Bir URL temsil eden bir dize</span><span class="sxs-lookup"><span data-stu-id="99148-114">A string representing a URL</span></span>  
  
 <span data-ttu-id="99148-115">Var. farklı bir <xref:System.Xml.Xsl.XslTransform.Load%2A> yukarıdaki Giriş sınıfların her biri için yöntem.</span><span class="sxs-lookup"><span data-stu-id="99148-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="99148-116">Bu sınıfların birinin bir arada bazı yöntemler alın ve <xref:System.Xml.XmlResolver> bağımsız değişken olarak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="99148-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="99148-117"><xref:System.Xml.XmlResolver> Tarafından başvurulan kaynaklar bulur `<xsl:import>` veya `<xsl:include>` stil sayfanızda bulundu.</span><span class="sxs-lookup"><span data-stu-id="99148-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="99148-118">Aşağıdaki yöntemlerden bir dize olması <xref:System.Xml.XmlReader>, veya <xref:System.Xml.XPath.XPathNavigator> giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="99148-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>  
  
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
  
 <span data-ttu-id="99148-119">Çoğu <xref:System.Xml.Xsl.XslTransform.Load%2A> Al gösterilen yöntemleri bir <xref:System.Xml.XmlResolver> bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="99148-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="99148-120"><xref:System.Xml.XmlResolver> Stil sayfası ve import ve xsl başvuruda bulunulan tüm stil sayfalar yüklemek için kullanılan: öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="99148-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>  
  
 <span data-ttu-id="99148-121">Çoğu <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemleri de kanıt bir parametre olarak alın.</span><span class="sxs-lookup"><span data-stu-id="99148-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="99148-122">Kanıt parametresi <xref:System.Security.Policy.Evidence> stil sayfası ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="99148-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="99148-123">Stil sayfası güvenlik düzeyini başvurduğu tüm sonraki kaynakları güvenlik düzeyini etkiler, komut dosyası gibi içerdiği, herhangi bir `document()` işlevleri kullanır ve herhangi bir uzantı nesne tarafından kullanılan <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="99148-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="99148-124">Stil sayfası kullanarak yüklü ise bir <xref:System.Xml.Xsl.XslTransform.Load%2A> bir URL parametresi ve kanıt içeren yöntemi sağlanır, stil sayfası kanıtı kendi site ve bölge verilen URL'nin birleştirerek hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="99148-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>  
  
 <span data-ttu-id="99148-125">Herhangi bir URI veya kanıt sağlanırsa, stil sayfası ayarlamak kanıt tam güvenilir.</span><span class="sxs-lookup"><span data-stu-id="99148-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="99148-126">Stil sayfaları güvenilmeyen kaynaklardan yüklenemedi, veya güvenilmeyen uzantı nesneleri eklemek <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="99148-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="99148-127">Güvenlik düzeyleri ve kanıt ve komut dosyası nasıl etkilediği hakkında daha fazla bilgi için bkz: [XSLT stil sayfası komut dosyası kullanarak \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="99148-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="99148-128">Güvenlik düzeyleri ve kanıt ve uzantısı nesnelerinin nasıl etkilediği hakkında daha fazla bilgi için bkz: [XsltArgumentList stil sayfası parametreleri ve uzantı nesneleri için](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="99148-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>  
  
 <span data-ttu-id="99148-129">Güvenlik düzeyleri ve kanıt ve nasıl etkilediği hakkında bilgi için `document()` işlev, bkz: [çözme dış XSLT stil sayfaları ve belgeleri](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="99148-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>  
  
 <span data-ttu-id="99148-130">Stil sayfası girdi parametresi sayısı ile sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="99148-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="99148-131">Stil sayfası aynı zamanda uzantısı nesnelerde işlevleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="99148-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="99148-132">Parametreleri ve uzantı nesneleri sağlanacak olan stil sayfası kullanılarak <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="99148-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="99148-133">Hakkında daha fazla bilgi için <xref:System.Xml.Xsl.XsltArgumentList>, bkz: <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="99148-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="99148-134">Önerilen güvenli kullanımı çok sınıfı</span><span class="sxs-lookup"><span data-stu-id="99148-134">Recommended Secure Use of XslTransform Class</span></span>  
 <span data-ttu-id="99148-135">Stil sayfası, güvenlik ayrıcalıklarını sağlanan kanıt üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="99148-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="99148-136">Aşağıdaki tabloda, stil sayfası konumunu özetler ve ne tür bir kanıt sağlamak için bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="99148-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>  
  
-   <span data-ttu-id="99148-137">XSLT stil sayfası dış başvuru içermiyorsa veya güvendiğiniz bir kod taban stil sayfası gelir.</span><span class="sxs-lookup"><span data-stu-id="99148-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>  
  
    -   <span data-ttu-id="99148-138">Derleme kanıt:</span><span class="sxs-lookup"><span data-stu-id="99148-138">Provide the evidence from your assembly:</span></span>  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   <span data-ttu-id="99148-139">XSLT stil sayfası bir dış kaynaktan geliyor.</span><span class="sxs-lookup"><span data-stu-id="99148-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="99148-140">Kaynak kökeni bilinen ve doğrulanabilen bir URI yok.</span><span class="sxs-lookup"><span data-stu-id="99148-140">The origin of the source is known and there is a verifiable URI.</span></span>  
  
    -   <span data-ttu-id="99148-141">URI'ı kullanarak kanıt oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99148-141">Create evidence using the URI.</span></span>  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   <span data-ttu-id="99148-142">XSLT stil sayfası bir dış kaynaktan geliyor.</span><span class="sxs-lookup"><span data-stu-id="99148-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="99148-143">Kaynak kaynağı bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="99148-143">The origin of the source is not known.</span></span>  
  
    -   <span data-ttu-id="99148-144">Kümesine kanıt `null`.</span><span class="sxs-lookup"><span data-stu-id="99148-144">Set evidence to `null`.</span></span> <span data-ttu-id="99148-145">Komut dosyası blokları işlenmedi, XSLT `document()` işlevi desteklenmiyor ve ayrıcalıklı uzantısı nesnelerinin izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="99148-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>  
  
         <span data-ttu-id="99148-146">Ayrıca, aynı zamanda ayarlayabileceğiniz `resolver` parametresi `null` bu sağlar `xsl:import` ve `xsl:include` öğeleri işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="99148-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>  
  
-   <span data-ttu-id="99148-147">XSLT stil sayfası bir dış kaynaktan geliyor.</span><span class="sxs-lookup"><span data-stu-id="99148-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="99148-148">Kaynak kaynak bilinmiyor, ancak komut dosyası desteği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="99148-148">The origin of the source is not known, but you require script support.</span></span>  
  
    -   <span data-ttu-id="99148-149">Kanıt çağrıyı yapandan isteyin.</span><span class="sxs-lookup"><span data-stu-id="99148-149">Request evidence from the caller.</span></span>  
  
## <a name="transformation-of-xml-data"></a><span data-ttu-id="99148-150">XML veri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="99148-150">Transformation of XML Data</span></span>  
 <span data-ttu-id="99148-151">Stil sayfası yüklendikten sonra dönüştürme birini çağırarak başlatır <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemleri ve bir giriş kaynağı belge sağlama.</span><span class="sxs-lookup"><span data-stu-id="99148-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="99148-152"><xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntemi aşırı yüklenmiş farklı dönüştürme çıkışları sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="99148-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="99148-153">Dönüştürme, aşağıdaki çıkış biçimlerde neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="99148-153">The transformation can result in the following output formats:</span></span>  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   <span data-ttu-id="99148-154">Dosyanın URL'sini dize</span><span class="sxs-lookup"><span data-stu-id="99148-154">String URL of file</span></span>  
  
 <span data-ttu-id="99148-155">Bir URL'de bulunan bir giriş belge dönüştürme, yaygın olarak kullanılan bir senaryo için bu son biçim dizesi URL sağlar ve çıktı URL'sine belge yazma.</span><span class="sxs-lookup"><span data-stu-id="99148-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="99148-156">Bu <xref:System.Xml.Xsl.XslTransform.Transform%2A> bir dosyadan bir XML belgesi yüklemek, XSLT dönüşümü gerçekleştirmeye ve çıktıyı bir dosyaya yazmak için bir kolaylık yöntem bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="99148-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="99148-157">Bu oluşturma ve giriş kaynak belge yükleme zorunluluğunu ortadan kaldırır ve ardından bir dosya akışı yazın.</span><span class="sxs-lookup"><span data-stu-id="99148-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="99148-158">Aşağıdaki kod örneği bu kullanımını göstermektedir <xref:System.Xml.Xsl.XslTransform.Transform%2A> giriş ve çıkış dize URL'yi kullanarak yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99148-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>  
  
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
  
## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="99148-159">Bir XML belgesi bir bölümünü dönüştürme</span><span class="sxs-lookup"><span data-stu-id="99148-159">Transforming a Section of an XML Document</span></span>  
 <span data-ttu-id="99148-160">Dönüşümleri belgeye bir bütün olarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="99148-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="99148-161">Belge kök düğümü dışında bir düğümünde geçirirseniz, diğer bir deyişle, bu dönüştürme süreci yüklenen belgedeki tüm düğümleri erişmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="99148-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="99148-162">Sonuç ağacı parçası dönüştürmek için oluşturmalısınız bir <xref:System.Xml.XmlDocument> yalnızca sonuç ağaç içeren parçalara ve, geçirin <xref:System.Xml.XmlDocument> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99148-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="99148-163">Aşağıdaki örnek, bir sonuç ağaç parçasını dönüştürme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="99148-163">The following example performs a transformation on a result tree fragment.</span></span>  
  
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
  
 <span data-ttu-id="99148-164">Örnek library.xml kullanır ve print_root.xsl giriş olarak dosyaları ve aşağıdaki konsola çıkarır.</span><span class="sxs-lookup"><span data-stu-id="99148-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console.</span></span>  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 <span data-ttu-id="99148-165">Library.XML</span><span class="sxs-lookup"><span data-stu-id="99148-165">library.xml</span></span>  
  
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
  
 <span data-ttu-id="99148-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="99148-166">print_root.xsl</span></span>  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="99148-167">.NET Framework sürüm 1.1 için .NET Framework sürüm 1.0 gelen XSLT geçişi</span><span class="sxs-lookup"><span data-stu-id="99148-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>  
 <span data-ttu-id="99148-168">Aşağıdaki tabloda artık kullanılmayan gösterilmektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 yöntemleri ve yeni [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için sürüm 1.1 yöntemleri <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99148-168">The following table shows the obsolete [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0 methods and new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="99148-169">Yeni yöntemleri kanıt belirterek stil sayfası izinleri sınırlamak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="99148-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>  
  
|<span data-ttu-id="99148-170">.NET Framework sürüm 1.0 yükleme yöntemlerini geçersiz</span><span class="sxs-lookup"><span data-stu-id="99148-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="99148-171">Değiştirme .NET Framework sürüm 1.1 yükleme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="99148-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|  
|------------------------------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="99148-172">(XPathNavigator giriş) yük;</span><span class="sxs-lookup"><span data-stu-id="99148-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="99148-173">Yük (XPathNavigator giriş, XmlResolver Çözümleyicisi);</span><span class="sxs-lookup"><span data-stu-id="99148-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="99148-174">Yük (XPathNavigator stil sayfası, XmlResolver Çözümleyici, kanıt kanıt);</span><span class="sxs-lookup"><span data-stu-id="99148-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="99148-175">(IXPathNavigable stil) yük;</span><span class="sxs-lookup"><span data-stu-id="99148-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="99148-176">Yük (IXPathNavigable stil sayfası, XmlResolver Çözümleyicisi);</span><span class="sxs-lookup"><span data-stu-id="99148-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="99148-177">Yük (IXPathNavigable stil sayfası, XmlResolver Çözümleyici, kanıt kanıt);</span><span class="sxs-lookup"><span data-stu-id="99148-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="99148-178">(XmlReader stil) yük;</span><span class="sxs-lookup"><span data-stu-id="99148-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="99148-179">Yük (XmlReader stil sayfası, XmlResolver Çözümleyicisi);</span><span class="sxs-lookup"><span data-stu-id="99148-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="99148-180">Yük (XmlReader stil sayfası, XmlResolver Çözümleyici, kanıt kanıt);</span><span class="sxs-lookup"><span data-stu-id="99148-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
  
 <span data-ttu-id="99148-181">Aşağıdaki tabloda eski ve yeni yöntemleri gösterilmektedir <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99148-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="99148-182">Yeni yöntemler ele bir <xref:System.Xml.XmlResolver> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="99148-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
|<span data-ttu-id="99148-183">.NET Framework sürüm 1.0 dönüştürme yöntemleri geçersiz</span><span class="sxs-lookup"><span data-stu-id="99148-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="99148-184">Değiştirme .NET Framework sürüm 1.1 yöntemleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="99148-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="99148-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="99148-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="99148-186">XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="99148-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="99148-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="99148-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="99148-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="99148-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="99148-189">Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, XmlWriter çıktı)</span><span class="sxs-lookup"><span data-stu-id="99148-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="99148-190">Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, XmlWriter çıktı, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="99148-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="99148-191">Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, XmlWriter çıktı)</span><span class="sxs-lookup"><span data-stu-id="99148-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="99148-192">Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, XmlWriter çıktı, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="99148-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="99148-193">Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, TextWriter çıktı)</span><span class="sxs-lookup"><span data-stu-id="99148-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="99148-194">Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, TextWriter çıktı, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="99148-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="99148-195">Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, TextWriter çıktı)</span><span class="sxs-lookup"><span data-stu-id="99148-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="99148-196">Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, TextWriter çıktı, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="99148-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="99148-197">Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, akış çıkışı)</span><span class="sxs-lookup"><span data-stu-id="99148-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="99148-198">Void dönüştürme (XPathNavigator giriş, XsltArgumentList bağımsız değişken, akış çıkışı, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="99148-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="99148-199">Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, akış çıkışı)</span><span class="sxs-lookup"><span data-stu-id="99148-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="99148-200">Void dönüştürme (IXPathNavigable giriş, XsltArgumentList bağımsız değişken, akış çıkışı, XmlResolver Çözümleyicisi)</span><span class="sxs-lookup"><span data-stu-id="99148-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="99148-201">Geçersiz kılma (dize giriş, dize çıktı) dönüştürme;</span><span class="sxs-lookup"><span data-stu-id="99148-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="99148-202">Geçersiz kılma (dize giriş, dize çıktısı, XmlResolver Çözümleyicisi) dönüştürme;</span><span class="sxs-lookup"><span data-stu-id="99148-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|  
  
 <span data-ttu-id="99148-203"><xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Özelliği, içinde kullanılmıyor [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1.</span><span class="sxs-lookup"><span data-stu-id="99148-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1.</span></span> <span data-ttu-id="99148-204">Bunun yerine, yeni kullanın <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads hangi Al bir <xref:System.Xml.XmlResolver> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="99148-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99148-205">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99148-205">See Also</span></span>  
 <xref:System.Xml.Xsl.XslTransform>  
 [<span data-ttu-id="99148-206">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="99148-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="99148-207">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="99148-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="99148-208">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="99148-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="99148-209">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="99148-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="99148-210">XslTransform’a XmlDataDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="99148-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="99148-211">XslTransform’a XmlDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="99148-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
