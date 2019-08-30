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
ms.openlocfilehash: 5232c5bd2d4fad8104d156bfa86141ceb7f0dd93
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167697"
---
# <a name="compilers-element"></a><span data-ttu-id="74faa-102">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="74faa-102">\<compilers> Element</span></span>
<span data-ttu-id="74faa-103">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="74faa-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  
  
[<span data-ttu-id="74faa-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="74faa-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="74faa-105">&nbsp;&nbsp;[ **\<System. CodeDom >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="74faa-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>  
<span data-ttu-id="74faa-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<derleyiciler >**</span><span class="sxs-lookup"><span data-stu-id="74faa-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74faa-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74faa-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74faa-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="74faa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="74faa-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74faa-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74faa-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74faa-110">Attributes</span></span>  
 <span data-ttu-id="74faa-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="74faa-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="74faa-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="74faa-112">Child Elements</span></span>  
  
|<span data-ttu-id="74faa-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="74faa-113">Element</span></span>|<span data-ttu-id="74faa-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74faa-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74faa-115">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="74faa-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="74faa-116">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="74faa-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74faa-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="74faa-117">Parent Elements</span></span>  
  
|<span data-ttu-id="74faa-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="74faa-118">Element</span></span>|<span data-ttu-id="74faa-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74faa-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74faa-120">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="74faa-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="74faa-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="74faa-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="74faa-122">\<System. CodeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="74faa-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="74faa-123">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="74faa-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74faa-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74faa-124">Remarks</span></span>  
 <span data-ttu-id="74faa-125">Derleyiciler > öğesi bir bilgisayardaki dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir. [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="74faa-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="74faa-126">[ Her\<derleyici >](compiler-element.md) öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="74faa-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="74faa-127">.NET Framework, makine yapılandırma dosyasında (Machine. config) ilk derleyici ve dil sağlayıcısı ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74faa-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="74faa-128">Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> bir uygulama için yapılandırma ayarları ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="74faa-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="74faa-129">Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="74faa-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="74faa-130">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="74faa-130">Configuration File</span></span>  
 <span data-ttu-id="74faa-131">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74faa-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74faa-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="74faa-132">Example</span></span>  
 <span data-ttu-id="74faa-133">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="74faa-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74faa-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74faa-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="74faa-135">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="74faa-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="74faa-136">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="74faa-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="74faa-137">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="74faa-137">\<compiler> Element</span></span>](compiler-element.md)
