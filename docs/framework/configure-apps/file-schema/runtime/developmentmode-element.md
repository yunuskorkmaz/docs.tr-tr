---
title: '&lt;developmentMode&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71b4eb1dfb50774cea2f7a50d5e5350b0338f41e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="d31f0-102">&lt;developmentMode&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="d31f0-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="d31f0-103">Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31f0-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="d31f0-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d31f0-104">\<configuration></span></span>  
<span data-ttu-id="d31f0-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="d31f0-105">\<runtime></span></span>  
<span data-ttu-id="d31f0-106">\<developmentMode ></span><span class="sxs-lookup"><span data-stu-id="d31f0-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d31f0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d31f0-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d31f0-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d31f0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d31f0-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d31f0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d31f0-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d31f0-110">Attributes</span></span>  
  
|<span data-ttu-id="d31f0-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d31f0-111">Attribute</span></span>|<span data-ttu-id="d31f0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d31f0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d31f0-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="d31f0-113">**developerInstallation**</span></span>|<span data-ttu-id="d31f0-114">Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31f0-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="d31f0-115">developerInstallation özniteliği</span><span class="sxs-lookup"><span data-stu-id="d31f0-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="d31f0-116">Değer</span><span class="sxs-lookup"><span data-stu-id="d31f0-116">Value</span></span>|<span data-ttu-id="d31f0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d31f0-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d31f0-118">**true**</span><span class="sxs-lookup"><span data-stu-id="d31f0-118">**true**</span></span>|<span data-ttu-id="d31f0-119">Derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="d31f0-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="d31f0-120">**false**</span><span class="sxs-lookup"><span data-stu-id="d31f0-120">**false**</span></span>|<span data-ttu-id="d31f0-121">Derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde aramaz.</span><span class="sxs-lookup"><span data-stu-id="d31f0-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="d31f0-122">Bu varsayılan değerdir</span><span class="sxs-lookup"><span data-stu-id="d31f0-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d31f0-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d31f0-123">Child Elements</span></span>  
 <span data-ttu-id="d31f0-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="d31f0-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d31f0-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d31f0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d31f0-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="d31f0-126">Element</span></span>|<span data-ttu-id="d31f0-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d31f0-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d31f0-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d31f0-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d31f0-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d31f0-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d31f0-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d31f0-130">Remarks</span></span>  
 <span data-ttu-id="d31f0-131">Bu ayar yalnızca geliştirme sırasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="d31f0-131">Use this setting only at development time.</span></span> <span data-ttu-id="d31f0-132">Çalışma zamanı tanımlayıcı adlı derlemeler DEVPATH bulunan sürümlerinde denetlemez.</span><span class="sxs-lookup"><span data-stu-id="d31f0-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="d31f0-133">Yalnızca, bulduğu ilk derleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="d31f0-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d31f0-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="d31f0-134">Example</span></span>  
 <span data-ttu-id="d31f0-135">Aşağıdaki örnek, çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde aramak neden gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d31f0-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d31f0-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d31f0-136">See Also</span></span>  
 [<span data-ttu-id="d31f0-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d31f0-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d31f0-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d31f0-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d31f0-139">Nasıl yapılır: DEVPATH Kullanarak Bütünleştirilmiş Kodların Konumunu Bulma</span><span class="sxs-lookup"><span data-stu-id="d31f0-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
