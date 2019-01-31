---
title: <UseSmallInternalThreadStacks> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d78d03956db3f50b4d01f06c9a6438afd62fac5d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289802"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="12c91-102">\<Usesmallınternalthreadstacks > öğesi</span><span class="sxs-lookup"><span data-stu-id="12c91-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="12c91-103">Ortak dil çalışma zamanı (CLR) bellek miktarını azaltmak istekleri, dahili olarak, bu iş parçacıkları için varsayılan yığın boyutu kullanmak yerine kullanan belirli iş parçacıklarını oluşturduğunda açık yığın boyutlarını belirterek kullanır.</span><span class="sxs-lookup"><span data-stu-id="12c91-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="12c91-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="12c91-104">\<configuration> Element</span></span>  
<span data-ttu-id="12c91-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="12c91-105">\<runtime> Element</span></span>  
<span data-ttu-id="12c91-106">\<Usesmallınternalthreadstacks > öğesi</span><span class="sxs-lookup"><span data-stu-id="12c91-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c91-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12c91-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12c91-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="12c91-108">Attributes and Elements</span></span>  
 <span data-ttu-id="12c91-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12c91-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12c91-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12c91-110">Attributes</span></span>  
  
|<span data-ttu-id="12c91-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="12c91-111">Attribute</span></span>|<span data-ttu-id="12c91-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12c91-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12c91-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="12c91-113">enabled</span></span>|<span data-ttu-id="12c91-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="12c91-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="12c91-115">Dahili olarak kullandığı belirli bir iş parçacığı oluşturur CLR kullanın açık yığın boyutu varsayılan yığın boyutu yerine, istenip istenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="12c91-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="12c91-116">Açık yığın boyutu varsayılan yığın boyutu 1 MB küçüktür.</span><span class="sxs-lookup"><span data-stu-id="12c91-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="12c91-117">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="12c91-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="12c91-118">Değer</span><span class="sxs-lookup"><span data-stu-id="12c91-118">Value</span></span>|<span data-ttu-id="12c91-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12c91-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="12c91-120">true</span><span class="sxs-lookup"><span data-stu-id="12c91-120">true</span></span>|<span data-ttu-id="12c91-121">Açık yığın boyutlarını isteyin.</span><span class="sxs-lookup"><span data-stu-id="12c91-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="12c91-122">false</span><span class="sxs-lookup"><span data-stu-id="12c91-122">false</span></span>|<span data-ttu-id="12c91-123">Varsayılan yığın boyutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="12c91-123">Use the default stack size.</span></span> <span data-ttu-id="12c91-124">İçin varsayılan [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12c91-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12c91-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="12c91-125">Child Elements</span></span>  
 <span data-ttu-id="12c91-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="12c91-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12c91-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="12c91-127">Parent Elements</span></span>  
  
|<span data-ttu-id="12c91-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="12c91-128">Element</span></span>|<span data-ttu-id="12c91-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12c91-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="12c91-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="12c91-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="12c91-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="12c91-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12c91-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12c91-132">Remarks</span></span>  
 <span data-ttu-id="12c91-133">İstek dikkate alınır, iç iş parçacıkları için CLR kullanan açık bir iş parçacığı boyutları varsayılan boyuttan daha küçük olduğundan, bu yapılandırma öğesi, bir işlemde daha az sanal bellek kullanımı istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12c91-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="12c91-134">Bu yapılandırma öğesi, mutlak bir gereksinim yerine CLR isteğidir.</span><span class="sxs-lookup"><span data-stu-id="12c91-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="12c91-135">İçinde [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], isteğin yalnızca x86 için geçerli olur mimarisi.</span><span class="sxs-lookup"><span data-stu-id="12c91-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="12c91-136">Bu öğe CLR'ın gelecek sürümlerinde tamamen yoksayıldı ya da seçili iç iş parçacıkları için kullanılan her zaman açık yığın boyutlarını değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="12c91-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="12c91-137">CLR, isteği kabul eder, daha küçük yığın boyutlarını yığın olası hale getirebilecek çünkü bu yapılandırma öğesi daha küçük sanal bellek kullanımı için güvenilirlik arasında denge kurar belirterek büyük olasılıkla taşıyor.</span><span class="sxs-lookup"><span data-stu-id="12c91-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12c91-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="12c91-138">Example</span></span>  
 <span data-ttu-id="12c91-139">Aşağıdaki örnek, CLR kullanım açık yığın belirli dahili olarak kullandığı iş parçacıklarının boyutları istek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="12c91-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="12c91-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12c91-140">See also</span></span>
- [<span data-ttu-id="12c91-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="12c91-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="12c91-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="12c91-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
