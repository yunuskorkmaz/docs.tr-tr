---
title: '&lt;derleyicileri&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fc85610f5c3db7929f824fda2dd211300d9b05c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742997"
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="55484-102">&lt;derleyicileri&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="55484-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="55484-103">Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazla bilgi içeren [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="55484-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="55484-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="55484-104">\<configuration></span></span>  
<span data-ttu-id="55484-105">\<System.codeDom ></span><span class="sxs-lookup"><span data-stu-id="55484-105">\<system.codedom></span></span>  
<span data-ttu-id="55484-106">\<derleyicileri > öğesi</span><span class="sxs-lookup"><span data-stu-id="55484-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55484-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55484-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55484-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55484-108">Attributes and Elements</span></span>  
 <span data-ttu-id="55484-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55484-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55484-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55484-110">Attributes</span></span>  
 <span data-ttu-id="55484-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="55484-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55484-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55484-112">Child Elements</span></span>  
  
|<span data-ttu-id="55484-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="55484-113">Element</span></span>|<span data-ttu-id="55484-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55484-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55484-115">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="55484-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="55484-116">Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="55484-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55484-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55484-117">Parent Elements</span></span>  
  
|<span data-ttu-id="55484-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="55484-118">Element</span></span>|<span data-ttu-id="55484-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55484-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55484-120">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="55484-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="55484-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="55484-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="55484-122">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="55484-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="55484-123">Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55484-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55484-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55484-124">Remarks</span></span>  
 <span data-ttu-id="55484-125">[ \<Derleyicileri >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) öğesi bir bilgisayar üzerinde dil sağlayıcıları için derleyici yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="55484-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="55484-126">Her [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğesi için özgün dil sağlayıcısı compiler configuration öznitelikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="55484-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="55484-127">.NET Framework makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ve dil sağlayıcısı ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55484-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="55484-128">Geliştiriciler ve derleyici satıcılar ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="55484-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="55484-129">Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarları bir bilgisayarda program aracılığıyla listeleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="55484-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="55484-130">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="55484-130">Configuration File</span></span>  
 <span data-ttu-id="55484-131">Bu öğe makine yapılandırma dosyası ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55484-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55484-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="55484-132">Example</span></span>  
 <span data-ttu-id="55484-133">Aşağıdaki örnek tipik derleyici yapılandırma öğesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="55484-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55484-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55484-134">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="55484-135">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="55484-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="55484-136">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="55484-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="55484-137">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="55484-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
