---
title: <NetFx40_LegacySecurityPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cd6f937811ae503dd4de7ff989510c4eb8b8933
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252439"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="cef2b-102">\<NetFx40_LegacySecurityPolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="cef2b-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="cef2b-103">Çalışma zamanının eski kod erişim güvenliği (CAS) ilkesi kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

<span data-ttu-id="cef2b-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cef2b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cef2b-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="cef2b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="cef2b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx40_LegacySecurityPolicy >**</span><span class="sxs-lookup"><span data-stu-id="cef2b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="cef2b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cef2b-107">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cef2b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cef2b-108">Attributes and Elements</span></span>

<span data-ttu-id="cef2b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cef2b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cef2b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cef2b-110">Attributes</span></span>

|<span data-ttu-id="cef2b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cef2b-111">Attribute</span></span>|<span data-ttu-id="cef2b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cef2b-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="cef2b-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cef2b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="cef2b-114">Çalışma zamanının eski CAS ilkesini kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="cef2b-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cef2b-115">enabled Attribute</span></span>

|<span data-ttu-id="cef2b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="cef2b-116">Value</span></span>|<span data-ttu-id="cef2b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cef2b-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="cef2b-118">Çalışma zamanı eski CAS ilkesini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="cef2b-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="cef2b-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cef2b-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="cef2b-120">Çalışma zamanı eski CAS ilkesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cef2b-120">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cef2b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cef2b-121">Child Elements</span></span>

<span data-ttu-id="cef2b-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="cef2b-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cef2b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cef2b-123">Parent Elements</span></span>

|<span data-ttu-id="cef2b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="cef2b-124">Element</span></span>|<span data-ttu-id="cef2b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cef2b-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="cef2b-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cef2b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="cef2b-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cef2b-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cef2b-128">Remarks</span></span>

<span data-ttu-id="cef2b-129">.NET Framework sürüm 3,5 ve önceki sürümlerde CAS ilkesi her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="cef2b-130">.NET Framework 4 ' te CAS ilkesinin etkinleştirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-130">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="cef2b-131">CAS ilkesi sürüme özgüdür.</span><span class="sxs-lookup"><span data-stu-id="cef2b-131">CAS policy is version-specific.</span></span> <span data-ttu-id="cef2b-132">.NET Framework önceki sürümlerinde bulunan özel CA ilkelerinin .NET Framework 4 ' te önceden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="cef2b-133">Öğesini bir .NET Framework 4 derlemesine uygulamak, [güvenlik açısından saydam kodu](../../../misc/security-transparent-code.md)etkilemez; saydamlık kuralları yine de geçerlidir. `<NetFx40_LegacySecurityPolicy>`</span><span class="sxs-lookup"><span data-stu-id="cef2b-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cef2b-134">Öğesi uygulandığında `<NetFx40_LegacySecurityPolicy>` , [genel derleme önbelleğinde](../../../app-domains/gac.md)yüklü olmayan [Yerel Görüntü Oluşturucu (Ngen. exe)](../../../tools/ngen-exe-native-image-generator.md) tarafından oluşturulan yerel görüntü derlemeleri için önemli performans cezaları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="cef2b-135">Performans düşüşü, çalışma zamanının öznitelik uygulandığında derlemeleri yerel görüntü olarak yüklemesi nedeniyle oluşur ve bu, tam zamanında derlemeler olarak yüklenmekte olur.</span><span class="sxs-lookup"><span data-stu-id="cef2b-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="cef2b-136">Visual Studio projeniz için proje ayarları içindeki .NET Framework 4 ' ten daha eski bir hedef .NET Framework sürümünü belirtirseniz, bu sürüm için belirttiğiniz özel CAS ilkeleri de dahil olmak üzere CAS ilkesi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-136">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="cef2b-137">Ancak, yeni .NET Framework 4 türlerini ve üyelerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="cef2b-137">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="cef2b-138">Ayrıca, [uygulama yapılandırma dosyanızdaki](../../index.md)başlangıç ayarları şemasında [ \<supportedRuntime > öğesini](../startup/supportedruntime-element.md) kullanarak .NET Framework önceki bir sürümünü de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef2b-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="cef2b-139">Yapılandırma dosyası söz dizimi büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="cef2b-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="cef2b-140">Söz dizimini sözdizimi ve örnek bölümlerinde belirtilen şekilde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="cef2b-141">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="cef2b-141">Configuration File</span></span>

<span data-ttu-id="cef2b-142">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-142">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="cef2b-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="cef2b-143">Example</span></span>

<span data-ttu-id="cef2b-144">Aşağıdaki örnekte, bir uygulama için eski CAS ilkesinin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cef2b-144">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="cef2b-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cef2b-145">See also</span></span>

- [<span data-ttu-id="cef2b-146">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cef2b-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cef2b-147">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="cef2b-147">Configuration File Schema</span></span>](../index.md)
