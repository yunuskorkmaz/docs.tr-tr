---
description: 'Daha fazla bilgi edinin: <developmentMode> öğesi'
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
ms.openlocfilehash: 668461d13c8a1767268692804e9783bb6d4b9a56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787129"
---
# <a name="developmentmode-element"></a><span data-ttu-id="272ed-103">\<developmentMode> Öğesi</span><span class="sxs-lookup"><span data-stu-id="272ed-103">\<developmentMode> Element</span></span>

<span data-ttu-id="272ed-104">Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="272ed-104">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="272ed-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="272ed-105">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="272ed-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="272ed-106">Attributes and Elements</span></span>  

 <span data-ttu-id="272ed-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="272ed-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="272ed-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="272ed-108">Attributes</span></span>  
  
|<span data-ttu-id="272ed-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="272ed-109">Attribute</span></span>|<span data-ttu-id="272ed-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="272ed-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="272ed-111">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="272ed-111">**developerInstallation**</span></span>|<span data-ttu-id="272ed-112">Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="272ed-112">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="272ed-113">developerInstallation özniteliği</span><span class="sxs-lookup"><span data-stu-id="272ed-113">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="272ed-114">Değer</span><span class="sxs-lookup"><span data-stu-id="272ed-114">Value</span></span>|<span data-ttu-id="272ed-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="272ed-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="272ed-116">**değeri**</span><span class="sxs-lookup"><span data-stu-id="272ed-116">**true**</span></span>|<span data-ttu-id="272ed-117">DEVPATH ortam değişkeni tarafından belirtilen dizinlerdeki derlemeleri arar.</span><span class="sxs-lookup"><span data-stu-id="272ed-117">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="272ed-118">**yanlýþ**</span><span class="sxs-lookup"><span data-stu-id="272ed-118">**false**</span></span>|<span data-ttu-id="272ed-119">, DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramaz.</span><span class="sxs-lookup"><span data-stu-id="272ed-119">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="272ed-120">Bu, varsayılan</span><span class="sxs-lookup"><span data-stu-id="272ed-120">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="272ed-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="272ed-121">Child Elements</span></span>  

 <span data-ttu-id="272ed-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="272ed-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="272ed-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="272ed-123">Parent Elements</span></span>  
  
|<span data-ttu-id="272ed-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="272ed-124">Element</span></span>|<span data-ttu-id="272ed-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="272ed-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="272ed-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="272ed-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="272ed-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="272ed-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="272ed-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="272ed-128">Remarks</span></span>  

 <span data-ttu-id="272ed-129">Bu ayarı yalnızca geliştirme zamanında kullanın.</span><span class="sxs-lookup"><span data-stu-id="272ed-129">Use this setting only at development time.</span></span> <span data-ttu-id="272ed-130">Çalışma zamanı, DEVPATH 'de bulunan kesin adlı derlemelerin sürümlerini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="272ed-130">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="272ed-131">Yalnızca bulduğu ilk derlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="272ed-131">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="272ed-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="272ed-132">Example</span></span>  

 <span data-ttu-id="272ed-133">Aşağıdaki örnek, çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramasına neden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="272ed-133">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="272ed-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="272ed-134">See also</span></span>

- [<span data-ttu-id="272ed-135">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="272ed-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="272ed-136">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="272ed-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="272ed-137">Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma</span><span class="sxs-lookup"><span data-stu-id="272ed-137">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
