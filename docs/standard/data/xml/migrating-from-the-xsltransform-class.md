---
title: XslTransform Sınıfından Geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 8383d8cb3e5819c46a0716c59323e492bb9add8e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937985"
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="5c13e-102">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="5c13e-102">Migrating From the XslTransform Class</span></span>

<span data-ttu-id="5c13e-103">XSLT mimarisi, Visual Studio 2005 sürümünde yeniden tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5c13e-103">The XSLT architecture was redesigned in the Visual Studio 2005 release.</span></span> <span data-ttu-id="5c13e-104"><xref:System.Xml.Xsl.XslTransform> Sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfıyla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-104">The <xref:System.Xml.Xsl.XslTransform> class was replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

<span data-ttu-id="5c13e-105">Aşağıdaki bölümlerde, <xref:System.Xml.Xsl.XslCompiledTransform> ve <xref:System.Xml.Xsl.XslTransform> sınıfları arasındaki bazı önemli farklılıklar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="5c13e-105">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>

## <a name="performance"></a><span data-ttu-id="5c13e-106">Performans</span><span class="sxs-lookup"><span data-stu-id="5c13e-106">Performance</span></span>

<span data-ttu-id="5c13e-107"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı birçok performans geliştirmesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="5c13e-108">Yeni XSLT işlemcisi, XSLT stil sayfasını, diğer programlama dilleri için ortak dil çalışma zamanının (CLR) yaptığı gibi ortak bir ara biçimde derler.</span><span class="sxs-lookup"><span data-stu-id="5c13e-108">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="5c13e-109">Stil sayfası derlendikten sonra, önbelleğe alınmış ve yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-109">Once the style sheet is compiled, it can be cached and reused.</span></span>

<span data-ttu-id="5c13e-110"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, <xref:System.Xml.Xsl.XslTransform> sınıfından çok daha hızlı hale gelen diğer iyileştirmeler da içerir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-110">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

