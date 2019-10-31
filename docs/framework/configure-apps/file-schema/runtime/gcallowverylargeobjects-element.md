---
title: <gcAllowVeryLargeObjects> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: b6230833808ec45d702502e36f929db4e03173e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116799"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="b5a2e-102">\<gcAllowVeryLargeObjects > öğesi</span><span class="sxs-lookup"><span data-stu-id="b5a2e-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="b5a2e-103">64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="b5a2e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b5a2e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b5a2e-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="b5a2e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b5a2e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcAllowVeryLargeObjects >**</span><span class="sxs-lookup"><span data-stu-id="b5a2e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a2e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5a2e-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5a2e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5a2e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b5a2e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5a2e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b5a2e-110">Attributes</span></span>  
  
|<span data-ttu-id="b5a2e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b5a2e-111">Attribute</span></span>|<span data-ttu-id="b5a2e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5a2e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b5a2e-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b5a2e-114">Toplam boyutu 2 GB'tan büyük dizilerin 64-Bit platformlarda etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b5a2e-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b5a2e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b5a2e-116">Değer</span><span class="sxs-lookup"><span data-stu-id="b5a2e-116">Value</span></span>|<span data-ttu-id="b5a2e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5a2e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b5a2e-118">Toplam boyutu 2 GB'den büyük diziler etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="b5a2e-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b5a2e-120">Toplam boyutu 2 GB'den büyük diziler 64-bit platformlarda etkindir.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5a2e-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5a2e-121">Child Elements</span></span>  
 <span data-ttu-id="b5a2e-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5a2e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5a2e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b5a2e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b5a2e-124">Element</span></span>|<span data-ttu-id="b5a2e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5a2e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b5a2e-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b5a2e-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5a2e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5a2e-128">Remarks</span></span>  
 <span data-ttu-id="b5a2e-129">Uygulama yapılandırma dosyanızda bu öğenin kullanılması, boyutu 2 GB'tan büyük dizileri etkinleştirir, ancak nesne boyutu veya dizi boyutundaki diğer sınırlamaları değiştirmez:</span><span class="sxs-lookup"><span data-stu-id="b5a2e-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="b5a2e-130">Bir dizideki öğelerin sayısı en fazla şudur: <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="b5a2e-131">Bir bayt dizisi ve tek baytlı yapı dizileri için herhangi tek bir boyuttaki en büyük dizin 2,147,483,591 (0x7FFFFFC7), diğer türler için ise 2,146,435,071'dir (0X7FEFFFFF).</span><span class="sxs-lookup"><span data-stu-id="b5a2e-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="b5a2e-132">Dizeler ve dizi olmayan diğer nesnelerin en büyük boyutu değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b5a2e-133">Bu özelliği etkinleştirmeden önce uygulamanızın, tüm dizilerin 2 GB'dan daha küçük olduğunu varsayan güvenli olmayan kod içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="b5a2e-134">Örneğin, dizileri arabellek olarak kullanan güvenilir olmayan kod, dizilerin 2 GB boyutunu geçmeyeceği varsayımıyla yazılmışsa arabellek aşımlarına maruz kalabilir.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5a2e-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5a2e-135">Example</span></span>  
 <span data-ttu-id="b5a2e-136">Aşağıdaki örnek, bir uygulama için bu özelliğin nasıl etkinleştirileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="b5a2e-137">Destekleyen:</span><span class="sxs-lookup"><span data-stu-id="b5a2e-137">Supported in</span></span>

<span data-ttu-id="b5a2e-138">.NET Framework 4,5 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="b5a2e-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="b5a2e-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5a2e-139">See also</span></span>

- [<span data-ttu-id="b5a2e-140">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b5a2e-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b5a2e-141">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="b5a2e-141">Configuration File Schema</span></span>](../index.md)
