---
title: msxsl:script Kullanan Betik Blokları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
ms.openlocfilehash: a63452df16e452a90eff3977ac8726cc0a5ac439
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710199"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="8867b-102">msxsl:script Kullanan Betik Blokları</span><span class="sxs-lookup"><span data-stu-id="8867b-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="8867b-103"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, `msxsl:script` öğesini kullanarak katıştırılmış betikleri destekler.</span><span class="sxs-lookup"><span data-stu-id="8867b-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="8867b-104">Stil sayfası yüklendiğinde, tanımlanmış tüm işlevler Kod Belge Nesne Modeli (CodeDOM) tarafından Microsoft ara dili (MSIL) ile derlenir ve çalışma zamanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8867b-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="8867b-105">Katıştırılmış betik bloğundan oluşturulan derleme, stil sayfası için oluşturulan derlemeden ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="8867b-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="8867b-106">XSLT betiğini etkinleştir</span><span class="sxs-lookup"><span data-stu-id="8867b-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="8867b-107">Katıştırılmış betikler için destek, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfında isteğe bağlı bir XSLT ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="8867b-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="8867b-108">Komut dosyası desteği varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="8867b-108">Script support is disabled by default.</span></span> <span data-ttu-id="8867b-109">Betik desteğini etkinleştirmek için, <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> özelliği `true` olarak ayarlanmış bir <xref:System.Xml.Xsl.XsltSettings> nesnesi oluşturun ve nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoduna geçirin.</span><span class="sxs-lookup"><span data-stu-id="8867b-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8867b-110">XSLT betiği oluşturma yalnızca betik desteğine ihtiyacınız varsa ve tamamen güvenilir bir ortamda çalışıyorsanız etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8867b-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="8867b-111">msxsl: betik öğesi tanımı</span><span class="sxs-lookup"><span data-stu-id="8867b-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="8867b-112">`msxsl:script` öğesi, XSLT 1,0 önerisi için Microsoft uzantısıdır ve aşağıdaki tanıma sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8867b-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="8867b-113">`msxsl` ön eki `urn:schemas-microsoft-com:xslt` ad alanı URI 'sine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="8867b-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="8867b-114">Stil sayfası `xmlns:msxsl=urn:schemas-microsoft-com:xslt` ad alanı bildirimini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="8867b-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="8867b-115">`language` özniteliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8867b-115">The `language` attribute is optional.</span></span> <span data-ttu-id="8867b-116">Değeri, gömülü kod bloğunun kod dilidir.</span><span class="sxs-lookup"><span data-stu-id="8867b-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="8867b-117">Dil <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> yöntemi kullanılarak uygun CodeDOM derleyicisi ile eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8867b-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8867b-118"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, uygun sağlayıcının makinede yüklü olduğunu varsayarak ve Machine. config dosyasının System. CodeDom bölümünde kayıtlı olan tüm Microsoft .NET dillerini destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8867b-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="8867b-119">Bir `language` özniteliği belirtilmemişse, dilin varsayılan değeri JScript ' dir.</span><span class="sxs-lookup"><span data-stu-id="8867b-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="8867b-120">Dil adı büyük/küçük harfe duyarlı değildir, bu nedenle ' JavaScript ' ve ' JavaScript ' eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8867b-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="8867b-121">`implements-prefix` özniteliği zorunludur.</span><span class="sxs-lookup"><span data-stu-id="8867b-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="8867b-122">Bu öznitelik, bir ad alanını bildirmek ve betik bloğu ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8867b-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="8867b-123">Bu özniteliğin değeri, ad alanını temsil eden önekidir.</span><span class="sxs-lookup"><span data-stu-id="8867b-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="8867b-124">Bu ön ek, bir stil sayfasında bir yerde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8867b-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8867b-125">`msxsl:script` öğesi kullanılırken, dilden bağımsız olarak betiğin bir CDATA bölümünün içine yerleştirilmesi kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="8867b-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="8867b-126">Komut dosyası belirli bir dil için işleç, tanımlayıcı veya sınırlayıcılar içerebildiğinden, CDATA bölümünde yoksa, XML olarak yanlış yorumlanmakta olma olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="8867b-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="8867b-127">Aşağıdaki XML, kodun yerleştirilebileceği CDATA bölümünün bir şablonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8867b-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="8867b-128">Betik Işlevleri</span><span class="sxs-lookup"><span data-stu-id="8867b-128">Script Functions</span></span>  
 <span data-ttu-id="8867b-129">İşlevler `msxsl:script` öğesi içinde bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="8867b-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="8867b-130">Bir işlev bildirildiğinde, bir betik bloğunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8867b-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="8867b-131">Stil sayfaları, her biri diğerinin bağımsız olarak çalışan birden çok betik bloğu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8867b-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="8867b-132">Diğer bir deyişle, bir betik bloğunun içinde yürütüyorsunuz, aynı ad alanına ve aynı komut dosyası diline sahip olmak üzere bildirilmeden, başka bir betik bloğunda tanımladığınız bir işlevi çağıramadığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8867b-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="8867b-133">Her bir betik bloğu kendi dilinde olabileceğinden ve blok söz konusu dil ayrıştırıcısının dilbilgisi kurallarına göre ayrıştırılacağından, kullanımda olan dil için doğru sözdizimini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="8867b-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="8867b-134">Örneğin, bir Microsoft C# komut dosyası bloğunda, C# açıklama sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8867b-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="8867b-135">Sağlanan bağımsız değişkenler ve işlevin dönüş değerleri herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="8867b-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="8867b-136">W3C XPath türleri ortak dil çalışma zamanı (CLR) türlerinin bir alt kümesi olduğundan, bir XPath türü olarak kabul etmeyen türler için tür dönüştürme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="8867b-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="8867b-137">Aşağıdaki tabloda karşılık gelen W3C türleri ve eşdeğer CLR türü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8867b-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="8867b-138">W3C türü</span><span class="sxs-lookup"><span data-stu-id="8867b-138">W3C type</span></span>|<span data-ttu-id="8867b-139">CLR türü</span><span class="sxs-lookup"><span data-stu-id="8867b-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="8867b-140">CLR sayısal türleri <xref:System.Double>dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8867b-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="8867b-141"><xref:System.DateTime> türü <xref:System.String>dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8867b-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="8867b-142"><xref:System.Xml.XPath.IXPathNavigable> türler <xref:System.Xml.XPath.XPathNavigator>dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8867b-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="8867b-143">**XPathNavigator []** <xref:System.Xml.XPath.XPathNodeIterator>dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="8867b-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="8867b-144">Diğer tüm türler bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8867b-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="8867b-145">Ad alanları ve derlemeler içeri aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="8867b-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="8867b-146"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, varsayılan olarak `msxsl:script` öğesi tarafından desteklenen derleme ve ad alanları kümesini önceden tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8867b-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="8867b-147">Ancak, `msxsl:script` bloğunda derlemeyi ve ad alanını içeri aktararak önceden tanımlanmış listede olmayan bir ad alanına ait sınıfları ve üyeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8867b-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="8867b-148">Derlemeler</span><span class="sxs-lookup"><span data-stu-id="8867b-148">Assemblies</span></span>  
 <span data-ttu-id="8867b-149">Aşağıdaki iki derlemeye varsayılan olarak başvurulur:</span><span class="sxs-lookup"><span data-stu-id="8867b-149">The following two assemblies are referenced by default:</span></span>  
  
