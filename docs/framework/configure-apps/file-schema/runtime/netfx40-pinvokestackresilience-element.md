---
title: <NetFx40_PInvokeStackResilience> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf97cc1ec544c7cf640c43b1b45760fca8cffe89
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663549"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="4ab39-102">\<NetFx40_PInvokeStackResilience > öğesi</span><span class="sxs-lookup"><span data-stu-id="4ab39-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="4ab39-103">Çalışma zamanının, yönetilen ve yönetilmeyen kod arasındaki yavaş geçişlerin maliyetinde, çalışma zamanında hatalı platform çağırma bildirimlerini otomatik olarak düzeltilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ab39-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

<span data-ttu-id="4ab39-104">\<Yapılandırma > </span><span class="sxs-lookup"><span data-stu-id="4ab39-104">\<configuration></span></span>\
<span data-ttu-id="4ab39-105">\<çalışma zamanı > </span><span class="sxs-lookup"><span data-stu-id="4ab39-105">\<runtime></span></span>\
<span data-ttu-id="4ab39-106">\<NetFx40_PInvokeStackResilience ></span><span class="sxs-lookup"><span data-stu-id="4ab39-106">\<NetFx40_PInvokeStackResilience></span></span>

## <a name="syntax"></a><span data-ttu-id="4ab39-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ab39-107">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ab39-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ab39-108">Attributes and Elements</span></span>

<span data-ttu-id="4ab39-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ab39-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ab39-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4ab39-110">Attributes</span></span>

|<span data-ttu-id="4ab39-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4ab39-111">Attribute</span></span>|<span data-ttu-id="4ab39-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ab39-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="4ab39-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4ab39-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4ab39-114">Çalışma zamanının yanlış platform çağırma bildirimleri algıladığını ve 32-bit platformlarda çalışma zamanında yığını otomatik olarak düzeltmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ab39-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="4ab39-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4ab39-115">enabled Attribute</span></span>

|<span data-ttu-id="4ab39-116">Değer</span><span class="sxs-lookup"><span data-stu-id="4ab39-116">Value</span></span>|<span data-ttu-id="4ab39-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ab39-117">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="4ab39-118">Çalışma zamanı, yanlış platform çağırma bildirimlerini algılamadığında ve gideremeyecek .NET Framework 4 ' te tanıtılan daha hızlı birlikte çalışma hazırlama mimarisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ab39-118">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="4ab39-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4ab39-119">This is the default.</span></span>|
|`1`|<span data-ttu-id="4ab39-120">Çalışma zamanı, hatalı platform çağırma bildirimlerini algılayan ve giderecek daha yavaş geçişler kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ab39-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4ab39-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ab39-121">Child Elements</span></span>

<span data-ttu-id="4ab39-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="4ab39-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ab39-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ab39-123">Parent Elements</span></span>

|<span data-ttu-id="4ab39-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ab39-124">Element</span></span>|<span data-ttu-id="4ab39-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ab39-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="4ab39-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4ab39-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="4ab39-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4ab39-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4ab39-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ab39-128">Remarks</span></span>

<span data-ttu-id="4ab39-129">Bu öğe, yanlış platform çağırma bildirimlerine karşı çalışma zamanı esnekliği için daha hızlı birlikte çalışma sıralaması sunmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ab39-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="4ab39-130">.NET Framework 4 ' ten itibaren, kolaylaştırılmış bir birlikte çalışma hazırlama mimarisi yönetilen koddan yönetilmeyen koda yapılan geçişler için önemli bir performans geliştirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ab39-130">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="4ab39-131">.NET Framework önceki sürümlerinde, sıralama katmanı 32-bit platformlarda hatalı platform çağırma bildirimleri algıladı ve yığını otomatik olarak düzeltti.</span><span class="sxs-lookup"><span data-stu-id="4ab39-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="4ab39-132">Yeni sıralama mimarisi bu adımı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4ab39-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="4ab39-133">Sonuç olarak, geçişler çok hızlıdır, ancak yanlış platform çağırma bildirimi program hatasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ab39-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="4ab39-134">Geliştirme sırasında yanlış bildirimleri algılamaya kolay hale getirmek için, Visual Studio hata ayıklama deneyimi geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4ab39-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="4ab39-135">[PInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) yönetilen hata ayıklama Yardımcısı (MDA), uygulamanız, ekli hata ayıklayıcı ile çalışırken hatalı platform çağırma bildirimlerini size bildirir.</span><span class="sxs-lookup"><span data-stu-id="4ab39-135">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="4ab39-136">Uygulamanızın, yeniden derleyemediği ve yanlış platform çağırma bildirimlerine sahip olan bileşenleri kullandığı senaryolara yönelik senaryolar için `NetFx40_PInvokeStackResilience` öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ab39-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="4ab39-137">Bu öğeyi, daha düşük geçişlerin maliyetinde, `enabled="1"` .NET Framework önceki sürümlerinin davranışıyla birlikte bir uyumluluk moduna ekleyerek uygulama yapılandırma dosyanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ab39-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="4ab39-138">Önceki .NET Framework sürümleriyle derlenen derlemeler otomatik olarak bu uyumluluk moduna alınır ve bu öğeye gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="4ab39-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="4ab39-139">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="4ab39-139">Configuration File</span></span>

<span data-ttu-id="4ab39-140">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ab39-140">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="4ab39-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ab39-141">Example</span></span>

<span data-ttu-id="4ab39-142">Aşağıdaki örnek, yönetilen ve yönetilmeyen kod arasındaki yavaş geçişlerin maliyetinde, bir uygulamanın yanlış platform çağırma bildirimlerine karşı artan esnekliği nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ab39-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4ab39-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ab39-143">See also</span></span>

- [<span data-ttu-id="4ab39-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4ab39-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4ab39-145">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="4ab39-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4ab39-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="4ab39-146">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
