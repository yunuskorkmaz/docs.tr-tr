---
description: 'Hakkında daha fazla bilgi için bkz. <msxsl: Script> kullanarak XSLT stil sayfası betiği'
title: <msxsl:script> Kullanarak XSLT Stil Sayfası Betiğini Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 4ed2caf5b31fb5a6494c294b2619535699e09905
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731987"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="cc6e3-103">Kullanarak XSLT stil sayfası betiği oluşturma \<msxsl:script></span><span class="sxs-lookup"><span data-stu-id="cc6e3-103">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>

<span data-ttu-id="cc6e3-104"><xref:System.Xml.Xsl.XslTransform>Sınıfı, öğesini kullanarak gömülü komut dosyalarını destekler `script` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-104">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc6e3-105"><xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="cc6e3-106">Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="cc6e3-107">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="cc6e3-108"><xref:System.Xml.Xsl.XslTransform>Sınıfı, öğesini kullanarak gömülü komut dosyalarını destekler `script` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-108">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="cc6e3-109">Stil sayfası yüklendiğinde, tanımlanmış tüm işlevler bir sınıf tanımına sarmalanarak Microsoft ara dili 'ne (MSIL) derlenir ve sonuç olarak performans kaybı olmaz.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-109">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="cc6e3-110">`<msxsl:script>`Öğe aşağıda tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="cc6e3-110">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="cc6e3-111">, `msxsl` ad alanına göre bir ön ek olur `urn:schemas-microsoft-com:xslt` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-111">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="cc6e3-112">`language`Özniteliği zorunlu değildir, ancak belirtilmişse değeri şunlardan biri olmalıdır: `C#` , `VB` ,, `JScript` `JavaScript` , `VisualBasic` veya `CSharp` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-112">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="cc6e3-113">Belirtilmemişse, dil varsayılan olarak JScript olur.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-113">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="cc6e3-114">`language-name`Büyük/küçük harfe duyarlı değildir, bu nedenle ' JavaScript ' ve ' JavaScript ' eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-114">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="cc6e3-115">`implements-prefix`Özniteliği zorunludur.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-115">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="cc6e3-116">Bu öznitelik, bir ad alanını bildirmek ve betik bloğu ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-116">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="cc6e3-117">Bu özniteliğin değeri, ad alanını temsil eden önekidir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-117">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="cc6e3-118">Bu ad alanı, bir stil sayfasında bir yerde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-118">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="cc6e3-119">`msxsl:script`Öğesi ad alanına ait olduğundan `urn:schemas-microsoft-com:xslt` , stil sayfası ad alanı bildirimini içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-119">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="cc6e3-120">Komut dosyası çağıranın <xref:System.Security.Permissions.SecurityPermissionFlag> erişim izni yoksa, bir stil sayfasındaki betiği hiçbir şekilde derlenmez ve çağrısı <xref:System.Xml.Xsl.XslTransform.Load%2A> başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-120">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="cc6e3-121">Çağıranın `UnmanagedCode` izni varsa, komut dosyası derlenir, ancak izin verilen işlemler, yükleme zamanında sağlanan kanıta bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-121">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="cc6e3-122"><xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.XmlReader> Stil sayfasını yüklemek veya içeren yöntemlerden birini kullanıyorsanız <xref:System.Xml.XPath.XPathNavigator> , <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Security.Policy.Evidence> bağımsız değişkenlerinden biri olarak bir parametre alan aşırı yüklemeyi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-122">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="cc6e3-123">Kanıt sağlamak için çağıranın <xref:System.Security.Permissions.SecurityPermissionFlag> betik derlemesini sağlama izni olması gerekir `Evidence` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-123">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="cc6e3-124">Çağıranın bu izni yoksa, `Evidence` parametresini olarak ayarlayabilirler `null` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-124">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="cc6e3-125">Bu, <xref:System.Xml.Xsl.XslTransform.Load%2A> komut dosyası bulursa işlevin başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-125">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="cc6e3-126">`ControlEvidence`İzin, yalnızca son derece güvenilen koda verilmesi gereken çok güçlü bir izin olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-126">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="cc6e3-127">Derlemeinizden kanıt almak için kullanın `this.GetType().Assembly.Evidence` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-127">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="cc6e3-128">Bir Tekdüzen Kaynak tanımlayıcısından (URI) kanıt almak için kullanın `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-128">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="cc6e3-129"><xref:System.Xml.Xsl.XslTransform.Load%2A>Ancak Hayır alan yöntemler kullanıyorsanız <xref:System.Xml.XmlResolver> `Evidence` , derleme için güvenlik bölgesi varsayılan olarak tam güven olur.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-129">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="cc6e3-130">Daha fazla bilgi için bkz <xref:System.Security.SecurityZone> . ve [adlandırılmış izin kümeleri](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cc6e3-130">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="cc6e3-131">İşlevler, öğesi içinde bildirilebilecek `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-131">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="cc6e3-132">Aşağıdaki tabloda, varsayılan olarak desteklenen ad alanları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-132">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="cc6e3-133">Sınıfları listelenen ad alanları dışında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-133">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="cc6e3-134">Ancak, bu sınıfların tam nitelikli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-134">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="cc6e3-135">Varsayılan ad alanları</span><span class="sxs-lookup"><span data-stu-id="cc6e3-135">Default Namespaces</span></span>|<span data-ttu-id="cc6e3-136">Description</span><span class="sxs-lookup"><span data-stu-id="cc6e3-136">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="cc6e3-137">Sistem</span><span class="sxs-lookup"><span data-stu-id="cc6e3-137">System</span></span>|<span data-ttu-id="cc6e3-138">Sistem sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-138">System class.</span></span>|  
|<span data-ttu-id="cc6e3-139">System.Collection</span><span class="sxs-lookup"><span data-stu-id="cc6e3-139">System.Collection</span></span>|<span data-ttu-id="cc6e3-140">Koleksiyon sınıfları.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-140">Collection classes.</span></span>|  
|<span data-ttu-id="cc6e3-141">System.Text</span><span class="sxs-lookup"><span data-stu-id="cc6e3-141">System.Text</span></span>|<span data-ttu-id="cc6e3-142">Metin sınıfları.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-142">Text classes.</span></span>|  
|<span data-ttu-id="cc6e3-143">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="cc6e3-143">System.Text.RegularExpressions</span></span>|<span data-ttu-id="cc6e3-144">Normal ifade sınıfları.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-144">Regular expression classes.</span></span>|  
|<span data-ttu-id="cc6e3-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="cc6e3-145">System.Xml</span></span>|<span data-ttu-id="cc6e3-146">Çekirdek XML sınıfları.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-146">Core XML classes.</span></span>|  
|<span data-ttu-id="cc6e3-147">System.Xml. Xls</span><span class="sxs-lookup"><span data-stu-id="cc6e3-147">System.Xml.Xsl</span></span>|<span data-ttu-id="cc6e3-148">XSLT sınıfları.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-148">XSLT classes.</span></span>|  
|<span data-ttu-id="cc6e3-149">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="cc6e3-149">System.Xml.XPath</span></span>|<span data-ttu-id="cc6e3-150">XML Path Language (XPath) sınıfları.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-150">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="cc6e3-151">Microsoft. VisualBasic</span><span class="sxs-lookup"><span data-stu-id="cc6e3-151">Microsoft.VisualBasic</span></span>|<span data-ttu-id="cc6e3-152">Microsoft Visual Basic betikleri için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-152">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="cc6e3-153">Bir işlev bildirildiğinde, bir betik bloğunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-153">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="cc6e3-154">Stil sayfaları, her biri diğerinin bağımsız olarak çalışan birden çok betik bloğu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-154">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="cc6e3-155">Diğer bir deyişle, bir betik bloğunun içinde yürütüyorsunuz, aynı ad alanına ve aynı komut dosyası diline sahip olmak üzere bildirilmeden, başka bir betik bloğunda tanımladığınız bir işlevi çağıramadığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-155">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="cc6e3-156">Her bir betik bloğu kendi dilinde olabileceğinden ve blok söz konusu dil ayrıştırıcısının dilbilgisi kurallarına göre ayrıştırılacağından, kullanımda olan dil için doğru sözdizimini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-156">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="cc6e3-157">Örneğin, bir C# komut dosyası bloğunda, bloğunda bir XML açıklama düğümü kullanılması hatadır `<!-- an XML comment -->` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-157">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="cc6e3-158">Sağlanan bağımsız değişkenler ve betik işlevleri tarafından tanımlanan dönüş değerleri World Wide Web Konsorsiyumu (W3C) XPath veya XSLT türlerinden biri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-158">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="cc6e3-159">Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer .NET Framework sınıfları (türü) ve W3C türünün bir XPath türü veya XSLT türü olup olmadığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-159">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="cc6e3-160">Tür</span><span class="sxs-lookup"><span data-stu-id="cc6e3-160">Type</span></span>|<span data-ttu-id="cc6e3-161">Eşdeğer .NET Framework sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="cc6e3-161">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="cc6e3-162">XPath türü veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="cc6e3-162">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="cc6e3-163">Dize</span><span class="sxs-lookup"><span data-stu-id="cc6e3-163">String</span></span>|<span data-ttu-id="cc6e3-164">System. String</span><span class="sxs-lookup"><span data-stu-id="cc6e3-164">System.String</span></span>|<span data-ttu-id="cc6e3-165">XPath</span><span class="sxs-lookup"><span data-stu-id="cc6e3-165">XPath</span></span>|  
|<span data-ttu-id="cc6e3-166">Boole</span><span class="sxs-lookup"><span data-stu-id="cc6e3-166">Boolean</span></span>|<span data-ttu-id="cc6e3-167">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="cc6e3-167">System.Boolean</span></span>|<span data-ttu-id="cc6e3-168">XPath</span><span class="sxs-lookup"><span data-stu-id="cc6e3-168">XPath</span></span>|  
|<span data-ttu-id="cc6e3-169">Sayı</span><span class="sxs-lookup"><span data-stu-id="cc6e3-169">Number</span></span>|<span data-ttu-id="cc6e3-170">System. Double</span><span class="sxs-lookup"><span data-stu-id="cc6e3-170">System.Double</span></span>|<span data-ttu-id="cc6e3-171">XPath</span><span class="sxs-lookup"><span data-stu-id="cc6e3-171">XPath</span></span>|  
|<span data-ttu-id="cc6e3-172">Sonuç ağacı parçası</span><span class="sxs-lookup"><span data-stu-id="cc6e3-172">Result Tree Fragment</span></span>|<span data-ttu-id="cc6e3-173">System.Xml. XPath. XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cc6e3-173">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="cc6e3-174">XSLT</span><span class="sxs-lookup"><span data-stu-id="cc6e3-174">XSLT</span></span>|  
|<span data-ttu-id="cc6e3-175">Düğüm kümesi</span><span class="sxs-lookup"><span data-stu-id="cc6e3-175">Node Set</span></span>|<span data-ttu-id="cc6e3-176">System.Xml. XPath. XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="cc6e3-176">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="cc6e3-177">XPath</span><span class="sxs-lookup"><span data-stu-id="cc6e3-177">XPath</span></span>|  
  
 <span data-ttu-id="cc6e3-178">Betik işlevi şu sayısal türlerden birini kullanıyorsa: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single veya Decimal, W3C XPath tür numarasıyla eşlenen Double olarak zorlanır.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-178">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="cc6e3-179">Tüm diğer türler, yöntemi çağırarak bir dizeye zorlanır `ToString` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-179">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="cc6e3-180">Betik işlevi yukarıda bahsedilen olanlardan farklı bir tür kullanıyorsa veya işlev, nesne içine yüklendiğinde işlev derlenmezse, <xref:System.Xml.Xsl.XslTransform> bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-180">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="cc6e3-181">`msxsl:script`Öğesi kullanılırken, dilden bağımsız olarak betiğin BIR CDATA bölümünün içine yerleştirilmesi kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-181">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="cc6e3-182">Örneğin, aşağıdaki XML, kodunuzun yerleştirildiği CDATA bölümünün şablonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-182">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="cc6e3-183">Belirli bir dilin işleçleri, tanımlayıcıları veya sınırlandırıcılarının XML olarak yanlış yorumlanmasına sahip olması nedeniyle, tüm betik içeriğinin bir CDATA bölümüne yerleştirilmesi kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-183">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="cc6e3-184">Aşağıdaki örnek, komut dosyasında mantıksal AND işlecinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-184">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="cc6e3-185">Bu, ve işaretleri hariç olmadığından bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-185">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="cc6e3-186">Belge XML olarak yüklenir ve öğe etiketleri arasındaki metne özel bir işleme uygulanmaz `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="cc6e3-186">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc6e3-187">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc6e3-187">Example</span></span>  

 <span data-ttu-id="cc6e3-188">Aşağıdaki örnek, yarıçapı verilen bir dairenin çevresini hesaplamak için gömülü bir betiği kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-188">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a><span data-ttu-id="cc6e3-189">Giriş</span><span class="sxs-lookup"><span data-stu-id="cc6e3-189">Input</span></span>  

 <span data-ttu-id="cc6e3-190">number.xml</span><span class="sxs-lookup"><span data-stu-id="cc6e3-190">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="cc6e3-191">Calc. Xsl</span><span class="sxs-lookup"><span data-stu-id="cc6e3-191">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="cc6e3-192">Çıktı</span><span class="sxs-lookup"><span data-stu-id="cc6e3-192">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>
```  
  
## <a name="see-also"></a><span data-ttu-id="cc6e3-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc6e3-193">See also</span></span>

- [<span data-ttu-id="cc6e3-194">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="cc6e3-194">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
