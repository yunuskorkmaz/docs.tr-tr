---
title: "&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e21377b28adb7668108064b770c2c5e0f9fee8f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a><span data-ttu-id="ecc0b-102">&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="ecc0b-102">&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; Element</span></span>
<span data-ttu-id="ecc0b-103">Çalışma zamanı için karma kodları hesaplamak için sabit miktarlı bellek kullanıp kullanmadığını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ecc0b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="ecc0b-104">\<configuration></span></span>  
<span data-ttu-id="ecc0b-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="ecc0b-105">\<runtime></span></span>  
<span data-ttu-id="ecc0b-106">< NetFx45_CultureAwareComparerGetHashCode_LongStrings ></span><span class="sxs-lookup"><span data-stu-id="ecc0b-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc0b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecc0b-107">Syntax</span></span>  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecc0b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecc0b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ecc0b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecc0b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ecc0b-110">Attributes</span></span>  
  
|<span data-ttu-id="ecc0b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ecc0b-111">Attribute</span></span>|<span data-ttu-id="ecc0b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecc0b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ecc0b-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ecc0b-114">Ortak dil çalışma zamanının karma kodları hesaplarken sabit miktarda bellek ayırıp ayırmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ecc0b-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ecc0b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ecc0b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="ecc0b-116">Value</span></span>|<span data-ttu-id="ecc0b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecc0b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecc0b-118">0</span><span class="sxs-lookup"><span data-stu-id="ecc0b-118">0</span></span>|<span data-ttu-id="ecc0b-119">Ortak dil çalışma zamanı bir değişken için bellek miktarı ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodlarını hesaplamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="ecc0b-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-120">This is the default.</span></span>|  
|<span data-ttu-id="ecc0b-121">1.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-121">1</span></span>|<span data-ttu-id="ecc0b-122">Sabit miktarlı bellek için ortak dil çalışma zamanı ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodlarını hesaplamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecc0b-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecc0b-123">Child Elements</span></span>  
 <span data-ttu-id="ecc0b-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecc0b-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecc0b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ecc0b-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecc0b-126">Element</span></span>|<span data-ttu-id="ecc0b-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecc0b-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ecc0b-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ecc0b-129">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-129">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecc0b-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecc0b-130">Remarks</span></span>  
 <span data-ttu-id="ecc0b-131">Varsayılan olarak, ortak dil çalışma zamanı bir değişken için bellek miktarı ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi bir <xref:System.ArgumentException> yöntemi (birkaç milyon karakterden uzun) çok büyük dizeleri karma kodunu işlem girişiminde bulunduğunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="ecc0b-132">Bu öğe bir uygulama yapılandırma dosyası ve ayarı ekleyerek kendi `enabled` özniteliği, belirtin "1", <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi karma kodlarını hesaplama için sabit miktarlı bellek ayırır alternatif bir algoritma kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ecc0b-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Öğesi kullanılan değil [!INCLUDE[win8](../../../../../includes/win8-md.md)] ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc0b-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-134">See Also</span></span>  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="ecc0b-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ecc0b-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ecc0b-136">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ecc0b-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
