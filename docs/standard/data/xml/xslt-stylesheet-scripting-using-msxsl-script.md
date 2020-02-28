---
title: <msxsl:script> Kullanarak XSLT Stil Sayfası Betiğini Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 9bf57e0f74a353fb6512a24214e9479c1d813aab
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160215"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="3c630-102">\<msxsl: script > kullanarak XSLT stil sayfası betiği oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c630-102">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>
<span data-ttu-id="3c630-103"><xref:System.Xml.Xsl.XslTransform> sınıfı, `script` öğesi kullanılarak gömülü komut dosyalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="3c630-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c630-104"><xref:System.Xml.Xsl.XslTransform> sınıfı, .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3c630-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="3c630-105"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c630-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="3c630-106">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="3c630-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="3c630-107"><xref:System.Xml.Xsl.XslTransform> sınıfı, `script` öğesi kullanılarak gömülü komut dosyalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="3c630-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="3c630-108">Stil sayfası yüklendiğinde, tanımlanmış tüm işlevler bir sınıf tanımına sarmalanarak Microsoft ara dili 'ne (MSIL) derlenir ve sonuç olarak performans kaybı olmaz.</span><span class="sxs-lookup"><span data-stu-id="3c630-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="3c630-109">`<msxsl:script>` öğesi aşağıda tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="3c630-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="3c630-110">Burada `msxsl` ad alanına `urn:schemas-microsoft-com:xslt`bir ön ektir.</span><span class="sxs-lookup"><span data-stu-id="3c630-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="3c630-111">`language` özniteliği zorunlu değildir, ancak belirtilmişse değerinin aşağıdakilerden biri olması gerekir: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`veya `CSharp`.</span><span class="sxs-lookup"><span data-stu-id="3c630-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="3c630-112">Belirtilmemişse, dil varsayılan olarak JScript olur.</span><span class="sxs-lookup"><span data-stu-id="3c630-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="3c630-113">`language-name`, büyük/küçük harfe duyarlı değildir, bu nedenle ' JavaScript ' ve ' JavaScript ' eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="3c630-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="3c630-114">`implements-prefix` özniteliği zorunludur.</span><span class="sxs-lookup"><span data-stu-id="3c630-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="3c630-115">Bu öznitelik, bir ad alanını bildirmek ve betik bloğu ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c630-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="3c630-116">Bu özniteliğin değeri, ad alanını temsil eden önekidir.</span><span class="sxs-lookup"><span data-stu-id="3c630-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="3c630-117">Bu ad alanı, bir stil sayfasında bir yerde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3c630-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="3c630-118">`msxsl:script` öğesi `urn:schemas-microsoft-com:xslt`ad alanına ait olduğundan, stil sayfası, ad alanı bildirimi `xmlns:msxsl=urn:schemas-microsoft-com:xslt`içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3c630-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="3c630-119">Betik çağıranın <xref:System.Security.Permissions.SecurityPermissionFlag> erişim izni yoksa, bir stil sayfasındaki betik hiçbir şekilde derlenmez ve <xref:System.Xml.Xsl.XslTransform.Load%2A> çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3c630-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="3c630-120">Çağıranın `UnmanagedCode` izni varsa, betik derlenir, ancak izin verilen işlemler, yükleme zamanında sağlanan kanıta bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="3c630-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="3c630-121">Stil sayfasını yüklemek için <xref:System.Xml.XmlReader> veya <xref:System.Xml.XPath.XPathNavigator> alan <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemlerinden birini kullanıyorsanız, bağımsız değişkenlerinden biri olarak bir <xref:System.Security.Policy.Evidence> parametresi alan <xref:System.Xml.Xsl.XslTransform.Load%2A> aşırı yüklemeyi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c630-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="3c630-122">Kanıt sağlamak için çağıranın betik derlemesi için `Evidence` sağlaması için <xref:System.Security.Permissions.SecurityPermissionFlag> iznine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c630-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="3c630-123">Çağıranın bu izni yoksa, `Evidence` parametresini `null`olarak ayarlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="3c630-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="3c630-124">Bu, komut dosyası bulursa <xref:System.Xml.Xsl.XslTransform.Load%2A> işlevinin başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3c630-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="3c630-125">`ControlEvidence` izin, yalnızca son derece güvenilen koda verilmesi gereken çok güçlü bir izin olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3c630-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="3c630-126">Derlemeinizden kanıt almak için `this.GetType().Assembly.Evidence`kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c630-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="3c630-127">Bir Tekdüzen Kaynak tanımlayıcısından (URI) kanıt almak için `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c630-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="3c630-128"><xref:System.Xml.XmlResolver> olan ancak `Evidence`olmayan <xref:System.Xml.Xsl.XslTransform.Load%2A> Yöntemler kullanırsanız, derleme için güvenlik bölgesi varsayılan olarak tam güven olur.</span><span class="sxs-lookup"><span data-stu-id="3c630-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="3c630-129">Daha fazla bilgi için bkz. <xref:System.Security.SecurityZone> ve [adlandırılmış Izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3c630-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="3c630-130">İşlevler `msxsl:script` öğesi içinde bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="3c630-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="3c630-131">Aşağıdaki tabloda, varsayılan olarak desteklenen ad alanları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3c630-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="3c630-132">Sınıfları listelenen ad alanları dışında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c630-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="3c630-133">Ancak, bu sınıfların tam nitelikli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c630-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="3c630-134">Varsayılan ad alanları</span><span class="sxs-lookup"><span data-stu-id="3c630-134">Default Namespaces</span></span>|<span data-ttu-id="3c630-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c630-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="3c630-136">Sistem</span><span class="sxs-lookup"><span data-stu-id="3c630-136">System</span></span>|<span data-ttu-id="3c630-137">Sistem sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3c630-137">System class.</span></span>|  
|<span data-ttu-id="3c630-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="3c630-138">System.Collection</span></span>|<span data-ttu-id="3c630-139">Koleksiyon sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3c630-139">Collection classes.</span></span>|  
|<span data-ttu-id="3c630-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="3c630-140">System.Text</span></span>|<span data-ttu-id="3c630-141">Metin sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3c630-141">Text classes.</span></span>|  
|<span data-ttu-id="3c630-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="3c630-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="3c630-143">Normal ifade sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3c630-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="3c630-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="3c630-144">System.Xml</span></span>|<span data-ttu-id="3c630-145">Çekirdek XML sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3c630-145">Core XML classes.</span></span>|  
|<span data-ttu-id="3c630-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="3c630-146">System.Xml.Xsl</span></span>|<span data-ttu-id="3c630-147">XSLT sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3c630-147">XSLT classes.</span></span>|  
|<span data-ttu-id="3c630-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="3c630-148">System.Xml.XPath</span></span>|<span data-ttu-id="3c630-149">XML Path Language (XPath) sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3c630-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="3c630-150">Microsoft. VisualBasic</span><span class="sxs-lookup"><span data-stu-id="3c630-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="3c630-151">Microsoft Visual Basic betikleri için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="3c630-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="3c630-152">Bir işlev bildirildiğinde, bir betik bloğunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="3c630-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="3c630-153">Stil sayfaları, her biri diğerinin bağımsız olarak çalışan birden çok betik bloğu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3c630-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="3c630-154">Diğer bir deyişle, bir betik bloğunun içinde yürütüyorsunuz, aynı ad alanına ve aynı komut dosyası diline sahip olmak üzere bildirilmeden, başka bir betik bloğunda tanımladığınız bir işlevi çağıramadığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3c630-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="3c630-155">Her bir betik bloğu kendi dilinde olabileceğinden ve blok söz konusu dil ayrıştırıcısının dilbilgisi kurallarına göre ayrıştırılacağından, kullanımda olan dil için doğru sözdizimini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c630-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="3c630-156">Örneğin, bir C# betik bloğudur, bloğunda `<!-- an XML comment -->` bir XML açıklama düğümü kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="3c630-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="3c630-157">Sağlanan bağımsız değişkenler ve betik işlevleri tarafından tanımlanan dönüş değerleri World Wide Web Konsorsiyumu (W3C) XPath veya XSLT türlerinden biri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c630-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="3c630-158">Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer .NET Framework sınıfları (türü) ve W3C türünün bir XPath türü veya XSLT türü olup olmadığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3c630-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="3c630-159">Tür</span><span class="sxs-lookup"><span data-stu-id="3c630-159">Type</span></span>|<span data-ttu-id="3c630-160">Eşdeğer .NET Framework sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="3c630-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="3c630-161">XPath türü veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="3c630-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="3c630-162">Dize</span><span class="sxs-lookup"><span data-stu-id="3c630-162">String</span></span>|<span data-ttu-id="3c630-163">System. String</span><span class="sxs-lookup"><span data-stu-id="3c630-163">System.String</span></span>|<span data-ttu-id="3c630-164">XPath</span><span class="sxs-lookup"><span data-stu-id="3c630-164">XPath</span></span>|  
|<span data-ttu-id="3c630-165">Boole</span><span class="sxs-lookup"><span data-stu-id="3c630-165">Boolean</span></span>|<span data-ttu-id="3c630-166">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="3c630-166">System.Boolean</span></span>|<span data-ttu-id="3c630-167">XPath</span><span class="sxs-lookup"><span data-stu-id="3c630-167">XPath</span></span>|  
|<span data-ttu-id="3c630-168">Sayı</span><span class="sxs-lookup"><span data-stu-id="3c630-168">Number</span></span>|<span data-ttu-id="3c630-169">System. Double</span><span class="sxs-lookup"><span data-stu-id="3c630-169">System.Double</span></span>|<span data-ttu-id="3c630-170">XPath</span><span class="sxs-lookup"><span data-stu-id="3c630-170">XPath</span></span>|  
|<span data-ttu-id="3c630-171">Sonuç ağacı parçası</span><span class="sxs-lookup"><span data-stu-id="3c630-171">Result Tree Fragment</span></span>|<span data-ttu-id="3c630-172">System. xml. XPath. XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3c630-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="3c630-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="3c630-173">XSLT</span></span>|  
|<span data-ttu-id="3c630-174">Düğüm kümesi</span><span class="sxs-lookup"><span data-stu-id="3c630-174">Node Set</span></span>|<span data-ttu-id="3c630-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="3c630-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="3c630-176">XPath</span><span class="sxs-lookup"><span data-stu-id="3c630-176">XPath</span></span>|  
  
 <span data-ttu-id="3c630-177">Betik işlevi şu sayısal türlerden birini kullanıyorsa: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single veya Decimal, W3C XPath tür numarasıyla eşlenen Double olarak zorlanır.</span><span class="sxs-lookup"><span data-stu-id="3c630-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="3c630-178">Tüm diğer türler `ToString` yöntemi çağırarak bir dizeye zorlanır.</span><span class="sxs-lookup"><span data-stu-id="3c630-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="3c630-179">Betik işlevi yukarıda belirtilenlerden farklı bir tür kullanıyorsa veya stil sayfası <xref:System.Xml.Xsl.XslTransform> nesnesine yüklendiğinde işlev derlenmezse, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3c630-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="3c630-180">`msxsl:script` öğesi kullanılırken, dilden bağımsız olarak betiğin bir CDATA bölümünün içine yerleştirilmesi kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="3c630-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="3c630-181">Örneğin, aşağıdaki XML, kodunuzun yerleştirildiği CDATA bölümünün şablonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c630-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="3c630-182">Belirli bir dilin işleçleri, tanımlayıcıları veya sınırlandırıcılarının XML olarak yanlış yorumlanmasına sahip olması nedeniyle, tüm betik içeriğinin bir CDATA bölümüne yerleştirilmesi kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="3c630-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="3c630-183">Aşağıdaki örnek, komut dosyasında mantıksal AND işlecinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c630-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="3c630-184">Bu, ve işaretleri hariç olmadığından bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c630-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="3c630-185">Belge XML olarak yüklenir ve `msxsl:script` öğesi etiketleri arasındaki metne özel bir işleme uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="3c630-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c630-186">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c630-186">Example</span></span>  
 <span data-ttu-id="3c630-187">Aşağıdaki örnek, yarıçapı verilen bir dairenin çevresini hesaplamak için gömülü bir betiği kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c630-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="3c630-188">Girdi</span><span class="sxs-lookup"><span data-stu-id="3c630-188">Input</span></span>  
 <span data-ttu-id="3c630-189">Number. xml</span><span class="sxs-lookup"><span data-stu-id="3c630-189">number.xml</span></span>  
  
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
  
 <span data-ttu-id="3c630-190">Calc. Xsl</span><span class="sxs-lookup"><span data-stu-id="3c630-190">calc.xsl</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="3c630-191">Çıktı</span><span class="sxs-lookup"><span data-stu-id="3c630-191">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c630-192">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c630-192">See also</span></span>

- [<span data-ttu-id="3c630-193">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="3c630-193">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
