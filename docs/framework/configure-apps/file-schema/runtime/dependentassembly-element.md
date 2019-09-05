---
title: <dependentAssembly> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0604161ed6e7c3ead4a2e518daebc8414689af
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252699"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="dbe7c-102">\<dependentAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="dbe7c-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="dbe7c-103">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="dbe7c-104">Her derleme `dependentAssembly` için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
<span data-ttu-id="dbe7c-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dbe7c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dbe7c-106">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="dbe7c-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="dbe7c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="dbe7c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="dbe7c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dependentAssembly >**</span><span class="sxs-lookup"><span data-stu-id="dbe7c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe7c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbe7c-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbe7c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbe7c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dbe7c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbe7c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbe7c-112">Attributes</span></span>  
 <span data-ttu-id="dbe7c-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dbe7c-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbe7c-114">Child Elements</span></span>  
  
|<span data-ttu-id="dbe7c-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbe7c-115">Element</span></span>|<span data-ttu-id="dbe7c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbe7c-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="dbe7c-117">Derlemeyle ilgili tanımlama bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="dbe7c-118">Bu öğe her `dependentAssembly` bir öğeye eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="dbe7c-119">Çalışma zamanının, bilgisayarda yüklü değilse paylaşılan bir derlemeyi bulabilecekleri yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="dbe7c-120">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="dbe7c-121">Çalışma zamanının bu derleme için yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbe7c-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbe7c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="dbe7c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbe7c-123">Element</span></span>|<span data-ttu-id="dbe7c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbe7c-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="dbe7c-125">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="dbe7c-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dbe7c-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dbe7c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbe7c-128">Example</span></span>  
 <span data-ttu-id="dbe7c-129">Aşağıdaki örnek, iki derleme için derleme bilgilerinin nasıl kapsüllagösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbe7c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbe7c-130">See also</span></span>

- [<span data-ttu-id="dbe7c-131">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="dbe7c-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dbe7c-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="dbe7c-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="dbe7c-133">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="dbe7c-133">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
