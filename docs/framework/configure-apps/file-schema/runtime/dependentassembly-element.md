---
description: 'Daha fazla bilgi edinin: <dependentAssembly> öğesi'
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
ms.openlocfilehash: c804920de961fc609fd04a0853ecbdbc9202e5be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719090"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="920c4-103">\<dependentAssembly> Öğesi</span><span class="sxs-lookup"><span data-stu-id="920c4-103">\<dependentAssembly> Element</span></span>

<span data-ttu-id="920c4-104">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="920c4-104">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="920c4-105">`dependentAssembly`Her derleme için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="920c4-105">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="920c4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="920c4-106">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="920c4-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="920c4-107">Attributes and Elements</span></span>  

 <span data-ttu-id="920c4-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="920c4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="920c4-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="920c4-109">Attributes</span></span>  

 <span data-ttu-id="920c4-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="920c4-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="920c4-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="920c4-111">Child Elements</span></span>  
  
|<span data-ttu-id="920c4-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="920c4-112">Element</span></span>|<span data-ttu-id="920c4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="920c4-113">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="920c4-114">Derlemeyle ilgili tanımlama bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="920c4-114">Contains identifying information about the assembly.</span></span> <span data-ttu-id="920c4-115">Bu öğe her bir `dependentAssembly` öğeye eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="920c4-115">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="920c4-116">Çalışma zamanının, bilgisayarda yüklü değilse paylaşılan bir derlemeyi bulabilecekleri yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="920c4-116">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="920c4-117">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="920c4-117">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="920c4-118">Çalışma zamanının bu derleme için yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="920c4-118">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="920c4-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="920c4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="920c4-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="920c4-120">Element</span></span>|<span data-ttu-id="920c4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="920c4-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="920c4-122">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="920c4-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="920c4-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="920c4-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="920c4-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="920c4-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="920c4-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="920c4-125">Example</span></span>  

 <span data-ttu-id="920c4-126">Aşağıdaki örnek, iki derleme için derleme bilgilerinin nasıl kapsüllagösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="920c4-126">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="920c4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="920c4-127">See also</span></span>

- [<span data-ttu-id="920c4-128">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="920c4-128">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="920c4-129">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="920c4-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="920c4-130">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="920c4-130">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
