---
title: 'Komut dosyası blokları msxsl: Script kullanan'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4d7dee9ebaed20970f715026661c29aae701289
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970636"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="bbd49-102">Komut dosyası blokları msxsl: Script kullanan</span><span class="sxs-lookup"><span data-stu-id="bbd49-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="bbd49-103"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı kullanarak katıştırılmış betikleri destekler `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bbd49-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="bbd49-104">Stil sayfası yüklendiğinde, herhangi bir tanımlı işlevlere kod belge nesne modeli (CodeDOM) tarafından derlenmiş Microsoft Ara dili (MSIL) ve çalışma zamanı sırasında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="bbd49-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="bbd49-105">Katıştırılmış betik bloğundan oluşturulan derleme, stil sayfası için oluşturulan derlemesinden ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="bbd49-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="bbd49-106">XSLT betik etkinleştir</span><span class="sxs-lookup"><span data-stu-id="bbd49-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="bbd49-107">Gömülü betikler için destek etkin isteğe bağlı bir XSLT ayar <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bbd49-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="bbd49-108">Betik desteği, varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="bbd49-108">Script support is disabled by default.</span></span> <span data-ttu-id="bbd49-109">Betik desteği etkinleştirmek için oluşturun bir <xref:System.Xml.Xsl.XsltSettings> nesnesi ile <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> özelliğini `true` ve nesneyi geçirin <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bbd49-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbd49-110">XSLT betik yalnızca betik desteği gerektiriyorsa ve tam olarak güvenilen bir ortamda çalışıyorsanız etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="bbd49-111">msxsl: Script öğesi tanımı</span><span class="sxs-lookup"><span data-stu-id="bbd49-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="bbd49-112">`msxsl:script` Öğesi XSLT 1.0 öneri bir Microsoft uzantısıdır ve aşağıdaki tanımları içerir:</span><span class="sxs-lookup"><span data-stu-id="bbd49-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="bbd49-113">`msxsl` İçin bağlı öneki `urn:schemas-microsoft-com:xslt` ad alanı URI.</span><span class="sxs-lookup"><span data-stu-id="bbd49-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="bbd49-114">Stil sayfası içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt` ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="bbd49-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="bbd49-115">`language` İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bbd49-115">The `language` attribute is optional.</span></span> <span data-ttu-id="bbd49-116">Değerini, gömülü kod bloğunun kod dilidir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="bbd49-117">Dil uygun CodeDOM derleyici kullanmayı eşlenir <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bbd49-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bbd49-118"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı uygun sağlayıcıyı makineye yüklenir ve machine.config dosyasının system.codedom bölümünde kayıtlı olduğundan, herhangi bir Microsoft .NET dil destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="bbd49-119">Varsa bir `language` özniteliği belirtilmezse, dil Varsayılanları JScript için.</span><span class="sxs-lookup"><span data-stu-id="bbd49-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="bbd49-120">Dil adı büyük küçük harfe duyarlı değil 'JavaScript' ve 'javascript' eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="bbd49-121">`implements-prefix` Özniteliği zorunludur.</span><span class="sxs-lookup"><span data-stu-id="bbd49-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="bbd49-122">Bu öznitelik, bir ad alanı bildirin ve komut dosyası bloğu ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbd49-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="bbd49-123">Bu özniteliğin değeri ad alanını temsil eden önekidir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="bbd49-124">Bu ön ek bir yerde bir stil sayfası içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbd49-125">Kullanırken `msxsl:script` öğesi öneririz, diline bakılmaksızın komut içindeki CDATA bölümüne yerleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="bbd49-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="bbd49-126">Bir CDATA bölümde yer bulunmuyorsa betik operatörler, tanımlayıcılar ya da belirli bir dil için sınırlayıcılar içerebileceği için XML olarak yanlış olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="bbd49-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="bbd49-127">Aşağıdaki XML kodu nereye yerleştirilmesi CDATA bölümünün bir şablon gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="bbd49-128">Betik işlevleri</span><span class="sxs-lookup"><span data-stu-id="bbd49-128">Script Functions</span></span>  
 <span data-ttu-id="bbd49-129">İşlevler içinde bildirilebilir `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bbd49-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="bbd49-130">Bildirilen bir işlev, bir komut dosyası bloğu içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="bbd49-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="bbd49-131">Stil sayfaları, birden çok komut dosyası blokları, diğerinden bağımsız çalışan her içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="bbd49-132">Bir betik bloğu içinde yürütülen, aynı ad ve aynı komut dosyası dili bildirildiği sürece başka bir betik bloğu içinde tanımlanan bir işlev çağrısı yapamazsınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="bbd49-133">Her komut dosyası bloğu kendi dilinde olabilir ve blok o dil ayrıştırıcı dilbilgisi kurallara göre ayrıştırılır çünkü dili kullanmak için doğru sözdizimi kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="bbd49-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="bbd49-134">Örneğin, bir Microsoft C# betik bloğu içinde varsa, C# yorum sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bbd49-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="bbd49-135">Sağlanan bağımsız değişkenler ve dönüş değerleri işlevi herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="bbd49-136">W3C XPath türlerde ortak dil çalışma zamanı (CLR) türlerinin bir alt kümesi olduğundan, tür dönüştürme bir XPath türü olmasını dikkate alınmaz türleri üzerinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="bbd49-137">Aşağıdaki tablo W3C türleri ve karşılık gelen ve eşdeğer CLR türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="bbd49-138">W3C türü</span><span class="sxs-lookup"><span data-stu-id="bbd49-138">W3C type</span></span>|<span data-ttu-id="bbd49-139">CLR türü</span><span class="sxs-lookup"><span data-stu-id="bbd49-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="bbd49-140">CLR sayısal türleri dönüştürülür <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="bbd49-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="bbd49-141"><xref:System.DateTime> Türüne dönüştürülür <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bbd49-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="bbd49-142"><xref:System.Xml.XPath.IXPathNavigable> türleri dönüştürülür <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="bbd49-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="bbd49-143">**XPathNavigator []** dönüştürülür <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="bbd49-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="bbd49-144">Diğer tüm türlerin bir hata atar.</span><span class="sxs-lookup"><span data-stu-id="bbd49-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="bbd49-145">Ad alanları ve derlemeler alınıyor</span><span class="sxs-lookup"><span data-stu-id="bbd49-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="bbd49-146"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı önceden belirler, derlemeleri ve varsayılan olarak tarafından desteklenen ad alanları kümesi `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bbd49-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="bbd49-147">Ancak, sınıflar ve üyeler derlemenin ve ad alanındaki içeri aktararak önceden tanımlanmış listede olmayan bir ad alanına ait kullanabilirsiniz `msxsl:script` blok.</span><span class="sxs-lookup"><span data-stu-id="bbd49-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="bbd49-148">Derlemeleri</span><span class="sxs-lookup"><span data-stu-id="bbd49-148">Assemblies</span></span>  
 <span data-ttu-id="bbd49-149">Varsayılan olarak aşağıdaki iki derlemelerini başvurulan:</span><span class="sxs-lookup"><span data-stu-id="bbd49-149">The following two assemblies are referenced by default:</span></span>  
  
