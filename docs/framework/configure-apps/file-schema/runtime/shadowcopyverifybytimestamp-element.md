---
title: <shadowCopyVerifyByTimestamp> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f3ea57364832553d16c7e34fc887b1c9f821602
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663444"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="df8cc-102">\<shadowCopyVerifyByTimestamp > öğesi</span><span class="sxs-lookup"><span data-stu-id="df8cc-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="df8cc-103">Gölge kopyalamanın .NET Framework 4 ' te tanıtılan varsayılan başlangıç davranışını kullanıp kullanmadığını veya .NET Framework önceki sürümlerinin başlangıç davranışına geri dönmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="df8cc-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="df8cc-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="df8cc-104">\<configuration> Element</span></span>  
<span data-ttu-id="df8cc-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="df8cc-105">\<runtime> Element</span></span>  
<span data-ttu-id="df8cc-106">\<shadowCopyVerifyByTimestamp > öğesi</span><span class="sxs-lookup"><span data-stu-id="df8cc-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df8cc-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df8cc-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df8cc-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="df8cc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="df8cc-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df8cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df8cc-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="df8cc-110">Attributes</span></span>  
  
|<span data-ttu-id="df8cc-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="df8cc-111">Attribute</span></span>|<span data-ttu-id="df8cc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df8cc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df8cc-113">etkinletir</span><span class="sxs-lookup"><span data-stu-id="df8cc-113">enabled</span></span>|<span data-ttu-id="df8cc-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="df8cc-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="df8cc-115">Derlemeyi gölge kopyalamadan önce bir derlemenin güncelleştirilip güncelleştirilmediğini anlamak için, gölge kopyalamayı kullanan uygulama etki alanlarının derleme zaman damgalarını karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="df8cc-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="df8cc-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="df8cc-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="df8cc-117">Değer</span><span class="sxs-lookup"><span data-stu-id="df8cc-117">Value</span></span>|<span data-ttu-id="df8cc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df8cc-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="df8cc-119">true</span><span class="sxs-lookup"><span data-stu-id="df8cc-119">true</span></span>|<span data-ttu-id="df8cc-120">Başlangıçta, yalnızca gölge kopya dizinine son kopyalandıklarından bu yana güncelleştirilmiş derlemeleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="df8cc-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="df8cc-121">.NET Framework 4 için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="df8cc-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="df8cc-122">false</span><span class="sxs-lookup"><span data-stu-id="df8cc-122">false</span></span>|<span data-ttu-id="df8cc-123">Başlangıçtaki tüm dosyaları kopyalamak için .NET Framework önceki sürümlerinin başlangıç davranışına geri döner.</span><span class="sxs-lookup"><span data-stu-id="df8cc-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df8cc-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="df8cc-124">Child Elements</span></span>  
 <span data-ttu-id="df8cc-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="df8cc-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df8cc-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="df8cc-126">Parent Elements</span></span>  
  
|<span data-ttu-id="df8cc-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="df8cc-127">Element</span></span>|<span data-ttu-id="df8cc-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df8cc-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="df8cc-129">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="df8cc-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="df8cc-130">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="df8cc-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df8cc-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df8cc-131">Remarks</span></span>  
 <span data-ttu-id="df8cc-132">.NET Framework 4 ' te başlayarak, derlemeler yalnızca, zaman damgaları, gölge kopya dizinine en son kopyalandıklarından bu yana değiştirildikleri belirtilmişse gölge olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="df8cc-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="df8cc-133">Bu, gölge kopyalama [derlemeler](../../../app-domains/shadow-copy-assemblies.md)' de açıklandığı gibi, gölge kopyalamayı kullanan birçok uygulama için başlangıç zamanlarını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="df8cc-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="df8cc-134">Yüksek oranda yüzdesi ve derleme güncelleştirmelerinin sıklığı olan uygulamalar bu değişiklikten daha fazla avantaj sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="df8cc-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="df8cc-135">Bu durumda, .NET Framework önceki sürümlerinin davranışını geri yüklemek için bu öğeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df8cc-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df8cc-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="df8cc-136">Example</span></span>  
 <span data-ttu-id="df8cc-137">Aşağıdaki örnek, .NET Framework 4 ' te gölge kopyalamanın varsayılan başlatma davranışının nasıl devre dışı bırakılacağını ve .NET Framework önceki sürümlerinin başlangıç davranışına geri dönmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="df8cc-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df8cc-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df8cc-138">See also</span></span>

- [<span data-ttu-id="df8cc-139">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="df8cc-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="df8cc-140">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="df8cc-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="df8cc-141">Gölge Kopyalama Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="df8cc-141">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
