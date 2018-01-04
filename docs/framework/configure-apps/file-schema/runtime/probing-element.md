---
title: "&lt;yoklama&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e846cb1386dc64161d91ab50b6a04e5560e9c6da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="6f1b0-102">&lt;yoklama&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="6f1b0-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="6f1b0-103">Uygulama derlemeleri yüklenirken aramak ortak dil çalışma zamanı için temel alt dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="6f1b0-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="6f1b0-104">\<configuration></span></span>  
<span data-ttu-id="6f1b0-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="6f1b0-105">\<runtime></span></span>  
<span data-ttu-id="6f1b0-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="6f1b0-106">\<assemblyBinding></span></span>  
<span data-ttu-id="6f1b0-107">\<yoklama ></span><span class="sxs-lookup"><span data-stu-id="6f1b0-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f1b0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f1b0-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f1b0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f1b0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6f1b0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f1b0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f1b0-111">Attributes</span></span>  
  
|<span data-ttu-id="6f1b0-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6f1b0-112">Attribute</span></span>|<span data-ttu-id="6f1b0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f1b0-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="6f1b0-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="6f1b0-115">Derlemeler içerebilir uygulamanın ana dizin alt dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="6f1b0-116">Her alt noktalı virgül ile sınırlar.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f1b0-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f1b0-117">Child Elements</span></span>  
 <span data-ttu-id="6f1b0-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f1b0-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f1b0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6f1b0-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f1b0-120">Element</span></span>|<span data-ttu-id="6f1b0-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f1b0-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="6f1b0-122">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="6f1b0-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6f1b0-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6f1b0-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f1b0-125">Example</span></span>  
 <span data-ttu-id="6f1b0-126">Aşağıdaki örnek, çalışma zamanı derlemeleri için arayacağı uygulama temel alt dizinleri belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f1b0-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-127">See Also</span></span>  
 [<span data-ttu-id="6f1b0-128">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6f1b0-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="6f1b0-129">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="6f1b0-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6f1b0-130">Bütünleştirilmiş Kodun Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="6f1b0-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="6f1b0-131">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="6f1b0-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