-   <span data-ttu-id="bbd49-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="bbd49-150">System.dll</span></span>  
  
-   <span data-ttu-id="bbd49-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="bbd49-151">System.Xml.dll</span></span>  
  
-   <span data-ttu-id="bbd49-152">(Komut dosyası dili VB olduğunda) Microsoft.VisualBasic.dll içinde</span><span class="sxs-lookup"><span data-stu-id="bbd49-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="bbd49-153">Ek bütünleştirilmiş kodları kullanarak içeri aktarabilirsiniz `msxsl:assembly` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bbd49-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="bbd49-154">Bu, stil sayfası derlendiğinde derleme içerir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="bbd49-155">`msxsl:assembly` Öğesinin aşağıdaki tanımı:</span><span class="sxs-lookup"><span data-stu-id="bbd49-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="bbd49-156">`name` Özniteliği, derlemenin adını içerir ve `href` özniteliği derleme yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="bbd49-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="bbd49-157">Derleme adı gibi tam bir ad olabilir "System.Data, sürüm 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", veya "System.Web" gibi kısa bir ad.</span><span class="sxs-lookup"><span data-stu-id="bbd49-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="bbd49-158">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="bbd49-158">Namespaces</span></span>  
 <span data-ttu-id="bbd49-159">Aşağıdaki ad alanları, varsayılan olarak dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bbd49-159">The following namespaces are included by default:</span></span>  
  
-   <span data-ttu-id="bbd49-160">Sistem</span><span class="sxs-lookup"><span data-stu-id="bbd49-160">System</span></span>  
  
-   <span data-ttu-id="bbd49-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="bbd49-161">System.Collection</span></span>  
  
-   <span data-ttu-id="bbd49-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="bbd49-162">System.Text</span></span>  
  
-   <span data-ttu-id="bbd49-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="bbd49-163">System.Text.RegularExpressions</span></span>  
  
-   <span data-ttu-id="bbd49-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="bbd49-164">System.Xml</span></span>  
  
-   <span data-ttu-id="bbd49-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="bbd49-165">System.Xml.Xsl</span></span>  
  
-   <span data-ttu-id="bbd49-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="bbd49-166">System.Xml.XPath</span></span>  
  
-   <span data-ttu-id="bbd49-167">(Komut dosyası dili VB olduğunda) Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="bbd49-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="bbd49-168">Ek ad alanlarını kullanma için destek ekleyebilirsiniz `namespace` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bbd49-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="bbd49-169">Öznitelik değeri, ad alanının adıdır.</span><span class="sxs-lookup"><span data-stu-id="bbd49-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="bbd49-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbd49-170">Example</span></span>  
 <span data-ttu-id="bbd49-171">Aşağıdaki örnek bir katıştırılmış betik, RADIUS verilmiş bir daire çevresi hesaplamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbd49-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="bbd49-172">Number.XML</span><span class="sxs-lookup"><span data-stu-id="bbd49-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="bbd49-173">CALC.xsl</span><span class="sxs-lookup"><span data-stu-id="bbd49-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="bbd49-174">Çıkış</span><span class="sxs-lookup"><span data-stu-id="bbd49-174">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bbd49-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbd49-175">See also</span></span>

- [<span data-ttu-id="bbd49-176">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="bbd49-176">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [<span data-ttu-id="bbd49-177">Dinamik Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="bbd49-177">Dynamic Source Code Generation and Compilation</span></span>](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
