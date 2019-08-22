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
ms.openlocfilehash: d7c7f866cdbcd39194d61a3db821bf973b4e057e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663811"
---
# <a name="developmentmode-element"></a><span data-ttu-id="0bd9c-102">\<developmentMode > öğesi</span><span class="sxs-lookup"><span data-stu-id="0bd9c-102">\<developmentMode> Element</span></span>
<span data-ttu-id="0bd9c-103">Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="0bd9c-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0bd9c-104">\<configuration></span></span>  
<span data-ttu-id="0bd9c-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="0bd9c-105">\<runtime></span></span>  
<span data-ttu-id="0bd9c-106">\<developmentMode ></span><span class="sxs-lookup"><span data-stu-id="0bd9c-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd9c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bd9c-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bd9c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bd9c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0bd9c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bd9c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0bd9c-110">Attributes</span></span>  
  
|<span data-ttu-id="0bd9c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0bd9c-111">Attribute</span></span>|<span data-ttu-id="0bd9c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bd9c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0bd9c-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="0bd9c-113">**developerInstallation**</span></span>|<span data-ttu-id="0bd9c-114">Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="0bd9c-115">developerInstallation özniteliği</span><span class="sxs-lookup"><span data-stu-id="0bd9c-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="0bd9c-116">Değer</span><span class="sxs-lookup"><span data-stu-id="0bd9c-116">Value</span></span>|<span data-ttu-id="0bd9c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bd9c-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0bd9c-118">**true**</span><span class="sxs-lookup"><span data-stu-id="0bd9c-118">**true**</span></span>|<span data-ttu-id="0bd9c-119">DEVPATH ortam değişkeni tarafından belirtilen dizinlerdeki derlemeleri arar.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="0bd9c-120">**false**</span><span class="sxs-lookup"><span data-stu-id="0bd9c-120">**false**</span></span>|<span data-ttu-id="0bd9c-121">, DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramaz.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="0bd9c-122">Bu, varsayılan</span><span class="sxs-lookup"><span data-stu-id="0bd9c-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bd9c-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bd9c-123">Child Elements</span></span>  
 <span data-ttu-id="0bd9c-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0bd9c-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bd9c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0bd9c-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="0bd9c-126">Element</span></span>|<span data-ttu-id="0bd9c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bd9c-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0bd9c-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0bd9c-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bd9c-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0bd9c-130">Remarks</span></span>  
 <span data-ttu-id="0bd9c-131">Bu ayarı yalnızca geliştirme zamanında kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-131">Use this setting only at development time.</span></span> <span data-ttu-id="0bd9c-132">Çalışma zamanı, DEVPATH 'de bulunan kesin adlı derlemelerin sürümlerini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="0bd9c-133">Yalnızca bulduğu ilk derlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bd9c-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bd9c-134">Example</span></span>  
 <span data-ttu-id="0bd9c-135">Aşağıdaki örnek, çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramasına neden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bd9c-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bd9c-136">See also</span></span>

- [<span data-ttu-id="0bd9c-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0bd9c-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0bd9c-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="0bd9c-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0bd9c-139">Nasıl yapılır: DEVPATH kullanarak derlemeleri bulma</span><span class="sxs-lookup"><span data-stu-id="0bd9c-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