> [!NOTE]
> <span data-ttu-id="5c13e-111">Sınıfının genel <xref:System.Xml.Xsl.XslCompiledTransform> performansı <xref:System.Xml.Xsl.XslTransform> sınıfından daha iyidir, ancak <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> <xref:System.Xml.Xsl.XslCompiledTransform> sınıfın yöntemi, bir dönüşümde ilk kez çağrıldığında sınıfının <xref:System.Xml.Xsl.XslTransform.Load%2A> yönteminden <xref:System.Xml.Xsl.XslTransform> daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-111">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="5c13e-112">Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-112">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="5c13e-113">Daha fazla bilgi için şu blog gönderisine bakın: [XslCompiledTransform, XslTransform 'Dan daha yavaş?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span><span class="sxs-lookup"><span data-stu-id="5c13e-113">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>

## <a name="security"></a><span data-ttu-id="5c13e-114">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="5c13e-114">Security</span></span>

<span data-ttu-id="5c13e-115">Varsayılan olarak, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı XSLT `document()` işlevi ve katıştırılmış komut dosyası desteğini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5c13e-115">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="5c13e-116">Bu özellikler, özelliği etkinleştirilmiş ve <xref:System.Xml.Xsl.XsltSettings> <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine geçen bir nesne oluşturularak etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-116">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="5c13e-117">Aşağıdaki örnek, komut dosyasının nasıl etkinleştirileceğini ve XSLT dönüşümünün nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-117">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

<span data-ttu-id="5c13e-118">Daha fazla bilgi için bkz. [XSLT güvenlik konuları](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="5c13e-118">For more information, see [XSLT Security Considerations](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span></span>

## <a name="new-features"></a><span data-ttu-id="5c13e-119">Yeni Özellikler</span><span class="sxs-lookup"><span data-stu-id="5c13e-119">New Features</span></span>

### <a name="temporary-files"></a><span data-ttu-id="5c13e-120">Geçici dosyalar</span><span class="sxs-lookup"><span data-stu-id="5c13e-120">Temporary Files</span></span>

<span data-ttu-id="5c13e-121">Geçici dosyalar bazen XSLT işleme sırasında üretilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-121">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="5c13e-122">Bir stil sayfası betik blokları içeriyorsa veya hata ayıklama ayarı true olarak ayarlandıysa derlenmiş ise, geçici dosyalar% TEMP% klasöründe oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-122">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="5c13e-123">Zamanlama sorunları nedeniyle bazı geçici dosyalar silinmediği durumlarda örnek olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-123">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="5c13e-124">Örneğin, dosyalar geçerli AppDomain veya hata ayıklayıcı tarafından kullanılıyorsa, <xref:System.CodeDom.Compiler.TempFileCollection> nesne sonlandırıcısı bunları kaldıramayacak.</span><span class="sxs-lookup"><span data-stu-id="5c13e-124">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>

<span data-ttu-id="5c13e-125"><xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Özelliği, tüm geçici dosyaların istemciden kaldırıldığından emin olmak için ek temizleme işlemleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-125">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="5c13e-126">Xsl: output öğesi ve XmlWriter desteği</span><span class="sxs-lookup"><span data-stu-id="5c13e-126">Support for the xsl:output Element and XmlWriter</span></span>

<span data-ttu-id="5c13e-127">Dönüştürme <xref:System.Xml.Xsl.XslTransform> çıktısı bir `xsl:output` <xref:System.Xml.XmlWriter> nesneye gönderildiğinde, sınıfı yoksayılan ayarları yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="5c13e-127">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="5c13e-128"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, stil sayfası <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> `xsl:output` öğesinden türetilmiş çıkış bilgilerini <xref:System.Xml.XmlWriterSettings> içeren bir nesne döndüren bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-128">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="5c13e-129"><xref:System.Xml.XmlWriterSettings> Nesnesi, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirilebilecek doğru ayarlarla bir <xref:System.Xml.XmlWriter> nesne oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c13e-129">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="5c13e-130">Aşağıdaki C# kodu bu davranışı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5c13e-130">The following C# code illustrates this behavior:</span></span>

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

### <a name="debug-option"></a><span data-ttu-id="5c13e-131">Hata ayıklama seçeneği</span><span class="sxs-lookup"><span data-stu-id="5c13e-131">Debug Option</span></span>

<span data-ttu-id="5c13e-132"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıf, Microsoft Visual Studio hata ayıklayıcı ile stil sayfasında hata ayıklamanızı sağlayan hata ayıklama bilgileri oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-132">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft Visual Studio Debugger.</span></span> <span data-ttu-id="5c13e-133">Daha fazla bilgi edinmek için bkz. <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="5c13e-133">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="5c13e-134">Davranış farkları</span><span class="sxs-lookup"><span data-stu-id="5c13e-134">Behavioral Differences</span></span>

### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="5c13e-135">XmlReader 'a dönüştürme</span><span class="sxs-lookup"><span data-stu-id="5c13e-135">Transforming to an XmlReader</span></span>

<span data-ttu-id="5c13e-136"><xref:System.Xml.Xsl.XslTransform> Sınıfında bir <xref:System.Xml.XmlReader> nesne olarak dönüştürme sonuçlarını döndüren birkaç dönüşüm aşırı yüklemesi vardır.</span><span class="sxs-lookup"><span data-stu-id="5c13e-136">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="5c13e-137">Bu aşırı yüklemeler, elde edilen XML ağacının serileştirme ve serisini kaldırma yükünü ortadan kaldırmadan, dönüştürme sonuçlarını bellek <xref:System.Xml.XmlDocument> içi <xref:System.Xml.XPath.XPathDocument>bir gösterimine (veya gibi) yüklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-137">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="5c13e-138">Aşağıdaki C# kodu, dönüştürme sonuçlarının bir <xref:System.Xml.XmlDocument> nesnesine nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-138">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<span data-ttu-id="5c13e-139">Sınıf <xref:System.Xml.Xsl.XslCompiledTransform> , bir <xref:System.Xml.XmlReader> nesneye dönüştürmeyi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="5c13e-139">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="5c13e-140">Ancak, elde edilen XML ağacını doğrudan bir <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> <xref:System.Xml.XmlWriter>öğesinden yüklemek için yöntemini kullanarak benzer bir şey yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c13e-140">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="5c13e-141">Aşağıdaki C# kodu, kullanılarak <xref:System.Xml.Xsl.XslCompiledTransform>aynı görevin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-141">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a><span data-ttu-id="5c13e-142">İsteğe bağlı davranış</span><span class="sxs-lookup"><span data-stu-id="5c13e-142">Discretionary Behavior</span></span>

<span data-ttu-id="5c13e-143">W3C XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi, uygulama sağlayıcısının bir durumu nasıl ele verileceğine karar vermesine olanak tanıyan bölgeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-143">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="5c13e-144">Bu alanların kısıtlı davranış olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-144">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="5c13e-145"><xref:System.Xml.Xsl.XslTransform> Sınıfından farklı <xref:System.Xml.Xsl.XslCompiledTransform> davrandığı birkaç alan vardır.</span><span class="sxs-lookup"><span data-stu-id="5c13e-145">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="5c13e-146">Daha fazla bilgi için bkz. [KURTARıLABILIR XSLT hataları](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span><span class="sxs-lookup"><span data-stu-id="5c13e-146">For more information, see [Recoverable XSLT Errors](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span></span>

### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="5c13e-147">Uzantı nesneleri ve betik Işlevleri</span><span class="sxs-lookup"><span data-stu-id="5c13e-147">Extension Objects and Script Functions</span></span>

<span data-ttu-id="5c13e-148"><xref:System.Xml.Xsl.XslCompiledTransform>betik işlevlerinin kullanımıyla ilgili iki yeni kısıtlama sunar:</span><span class="sxs-lookup"><span data-stu-id="5c13e-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>

- <span data-ttu-id="5c13e-149">XPath ifadelerinden yalnızca ortak Yöntemler çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-149">Only public methods may be called from XPath expressions.</span></span>

- <span data-ttu-id="5c13e-150">Aşırı Yüklemeler, bağımsız değişken sayısına göre birbirinden ayırt edilemez.</span><span class="sxs-lookup"><span data-stu-id="5c13e-150">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="5c13e-151">Birden fazla aşırı yükleme aynı sayıda bağımsız değişkene sahipse, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5c13e-151">If more than one overload has the same number of arguments, an exception will be raised.</span></span>

<span data-ttu-id="5c13e-152">' <xref:System.Xml.Xsl.XslCompiledTransform>De, derleme zamanında betik işlevlerine bir bağlama (Yöntem adı araması) oluşur ve XslTransform ile çalışan stil sayfaları, ile <xref:System.Xml.Xsl.XslCompiledTransform>yüklendiğinde bir özel duruma neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-152">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTransform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="5c13e-153"><xref:System.Xml.Xsl.XslCompiledTransform>öğesi içinde `msxsl:using` ve `msxsl:assembly` alt öğelerini destekler. `msxsl:script`</span><span class="sxs-lookup"><span data-stu-id="5c13e-153"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="5c13e-154">`msxsl:using` Ve `msxsl:assembly` öğeleri, komut dosyası bloğunda kullanılmak üzere ek ad alanları ve derlemeler bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c13e-154">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="5c13e-155">Daha fazla bilgi için bkz. [msxsl: script kullanarak betik blokları](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) .</span><span class="sxs-lookup"><span data-stu-id="5c13e-155">See [Script Blocks Using msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) for more information.</span></span>

<span data-ttu-id="5c13e-156"><xref:System.Xml.Xsl.XslCompiledTransform>aynı sayıda bağımsız değişkene sahip birden fazla aşırı yüklemesi olan uzantı nesnelerini yasaklar.</span><span class="sxs-lookup"><span data-stu-id="5c13e-156"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>

### <a name="msxml-functions"></a><span data-ttu-id="5c13e-157">MSXML Işlevleri</span><span class="sxs-lookup"><span data-stu-id="5c13e-157">MSXML Functions</span></span>

<span data-ttu-id="5c13e-158"><xref:System.Xml.Xsl.XslCompiledTransform> SıNıFA ek MSXML işlevleri desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-158">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="5c13e-159">Aşağıdaki listede yeni veya geliştirilmiş işlevler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="5c13e-159">The following list describes new or improved functionality:</span></span>

- <span data-ttu-id="5c13e-160">msxsl: node-set: <xref:System.Xml.Xsl.XslTransform> [düğüm kümesi işlev](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) işlevinin bağımsız değişkeni bir sonuç ağacı parçası olacak şekilde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) function to be a result tree fragment.</span></span> <span data-ttu-id="5c13e-161"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfta bu gereksinim yoktur.</span><span class="sxs-lookup"><span data-stu-id="5c13e-161">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>

- <span data-ttu-id="5c13e-162">msxsl: Version: Bu işlev ' de <xref:System.Xml.Xsl.XslCompiledTransform>desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-162">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

- <span data-ttu-id="5c13e-163">XPath uzantı işlevleri: [MS: String-Compare işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: namespace-uri işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: yerel-adı işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), MS: [Format-Date](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))işlevi ve [MS: biçim-zamanı işlev](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) işlevleri artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-163">XPath extension functions: The [ms:string-compare Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)), and [ms:format-time Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) functions are now supported.</span></span>

- <span data-ttu-id="5c13e-164">Şemaya ilişkin XPath uzantı işlevleri: Bu işlevler tarafından yerel olarak <xref:System.Xml.Xsl.XslCompiledTransform>desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5c13e-164">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="5c13e-165">Ancak, uzantı işlevleri olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-165">However, they can be implemented as extension functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c13e-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c13e-166">See also</span></span>

- [<span data-ttu-id="5c13e-167">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="5c13e-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
- [<span data-ttu-id="5c13e-168">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="5c13e-168">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
