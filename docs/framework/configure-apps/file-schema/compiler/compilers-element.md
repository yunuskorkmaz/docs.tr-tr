---
description: 'Daha fazla bilgi edinin: <compilers> öğesi'
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
ms.openlocfilehash: 6ced6bc81bc7d829ccebab50e0a361985c970f5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699174"
---
# <a name="compilers-element"></a><span data-ttu-id="6f406-103">\<compilers> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6f406-103">\<compilers> Element</span></span>

<span data-ttu-id="6f406-104">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [\<compiler>](compiler-element.md) öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6f406-104">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="6f406-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6f406-105">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f406-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f406-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6f406-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f406-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f406-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f406-108">Attributes</span></span>  

 <span data-ttu-id="6f406-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f406-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f406-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f406-110">Child Elements</span></span>  
  
|<span data-ttu-id="6f406-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f406-111">Element</span></span>|<span data-ttu-id="6f406-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f406-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f406-113">\<compiler> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="6f406-113">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="6f406-114">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f406-114">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f406-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f406-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6f406-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f406-116">Element</span></span>|<span data-ttu-id="6f406-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f406-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f406-118">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="6f406-118">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="6f406-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6f406-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="6f406-120">\<system.codedom> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="6f406-120">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="6f406-121">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f406-121">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f406-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f406-122">Remarks</span></span>  

 <span data-ttu-id="6f406-123">[\<compilers>](compilers-element.md)Öğesi, bir bilgisayardaki dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6f406-123">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="6f406-124">Her [\<compiler>](compiler-element.md) öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f406-124">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="6f406-125">.NET Framework, makine yapılandırma dosyasında (Machine.config) ilk derleyicisini ve dil sağlayıcısı ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f406-125">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="6f406-126">Geliştiriciler ve derleyici satıcıları, yeni bir uygulama için yapılandırma ayarları ekleyebilir <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6f406-126">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="6f406-127"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f406-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6f406-128">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="6f406-128">Configuration File</span></span>  

 <span data-ttu-id="6f406-129">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f406-129">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f406-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f406-130">Example</span></span>  

 <span data-ttu-id="6f406-131">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6f406-131">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f406-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f406-132">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="6f406-133">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6f406-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6f406-134">Derleyici ve dil sağlayıcısı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6f406-134">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6f406-135">\<compiler> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="6f406-135">\<compiler> Element</span></span>](compiler-element.md)
