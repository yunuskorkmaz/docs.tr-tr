---
title: <NetFx40_LegacySecurityPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: d5192eb56bb8b640544bdc52a0bb9d8a5277efef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116247"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="ae0a6-102">\<NetFx40_LegacySecurityPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ae0a6-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="ae0a6-103">Çalışma zamanının eski kod erişim güvenliği (CAS) ilkesi kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**  

## <a name="syntax"></a><span data-ttu-id="ae0a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae0a6-104">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae0a6-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae0a6-105">Attributes and Elements</span></span>

<span data-ttu-id="ae0a6-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae0a6-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ae0a6-107">Attributes</span></span>

|<span data-ttu-id="ae0a6-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ae0a6-108">Attribute</span></span>|<span data-ttu-id="ae0a6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae0a6-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ae0a6-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ae0a6-111">Çalışma zamanının eski CAS ilkesini kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-111">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="ae0a6-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ae0a6-112">enabled Attribute</span></span>

|<span data-ttu-id="ae0a6-113">Değer</span><span class="sxs-lookup"><span data-stu-id="ae0a6-113">Value</span></span>|<span data-ttu-id="ae0a6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae0a6-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="ae0a6-115">Çalışma zamanı eski CAS ilkesini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-115">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="ae0a6-116">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="ae0a6-117">Çalışma zamanı eski CAS ilkesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-117">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ae0a6-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae0a6-118">Child Elements</span></span>

<span data-ttu-id="ae0a6-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ae0a6-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae0a6-120">Parent Elements</span></span>

|<span data-ttu-id="ae0a6-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae0a6-121">Element</span></span>|<span data-ttu-id="ae0a6-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae0a6-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ae0a6-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ae0a6-124">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ae0a6-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae0a6-125">Remarks</span></span>

<span data-ttu-id="ae0a6-126">.NET Framework sürüm 3,5 ve önceki sürümlerde CAS ilkesi her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-126">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="ae0a6-127">.NET Framework 4 ' te CAS ilkesinin etkinleştirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-127">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="ae0a6-128">CAS ilkesi sürüme özgüdür.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-128">CAS policy is version-specific.</span></span> <span data-ttu-id="ae0a6-129">.NET Framework önceki sürümlerinde bulunan özel CA ilkelerinin .NET Framework 4 ' te önceden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-129">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="ae0a6-130">`<NetFx40_LegacySecurityPolicy>`Öğesini bir .NET Framework 4 derlemesine uygulamak, [güvenlik açısından saydam kodu](../../../misc/security-transparent-code.md)etkilemez; saydamlık kuralları yine de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-130">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae0a6-131">Öğesi uygulandığında, `<NetFx40_LegacySecurityPolicy>` [genel derleme önbelleğinde](../../../app-domains/gac.md)yüklü olmayan [Yerel Görüntü Oluşturucu (Ngen. exe)](../../../tools/ngen-exe-native-image-generator.md) tarafından oluşturulan yerel görüntü derlemeleri için önemli performans cezaları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-131">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="ae0a6-132">Performans düşüşü, çalışma zamanının öznitelik uygulandığında derlemeleri yerel görüntü olarak yüklemesi nedeniyle oluşur ve bu, tam zamanında derlemeler olarak yüklenmekte olur.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-132">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="ae0a6-133">Visual Studio projeniz için proje ayarları içindeki .NET Framework 4 ' ten daha eski bir hedef .NET Framework sürümünü belirtirseniz, bu sürüm için belirttiğiniz özel CAS ilkeleri de dahil olmak üzere CAS ilkesi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-133">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="ae0a6-134">Ancak, yeni .NET Framework 4 türlerini ve üyelerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-134">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="ae0a6-135">Ayrıca, [uygulama yapılandırma dosyanızdaki](../../index.md)başlangıç ayarları şemasında [ \<supportedRuntime> öğesini](../startup/supportedruntime-element.md) kullanarak .NET Framework önceki bir sürümünü de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-135">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ae0a6-136">Yapılandırma dosyası söz dizimi büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-136">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="ae0a6-137">Söz dizimini sözdizimi ve örnek bölümlerinde belirtilen şekilde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-137">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="ae0a6-138">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="ae0a6-138">Configuration File</span></span>

<span data-ttu-id="ae0a6-139">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-139">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="ae0a6-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae0a6-140">Example</span></span>

<span data-ttu-id="ae0a6-141">Aşağıdaki örnekte, bir uygulama için eski CAS ilkesinin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-141">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ae0a6-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae0a6-142">See also</span></span>

- [<span data-ttu-id="ae0a6-143">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="ae0a6-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ae0a6-144">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ae0a6-144">Configuration File Schema</span></span>](../index.md)
