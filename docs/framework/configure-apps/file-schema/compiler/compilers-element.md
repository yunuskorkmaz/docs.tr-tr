---
title: <compilers> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 53dc67d0046ef2f184535f373c5bf19c484c505a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664313"
---
# <a name="compilers-element"></a><span data-ttu-id="5c89f-102">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="5c89f-102">\<compilers> Element</span></span>
<span data-ttu-id="5c89f-103">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5c89f-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="5c89f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5c89f-104">\<configuration></span></span>  
<span data-ttu-id="5c89f-105">\<System. CodeDom ></span><span class="sxs-lookup"><span data-stu-id="5c89f-105">\<system.codedom></span></span>  
<span data-ttu-id="5c89f-106">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="5c89f-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c89f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c89f-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c89f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c89f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5c89f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c89f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c89f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c89f-110">Attributes</span></span>  
 <span data-ttu-id="5c89f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c89f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5c89f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c89f-112">Child Elements</span></span>  
  
|<span data-ttu-id="5c89f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c89f-113">Element</span></span>|<span data-ttu-id="5c89f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c89f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c89f-115">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="5c89f-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="5c89f-116">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c89f-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c89f-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c89f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5c89f-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c89f-118">Element</span></span>|<span data-ttu-id="5c89f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c89f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c89f-120">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="5c89f-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="5c89f-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5c89f-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="5c89f-122">\<System. CodeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="5c89f-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="5c89f-123">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c89f-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c89f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c89f-124">Remarks</span></span>  
 <span data-ttu-id="5c89f-125">Derleyiciler > öğesi bir bilgisayardaki dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir. [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="5c89f-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="5c89f-126">[ Her\<derleyici >](compiler-element.md) öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c89f-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="5c89f-127">.NET Framework, makine yapılandırma dosyasında (Machine. config) ilk derleyici ve dil sağlayıcısı ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5c89f-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="5c89f-128">Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> bir uygulama için yapılandırma ayarları ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5c89f-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="5c89f-129">Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5c89f-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5c89f-130">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="5c89f-130">Configuration File</span></span>  
 <span data-ttu-id="5c89f-131">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c89f-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c89f-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c89f-132">Example</span></span>  
 <span data-ttu-id="5c89f-133">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5c89f-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c89f-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c89f-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="5c89f-135">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="5c89f-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5c89f-136">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5c89f-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5c89f-137">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="5c89f-137">\<compiler> Element</span></span>](compiler-element.md)
