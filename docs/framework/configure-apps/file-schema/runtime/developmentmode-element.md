---
title: <developmentMode> Öğesi
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
ms.openlocfilehash: fdf840035150f08c894c984213af9a0abe6e95af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192062"
---
# <a name="developmentmode-element"></a><span data-ttu-id="f8837-102">\<developmentMode > öğesi</span><span class="sxs-lookup"><span data-stu-id="f8837-102">\<developmentMode> Element</span></span>
<span data-ttu-id="f8837-103">Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinleri arar olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8837-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="f8837-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f8837-104">\<configuration></span></span>  
<span data-ttu-id="f8837-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="f8837-105">\<runtime></span></span>  
<span data-ttu-id="f8837-106">\<developmentMode ></span><span class="sxs-lookup"><span data-stu-id="f8837-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8837-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8837-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8837-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8837-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f8837-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8837-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8837-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f8837-110">Attributes</span></span>  
  
|<span data-ttu-id="f8837-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f8837-111">Attribute</span></span>|<span data-ttu-id="f8837-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8837-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8837-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="f8837-113">**developerInstallation**</span></span>|<span data-ttu-id="f8837-114">Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinleri arar olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8837-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="f8837-115">developerInstallation özniteliği</span><span class="sxs-lookup"><span data-stu-id="f8837-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="f8837-116">Değer</span><span class="sxs-lookup"><span data-stu-id="f8837-116">Value</span></span>|<span data-ttu-id="f8837-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8837-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f8837-118">**true**</span><span class="sxs-lookup"><span data-stu-id="f8837-118">**true**</span></span>|<span data-ttu-id="f8837-119">Derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinleri arar.</span><span class="sxs-lookup"><span data-stu-id="f8837-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="f8837-120">**false**</span><span class="sxs-lookup"><span data-stu-id="f8837-120">**false**</span></span>|<span data-ttu-id="f8837-121">Derlemeler DEVPATH ortam değişkeni tarafından belirtilen dizinlerde arama yapmaz.</span><span class="sxs-lookup"><span data-stu-id="f8837-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="f8837-122">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="f8837-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8837-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8837-123">Child Elements</span></span>  
 <span data-ttu-id="f8837-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="f8837-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8837-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8837-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f8837-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="f8837-126">Element</span></span>|<span data-ttu-id="f8837-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8837-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f8837-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f8837-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f8837-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f8837-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8837-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8837-130">Remarks</span></span>  
 <span data-ttu-id="f8837-131">Yalnızca geliştirme sırasında bu ayarı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8837-131">Use this setting only at development time.</span></span> <span data-ttu-id="f8837-132">Çalışma zamanı, tanımlayıcı adlı derlemeler DEVPATH içinde bulunan sürümlerinde denetlemez.</span><span class="sxs-lookup"><span data-stu-id="f8837-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="f8837-133">Yalnızca bulduğu ilk derlemeyi de kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8837-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8837-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8837-134">Example</span></span>  
 <span data-ttu-id="f8837-135">Aşağıdaki örnek, çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinlerde arama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8837-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8837-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8837-136">See also</span></span>

- [<span data-ttu-id="f8837-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f8837-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="f8837-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="f8837-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f8837-139">Nasıl yapılır: DEVPATH kullanarak derlemelerin bulun</span><span class="sxs-lookup"><span data-stu-id="f8837-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
