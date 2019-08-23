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
ms.openlocfilehash: 43bc3c40bfc0b0ce4c0b18683092faf8b67e1c04
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927689"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="a5f81-102">\<System. CodeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="a5f81-102">\<system.codedom> Element</span></span>
<span data-ttu-id="a5f81-103">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5f81-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="a5f81-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="a5f81-104">\<configuration> Element</span></span>  
<span data-ttu-id="a5f81-105">\<System. CodeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="a5f81-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5f81-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5f81-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5f81-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5f81-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a5f81-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5f81-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5f81-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a5f81-109">Attributes</span></span>  
 <span data-ttu-id="a5f81-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a5f81-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5f81-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5f81-111">Child Elements</span></span>  
  
|<span data-ttu-id="a5f81-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="a5f81-112">Element</span></span>|<span data-ttu-id="a5f81-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5f81-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5f81-114">\<derleyiciler ></span><span class="sxs-lookup"><span data-stu-id="a5f81-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="a5f81-115">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a5f81-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5f81-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5f81-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a5f81-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a5f81-117">Element</span></span>|<span data-ttu-id="a5f81-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5f81-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5f81-119">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a5f81-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="a5f81-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a5f81-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5f81-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5f81-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="a5f81-122">.NET Framework sürüm 2,0</span><span class="sxs-lookup"><span data-stu-id="a5f81-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="a5f81-123"><xref:Microsoft.CSharp.CSharpCodeProvider> [ System.CodeDom>öğesi,vegibi.NETFrameworkyüklenmişvarsayılansağlayıcılaraekolarakbirbilgisayarayüklenendilsağlayıcılarının\<](system-codedom-element.md) derleyici yapılandırma ayarlarını içerir. <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="a5f81-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="a5f81-124">Derleyiciler > öğesi sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içeriyor. [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5f81-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="a5f81-125">[ Her\<derleyici >](compiler-element.md) öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5f81-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="a5f81-126">Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider> bir uygulama için yapılandırma ayarlarını makine yapılandırma dosyasına (Machine. config) ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a5f81-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a5f81-127">Bir bilgisayardaki derleyici yapılandırma ayarları tarafından tanımlanan varsayılan dil sağlayıcılarını ve dil sağlayıcılarını programlama yoluyla numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a5f81-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5f81-128">1,0 ve 1,1 .NET Framework sürümlerinde, .NET Framework tarafından sağlanan varsayılan dil sağlayıcıları [ \<compilers >](compilers-element.md) öğesinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a5f81-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="a5f81-129">.NET Framework sürüm 2,0 ' de, varsayılan dil sağlayıcıları [ \<compilers >](compilers-element.md) öğesinde tanımlanmaz, ancak <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> yöntemi kullanılarak Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5f81-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="a5f81-130">.NET Framework sürümleri 1,0 ve 1,1</span><span class="sxs-lookup"><span data-stu-id="a5f81-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="a5f81-131">System. CodeDom > öğesi bir bilgisayardaki dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir. [ \<](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5f81-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="a5f81-132">Derleyiciler > öğesi sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içeriyor. [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5f81-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="a5f81-133">[ Her\<derleyici >](compiler-element.md) öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5f81-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="a5f81-134">.NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5f81-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="a5f81-135">Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider> bir uygulama için yapılandırma ayarları ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a5f81-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a5f81-136">Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a5f81-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a5f81-137">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="a5f81-137">Configuration File</span></span>  
 <span data-ttu-id="a5f81-138">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5f81-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5f81-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5f81-139">Example</span></span>  
 <span data-ttu-id="a5f81-140">Aşağıdaki örnek tipik bir derleyici yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5f81-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5f81-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f81-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="a5f81-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="a5f81-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a5f81-143">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a5f81-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a5f81-144">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="a5f81-144">\<compiler> Element</span></span>](compiler-element.md)
