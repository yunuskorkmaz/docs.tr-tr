---
description: 'Daha fazla bilgi edinin: <gcAllowVeryLargeObjects> öğesi'
title: gcAllowVeryLargeObjects öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: ff8380a13c4284cc24178e185344207c3b9a39b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787025"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="9ea63-103">\<gcAllowVeryLargeObjects> öğesi</span><span class="sxs-lookup"><span data-stu-id="9ea63-103">\<gcAllowVeryLargeObjects> element</span></span>

<span data-ttu-id="9ea63-104">64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="9ea63-104">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="9ea63-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ea63-105">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a><span data-ttu-id="9ea63-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9ea63-106">Attributes</span></span>
  
|<span data-ttu-id="9ea63-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9ea63-107">Attribute</span></span>|<span data-ttu-id="9ea63-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ea63-108">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9ea63-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9ea63-109">Required attribute.</span></span><br /><br /> <span data-ttu-id="9ea63-110">Toplam boyutu 2 GB'tan büyük dizilerin 64-Bit platformlarda etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ea63-110">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="9ea63-111">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="9ea63-111">enabled attribute</span></span>  
  
|<span data-ttu-id="9ea63-112">Değer</span><span class="sxs-lookup"><span data-stu-id="9ea63-112">Value</span></span>|<span data-ttu-id="9ea63-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ea63-113">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="9ea63-114">Toplam boyutu 2 GB'den büyük diziler etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="9ea63-114">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="9ea63-115">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9ea63-115">This is the default.</span></span>|  
|`true`|<span data-ttu-id="9ea63-116">Toplam boyutu 2 GB'den büyük diziler 64-bit platformlarda etkindir.</span><span class="sxs-lookup"><span data-stu-id="9ea63-116">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="9ea63-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="9ea63-117">Child elements</span></span>  

<span data-ttu-id="9ea63-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="9ea63-118">None.</span></span>  
  
## <a name="parent-elements"></a><span data-ttu-id="9ea63-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="9ea63-119">Parent elements</span></span>
  
|<span data-ttu-id="9ea63-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ea63-120">Element</span></span>|<span data-ttu-id="9ea63-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ea63-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9ea63-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9ea63-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9ea63-123">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9ea63-123">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ea63-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ea63-124">Remarks</span></span>  

 <span data-ttu-id="9ea63-125">Uygulama yapılandırma dosyanızda bu öğenin kullanılması, boyutu 2 GB'tan büyük dizileri etkinleştirir, ancak nesne boyutu veya dizi boyutundaki diğer sınırlamaları değiştirmez:</span><span class="sxs-lookup"><span data-stu-id="9ea63-125">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="9ea63-126">Bir dizideki öğelerin sayısı en fazla şudur: <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9ea63-126">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="9ea63-127">Tek boyuttaki maksimum boyut, bayt dizileri ve tek baytlık yapıların dizileri için 2.147.483.591 (0x7FFFFFC7) ve diğer türleri içeren diziler için 2.146.435.071 (0X7FEFFFFF).</span><span class="sxs-lookup"><span data-stu-id="9ea63-127">The maximum size in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for arrays containing other types.</span></span>  
  
- <span data-ttu-id="9ea63-128">Dizeler ve dizi olmayan diğer nesnelerin en büyük boyutu değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="9ea63-128">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9ea63-129">Bu özelliği etkinleştirmeden önce uygulamanızın, tüm dizilerin 2 GB'dan daha küçük olduğunu varsayan güvenli olmayan kod içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9ea63-129">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="9ea63-130">Örneğin, arabellekler olarak dizileri kullanan güvenli olmayan kod, dizilerin 2 GB 'ı aşmaması durumunda yazılmışsa arabellek taşmalarına açıktır.</span><span class="sxs-lookup"><span data-stu-id="9ea63-130">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it's written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ea63-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ea63-131">Example</span></span>  

 <span data-ttu-id="9ea63-132">Aşağıdaki örnek, bir uygulama için bu özelliğin nasıl etkinleştirileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9ea63-132">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="9ea63-133">Destekleyen:</span><span class="sxs-lookup"><span data-stu-id="9ea63-133">Supported in</span></span>

<span data-ttu-id="9ea63-134">.NET Framework 4,5 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="9ea63-134">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="9ea63-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ea63-135">See also</span></span>

- [<span data-ttu-id="9ea63-136">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="9ea63-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9ea63-137">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="9ea63-137">Configuration File Schema</span></span>](../index.md)
