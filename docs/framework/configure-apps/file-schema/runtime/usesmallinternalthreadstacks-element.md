---
title: <UseSmallInternalThreadStacks> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 4917b47e9e8196eabe691f74531d12308ef80311
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174088"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="9f53d-102">\<UseSmallInternalThreadStacks> Öğesi</span><span class="sxs-lookup"><span data-stu-id="9f53d-102">\<UseSmallInternalThreadStacks> Element</span></span>

<span data-ttu-id="9f53d-103">Ortak dil çalışma zamanının (CLR), bu iş parçacıkları için varsayılan yığın boyutunu kullanmak yerine, dahili olarak kullandığı belirli iş parçacıklarını oluştururken açık yığın boyutları belirterek bellek kullanımını azaltmalarını ister.</span><span class="sxs-lookup"><span data-stu-id="9f53d-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a><span data-ttu-id="9f53d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9f53d-104">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f53d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f53d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9f53d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f53d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f53d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f53d-107">Attributes</span></span>  
  
|<span data-ttu-id="9f53d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9f53d-108">Attribute</span></span>|<span data-ttu-id="9f53d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f53d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f53d-110">enabled</span><span class="sxs-lookup"><span data-stu-id="9f53d-110">enabled</span></span>|<span data-ttu-id="9f53d-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9f53d-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="9f53d-112">CLR tarafından kullanılan belirli iş parçacıklarını oluşturduğunda, CLR 'nin varsayılan yığın boyutu yerine açık yığın boyutları kullanması istenip istenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f53d-112">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="9f53d-113">Açık yığın boyutları 1 MB varsayılan yığın boyutundan daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="9f53d-113">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9f53d-114">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9f53d-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="9f53d-115">Değer</span><span class="sxs-lookup"><span data-stu-id="9f53d-115">Value</span></span>|<span data-ttu-id="9f53d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f53d-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f53d-117">true</span><span class="sxs-lookup"><span data-stu-id="9f53d-117">true</span></span>|<span data-ttu-id="9f53d-118">Açık yığın boyutları isteyin.</span><span class="sxs-lookup"><span data-stu-id="9f53d-118">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="9f53d-119">yanlış</span><span class="sxs-lookup"><span data-stu-id="9f53d-119">false</span></span>|<span data-ttu-id="9f53d-120">Varsayılan yığın boyutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f53d-120">Use the default stack size.</span></span> <span data-ttu-id="9f53d-121">.NET Framework 4 için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="9f53d-121">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f53d-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f53d-122">Child Elements</span></span>  

 <span data-ttu-id="9f53d-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="9f53d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f53d-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f53d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9f53d-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f53d-125">Element</span></span>|<span data-ttu-id="9f53d-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f53d-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9f53d-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9f53d-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9f53d-128">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9f53d-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f53d-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f53d-129">Remarks</span></span>  

 <span data-ttu-id="9f53d-130">Bu yapılandırma öğesi, CLR 'nin iç iş parçacıkları için kullandığı açık iş parçacığı boyutları, isteğin kabul edildiği varsayılan boyuttan daha küçük olduğu için bir işlemde azaltılmış sanal bellek kullanımını istemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f53d-130">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9f53d-131">Bu yapılandırma öğesi, mutlak bir gereksinim yerine CLR için bir istek.</span><span class="sxs-lookup"><span data-stu-id="9f53d-131">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="9f53d-132">.NET Framework 4 ' te, istek yalnızca x86 mimarisi için kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9f53d-132">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="9f53d-133">Bu öğe, CLR 'nin gelecekteki sürümlerinde tamamen yoksayılabilir veya seçili iç iş parçacıkları için her zaman kullanılan açık yığın boyutlarına göre değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9f53d-133">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="9f53d-134">Bu yapılandırma öğesi, CLR isteği arsa, daha küçük bir yığın boyutu daha büyük olasılıkla yığını daha büyük bir zaman aşabileceğinden, daha küçük sanal bellek kullanımı için güvenilirliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="9f53d-134">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f53d-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f53d-135">Example</span></span>  

 <span data-ttu-id="9f53d-136">Aşağıdaki örnek, CLR 'nin dahili olarak kullandığı belirli iş parçacıkları için açık yığın boyutları kullanma isteğinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f53d-136">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f53d-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f53d-137">See also</span></span>

- [<span data-ttu-id="9f53d-138">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="9f53d-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9f53d-139">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="9f53d-139">Configuration File Schema</span></span>](../index.md)
