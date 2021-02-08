---
description: 'Hakkında daha fazla bilgi edinin: <NetFx40_LegacySecurityPolicy> öğesi'
title: <NetFx40_LegacySecurityPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: 6be520d4cfd4f9ec05f4aceec82e4fef5440f55d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782318"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="50e49-103">\<NetFx40_LegacySecurityPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="50e49-103">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="50e49-104">Çalışma zamanının eski kod erişim güvenliği (CAS) ilkesi kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="50e49-104">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**  

## <a name="syntax"></a><span data-ttu-id="50e49-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="50e49-105">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50e49-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="50e49-106">Attributes and Elements</span></span>

<span data-ttu-id="50e49-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="50e49-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="50e49-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="50e49-108">Attributes</span></span>

|<span data-ttu-id="50e49-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="50e49-109">Attribute</span></span>|<span data-ttu-id="50e49-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50e49-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="50e49-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="50e49-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="50e49-112">Çalışma zamanının eski CAS ilkesini kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="50e49-112">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="50e49-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="50e49-113">enabled Attribute</span></span>

|<span data-ttu-id="50e49-114">Değer</span><span class="sxs-lookup"><span data-stu-id="50e49-114">Value</span></span>|<span data-ttu-id="50e49-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50e49-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="50e49-116">Çalışma zamanı eski CAS ilkesini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="50e49-116">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="50e49-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="50e49-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="50e49-118">Çalışma zamanı eski CAS ilkesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50e49-118">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="50e49-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="50e49-119">Child Elements</span></span>

<span data-ttu-id="50e49-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="50e49-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="50e49-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="50e49-121">Parent Elements</span></span>

|<span data-ttu-id="50e49-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="50e49-122">Element</span></span>|<span data-ttu-id="50e49-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50e49-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="50e49-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="50e49-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="50e49-125">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="50e49-125">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50e49-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50e49-126">Remarks</span></span>

<span data-ttu-id="50e49-127">.NET Framework sürüm 3,5 ve önceki sürümlerde CAS ilkesi her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="50e49-127">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="50e49-128">.NET Framework 4 ' te CAS ilkesinin etkinleştirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="50e49-128">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="50e49-129">CAS ilkesi sürüme özgüdür.</span><span class="sxs-lookup"><span data-stu-id="50e49-129">CAS policy is version-specific.</span></span> <span data-ttu-id="50e49-130">.NET Framework önceki sürümlerinde bulunan özel CA ilkelerinin .NET Framework 4 ' te önceden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="50e49-130">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="50e49-131">`<NetFx40_LegacySecurityPolicy>`Öğesini bir .NET Framework 4 derlemesine uygulamak, [güvenlik açısından saydam kodu](../../../misc/security-transparent-code.md)etkilemez; saydamlık kuralları yine de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="50e49-131">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50e49-132">Öğesi uygulandığında, `<NetFx40_LegacySecurityPolicy>` [genel derleme önbelleğinde](../../../app-domains/gac.md)yüklü olmayan [yerel görüntü Oluşturucu (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) tarafından oluşturulan yerel görüntü derlemeleri için önemli performans cezaları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="50e49-132">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="50e49-133">Performans düşüşü, çalışma zamanının öznitelik uygulandığında derlemeleri yerel görüntü olarak yüklemesi nedeniyle oluşur ve bu, tam zamanında derlemeler olarak yüklenmekte olur.</span><span class="sxs-lookup"><span data-stu-id="50e49-133">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="50e49-134">Visual Studio projeniz için proje ayarları içindeki .NET Framework 4 ' ten daha eski bir hedef .NET Framework sürümünü belirtirseniz, bu sürüm için belirttiğiniz özel CAS ilkeleri de dahil olmak üzere CAS ilkesi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="50e49-134">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="50e49-135">Ancak, yeni .NET Framework 4 türlerini ve üyelerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="50e49-135">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="50e49-136">Ayrıca, [uygulama yapılandırma dosyanızdaki](../../index.md)başlangıç ayarları şemasında [ \<supportedRuntime> öğesini](../startup/supportedruntime-element.md) kullanarak .NET Framework önceki bir sürümünü de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50e49-136">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="50e49-137">Yapılandırma dosyası söz dizimi büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="50e49-137">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="50e49-138">Söz dizimini sözdizimi ve örnek bölümlerinde belirtilen şekilde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="50e49-138">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="50e49-139">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="50e49-139">Configuration File</span></span>

<span data-ttu-id="50e49-140">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50e49-140">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="50e49-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="50e49-141">Example</span></span>

<span data-ttu-id="50e49-142">Aşağıdaki örnekte, bir uygulama için eski CAS ilkesinin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50e49-142">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="50e49-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50e49-143">See also</span></span>

- [<span data-ttu-id="50e49-144">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="50e49-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="50e49-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="50e49-145">Configuration File Schema</span></span>](../index.md)
