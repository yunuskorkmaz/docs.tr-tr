---
title: gcAllowVeryLargeObjects öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 1e54b0780ffb5bbe81ab1be2b376ff7a038ee05c
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058135"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="f1afa-102">\<gcAllowVeryLargeObjects> öğesi</span><span class="sxs-lookup"><span data-stu-id="f1afa-102">\<gcAllowVeryLargeObjects> element</span></span>

<span data-ttu-id="f1afa-103">64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="f1afa-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="f1afa-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f1afa-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a><span data-ttu-id="f1afa-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f1afa-105">Attributes</span></span>
  
|<span data-ttu-id="f1afa-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f1afa-106">Attribute</span></span>|<span data-ttu-id="f1afa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1afa-107">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f1afa-108">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f1afa-108">Required attribute.</span></span><br /><br /> <span data-ttu-id="f1afa-109">Toplam boyutu 2 GB'tan büyük dizilerin 64-Bit platformlarda etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1afa-109">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="f1afa-110">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="f1afa-110">enabled attribute</span></span>  
  
|<span data-ttu-id="f1afa-111">Değer</span><span class="sxs-lookup"><span data-stu-id="f1afa-111">Value</span></span>|<span data-ttu-id="f1afa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1afa-112">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f1afa-113">Toplam boyutu 2 GB'den büyük diziler etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="f1afa-113">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="f1afa-114">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="f1afa-114">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f1afa-115">Toplam boyutu 2 GB'den büyük diziler 64-bit platformlarda etkindir.</span><span class="sxs-lookup"><span data-stu-id="f1afa-115">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="f1afa-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f1afa-116">Child elements</span></span>  

<span data-ttu-id="f1afa-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="f1afa-117">None.</span></span>  
  
## <a name="parent-elements"></a><span data-ttu-id="f1afa-118">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f1afa-118">Parent elements</span></span>
  
|<span data-ttu-id="f1afa-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="f1afa-119">Element</span></span>|<span data-ttu-id="f1afa-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1afa-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f1afa-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f1afa-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f1afa-122">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f1afa-122">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1afa-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1afa-123">Remarks</span></span>  

 <span data-ttu-id="f1afa-124">Uygulama yapılandırma dosyanızda bu öğenin kullanılması, boyutu 2 GB'tan büyük dizileri etkinleştirir, ancak nesne boyutu veya dizi boyutundaki diğer sınırlamaları değiştirmez:</span><span class="sxs-lookup"><span data-stu-id="f1afa-124">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="f1afa-125">Bir dizideki öğelerin sayısı en fazla şudur: <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1afa-125">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f1afa-126">Tek boyuttaki maksimum boyut, bayt dizileri ve tek baytlık yapıların dizileri için 2.147.483.591 (0x7FFFFFC7) ve diğer türleri içeren diziler için 2.146.435.071 (0X7FEFFFFF).</span><span class="sxs-lookup"><span data-stu-id="f1afa-126">The maximum size in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for arrays containing other types.</span></span>  
  
- <span data-ttu-id="f1afa-127">Dizeler ve dizi olmayan diğer nesnelerin en büyük boyutu değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="f1afa-127">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f1afa-128">Bu özelliği etkinleştirmeden önce uygulamanızın, tüm dizilerin 2 GB'dan daha küçük olduğunu varsayan güvenli olmayan kod içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f1afa-128">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="f1afa-129">Örneğin, arabellekler olarak dizileri kullanan güvenli olmayan kod, dizilerin 2 GB 'ı aşmaması durumunda yazılmışsa arabellek taşmalarına açıktır.</span><span class="sxs-lookup"><span data-stu-id="f1afa-129">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it's written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1afa-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1afa-130">Example</span></span>  

 <span data-ttu-id="f1afa-131">Aşağıdaki örnek, bir uygulama için bu özelliğin nasıl etkinleştirileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f1afa-131">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="f1afa-132">Destekleyen:</span><span class="sxs-lookup"><span data-stu-id="f1afa-132">Supported in</span></span>

<span data-ttu-id="f1afa-133">.NET Framework 4,5 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="f1afa-133">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="f1afa-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1afa-134">See also</span></span>

- [<span data-ttu-id="f1afa-135">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="f1afa-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f1afa-136">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="f1afa-136">Configuration File Schema</span></span>](../index.md)
