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
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155420"
---
# <a name="compilers-element"></a><span data-ttu-id="d3a2b-102">\<compilers> Öğesi</span><span class="sxs-lookup"><span data-stu-id="d3a2b-102">\<compilers> Element</span></span>
<span data-ttu-id="d3a2b-103">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [\<compiler>](compiler-element.md) öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="d3a2b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3a2b-104">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3a2b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3a2b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d3a2b-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3a2b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d3a2b-107">Attributes</span></span>  
 <span data-ttu-id="d3a2b-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3a2b-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3a2b-109">Child Elements</span></span>  
  
|<span data-ttu-id="d3a2b-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3a2b-110">Element</span></span>|<span data-ttu-id="d3a2b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3a2b-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3a2b-112">\<compiler>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="d3a2b-112">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="d3a2b-113">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3a2b-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3a2b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d3a2b-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3a2b-115">Element</span></span>|<span data-ttu-id="d3a2b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3a2b-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3a2b-117">\<configuration>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="d3a2b-117">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="d3a2b-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="d3a2b-119">\<system.codedom>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="d3a2b-119">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="d3a2b-120">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-120">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3a2b-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3a2b-121">Remarks</span></span>  
 <span data-ttu-id="d3a2b-122">[\<compilers>](compilers-element.md)Öğesi, bir bilgisayardaki dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-122">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="d3a2b-123">Her [\<compiler>](compiler-element.md) öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-123">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="d3a2b-124">.NET Framework, makine yapılandırma dosyasında (Machine. config) ilk derleyici ve dil sağlayıcısı ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-124">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="d3a2b-125">Geliştiriciler ve derleyici satıcıları, yeni bir uygulama için yapılandırma ayarları ekleyebilir <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d3a2b-125">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="d3a2b-126"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-126">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d3a2b-127">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="d3a2b-127">Configuration File</span></span>  
 <span data-ttu-id="d3a2b-128">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-128">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3a2b-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3a2b-129">Example</span></span>  
 <span data-ttu-id="d3a2b-130">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-130">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3a2b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3a2b-131">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="d3a2b-132">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d3a2b-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d3a2b-133">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d3a2b-133">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d3a2b-134">\<compiler>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="d3a2b-134">\<compiler> Element</span></span>](compiler-element.md)
