---
title: '&lt;gcAllowVeryLargeObjects&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5e0a443f86848a446a7233a2c2e80f693cae9be
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611418"
---
# <a name="ltgcallowverylargeobjectsgt-element"></a><span data-ttu-id="16e41-102">&lt;gcAllowVeryLargeObjects&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="16e41-102">&lt;gcAllowVeryLargeObjects&gt; Element</span></span>
<span data-ttu-id="16e41-103">64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="16e41-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="16e41-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="16e41-104">\<configuration> Element</span></span>  
<span data-ttu-id="16e41-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="16e41-105">\<runtime> Element</span></span>  
<span data-ttu-id="16e41-106">\<gcAllowVeryLargeObjects > öğesi</span><span class="sxs-lookup"><span data-stu-id="16e41-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e41-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16e41-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16e41-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="16e41-108">Attributes and Elements</span></span>  
 <span data-ttu-id="16e41-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16e41-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16e41-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="16e41-110">Attributes</span></span>  
  
|<span data-ttu-id="16e41-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="16e41-111">Attribute</span></span>|<span data-ttu-id="16e41-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16e41-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="16e41-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="16e41-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="16e41-114">Toplam boyutu 2 GB'tan büyük dizilerin 64-Bit platformlarda etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="16e41-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="16e41-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="16e41-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="16e41-116">Değer</span><span class="sxs-lookup"><span data-stu-id="16e41-116">Value</span></span>|<span data-ttu-id="16e41-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16e41-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="16e41-118">Toplam boyutu 2 GB'den büyük diziler etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="16e41-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="16e41-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="16e41-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="16e41-120">Toplam boyutu 2 GB'den büyük diziler 64-bit platformlarda etkindir.</span><span class="sxs-lookup"><span data-stu-id="16e41-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16e41-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="16e41-121">Child Elements</span></span>  
 <span data-ttu-id="16e41-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="16e41-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16e41-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="16e41-123">Parent Elements</span></span>  
  
|<span data-ttu-id="16e41-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="16e41-124">Element</span></span>|<span data-ttu-id="16e41-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16e41-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16e41-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="16e41-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16e41-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="16e41-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16e41-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16e41-128">Remarks</span></span>  
 <span data-ttu-id="16e41-129">Uygulama yapılandırma dosyanızda bu öğenin kullanılması, boyutu 2 GB'tan büyük dizileri etkinleştirir, ancak nesne boyutu veya dizi boyutundaki diğer sınırlamaları değiştirmez:</span><span class="sxs-lookup"><span data-stu-id="16e41-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
-   <span data-ttu-id="16e41-130">Bir dizideki öğelerin sayısı en fazla şudur: <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16e41-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="16e41-131">Bir bayt dizisi ve tek baytlı yapı dizileri için herhangi tek bir boyuttaki en büyük dizin 2,147,483,591 (0x7FFFFFC7), diğer türler için ise 2,146,435,071'dir (0X7FEFFFFF).</span><span class="sxs-lookup"><span data-stu-id="16e41-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
-   <span data-ttu-id="16e41-132">Dizeler ve dizi olmayan diğer nesnelerin en büyük boyutu değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="16e41-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="16e41-133">Bu özelliği etkinleştirmeden önce uygulamanızın, tüm dizilerin 2 GB'dan daha küçük olduğunu varsayan güvenli olmayan kod içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="16e41-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="16e41-134">Örneğin, dizileri arabellek olarak kullanan güvenilir olmayan kod, dizilerin 2 GB boyutunu geçmeyeceği varsayımıyla yazılmışsa arabellek aşımlarına maruz kalabilir.</span><span class="sxs-lookup"><span data-stu-id="16e41-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16e41-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="16e41-135">Example</span></span>  
 <span data-ttu-id="16e41-136">Aşağıdaki örnek, bir uygulama için bu özelliğin nasıl etkinleştirileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="16e41-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16e41-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16e41-137">See Also</span></span>  
- [<span data-ttu-id="16e41-138">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="16e41-138">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="16e41-139">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="16e41-139">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
