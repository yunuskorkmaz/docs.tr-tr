---
title: <system.codedom> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155394"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="9e3cd-102">\<system.codedom> Öğesi</span><span class="sxs-lookup"><span data-stu-id="9e3cd-102">\<system.codedom> Element</span></span>
<span data-ttu-id="9e3cd-103">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a><span data-ttu-id="9e3cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e3cd-104">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e3cd-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e3cd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9e3cd-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e3cd-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9e3cd-107">Attributes</span></span>  
 <span data-ttu-id="9e3cd-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9e3cd-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e3cd-109">Child Elements</span></span>  
  
|<span data-ttu-id="9e3cd-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e3cd-110">Element</span></span>|<span data-ttu-id="9e3cd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e3cd-111">Description</span></span>|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="9e3cd-112">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [\<compiler>](compiler-element.md) öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-112">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e3cd-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e3cd-113">Parent Elements</span></span>  
  
|<span data-ttu-id="9e3cd-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e3cd-114">Element</span></span>|<span data-ttu-id="9e3cd-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e3cd-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="9e3cd-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e3cd-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e3cd-117">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="9e3cd-118">.NET Framework sürüm 2,0</span><span class="sxs-lookup"><span data-stu-id="9e3cd-118">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="9e3cd-119">[\<system.codedom>](system-codedom-element.md)Öğesi, ve gibi .NET Framework yüklenen varsayılan sağlayıcılara ek olarak bir bilgisayara yüklenen dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider> .</span><span class="sxs-lookup"><span data-stu-id="9e3cd-119">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="9e3cd-120">[\<compilers>](compilers-element.md)Öğe sıfır veya daha fazla [\<compiler>](compiler-element.md) öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-120">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="9e3cd-121">Her [\<compiler>](compiler-element.md) öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-121">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="9e3cd-122">Geliştiriciler ve derleyici satıcıları, yeni bir uygulama için yapılandırma ayarlarını makine yapılandırma dosyasına (Machine. config) ekleyebilir <xref:System.CodeDom.Compiler.CodeDomProvider> .</span><span class="sxs-lookup"><span data-stu-id="9e3cd-122">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="9e3cd-123"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>Bir bilgisayardaki derleyici yapılandırma ayarları tarafından tanımlanan varsayılan dil sağlayıcılarını ve dil sağlayıcılarını programlama yoluyla numaralandırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-123">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e3cd-124">.NET Framework sürüm 1,0 ve 1,1 ' de, .NET Framework tarafından sağlanan varsayılan dil sağlayıcıları [\<compilers>](compilers-element.md) öğesinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-124">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="9e3cd-125">.NET Framework sürüm 2,0 ' de, varsayılan dil sağlayıcıları [\<compilers>](compilers-element.md) öğesinde tanımlanmaz, ancak yöntemi kullanılarak numaralandırılabilir <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> .</span><span class="sxs-lookup"><span data-stu-id="9e3cd-125">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="9e3cd-126">.NET Framework sürümleri 1,0 ve 1,1</span><span class="sxs-lookup"><span data-stu-id="9e3cd-126">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="9e3cd-127">[\<system.codedom>](system-codedom-element.md)Öğesi, bir bilgisayardaki dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-127">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="9e3cd-128">[\<compilers>](compilers-element.md)Öğe sıfır veya daha fazla [\<compiler>](compiler-element.md) öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-128">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="9e3cd-129">Her [\<compiler>](compiler-element.md) öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-129">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="9e3cd-130">.NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-130">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="9e3cd-131">Geliştiriciler ve derleyici satıcıları, yeni bir uygulama için yapılandırma ayarları ekleyebilir <xref:System.CodeDom.Compiler.CodeDomProvider> .</span><span class="sxs-lookup"><span data-stu-id="9e3cd-131">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="9e3cd-132"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-132">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="9e3cd-133">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="9e3cd-133">Configuration File</span></span>  
 <span data-ttu-id="9e3cd-134">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-134">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e3cd-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e3cd-135">Example</span></span>  
 <span data-ttu-id="9e3cd-136">Aşağıdaki örnek tipik bir derleyici yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-136">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e3cd-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e3cd-137">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="9e3cd-138">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="9e3cd-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9e3cd-139">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="9e3cd-139">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9e3cd-140">\<compiler>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="9e3cd-140">\<compiler> Element</span></span>](compiler-element.md)
