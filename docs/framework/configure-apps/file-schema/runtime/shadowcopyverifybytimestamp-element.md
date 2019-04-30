---
title: <shadowCopyVerifyByTimestamp> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad61b3824b8155cf3f68f61865891c023b4cf32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674018"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="fd8ad-102">\<shadowCopyVerifyByTimestamp > öğesi</span><span class="sxs-lookup"><span data-stu-id="fd8ad-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="fd8ad-103">Gölge kopyalama sunulan varsayılan başlangıç davranışını kullanıp kullanmayacağını belirtir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], veya .NET Framework'ün önceki sürümlerinde başlangıç davranışını geri döner.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="fd8ad-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="fd8ad-104">\<configuration> Element</span></span>  
<span data-ttu-id="fd8ad-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="fd8ad-105">\<runtime> Element</span></span>  
<span data-ttu-id="fd8ad-106">\<shadowCopyVerifyByTimestamp > öğesi</span><span class="sxs-lookup"><span data-stu-id="fd8ad-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8ad-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd8ad-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd8ad-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd8ad-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fd8ad-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd8ad-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd8ad-110">Attributes</span></span>  
  
|<span data-ttu-id="fd8ad-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd8ad-111">Attribute</span></span>|<span data-ttu-id="fd8ad-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd8ad-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd8ad-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="fd8ad-113">enabled</span></span>|<span data-ttu-id="fd8ad-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="fd8ad-115">Gölge kopyalama kullanan bir uygulama etki alanları önce gölge kopyalama bütünleştirilmiş kod derleme güncelleştirilip güncelleştirilmediğini belirlemek için başlatma sırasında derleme zaman damgaları karşılaştırma olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fd8ad-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd8ad-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="fd8ad-117">Değer</span><span class="sxs-lookup"><span data-stu-id="fd8ad-117">Value</span></span>|<span data-ttu-id="fd8ad-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd8ad-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd8ad-119">true</span><span class="sxs-lookup"><span data-stu-id="fd8ad-119">true</span></span>|<span data-ttu-id="fd8ad-120">Başlangıçta, yalnızca son gölge kopya dizine kopyalanan bu yana güncelleştirilen derlemeleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="fd8ad-121">İçin varsayılan [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd8ad-121">This is the default for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>|  
|<span data-ttu-id="fd8ad-122">false</span><span class="sxs-lookup"><span data-stu-id="fd8ad-122">false</span></span>|<span data-ttu-id="fd8ad-123">.NET Framework'ün önceki sürümlerini başlangıç davranışını, başlangıçta tüm dosyaları kopyalamak için olduğu döner.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd8ad-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd8ad-124">Child Elements</span></span>  
 <span data-ttu-id="fd8ad-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd8ad-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd8ad-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fd8ad-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd8ad-127">Element</span></span>|<span data-ttu-id="fd8ad-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd8ad-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fd8ad-129">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fd8ad-130">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd8ad-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd8ad-131">Remarks</span></span>  
 <span data-ttu-id="fd8ad-132">İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], yalnızca kendi zaman damgaları gölge kopya dizine son kopyalanan olduğundan bunlar değişmiş gösteriyorsa gölge derlemelerdir.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="fd8ad-133">Bu bölümünde anlatıldığı gibi gölge kopyalama, kullanma, birçok uygulama için başlangıç sürelerini iyileştirir [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="fd8ad-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="fd8ad-134">Yüksek yüzdesi ve derleme güncelleştirme sıklığına sahip uygulamalar, bu değişiklik davranış avantajlı olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="fd8ad-135">Bu durumda, bu öğe, .NET Framework'ün önceki sürümlerini davranışı geri yüklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd8ad-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd8ad-136">Example</span></span>  
 <span data-ttu-id="fd8ad-137">Aşağıdaki örnek, gölge kopyalama varsayılan başlangıç davranışını devre dışı bırakma gösterir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]ve .NET Framework'ün önceki sürümlerini başlangıç davranışını geri döndür.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-137">The following example shows how to disable the default startup behavior of shadow copying in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd8ad-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd8ad-138">See also</span></span>

- [<span data-ttu-id="fd8ad-139">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fd8ad-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="fd8ad-140">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="fd8ad-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="fd8ad-141">Gölge Kopyalama Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="fd8ad-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
