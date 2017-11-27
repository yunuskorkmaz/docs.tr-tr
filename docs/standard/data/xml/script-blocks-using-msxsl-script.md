---
title: "Komut dosyası blokları kullanarak msxsl: Script"
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
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e127fb02725d11e62c45157b4e45327fc9f1ace
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="ea5dd-102">Komut dosyası blokları kullanarak msxsl: Script</span><span class="sxs-lookup"><span data-stu-id="ea5dd-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="ea5dd-103"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı kullanarak katıştırılmış komut dosyalarını destekler `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="ea5dd-104">Stil sayfası yüklendiğinde, tanımlı hiçbir işlev Microsoft Ara dili (MSIL) kod belge nesne modeli (CodeDOM) tarafından derlenir ve çalışma zamanı sırasında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="ea5dd-105">Katıştırılmış betik bloğundan oluşturulan derleme için stil sayfası oluşturulan derleme daha ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="ea5dd-106">XSLT betik etkinleştir</span><span class="sxs-lookup"><span data-stu-id="ea5dd-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="ea5dd-107">Katıştırılmış komut dosyaları için destek olduğundan isteğe bağlı bir XSLT ayar <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="ea5dd-108">Komut dosyası desteği varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-108">Script support is disabled by default.</span></span> <span data-ttu-id="ea5dd-109">Komut dosyası desteğini etkinleştirmek için Oluştur bir <xref:System.Xml.Xsl.XsltSettings> nesnesi ile <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> özelliğini `true` ve nesneyi geçirin <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea5dd-110">XSLT betik oluşturma yalnızca komut dosyası desteği gerektirir ve tam güvenilen bir ortamda çalışıyorsanız etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="ea5dd-111">msxsl: Script öğesi tanımı</span><span class="sxs-lookup"><span data-stu-id="ea5dd-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="ea5dd-112">`msxsl:script` Öğesi XSLT 1.0 öneri için bir Microsoft uzantısı olup aşağıdaki tanımını içerir:</span><span class="sxs-lookup"><span data-stu-id="ea5dd-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="ea5dd-113">`msxsl` Öneki bağlı `urn:schemas-microsoft-com:xslt` ad alanı URI'si.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="ea5dd-114">Stil sayfası içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt` ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="ea5dd-115">`language` Özniteliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-115">The `language` attribute is optional.</span></span> <span data-ttu-id="ea5dd-116">Değerini katıştırılmış kod bloğu kod dilidir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="ea5dd-117">Dil uygun CodeDOM derleyici kullanmaya eşlendi <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ea5dd-118"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, uygun sağlayıcısı makineye yüklenir ve machine.config dosyasının system.codedom bölümünde kayıtlı olduğu varsayılarak, herhangi bir Microsoft .NET dil destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="ea5dd-119">Varsa bir `language` özniteliği belirtilmezse, dil, JScript için varsayılan olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="ea5dd-120">Dil adı büyük küçük harfe duyarlı değil 'JavaScript' ve 'javascript' eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="ea5dd-121">`implements-prefix` Özniteliği zorunludur.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="ea5dd-122">Bu öznitelik, bir ad alanı bildirimini ve betik bloğu ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="ea5dd-123">Bu özniteliğin değeri ad alanını temsil eden önekidir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="ea5dd-124">Bu ön ek bir stil sayfanızda bir yerde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea5dd-125">Kullanırken `msxsl:script` öğesi öneririz dil, bağımsız olarak komut içinde CDATA bölümü yerleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="ea5dd-126">CDATA bölüm içinde bulunmuyorsa betik operatörler, tanımlayıcılar ya da belirli bir dil için sınırlayıcılar içerebileceği için XML olarak yanlış yorumlayan, olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="ea5dd-127">Aşağıdaki XML kodunu nereye yerleştirileceğini CDATA bölümünün bir şablon gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="ea5dd-128">Komut dosyası işlevleri</span><span class="sxs-lookup"><span data-stu-id="ea5dd-128">Script Functions</span></span>  
 <span data-ttu-id="ea5dd-129">İşlevler içinde bildirilebilir `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="ea5dd-130">Bir işlev bildirirken bir betik bloğu içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="ea5dd-131">Stil sayfaları, birden çok komut dosyası blokları, diğerinden bağımsız çalışan her içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="ea5dd-132">Bir komut dosyası bloğunun içine çalıştırıldığında, aynı ad ve aynı komut dosyası dili bildirilir sürece, başka bir betik bloğu içinde tanımlanan bir işlev çağıramazsınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="ea5dd-133">Çünkü her komut dosyası bloğunun kendi dilde olabilir ve bu dil Ayrıştırıcıyı dilbilgisi kurallarına göre blok ayrıştırılır kullanımda dilin doğru sözdizimi kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="ea5dd-134">Microsoft C# betik bloğunda varsa, örneğin, C# açıklama sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="ea5dd-135">Sağlanan bağımsız değişkenler ve işlevinin dönüş değerleri herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="ea5dd-136">W3C XPath türleri ortak dil çalışma zamanı (CLR) türlerinin bir alt olduğundan, tür dönüştürme XPath tür olarak kabul edilmez türlerinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="ea5dd-137">Aşağıdaki tabloda, karşılık gelen W3C türleri ve eşdeğer CLR türü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="ea5dd-138">W3C türü</span><span class="sxs-lookup"><span data-stu-id="ea5dd-138">W3C type</span></span>|<span data-ttu-id="ea5dd-139">CLR türü</span><span class="sxs-lookup"><span data-stu-id="ea5dd-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="ea5dd-140">CLR sayısal türler dönüştürülür <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="ea5dd-141"><xref:System.DateTime> Türü için dönüştürülür <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="ea5dd-142"><xref:System.Xml.XPath.IXPathNavigable>türlerine dönüştürülür <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="ea5dd-143">**XPathNavigator []** dönüştürülür <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="ea5dd-144">Tüm diğer türleri hata atar.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="ea5dd-145">Ad alanları ve derlemeler içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="ea5dd-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="ea5dd-146"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı önceden belirler derlemeler ve varsayılan olarak tarafından desteklenen ad alanları kümesini `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="ea5dd-147">Ancak, sınıflar ve üyeleri derlemeyi ve ad alanında içeri aktararak önceden tanımlanmış listede olmayan bir ad alanına ait kullanabilirsiniz `msxsl:script` bloğu.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="ea5dd-148">Derlemeler</span><span class="sxs-lookup"><span data-stu-id="ea5dd-148">Assemblies</span></span>  
 <span data-ttu-id="ea5dd-149">Aşağıdaki iki derlemeler varsayılan olarak başvurulur:</span><span class="sxs-lookup"><span data-stu-id="ea5dd-149">The following two assemblies are referenced by default:</span></span>  
  
