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
ms.openlocfilehash: 0253c3ced52b575097fe5d18abb8ce188c0164fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252691"
---
# <a name="developmentmode-element"></a><span data-ttu-id="95e53-102">\<developmentMode > öğesi</span><span class="sxs-lookup"><span data-stu-id="95e53-102">\<developmentMode> Element</span></span>
<span data-ttu-id="95e53-103">Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="95e53-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
<span data-ttu-id="95e53-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="95e53-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="95e53-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="95e53-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="95e53-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<developmentMode >**</span><span class="sxs-lookup"><span data-stu-id="95e53-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e53-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95e53-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95e53-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="95e53-108">Attributes and Elements</span></span>  
 <span data-ttu-id="95e53-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="95e53-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95e53-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="95e53-110">Attributes</span></span>  
  
|<span data-ttu-id="95e53-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="95e53-111">Attribute</span></span>|<span data-ttu-id="95e53-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95e53-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95e53-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="95e53-113">**developerInstallation**</span></span>|<span data-ttu-id="95e53-114">Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="95e53-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="95e53-115">developerInstallation özniteliği</span><span class="sxs-lookup"><span data-stu-id="95e53-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="95e53-116">Değer</span><span class="sxs-lookup"><span data-stu-id="95e53-116">Value</span></span>|<span data-ttu-id="95e53-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95e53-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="95e53-118">**true**</span><span class="sxs-lookup"><span data-stu-id="95e53-118">**true**</span></span>|<span data-ttu-id="95e53-119">DEVPATH ortam değişkeni tarafından belirtilen dizinlerdeki derlemeleri arar.</span><span class="sxs-lookup"><span data-stu-id="95e53-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="95e53-120">**false**</span><span class="sxs-lookup"><span data-stu-id="95e53-120">**false**</span></span>|<span data-ttu-id="95e53-121">, DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramaz.</span><span class="sxs-lookup"><span data-stu-id="95e53-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="95e53-122">Bu, varsayılan</span><span class="sxs-lookup"><span data-stu-id="95e53-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95e53-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="95e53-123">Child Elements</span></span>  
 <span data-ttu-id="95e53-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="95e53-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95e53-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="95e53-125">Parent Elements</span></span>  
  
|<span data-ttu-id="95e53-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="95e53-126">Element</span></span>|<span data-ttu-id="95e53-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95e53-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="95e53-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="95e53-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="95e53-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="95e53-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95e53-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95e53-130">Remarks</span></span>  
 <span data-ttu-id="95e53-131">Bu ayarı yalnızca geliştirme zamanında kullanın.</span><span class="sxs-lookup"><span data-stu-id="95e53-131">Use this setting only at development time.</span></span> <span data-ttu-id="95e53-132">Çalışma zamanı, DEVPATH 'de bulunan kesin adlı derlemelerin sürümlerini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="95e53-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="95e53-133">Yalnızca bulduğu ilk derlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="95e53-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95e53-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="95e53-134">Example</span></span>  
 <span data-ttu-id="95e53-135">Aşağıdaki örnek, çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramasına neden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="95e53-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95e53-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95e53-136">See also</span></span>

- [<span data-ttu-id="95e53-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="95e53-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="95e53-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="95e53-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="95e53-139">Nasıl yapılır: DEVPATH kullanarak derlemeleri bulma</span><span class="sxs-lookup"><span data-stu-id="95e53-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
