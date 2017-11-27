---
title: "&lt;derleyicileri&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bea78fe5086a73e4cc588973764ac9bbef2fadc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="24c24-102">&lt;derleyicileri&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="24c24-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="24c24-103">Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazla bilgi içeren [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="24c24-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="24c24-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="24c24-104">\<configuration></span></span>  
<span data-ttu-id="24c24-105">\<System.codeDom ></span><span class="sxs-lookup"><span data-stu-id="24c24-105">\<system.codedom></span></span>  
<span data-ttu-id="24c24-106">\<derleyicileri > öğesi</span><span class="sxs-lookup"><span data-stu-id="24c24-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24c24-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24c24-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24c24-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="24c24-108">Attributes and Elements</span></span>  
 <span data-ttu-id="24c24-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24c24-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24c24-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="24c24-110">Attributes</span></span>  
 <span data-ttu-id="24c24-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="24c24-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24c24-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="24c24-112">Child Elements</span></span>  
  
|<span data-ttu-id="24c24-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="24c24-113">Element</span></span>|<span data-ttu-id="24c24-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24c24-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24c24-115">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="24c24-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="24c24-116">Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="24c24-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24c24-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="24c24-117">Parent Elements</span></span>  
  
|<span data-ttu-id="24c24-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="24c24-118">Element</span></span>|<span data-ttu-id="24c24-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24c24-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24c24-120">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="24c24-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="24c24-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="24c24-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="24c24-122">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="24c24-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="24c24-123">Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="24c24-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24c24-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24c24-124">Remarks</span></span>  
 <span data-ttu-id="24c24-125">[ \<Derleyicileri >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) öğesi bir bilgisayar üzerinde dil sağlayıcıları için derleyici yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="24c24-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="24c24-126">Her [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğesi için özgün dil sağlayıcısı compiler configuration öznitelikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="24c24-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="24c24-127">.NET Framework makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ve dil sağlayıcısı ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24c24-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="24c24-128">Geliştiriciler ve derleyici satıcılar ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="24c24-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="24c24-129">Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarları bir bilgisayarda program aracılığıyla listeleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="24c24-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="24c24-130">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="24c24-130">Configuration File</span></span>  
 <span data-ttu-id="24c24-131">Bu öğe makine yapılandırma dosyası ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24c24-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24c24-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="24c24-132">Example</span></span>  
 <span data-ttu-id="24c24-133">Aşağıdaki örnek tipik derleyici yapılandırma öğesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24c24-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24c24-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24c24-134">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="24c24-135">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="24c24-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="24c24-136">Derleyici ve dil sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="24c24-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="24c24-137">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="24c24-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