-   <span data-ttu-id="ea5dd-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="ea5dd-150">System.dll</span></span>  
  
-   <span data-ttu-id="ea5dd-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="ea5dd-151">System.Xml.dll</span></span>  
  
-   <span data-ttu-id="ea5dd-152">(Komut dosyası dili VB olduğunda) Microsoft.VisualBasic.dll içinde</span><span class="sxs-lookup"><span data-stu-id="ea5dd-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="ea5dd-153">Kullanarak ek derlemeler aktarabilirsiniz `msxsl:assembly` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="ea5dd-154">Bu, stil sayfası derlendiğinde derleme içerir.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="ea5dd-155">`msxsl:assembly` Öğesi aşağıdaki tanım var:</span><span class="sxs-lookup"><span data-stu-id="ea5dd-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="ea5dd-156">`name` Özniteliği içeren derlemenin adını ve `href` özniteliği içeren derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="ea5dd-157">Derleme adı bir tam ad gibi olabilir "System.Data, sürüm 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", veya "System.Web" gibi kısa bir ad.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="ea5dd-158">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="ea5dd-158">Namespaces</span></span>  
 <span data-ttu-id="ea5dd-159">Şu ad alanlarından varsayılan olarak eklenir:</span><span class="sxs-lookup"><span data-stu-id="ea5dd-159">The following namespaces are included by default:</span></span>  
  
-   <span data-ttu-id="ea5dd-160">Sistem</span><span class="sxs-lookup"><span data-stu-id="ea5dd-160">System</span></span>  
  
-   <span data-ttu-id="ea5dd-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="ea5dd-161">System.Collection</span></span>  
  
-   <span data-ttu-id="ea5dd-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="ea5dd-162">System.Text</span></span>  
  
-   <span data-ttu-id="ea5dd-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="ea5dd-163">System.Text.RegularExpressions</span></span>  
  
-   <span data-ttu-id="ea5dd-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="ea5dd-164">System.Xml</span></span>  
  
-   <span data-ttu-id="ea5dd-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="ea5dd-165">System.Xml.Xsl</span></span>  
  
-   <span data-ttu-id="ea5dd-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="ea5dd-166">System.Xml.XPath</span></span>  
  
-   <span data-ttu-id="ea5dd-167">(Komut dosyası dili VB olduğunda) Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="ea5dd-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="ea5dd-168">Ek ad alanlarını kullanma için destek ekleyebilirsiniz `namespace` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="ea5dd-169">Öznitelik değeri, ad alanının adıdır.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="ea5dd-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea5dd-170">Example</span></span>  
 <span data-ttu-id="ea5dd-171">Aşağıdaki örnek komut dosyası katıştırılmış kendi RADIUS verilen dairenin çevresi hesaplamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="ea5dd-172">Number.XML</span><span class="sxs-lookup"><span data-stu-id="ea5dd-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="ea5dd-173">CALC.xsl</span><span class="sxs-lookup"><span data-stu-id="ea5dd-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="ea5dd-174">Çıkış</span><span class="sxs-lookup"><span data-stu-id="ea5dd-174">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea5dd-175">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ea5dd-175">See Also</span></span>  
 [<span data-ttu-id="ea5dd-176">XSLT dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="ea5dd-176">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="ea5dd-177">Dinamik kaynak kodu oluşturma ve derleme</span><span class="sxs-lookup"><span data-stu-id="ea5dd-177">Dynamic Source Code Generation and Compilation</span></span>](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
