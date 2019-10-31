---
title: <UseSmallInternalThreadStacks> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 2fd776ce8605e6dcf288dcb3852ded16638a1873
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114921"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="9937e-102">\<Usesmallınternalthreadyığınları > öğesi</span><span class="sxs-lookup"><span data-stu-id="9937e-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="9937e-103">Ortak dil çalışma zamanının (CLR), bu iş parçacıkları için varsayılan yığın boyutunu kullanmak yerine, dahili olarak kullandığı belirli iş parçacıklarını oluştururken açık yığın boyutları belirterek bellek kullanımını azaltmalarını ister.</span><span class="sxs-lookup"><span data-stu-id="9937e-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
<span data-ttu-id="9937e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9937e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9937e-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="9937e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="9937e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Usesmallınternalthreadyığınları >**</span><span class="sxs-lookup"><span data-stu-id="9937e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9937e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9937e-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9937e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9937e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9937e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9937e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9937e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9937e-110">Attributes</span></span>  
  
|<span data-ttu-id="9937e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9937e-111">Attribute</span></span>|<span data-ttu-id="9937e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9937e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9937e-113">etkinletir</span><span class="sxs-lookup"><span data-stu-id="9937e-113">enabled</span></span>|<span data-ttu-id="9937e-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9937e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="9937e-115">CLR tarafından kullanılan belirli iş parçacıklarını oluşturduğunda, CLR 'nin varsayılan yığın boyutu yerine açık yığın boyutları kullanması istenip istenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9937e-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="9937e-116">Açık yığın boyutları 1 MB varsayılan yığın boyutundan daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="9937e-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9937e-117">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9937e-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="9937e-118">Değer</span><span class="sxs-lookup"><span data-stu-id="9937e-118">Value</span></span>|<span data-ttu-id="9937e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9937e-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9937e-120">true</span><span class="sxs-lookup"><span data-stu-id="9937e-120">true</span></span>|<span data-ttu-id="9937e-121">Açık yığın boyutları isteyin.</span><span class="sxs-lookup"><span data-stu-id="9937e-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="9937e-122">false</span><span class="sxs-lookup"><span data-stu-id="9937e-122">false</span></span>|<span data-ttu-id="9937e-123">Varsayılan yığın boyutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9937e-123">Use the default stack size.</span></span> <span data-ttu-id="9937e-124">.NET Framework 4 için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="9937e-124">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9937e-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9937e-125">Child Elements</span></span>  
 <span data-ttu-id="9937e-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="9937e-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9937e-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9937e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9937e-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="9937e-128">Element</span></span>|<span data-ttu-id="9937e-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9937e-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9937e-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9937e-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9937e-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9937e-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9937e-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9937e-132">Remarks</span></span>  
 <span data-ttu-id="9937e-133">Bu yapılandırma öğesi, CLR 'nin iç iş parçacıkları için kullandığı açık iş parçacığı boyutları, isteğin kabul edildiği varsayılan boyuttan daha küçük olduğu için bir işlemde azaltılmış sanal bellek kullanımını istemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9937e-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9937e-134">Bu yapılandırma öğesi, mutlak bir gereksinim yerine CLR için bir istek.</span><span class="sxs-lookup"><span data-stu-id="9937e-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="9937e-135">.NET Framework 4 ' te, istek yalnızca x86 mimarisi için kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9937e-135">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="9937e-136">Bu öğe, CLR 'nin gelecekteki sürümlerinde tamamen yoksayılabilir veya seçili iç iş parçacıkları için her zaman kullanılan açık yığın boyutlarına göre değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9937e-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="9937e-137">Bu yapılandırma öğesi, CLR isteği arsa, daha küçük bir yığın boyutu daha büyük olasılıkla yığını daha büyük bir zaman aşabileceğinden, daha küçük sanal bellek kullanımı için güvenilirliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="9937e-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9937e-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="9937e-138">Example</span></span>  
 <span data-ttu-id="9937e-139">Aşağıdaki örnek, CLR 'nin dahili olarak kullandığı belirli iş parçacıkları için açık yığın boyutları kullanma isteğinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9937e-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9937e-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9937e-140">See also</span></span>

- [<span data-ttu-id="9937e-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="9937e-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9937e-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="9937e-142">Configuration File Schema</span></span>](../index.md)
