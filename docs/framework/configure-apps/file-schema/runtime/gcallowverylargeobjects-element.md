---
title: <gcAllowVeryLargeObjects> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 78a42596aae6c3ea0d94ac759d11ed52d0ace539
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178235"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="f9e87-102">\<gcAllowVeryLargeObjects> Öğesi</span><span class="sxs-lookup"><span data-stu-id="f9e87-102">\<gcAllowVeryLargeObjects> Element</span></span>

<span data-ttu-id="f9e87-103">64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="f9e87-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="f9e87-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9e87-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9e87-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9e87-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f9e87-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9e87-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9e87-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9e87-107">Attributes</span></span>  
  
|<span data-ttu-id="f9e87-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9e87-108">Attribute</span></span>|<span data-ttu-id="f9e87-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9e87-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f9e87-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f9e87-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="f9e87-111">Toplam boyutu 2 GB'tan büyük dizilerin 64-Bit platformlarda etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9e87-111">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f9e87-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9e87-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="f9e87-113">Değer</span><span class="sxs-lookup"><span data-stu-id="f9e87-113">Value</span></span>|<span data-ttu-id="f9e87-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9e87-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f9e87-115">Toplam boyutu 2 GB'den büyük diziler etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="f9e87-115">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="f9e87-116">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="f9e87-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f9e87-117">Toplam boyutu 2 GB'den büyük diziler 64-bit platformlarda etkindir.</span><span class="sxs-lookup"><span data-stu-id="f9e87-117">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9e87-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9e87-118">Child Elements</span></span>  

 <span data-ttu-id="f9e87-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9e87-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9e87-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9e87-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f9e87-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9e87-121">Element</span></span>|<span data-ttu-id="f9e87-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9e87-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f9e87-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f9e87-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f9e87-124">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f9e87-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9e87-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9e87-125">Remarks</span></span>  

 <span data-ttu-id="f9e87-126">Uygulama yapılandırma dosyanızda bu öğenin kullanılması, boyutu 2 GB'tan büyük dizileri etkinleştirir, ancak nesne boyutu veya dizi boyutundaki diğer sınırlamaları değiştirmez:</span><span class="sxs-lookup"><span data-stu-id="f9e87-126">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="f9e87-127">Bir dizideki öğelerin sayısı en fazla şudur: <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9e87-127">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f9e87-128">Bir bayt dizisi ve tek baytlı yapı dizileri için herhangi tek bir boyuttaki en büyük dizin 2,147,483,591 (0x7FFFFFC7), diğer türler için ise 2,146,435,071'dir (0X7FEFFFFF).</span><span class="sxs-lookup"><span data-stu-id="f9e87-128">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="f9e87-129">Dizeler ve dizi olmayan diğer nesnelerin en büyük boyutu değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="f9e87-129">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f9e87-130">Bu özelliği etkinleştirmeden önce uygulamanızın, tüm dizilerin 2 GB'dan daha küçük olduğunu varsayan güvenli olmayan kod içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f9e87-130">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="f9e87-131">Örneğin, dizileri arabellek olarak kullanan güvenilir olmayan kod, dizilerin 2 GB boyutunu geçmeyeceği varsayımıyla yazılmışsa arabellek aşımlarına maruz kalabilir.</span><span class="sxs-lookup"><span data-stu-id="f9e87-131">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9e87-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9e87-132">Example</span></span>  

 <span data-ttu-id="f9e87-133">Aşağıdaki örnek, bir uygulama için bu özelliğin nasıl etkinleştirileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f9e87-133">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="f9e87-134">Destekleyen:</span><span class="sxs-lookup"><span data-stu-id="f9e87-134">Supported in</span></span>

<span data-ttu-id="f9e87-135">.NET Framework 4,5 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="f9e87-135">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="f9e87-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9e87-136">See also</span></span>

- [<span data-ttu-id="f9e87-137">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="f9e87-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f9e87-138">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="f9e87-138">Configuration File Schema</span></span>](../index.md)