- <span data-ttu-id="8867b-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="8867b-150">System.dll</span></span>  
  
- <span data-ttu-id="8867b-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="8867b-151">System.Xml.dll</span></span>  
  
- <span data-ttu-id="8867b-152">Microsoft. VisualBasic. dll (komut dosyası dili VB olduğunda)</span><span class="sxs-lookup"><span data-stu-id="8867b-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="8867b-153">`msxsl:assembly` öğesini kullanarak ek derlemeleri içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8867b-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="8867b-154">Bu, stil sayfası derlendiğinde derlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="8867b-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="8867b-155">`msxsl:assembly` öğesi aşağıdaki tanıma sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8867b-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="8867b-156">`name` özniteliği derlemenin adını içerir ve `href` özniteliği derlemenin yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8867b-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="8867b-157">Derleme adı "System. Data, Version = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089" gibi bir tam ad veya "System. Web" gibi kısa bir ad olabilir.</span><span class="sxs-lookup"><span data-stu-id="8867b-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="8867b-158">{1&gt;Ad alanları&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8867b-158">Namespaces</span></span>  
 <span data-ttu-id="8867b-159">Aşağıdaki ad alanları varsayılan olarak dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8867b-159">The following namespaces are included by default:</span></span>  
  
- <span data-ttu-id="8867b-160">Sistem</span><span class="sxs-lookup"><span data-stu-id="8867b-160">System</span></span>  
  
- <span data-ttu-id="8867b-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="8867b-161">System.Collection</span></span>  
  
- <span data-ttu-id="8867b-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="8867b-162">System.Text</span></span>  
  
- <span data-ttu-id="8867b-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="8867b-163">System.Text.RegularExpressions</span></span>  
  
- <span data-ttu-id="8867b-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="8867b-164">System.Xml</span></span>  
  
- <span data-ttu-id="8867b-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="8867b-165">System.Xml.Xsl</span></span>  
  
- <span data-ttu-id="8867b-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="8867b-166">System.Xml.XPath</span></span>  
  
- <span data-ttu-id="8867b-167">Microsoft. VisualBasic (komut dosyası dili VB olduğunda)</span><span class="sxs-lookup"><span data-stu-id="8867b-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="8867b-168">`namespace` özniteliğini kullanarak, ek ad alanları için destek ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8867b-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="8867b-169">Öznitelik değeri, ad alanının adıdır.</span><span class="sxs-lookup"><span data-stu-id="8867b-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="8867b-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="8867b-170">Example</span></span>  
 <span data-ttu-id="8867b-171">Aşağıdaki örnek, yarıçapı verilen bir dairenin çevresini hesaplamak için gömülü bir betiği kullanır.</span><span class="sxs-lookup"><span data-stu-id="8867b-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="8867b-172">Number. xml</span><span class="sxs-lookup"><span data-stu-id="8867b-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="8867b-173">Calc. Xsl</span><span class="sxs-lookup"><span data-stu-id="8867b-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="8867b-174">Çıkış</span><span class="sxs-lookup"><span data-stu-id="8867b-174">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8867b-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8867b-175">See also</span></span>

- [<span data-ttu-id="8867b-176">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="8867b-176">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
- [<span data-ttu-id="8867b-177">Dinamik Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="8867b-177">Dynamic Source Code Generation and Compilation</span></span>](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
