---
title: "Komut dosyası stil XSLT kullanarak &lt;msxsl: Script&gt;"
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
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 83022c879abe324287d821cec90f65f1865f8281
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a><span data-ttu-id="74f0e-102">Komut dosyası stil XSLT kullanarak &lt;msxsl: Script&gt;</span><span class="sxs-lookup"><span data-stu-id="74f0e-102">XSLT Stylesheet Scripting Using &lt;msxsl:script&gt;</span></span>
<span data-ttu-id="74f0e-103"><xref:System.Xml.Xsl.XslTransform> Sınıfı destekler kullanarak katıştırılmış komut dosyası `script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="74f0e-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74f0e-104"><xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74f0e-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="74f0e-105">Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="74f0e-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="74f0e-106">Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="74f0e-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="74f0e-107"><xref:System.Xml.Xsl.XslTransform> Sınıfı destekler kullanarak katıştırılmış komut dosyası `script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="74f0e-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="74f0e-108">Stil sayfası yüklendiğinde, tanımlı hiçbir işlev Microsoft Ara dili (MSIL) bir sınıf tanımı Sarmalanan tarafından derlenir ve performans kaybı sonuç olarak sahip.</span><span class="sxs-lookup"><span data-stu-id="74f0e-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="74f0e-109">`<msxsl:script>` Öğesi aşağıda tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="74f0e-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="74f0e-110">Burada `msxsl` bir önek ad alanına bağlı `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="74f0e-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="74f0e-111">`language` Özniteliği zorunlu değildir, ancak belirtildiyse, değeri şunlardan biri olmalıdır: C#, VB, JScript, JavaScript, Visualbasic'tir veya CSharp.</span><span class="sxs-lookup"><span data-stu-id="74f0e-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: C#, VB, JScript, JavaScript, VisualBasic, or CSharp.</span></span> <span data-ttu-id="74f0e-112">Belirtilmezse, dil için JScript varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="74f0e-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="74f0e-113">`language-name` 'JavaScript' ve 'javascript' eşdeğer; bu nedenle, küçük harf duyarlıdır değil.</span><span class="sxs-lookup"><span data-stu-id="74f0e-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="74f0e-114">`implements-prefix` Özniteliği zorunludur.</span><span class="sxs-lookup"><span data-stu-id="74f0e-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="74f0e-115">Bu öznitelik, bir ad alanı bildirimini ve betik bloğu ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="74f0e-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="74f0e-116">Bu özniteliğin değeri ad alanını temsil eden önekidir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="74f0e-117">Bu ad, herhangi bir yerde bir stil sayfanızda tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="74f0e-118">Çünkü `msxsl:script` öğenin ait olduğu ad alanına `urn:schemas-microsoft-com:xslt`, stil sayfası ad alanı bildirimi içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="74f0e-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="74f0e-119">Komut dosyasını çağıran yoksa <xref:System.Security.Permissions.SecurityPermissionFlag> erişim izni, stil sayfasında komut dosyası hiçbir zaman derleme sonra ve çağrısı <xref:System.Xml.Xsl.XslTransform.Load%2A> başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="74f0e-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="74f0e-120">Arayan varsa `UnmanagedCode` izni, komut dosyasını derler, ancak izin verilen işlemler, yükleme zamanında sağlanan kanıt bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="74f0e-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="74f0e-121">Aşağıdakilerden birini kullanıyorsanız, <xref:System.Xml.Xsl.XslTransform.Load%2A> ele yöntemleri bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XPath.XPathNavigator> stil sayfası yüklemek için kullanmanız gerekir <xref:System.Xml.Xsl.XslTransform.Load%2A> alan aşırı bir <xref:System.Security.Policy.Evidence> parametre bağımsız değişkenlerinden biri olarak.</span><span class="sxs-lookup"><span data-stu-id="74f0e-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="74f0e-122">Kanıt için arayan olmalıdır <xref:System.Security.Permissions.SecurityPermissionFlag> tedarik izni `Evidence` komut dosyası derleme için.</span><span class="sxs-lookup"><span data-stu-id="74f0e-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="74f0e-123">Çağıranın bu izne sahip değil sonra ayarlayabilirsiniz `Evidence` parametresi `null`.</span><span class="sxs-lookup"><span data-stu-id="74f0e-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="74f0e-124">Bu neden <xref:System.Xml.Xsl.XslTransform.Load%2A> komut dosyası bulursa, başarısız işlev.</span><span class="sxs-lookup"><span data-stu-id="74f0e-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="74f0e-125">`ControlEvidence` İzni yalnızca yüksek oranda güvenilir kodu verilmelidir çok güçlü bir izin olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="74f0e-126">Kanıt, derlemesinden almak için `this.GetType().Assembly.Evidence`.</span><span class="sxs-lookup"><span data-stu-id="74f0e-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="74f0e-127">Bir Tekdüzen Kaynak Tanımlayıcısı (URI) gelen kanıt almak için `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span><span class="sxs-lookup"><span data-stu-id="74f0e-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="74f0e-128">Kullanırsanız <xref:System.Xml.Xsl.XslTransform.Load%2A> ele yöntemleri bir <xref:System.Xml.XmlResolver> ancak hiçbir `Evidence`, güvenlik bölgesi derleme için varsayılan olarak tam güven.</span><span class="sxs-lookup"><span data-stu-id="74f0e-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="74f0e-129">Daha fazla bilgi için bkz: <xref:System.Security.SecurityZone> ve [adlandırılmış izin kümeleri](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="74f0e-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="74f0e-130">İşlevler içinde bildirilebilir `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="74f0e-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="74f0e-131">Aşağıdaki tabloda, varsayılan olarak desteklenen ad alanlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="74f0e-132">Listelenen ad alanlarını dışında sınıflarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74f0e-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="74f0e-133">Ancak, bu sınıfların tam olarak nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74f0e-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="74f0e-134">Varsayılan ad alanları</span><span class="sxs-lookup"><span data-stu-id="74f0e-134">Default Namespaces</span></span>|<span data-ttu-id="74f0e-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74f0e-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="74f0e-136">Sistem</span><span class="sxs-lookup"><span data-stu-id="74f0e-136">System</span></span>|<span data-ttu-id="74f0e-137">Sistem sınıfı.</span><span class="sxs-lookup"><span data-stu-id="74f0e-137">System class.</span></span>|  
|<span data-ttu-id="74f0e-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="74f0e-138">System.Collection</span></span>|<span data-ttu-id="74f0e-139">Koleksiyon sınıfları.</span><span class="sxs-lookup"><span data-stu-id="74f0e-139">Collection classes.</span></span>|  
|<span data-ttu-id="74f0e-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="74f0e-140">System.Text</span></span>|<span data-ttu-id="74f0e-141">Metin sınıflar.</span><span class="sxs-lookup"><span data-stu-id="74f0e-141">Text classes.</span></span>|  
|<span data-ttu-id="74f0e-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="74f0e-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="74f0e-143">Normal ifade sınıfları.</span><span class="sxs-lookup"><span data-stu-id="74f0e-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="74f0e-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="74f0e-144">System.Xml</span></span>|<span data-ttu-id="74f0e-145">Çekirdek XML sınıfları.</span><span class="sxs-lookup"><span data-stu-id="74f0e-145">Core XML classes.</span></span>|  
|<span data-ttu-id="74f0e-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="74f0e-146">System.Xml.Xsl</span></span>|<span data-ttu-id="74f0e-147">XSLT sınıflar.</span><span class="sxs-lookup"><span data-stu-id="74f0e-147">XSLT classes.</span></span>|  
|<span data-ttu-id="74f0e-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="74f0e-148">System.Xml.XPath</span></span>|<span data-ttu-id="74f0e-149">XML Path dili (XPath) sınıfları.</span><span class="sxs-lookup"><span data-stu-id="74f0e-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="74f0e-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="74f0e-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="74f0e-151">Microsoft Visual Basic komut dosyası için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="74f0e-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="74f0e-152">Bir işlev bildirirken bir betik bloğu içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="74f0e-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="74f0e-153">Stil sayfaları, birden çok komut dosyası blokları, diğerinden bağımsız çalışan her içerebilir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="74f0e-154">Bir komut dosyası bloğunun içine çalıştırıldığında, aynı ad ve aynı komut dosyası dili bildirilir sürece, başka bir betik bloğu içinde tanımlanan bir işlev çağıramazsınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="74f0e-155">Her komut dosyası bloğunun kendi dilde olabilir ve bu dil Ayrıştırıcıyı dilbilgisi kurallarına göre blok ayrıştırılır olduğundan, kullanılan dil için doğru sözdizimini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="74f0e-156">C# betik bloğunda varsa, örneğin, ardından bir XML açıklama düğümü kullanılacak hatadır `<!-- an XML comment -->` bloğundaki.</span><span class="sxs-lookup"><span data-stu-id="74f0e-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="74f0e-157">Sağlanan bağımsız değişkenler ve dönüş değerleri komut dosyası işlevleri tarafından tanımlanan World Wide Web Konsorsiyumu (W3C) XPath veya XSLT türlerinden biri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="74f0e-158">Aşağıdaki tabloda W3C türleri karşılık gelen gösterir (tür) eşdeğer .NET Framework sınıfları ve W3C türü olup olmadığını bir XPath türü veya XSLT türü.</span><span class="sxs-lookup"><span data-stu-id="74f0e-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="74f0e-159">Tür</span><span class="sxs-lookup"><span data-stu-id="74f0e-159">Type</span></span>|<span data-ttu-id="74f0e-160">Eşdeğer .NET Framework sınıf (tür)</span><span class="sxs-lookup"><span data-stu-id="74f0e-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="74f0e-161">XPath türü veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="74f0e-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="74f0e-162">Dize</span><span class="sxs-lookup"><span data-stu-id="74f0e-162">String</span></span>|<span data-ttu-id="74f0e-163">System.String</span><span class="sxs-lookup"><span data-stu-id="74f0e-163">System.String</span></span>|<span data-ttu-id="74f0e-164">XPath</span><span class="sxs-lookup"><span data-stu-id="74f0e-164">XPath</span></span>|  
|<span data-ttu-id="74f0e-165">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="74f0e-165">Boolean</span></span>|<span data-ttu-id="74f0e-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="74f0e-166">System.Boolean</span></span>|<span data-ttu-id="74f0e-167">XPath</span><span class="sxs-lookup"><span data-stu-id="74f0e-167">XPath</span></span>|  
|<span data-ttu-id="74f0e-168">Sayı</span><span class="sxs-lookup"><span data-stu-id="74f0e-168">Number</span></span>|<span data-ttu-id="74f0e-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="74f0e-169">System.Double</span></span>|<span data-ttu-id="74f0e-170">XPath</span><span class="sxs-lookup"><span data-stu-id="74f0e-170">XPath</span></span>|  
|<span data-ttu-id="74f0e-171">Sonuç ağacı parçası</span><span class="sxs-lookup"><span data-stu-id="74f0e-171">Result Tree Fragment</span></span>|<span data-ttu-id="74f0e-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="74f0e-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="74f0e-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="74f0e-173">XSLT</span></span>|  
|<span data-ttu-id="74f0e-174">Düğüm kümesi</span><span class="sxs-lookup"><span data-stu-id="74f0e-174">Node Set</span></span>|<span data-ttu-id="74f0e-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="74f0e-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="74f0e-176">XPath</span><span class="sxs-lookup"><span data-stu-id="74f0e-176">XPath</span></span>|  
  
 <span data-ttu-id="74f0e-177">Betik işlevi aşağıdaki sayısal türlerinden birini kullanır,: Int16, UInt16, Int32, UInt32, Int64, UInt64, tek veya ondalık, bunlar zorunlu için çift, hangi W3C XPath türü sayıya eşler.</span><span class="sxs-lookup"><span data-stu-id="74f0e-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="74f0e-178">Tüm diğer türleri çağırarak bir dizeye zorlanır `ToString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="74f0e-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="74f0e-179">Yukarıda belirtilen dışındaki bir türü betik işlevi kullanır veya işlev derlenmez varsa ne zaman stil sayfası yüklendiği içine <xref:System.Xml.Xsl.XslTransform> nesnesi, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="74f0e-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="74f0e-180">Kullanırken `msxsl:script` öğesi, kesinlikle önerilir dil, bağımsız olarak komut içinde CDATA bölümü yerleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="74f0e-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="74f0e-181">Örneğin, aşağıdaki XML kodunuzu nereye yerleştirileceğini CDATA bölümünün şablonu gösterir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="74f0e-182">Operatörler, tanımlayıcılar ya da belirli bir dil için sınırlayıcılar XML olarak yanlış yorumlayan olası olduğundan tüm betik içeriği CDATA bölümünde yerleştirilmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="74f0e-183">Aşağıdaki örnek komut dosyasında mantıksal ve işlecini kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="74f0e-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="74f0e-184">Ve işaretlerini kaçışlı değil çünkü bu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74f0e-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="74f0e-185">Belge XML olarak yüklenir ve özel bir işlemden arasındaki metni uygulanan `msxsl:script` öğe etiketleri.</span><span class="sxs-lookup"><span data-stu-id="74f0e-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74f0e-186">Örnek</span><span class="sxs-lookup"><span data-stu-id="74f0e-186">Example</span></span>  
 <span data-ttu-id="74f0e-187">Aşağıdaki örnek komut dosyası katıştırılmış kendi RADIUS verilen dairenin çevresi hesaplamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="74f0e-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
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
  
   public static void Main() {  
  
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
  
## <a name="input"></a><span data-ttu-id="74f0e-188">Giriş</span><span class="sxs-lookup"><span data-stu-id="74f0e-188">Input</span></span>  
 <span data-ttu-id="74f0e-189">Number.XML</span><span class="sxs-lookup"><span data-stu-id="74f0e-189">number.xml</span></span>  
  
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
  
 <span data-ttu-id="74f0e-190">CALC.xsl</span><span class="sxs-lookup"><span data-stu-id="74f0e-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius){  
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
  
## <a name="output"></a><span data-ttu-id="74f0e-191">Çıkış</span><span class="sxs-lookup"><span data-stu-id="74f0e-191">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74f0e-192">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74f0e-192">See Also</span></span>  
 [<span data-ttu-id="74f0e-193">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="74f0e-193">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
