---
title: '&lt;shadowCopyVerifyByTimestamp&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2439a4812163562a73bd3520e65b9973e666a863
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749731"
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a><span data-ttu-id="e265b-102">&lt;shadowCopyVerifyByTimestamp&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="e265b-102">&lt;shadowCopyVerifyByTimestamp&gt; Element</span></span>
<span data-ttu-id="e265b-103">Gölge kopyalama sunulan varsayılan başlangıç davranışını kullanıp kullanmadığını belirtir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], veya .NET Framework'ün önceki sürümlerinde başlangıç davranışını döner.</span><span class="sxs-lookup"><span data-stu-id="e265b-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="e265b-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="e265b-104">\<configuration> Element</span></span>  
<span data-ttu-id="e265b-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="e265b-105">\<runtime> Element</span></span>  
<span data-ttu-id="e265b-106">\<shadowCopyVerifyByTimestamp > öğesi</span><span class="sxs-lookup"><span data-stu-id="e265b-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e265b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e265b-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e265b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e265b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e265b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e265b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e265b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e265b-110">Attributes</span></span>  
  
|<span data-ttu-id="e265b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e265b-111">Attribute</span></span>|<span data-ttu-id="e265b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e265b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e265b-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="e265b-113">enabled</span></span>|<span data-ttu-id="e265b-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e265b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e265b-115">Gölge kopyalama kullanan uygulama etki alanları derleme zaman damgaları, bir derlemeyi derleme kopyalama gölge önce güncelleştirilmiş olup olmadığını belirlemek için başlangıç karşılaştırmak olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e265b-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e265b-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e265b-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="e265b-117">Değer</span><span class="sxs-lookup"><span data-stu-id="e265b-117">Value</span></span>|<span data-ttu-id="e265b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e265b-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e265b-119">true</span><span class="sxs-lookup"><span data-stu-id="e265b-119">true</span></span>|<span data-ttu-id="e265b-120">Başlangıçta, yalnızca son gölge kopya dizinine kopyalanan bu yana güncelleştirilen derlemeleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="e265b-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="e265b-121">Bunun için varsayılan değer [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e265b-121">This is the default for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>|  
|<span data-ttu-id="e265b-122">false</span><span class="sxs-lookup"><span data-stu-id="e265b-122">false</span></span>|<span data-ttu-id="e265b-123">.NET Framework'ün önceki sürümlerini başlangıç davranışını Başlangıçta tüm dosyaları kopyalamak için olduğu döner.</span><span class="sxs-lookup"><span data-stu-id="e265b-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e265b-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e265b-124">Child Elements</span></span>  
 <span data-ttu-id="e265b-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="e265b-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e265b-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e265b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e265b-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="e265b-127">Element</span></span>|<span data-ttu-id="e265b-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e265b-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e265b-129">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e265b-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e265b-130">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e265b-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e265b-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e265b-131">Remarks</span></span>  
 <span data-ttu-id="e265b-132">İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], derlemeler yalnızca kendi zaman damgaları gölge kopya dizinine son kopyalanan sonra bunlar değişmiş gösteriyorsa gölge olan.</span><span class="sxs-lookup"><span data-stu-id="e265b-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="e265b-133">Bu açıklandığı gibi gölge kopyalama, kullanmak pek çok uygulama başlatma sürelerini artırır [gölge kopyalama derlemeleri](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="e265b-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="e265b-134">Yüksek yüzdesi ve derleme güncelleştirmelerinin sıklığını uygulamaları bu davranış değişikliği yararlı değil.</span><span class="sxs-lookup"><span data-stu-id="e265b-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="e265b-135">Bu durumda, .NET Framework'ün önceki sürümlerini davranışını geri yüklemek için bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e265b-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e265b-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="e265b-136">Example</span></span>  
 <span data-ttu-id="e265b-137">Aşağıdaki örnek, gölge kopyalama varsayılan başlangıç davranışını devre dışı bırakma gösterir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]ve .NET Framework'ün önceki sürümlerini başlangıç davranışını dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e265b-137">The following example shows how to disable the default startup behavior of shadow copying in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e265b-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e265b-138">See Also</span></span>  
 [<span data-ttu-id="e265b-139">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e265b-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="e265b-140">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e265b-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e265b-141">Gölge Kopyalama Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="e265b-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
