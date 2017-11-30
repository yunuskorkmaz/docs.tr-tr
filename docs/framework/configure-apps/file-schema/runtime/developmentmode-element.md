---
title: "&lt;developmentMode&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4573c3a5e0cf64996f2a4e109736d966b754494a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="841f3-102">&lt;developmentMode&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="841f3-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="841f3-103">Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="841f3-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="841f3-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="841f3-104">\<configuration></span></span>  
<span data-ttu-id="841f3-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="841f3-105">\<runtime></span></span>  
<span data-ttu-id="841f3-106">\<developmentMode ></span><span class="sxs-lookup"><span data-stu-id="841f3-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="841f3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="841f3-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="841f3-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="841f3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="841f3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="841f3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="841f3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="841f3-110">Attributes</span></span>  
  
|<span data-ttu-id="841f3-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="841f3-111">Attribute</span></span>|<span data-ttu-id="841f3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="841f3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="841f3-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="841f3-113">**developerInstallation**</span></span>|<span data-ttu-id="841f3-114">Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="841f3-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="841f3-115">developerInstallation özniteliği</span><span class="sxs-lookup"><span data-stu-id="841f3-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="841f3-116">Değer</span><span class="sxs-lookup"><span data-stu-id="841f3-116">Value</span></span>|<span data-ttu-id="841f3-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="841f3-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="841f3-118">**TRUE**</span><span class="sxs-lookup"><span data-stu-id="841f3-118">**true**</span></span>|<span data-ttu-id="841f3-119">Derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="841f3-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="841f3-120">**false**</span><span class="sxs-lookup"><span data-stu-id="841f3-120">**false**</span></span>|<span data-ttu-id="841f3-121">Derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde aramaz.</span><span class="sxs-lookup"><span data-stu-id="841f3-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="841f3-122">Bu varsayılan değerdir</span><span class="sxs-lookup"><span data-stu-id="841f3-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="841f3-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="841f3-123">Child Elements</span></span>  
 <span data-ttu-id="841f3-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="841f3-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="841f3-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="841f3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="841f3-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="841f3-126">Element</span></span>|<span data-ttu-id="841f3-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="841f3-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="841f3-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="841f3-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="841f3-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="841f3-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="841f3-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="841f3-130">Remarks</span></span>  
 <span data-ttu-id="841f3-131">Bu ayar yalnızca geliştirme sırasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="841f3-131">Use this setting only at development time.</span></span> <span data-ttu-id="841f3-132">Çalışma zamanı tanımlayıcı adlı derlemeler DEVPATH bulunan sürümlerinde denetlemez.</span><span class="sxs-lookup"><span data-stu-id="841f3-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="841f3-133">Yalnızca, bulduğu ilk derleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="841f3-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="841f3-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="841f3-134">Example</span></span>  
 <span data-ttu-id="841f3-135">Aşağıdaki örnek, çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde aramak neden gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="841f3-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="841f3-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="841f3-136">See Also</span></span>  
 [<span data-ttu-id="841f3-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="841f3-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="841f3-138">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="841f3-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="841f3-139">Nasıl yapılır: DEVPATH kullanarak derlemelerin bulun</span><span class="sxs-lookup"><span data-stu-id="841f3-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
