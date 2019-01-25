---
title: '&lt;NetFx40_LegacySecurityPolicy&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44120491756d467da94ce1f8557d9f71f70b306e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500333"
---
# <a name="ltnetfx40legacysecuritypolicygt-element"></a><span data-ttu-id="d228c-102">&lt;NetFx40_LegacySecurityPolicy&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="d228c-102">&lt;NetFx40_LegacySecurityPolicy&gt; Element</span></span>
<span data-ttu-id="d228c-103">Çalışma zamanının eski kod erişimi güvenliği (CAS) ilkesi kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d228c-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>  
  
 <span data-ttu-id="d228c-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d228c-104">\<configuration></span></span>  
<span data-ttu-id="d228c-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="d228c-105">\<runtime></span></span>  
<span data-ttu-id="d228c-106"><NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="d228c-106"><NetFx40_LegacySecurityPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d228c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d228c-107">Syntax</span></span>  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d228c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d228c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d228c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d228c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d228c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d228c-110">Attributes</span></span>  
  
|<span data-ttu-id="d228c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d228c-111">Attribute</span></span>|<span data-ttu-id="d228c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d228c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d228c-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d228c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d228c-114">Çalışma zamanının eski CAS İlkesi kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d228c-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d228c-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d228c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d228c-116">Değer</span><span class="sxs-lookup"><span data-stu-id="d228c-116">Value</span></span>|<span data-ttu-id="d228c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d228c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d228c-118">Çalışma zamanı, eski CAS ilkesini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="d228c-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="d228c-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d228c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d228c-120">Çalışma zamanı, eski CAS İlkesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d228c-120">The runtime uses legacy CAS policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d228c-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d228c-121">Child Elements</span></span>  
 <span data-ttu-id="d228c-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="d228c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d228c-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d228c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d228c-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d228c-124">Element</span></span>|<span data-ttu-id="d228c-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d228c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d228c-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d228c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d228c-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d228c-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d228c-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d228c-128">Remarks</span></span>  
 <span data-ttu-id="d228c-129">.NET Framework sürüm 3.5 ve önceki sürümlerinde, CAS ilkesini her zaman etkilidir.</span><span class="sxs-lookup"><span data-stu-id="d228c-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="d228c-130">İçinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], CAS ilkesini etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d228c-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], CAS policy must be enabled.</span></span>  
  
 <span data-ttu-id="d228c-131">CAS ilkesini sürümüne özeldir.</span><span class="sxs-lookup"><span data-stu-id="d228c-131">CAS policy is version-specific.</span></span> <span data-ttu-id="d228c-132">.NET Framework'ün önceki sürümlerinde bulunmayan özel CA ilkeleri respecified, içinde [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d228c-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="d228c-133">Uygulama `<NetFx40_LegacySecurityPolicy>` öğesine bir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] derleme etkilemez [güvenliği saydam kod](../../../../../docs/framework/misc/security-transparent-code.md); saydamlık kuralları hala geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d228c-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d228c-134">Uygulama `<NetFx40_LegacySecurityPolicy>` öğesi tarafından oluşturulan yerel görüntü derlemeleri için önemli performans yaptırımlarla sonuçlanabilir [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) yüklenmeyen içinde [Genel Derleme Önbelleği ](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="d228c-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="d228c-135">Öznitelik uygulandığında yerel görüntü derlemeleri yüklemek için yükleyememesine çalışma zamanı tarafından performans düşüşüne neden olur, kendi olan kaynaklanan yüklenen olarak tam zamanında derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="d228c-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d228c-136">Daha önceki hedef .NET Framework sürümü belirtirseniz [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] Visual Studio projeniz için proje ayarlarında CAS ilkesini, bu sürüm için belirttiğiniz tüm özel CA ilkeler de dahil olmak üzere etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d228c-136">If you specify a target .NET Framework version that is earlier than the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="d228c-137">Ancak, yeni kullanmanız mümkün olmayacaktır [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] türler ve üyeler.</span><span class="sxs-lookup"><span data-stu-id="d228c-137">However, you will not be able to use new [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] types and members.</span></span> <span data-ttu-id="d228c-138">.NET Framework'ün önceki bir sürümünü kullanarak da belirtebilirsiniz [ \<supportedRuntime > öğesi](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) başlangıç ayarlarını şemasında, [uygulama yapılandırma dosyası](../../../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="d228c-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d228c-139">Yapılandırma dosyası sözdizimi, büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="d228c-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="d228c-140">Söz dizimi ve örnek bölümlerinde sağlanan sözdizimini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d228c-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d228c-141">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="d228c-141">Configuration File</span></span>  
 <span data-ttu-id="d228c-142">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d228c-142">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d228c-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="d228c-143">Example</span></span>  
 <span data-ttu-id="d228c-144">Aşağıdaki örnek, bir uygulama için eski CAS ilkesini etkinleştirmek üzere gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d228c-144">The following example shows how to enable legacy CAS policy for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d228c-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d228c-145">See also</span></span>
- [<span data-ttu-id="d228c-146">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d228c-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="d228c-147">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d228c-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
