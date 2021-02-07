---
description: 'Daha fazla bilgi edinin: XslTransform sınıfından geçiş'
title: XslTransform Sınıfından Geçirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 6f4a08d3448f5735b9bd9e4c418ec3613fdc6a37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713630"
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="8f9e7-103">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="8f9e7-103">Migrating From the XslTransform Class</span></span>

<span data-ttu-id="8f9e7-104">XSLT mimarisi, Visual Studio 2005 sürümünde yeniden tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-104">The XSLT architecture was redesigned in the Visual Studio 2005 release.</span></span> <span data-ttu-id="8f9e7-105"><xref:System.Xml.Xsl.XslTransform>Sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfıyla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-105">The <xref:System.Xml.Xsl.XslTransform> class was replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

<span data-ttu-id="8f9e7-106">Aşağıdaki bölümlerde, ve sınıfları arasındaki bazı önemli farklılıklar açıklanır <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-106">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>

## <a name="performance"></a><span data-ttu-id="8f9e7-107">Performans</span><span class="sxs-lookup"><span data-stu-id="8f9e7-107">Performance</span></span>

<span data-ttu-id="8f9e7-108"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı birçok performans geliştirmesi içerir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-108">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="8f9e7-109">Yeni XSLT işlemcisi, XSLT stil sayfasını, diğer programlama dilleri için ortak dil çalışma zamanının (CLR) yaptığı gibi ortak bir ara biçimde derler.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-109">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="8f9e7-110">Stil sayfası derlendikten sonra, önbelleğe alınmış ve yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-110">Once the style sheet is compiled, it can be cached and reused.</span></span>

<span data-ttu-id="8f9e7-111"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, sınıfından çok daha hızlı hale gelen diğer iyileştirmeler da içerir <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-111">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

