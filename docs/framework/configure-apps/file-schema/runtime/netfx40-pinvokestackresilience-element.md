---
title: <NetFx40_PInvokeStackResilience> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 86f50aafe0b21d5080288e09ac7118ca1e4c939a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116153"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="625a7-102">\<NetFx40_PInvokeStackResilience> Öğesi</span><span class="sxs-lookup"><span data-stu-id="625a7-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="625a7-103">Çalışma zamanının, yönetilen ve yönetilmeyen kod arasındaki yavaş geçişlerin maliyetinde, çalışma zamanında hatalı platform çağırma bildirimlerini otomatik olarak düzeltilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="625a7-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**  

## <a name="syntax"></a><span data-ttu-id="625a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="625a7-104">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="625a7-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="625a7-105">Attributes and Elements</span></span>

<span data-ttu-id="625a7-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="625a7-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="625a7-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="625a7-107">Attributes</span></span>

|<span data-ttu-id="625a7-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="625a7-108">Attribute</span></span>|<span data-ttu-id="625a7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="625a7-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="625a7-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="625a7-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="625a7-111">Çalışma zamanının yanlış platform çağırma bildirimleri algıladığını ve 32-bit platformlarda çalışma zamanında yığını otomatik olarak düzeltmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="625a7-111">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="625a7-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="625a7-112">enabled Attribute</span></span>

|<span data-ttu-id="625a7-113">Değer</span><span class="sxs-lookup"><span data-stu-id="625a7-113">Value</span></span>|<span data-ttu-id="625a7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="625a7-114">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="625a7-115">Çalışma zamanı, yanlış platform çağırma bildirimlerini algılamadığında ve gideremeyecek .NET Framework 4 ' te tanıtılan daha hızlı birlikte çalışma hazırlama mimarisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="625a7-115">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="625a7-116">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="625a7-116">This is the default.</span></span>|
|`1`|<span data-ttu-id="625a7-117">Çalışma zamanı, hatalı platform çağırma bildirimlerini algılayan ve giderecek daha yavaş geçişler kullanır.</span><span class="sxs-lookup"><span data-stu-id="625a7-117">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="625a7-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="625a7-118">Child Elements</span></span>

<span data-ttu-id="625a7-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="625a7-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="625a7-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="625a7-120">Parent Elements</span></span>

|<span data-ttu-id="625a7-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="625a7-121">Element</span></span>|<span data-ttu-id="625a7-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="625a7-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="625a7-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="625a7-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="625a7-124">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="625a7-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="625a7-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="625a7-125">Remarks</span></span>

<span data-ttu-id="625a7-126">Bu öğe, yanlış platform çağırma bildirimlerine karşı çalışma zamanı esnekliği için daha hızlı birlikte çalışma sıralaması sunmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="625a7-126">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="625a7-127">.NET Framework 4 ' ten itibaren, kolaylaştırılmış bir birlikte çalışma hazırlama mimarisi yönetilen koddan yönetilmeyen koda yapılan geçişler için önemli bir performans geliştirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="625a7-127">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="625a7-128">.NET Framework önceki sürümlerinde, sıralama katmanı 32-bit platformlarda hatalı platform çağırma bildirimleri algıladı ve yığını otomatik olarak düzeltti.</span><span class="sxs-lookup"><span data-stu-id="625a7-128">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="625a7-129">Yeni sıralama mimarisi bu adımı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="625a7-129">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="625a7-130">Sonuç olarak, geçişler çok hızlıdır, ancak yanlış platform çağırma bildirimi program hatasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="625a7-130">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="625a7-131">Geliştirme sırasında yanlış bildirimleri algılamaya kolay hale getirmek için, Visual Studio hata ayıklama deneyimi geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="625a7-131">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="625a7-132">[PInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) yönetilen hata ayıklama Yardımcısı (MDA), uygulamanız, ekli hata ayıklayıcı ile çalışırken hatalı platform çağırma bildirimlerini size bildirir.</span><span class="sxs-lookup"><span data-stu-id="625a7-132">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="625a7-133">Uygulamanızın, yeniden derleyemediği ve yanlış platform çağırma bildirimlerine sahip olan bileşenleri kullandığı senaryolara yönelik senaryolar için `NetFx40_PInvokeStackResilience` öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="625a7-133">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="625a7-134">Bu öğeyi, daha `enabled="1"` düşük geçişlerin maliyetinde, .NET Framework önceki sürümlerinin davranışıyla birlikte bir uyumluluk moduna ekleyerek uygulama yapılandırma dosyanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="625a7-134">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="625a7-135">Önceki .NET Framework sürümleriyle derlenen derlemeler otomatik olarak bu uyumluluk moduna alınır ve bu öğeye gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="625a7-135">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="625a7-136">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="625a7-136">Configuration File</span></span>

<span data-ttu-id="625a7-137">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="625a7-137">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="625a7-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="625a7-138">Example</span></span>

<span data-ttu-id="625a7-139">Aşağıdaki örnek, yönetilen ve yönetilmeyen kod arasındaki yavaş geçişlerin maliyetinde, bir uygulamanın yanlış platform çağırma bildirimlerine karşı artan esnekliği nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="625a7-139">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="625a7-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="625a7-140">See also</span></span>

- [<span data-ttu-id="625a7-141">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="625a7-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="625a7-142">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="625a7-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="625a7-143">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="625a7-143">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
