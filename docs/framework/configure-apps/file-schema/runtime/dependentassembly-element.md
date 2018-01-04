---
title: "&lt;dependentAssembly&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a968d2d1abf6e77cddd9d0a0367822ee4f9723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependentassemblygt-element"></a><span data-ttu-id="fe516-102">&lt;dependentAssembly&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="fe516-102">&lt;dependentAssembly&gt; Element</span></span>
<span data-ttu-id="fe516-103">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="fe516-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="fe516-104">Kullanmayı `dependentAssembly` her derleme için öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe516-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
 <span data-ttu-id="fe516-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="fe516-105">\<configuration></span></span>  
<span data-ttu-id="fe516-106">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="fe516-106">\<runtime></span></span>  
<span data-ttu-id="fe516-107">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="fe516-107">\<assemblyBinding></span></span>  
<span data-ttu-id="fe516-108">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="fe516-108">\<dependentAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe516-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe516-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe516-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe516-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fe516-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe516-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe516-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe516-112">Attributes</span></span>  
 <span data-ttu-id="fe516-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe516-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe516-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe516-114">Child Elements</span></span>  
  
|<span data-ttu-id="fe516-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe516-115">Element</span></span>|<span data-ttu-id="fe516-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe516-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="fe516-117">Derleme hakkında tanımlayıcı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe516-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="fe516-118">Bu öğe her eklenmelidir `dependentAssembly` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe516-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="fe516-119">Çalışma zamanı bilgisayarda yüklü değilse paylaşılan bir derlemede bulabileceğiniz belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe516-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="fe516-120">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="fe516-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="fe516-121">Çalışma zamanı bu derleme için yayımcı ilkesi geçerli olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe516-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe516-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe516-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fe516-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe516-123">Element</span></span>|<span data-ttu-id="fe516-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe516-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="fe516-125">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fe516-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="fe516-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fe516-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fe516-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fe516-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe516-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe516-128">Example</span></span>  
 <span data-ttu-id="fe516-129">Aşağıdaki örnekte, iki derlemeler için derleme bilgileri yalıtan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe516-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe516-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe516-130">See Also</span></span>  
 [<span data-ttu-id="fe516-131">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fe516-131">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="fe516-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="fe516-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="fe516-133">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="fe516-133">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