> [!NOTE]
> <span data-ttu-id="8f9e7-112">Sınıfının genel performansı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfından daha iyidir <xref:System.Xml.Xsl.XslTransform> , ancak <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> sınıfın yöntemi, <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.Xsl.XslTransform> bir dönüşümde ilk kez çağrıldığında sınıfının yönteminden daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-112">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="8f9e7-113">Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-113">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="8f9e7-114">Daha fazla bilgi için şu blog gönderisine bakın: [XslCompiledTransform, XslTransform 'Dan daha yavaş?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span><span class="sxs-lookup"><span data-stu-id="8f9e7-114">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>

## <a name="security"></a><span data-ttu-id="8f9e7-115">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="8f9e7-115">Security</span></span>

<span data-ttu-id="8f9e7-116">Varsayılan olarak, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı XSLT `document()` işlevi ve katıştırılmış komut dosyası desteğini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-116">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="8f9e7-117">Bu özellikler, <xref:System.Xml.Xsl.XsltSettings> özelliği etkinleştirilmiş ve yöntemine geçen bir nesne oluşturularak etkinleştirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-117">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="8f9e7-118">Aşağıdaki örnek, komut dosyasının nasıl etkinleştirileceğini ve XSLT dönüşümünün nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-118">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

<span data-ttu-id="8f9e7-119">Daha fazla bilgi için bkz. [XSLT güvenlik konuları](xslt-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="8f9e7-119">For more information, see [XSLT Security Considerations](xslt-security-considerations.md).</span></span>

## <a name="new-features"></a><span data-ttu-id="8f9e7-120">Yeni Özellikler</span><span class="sxs-lookup"><span data-stu-id="8f9e7-120">New Features</span></span>

### <a name="temporary-files"></a><span data-ttu-id="8f9e7-121">Geçici dosyalar</span><span class="sxs-lookup"><span data-stu-id="8f9e7-121">Temporary Files</span></span>

<span data-ttu-id="8f9e7-122">Geçici dosyalar bazen XSLT işleme sırasında üretilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-122">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="8f9e7-123">Bir stil sayfası betik blokları içeriyorsa veya hata ayıklama ayarı true olarak ayarlandıysa derlenmiş ise, geçici dosyalar% TEMP% klasöründe oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-123">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="8f9e7-124">Zamanlama sorunları nedeniyle bazı geçici dosyalar silinmediği durumlarda örnek olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-124">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="8f9e7-125">Örneğin, dosyalar geçerli AppDomain veya hata ayıklayıcı tarafından kullanılıyorsa, nesne sonlandırıcısı <xref:System.CodeDom.Compiler.TempFileCollection> bunları kaldıramayacak.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-125">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>

<span data-ttu-id="8f9e7-126"><xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A>Özelliği, tüm geçici dosyaların istemciden kaldırıldığından emin olmak için ek temizleme işlemleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-126">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="8f9e7-127">Xsl: output öğesi ve XmlWriter desteği</span><span class="sxs-lookup"><span data-stu-id="8f9e7-127">Support for the xsl:output Element and XmlWriter</span></span>

<span data-ttu-id="8f9e7-128"><xref:System.Xml.Xsl.XslTransform> `xsl:output` Dönüştürme çıktısı bir nesneye gönderildiğinde, sınıfı yoksayılan ayarları yok sayılır <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-128">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="8f9e7-129"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> <xref:System.Xml.XmlWriterSettings> stil sayfası öğesinden türetilmiş çıkış bilgilerini içeren bir nesne döndüren bir özelliğe sahiptir `xsl:output` .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-129">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="8f9e7-130"><xref:System.Xml.XmlWriterSettings>Nesnesi, <xref:System.Xml.XmlWriter> yöntemine geçirilebilecek doğru ayarlarla bir nesne oluşturmak için kullanılır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-130">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="8f9e7-131">Aşağıdaki C# kodu bu davranışı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8f9e7-131">The following C# code illustrates this behavior:</span></span>

```csharp
// Create the XslTransform object and load the style sheet.
XslCompiledTransform xslt = new XslCompiledTransform();
xslt.Load(stylesheet);

// Load the file to transform.
XPathDocument doc = new XPathDocument(filename);

// Create the writer.
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);

// Transform the file and send the output to the console.
xslt.Transform(doc, writer);
writer.Close();
```

### <a name="debug-option"></a><span data-ttu-id="8f9e7-132">Hata ayıklama seçeneği</span><span class="sxs-lookup"><span data-stu-id="8f9e7-132">Debug Option</span></span>

<span data-ttu-id="8f9e7-133"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıf, Microsoft Visual Studio hata ayıklayıcı ile stil sayfasında hata ayıklamanızı sağlayan hata ayıklama bilgileri oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-133">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft Visual Studio Debugger.</span></span> <span data-ttu-id="8f9e7-134">Daha fazla bilgi edinmek için bkz. <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-134">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="8f9e7-135">Davranış farkları</span><span class="sxs-lookup"><span data-stu-id="8f9e7-135">Behavioral Differences</span></span>

### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="8f9e7-136">XmlReader 'a dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8f9e7-136">Transforming to an XmlReader</span></span>

<span data-ttu-id="8f9e7-137"><xref:System.Xml.Xsl.XslTransform>Sınıfında bir nesne olarak dönüştürme sonuçlarını döndüren birkaç dönüşüm aşırı yüklemesi vardır <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-137">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="8f9e7-138">Bu aşırı yüklemeler, <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> elde edilen XML ağacının serileştirme ve serisini kaldırma yükünü ortadan kaldırmadan, dönüştürme sonuçlarını bellek içi bir gösterimine (veya gibi) yüklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-138">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="8f9e7-139">Aşağıdaki C# kodu, dönüştürme sonuçlarının bir nesnesine nasıl yükleneceğini gösterir <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-139">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<span data-ttu-id="8f9e7-140"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıf, bir nesneye dönüştürmeyi desteklemiyor <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-140">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="8f9e7-141">Ancak, <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> elde EDILEN xml ağacını doğrudan bir öğesinden yüklemek için yöntemini kullanarak benzer bir şey yapabilirsiniz <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-141">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="8f9e7-142">Aşağıdaki C# kodu, kullanılarak aynı görevin nasıl gerçekleştirileceğini gösterir <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-142">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a><span data-ttu-id="8f9e7-143">İsteğe bağlı davranış</span><span class="sxs-lookup"><span data-stu-id="8f9e7-143">Discretionary Behavior</span></span>

<span data-ttu-id="8f9e7-144">W3C XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi, uygulama sağlayıcısının bir durumu nasıl ele verileceğine karar vermesine olanak tanıyan bölgeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-144">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="8f9e7-145">Bu alanların kısıtlı davranış olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-145">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="8f9e7-146"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfından farklı davrandığı birkaç alan vardır <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-146">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="8f9e7-147">Daha fazla bilgi için bkz. [KURTARıLABILIR XSLT hataları](recoverable-xslt-errors.md).</span><span class="sxs-lookup"><span data-stu-id="8f9e7-147">For more information, see [Recoverable XSLT Errors](recoverable-xslt-errors.md).</span></span>

### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="8f9e7-148">Uzantı nesneleri ve betik Işlevleri</span><span class="sxs-lookup"><span data-stu-id="8f9e7-148">Extension Objects and Script Functions</span></span>

<span data-ttu-id="8f9e7-149"><xref:System.Xml.Xsl.XslCompiledTransform> betik işlevlerinin kullanımıyla ilgili iki yeni kısıtlama sunar:</span><span class="sxs-lookup"><span data-stu-id="8f9e7-149"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>

- <span data-ttu-id="8f9e7-150">XPath ifadelerinden yalnızca ortak Yöntemler çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-150">Only public methods may be called from XPath expressions.</span></span>

- <span data-ttu-id="8f9e7-151">Aşırı Yüklemeler, bağımsız değişken sayısına göre birbirinden ayırt edilemez.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-151">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="8f9e7-152">Birden fazla aşırı yükleme aynı sayıda bağımsız değişkene sahipse, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-152">If more than one overload has the same number of arguments, an exception will be raised.</span></span>

<span data-ttu-id="8f9e7-153">' De <xref:System.Xml.Xsl.XslCompiledTransform> , derleme zamanında betik işlevlerine bir bağlama (Yöntem adı araması) oluşur ve XslTransform ile çalışan stil sayfaları, ile yüklendiğinde bir özel duruma neden olabilir <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-153">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTransform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="8f9e7-154"><xref:System.Xml.Xsl.XslCompiledTransform>`msxsl:using` `msxsl:assembly` öğesi içinde ve alt öğelerini destekler `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-154"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="8f9e7-155">`msxsl:using`Ve `msxsl:assembly` öğeleri, komut dosyası bloğunda kullanılmak üzere ek ad alanları ve derlemeler bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-155">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="8f9e7-156">Daha fazla bilgi için bkz. [msxsl: script kullanarak betik blokları](script-blocks-using-msxsl-script.md) .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-156">See [Script Blocks Using msxsl:script](script-blocks-using-msxsl-script.md) for more information.</span></span>

<span data-ttu-id="8f9e7-157"><xref:System.Xml.Xsl.XslCompiledTransform> aynı sayıda bağımsız değişkene sahip birden fazla aşırı yüklemesi olan uzantı nesnelerini yasaklar.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-157"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>

### <a name="msxml-functions"></a><span data-ttu-id="8f9e7-158">MSXML Işlevleri</span><span class="sxs-lookup"><span data-stu-id="8f9e7-158">MSXML Functions</span></span>

<span data-ttu-id="8f9e7-159">Sınıfa ek MSXML işlevleri desteği eklenmiştir <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-159">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="8f9e7-160">Aşağıdaki listede yeni veya geliştirilmiş işlevler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="8f9e7-160">The following list describes new or improved functionality:</span></span>

- <span data-ttu-id="8f9e7-161">msxsl: node-set: <xref:System.Xml.Xsl.XslTransform> [düğüm kümesi işlev](/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) işlevinin bağımsız değişkeni bir sonuç ağacı parçası olacak şekilde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-161">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) function to be a result tree fragment.</span></span> <span data-ttu-id="8f9e7-162"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfta bu gereksinim yoktur.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-162">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>

- <span data-ttu-id="8f9e7-163">msxsl: Version: Bu işlev ' de desteklenir <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-163">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

- <span data-ttu-id="8f9e7-164">XPath uzantı işlevleri: [MS: String-Compare işlevi](/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC işlevi](/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: namespace-uri işlevi](/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: yerel-adı işlevi](/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number işlevi](/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), MS: [Format-Date](/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))işlevi ve [MS: biçim-zamanı işlev](/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) işlevleri artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-164">XPath extension functions: The [ms:string-compare Function](/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc Function](/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri Function](/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name Function](/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number Function](/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date Function](/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)), and [ms:format-time Function](/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) functions are now supported.</span></span>

- <span data-ttu-id="8f9e7-165">Şemaya ilişkin XPath uzantı işlevleri: Bu işlevler tarafından yerel olarak desteklenmez <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="8f9e7-165">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="8f9e7-166">Ancak, uzantı işlevleri olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-166">However, they can be implemented as extension functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f9e7-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f9e7-167">See also</span></span>

- [<span data-ttu-id="8f9e7-168">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="8f9e7-168">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="8f9e7-169">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8f9e7-169">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
