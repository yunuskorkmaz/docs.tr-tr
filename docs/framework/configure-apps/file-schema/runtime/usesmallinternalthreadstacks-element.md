---
title: <UseSmallInternalThreadStacks> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74678089bb1b19295983064eb7ad54fbf0a1e361
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663383"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="ce8af-102">\<Usesmallınternalthreadyığınları > öğesi</span><span class="sxs-lookup"><span data-stu-id="ce8af-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="ce8af-103">Ortak dil çalışma zamanının (CLR), bu iş parçacıkları için varsayılan yığın boyutunu kullanmak yerine, dahili olarak kullandığı belirli iş parçacıklarını oluştururken açık yığın boyutları belirterek bellek kullanımını azaltmalarını ister.</span><span class="sxs-lookup"><span data-stu-id="ce8af-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="ce8af-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="ce8af-104">\<configuration> Element</span></span>  
<span data-ttu-id="ce8af-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="ce8af-105">\<runtime> Element</span></span>  
<span data-ttu-id="ce8af-106">\<Usesmallınternalthreadyığınları > öğesi</span><span class="sxs-lookup"><span data-stu-id="ce8af-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce8af-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce8af-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce8af-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce8af-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ce8af-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ce8af-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce8af-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ce8af-110">Attributes</span></span>  
  
|<span data-ttu-id="ce8af-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ce8af-111">Attribute</span></span>|<span data-ttu-id="ce8af-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce8af-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce8af-113">etkinletir</span><span class="sxs-lookup"><span data-stu-id="ce8af-113">enabled</span></span>|<span data-ttu-id="ce8af-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ce8af-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce8af-115">CLR tarafından kullanılan belirli iş parçacıklarını oluşturduğunda, CLR 'nin varsayılan yığın boyutu yerine açık yığın boyutları kullanması istenip istenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce8af-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="ce8af-116">Açık yığın boyutları 1 MB varsayılan yığın boyutundan daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="ce8af-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ce8af-117">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ce8af-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="ce8af-118">Değer</span><span class="sxs-lookup"><span data-stu-id="ce8af-118">Value</span></span>|<span data-ttu-id="ce8af-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce8af-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce8af-120">true</span><span class="sxs-lookup"><span data-stu-id="ce8af-120">true</span></span>|<span data-ttu-id="ce8af-121">Açık yığın boyutları isteyin.</span><span class="sxs-lookup"><span data-stu-id="ce8af-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="ce8af-122">false</span><span class="sxs-lookup"><span data-stu-id="ce8af-122">false</span></span>|<span data-ttu-id="ce8af-123">Varsayılan yığın boyutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ce8af-123">Use the default stack size.</span></span> <span data-ttu-id="ce8af-124">.NET Framework 4 için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="ce8af-124">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce8af-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce8af-125">Child Elements</span></span>  
 <span data-ttu-id="ce8af-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="ce8af-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce8af-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce8af-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ce8af-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="ce8af-128">Element</span></span>|<span data-ttu-id="ce8af-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce8af-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce8af-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ce8af-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ce8af-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ce8af-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce8af-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce8af-132">Remarks</span></span>  
 <span data-ttu-id="ce8af-133">Bu yapılandırma öğesi, CLR 'nin iç iş parçacıkları için kullandığı açık iş parçacığı boyutları, isteğin kabul edildiği varsayılan boyuttan daha küçük olduğu için bir işlemde azaltılmış sanal bellek kullanımını istemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce8af-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ce8af-134">Bu yapılandırma öğesi, mutlak bir gereksinim yerine CLR için bir istek.</span><span class="sxs-lookup"><span data-stu-id="ce8af-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="ce8af-135">.NET Framework 4 ' te, istek yalnızca x86 mimarisi için kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ce8af-135">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="ce8af-136">Bu öğe, CLR 'nin gelecekteki sürümlerinde tamamen yoksayılabilir veya seçili iç iş parçacıkları için her zaman kullanılan açık yığın boyutlarına göre değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ce8af-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="ce8af-137">Bu yapılandırma öğesi, CLR isteği arsa, daha küçük bir yığın boyutu daha büyük olasılıkla yığını daha büyük bir zaman aşabileceğinden, daha küçük sanal bellek kullanımı için güvenilirliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="ce8af-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce8af-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce8af-138">Example</span></span>  
 <span data-ttu-id="ce8af-139">Aşağıdaki örnek, CLR 'nin dahili olarak kullandığı belirli iş parçacıkları için açık yığın boyutları kullanma isteğinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce8af-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce8af-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce8af-140">See also</span></span>

- [<span data-ttu-id="ce8af-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ce8af-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ce8af-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ce8af-142">Configuration File Schema</span></span>](../index.md)
