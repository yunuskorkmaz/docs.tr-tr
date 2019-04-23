---
title: <Thread_UseAllCpuGroups> Öğesi
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 236953cc1a430a1dd2a2fbb633c7ef06e6ba200f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230843"
---
# <a name="threaduseallcpugroups-element"></a><span data-ttu-id="89320-102">\<Thread_UseAllCpuGroups > öğesi</span><span class="sxs-lookup"><span data-stu-id="89320-102">\<Thread_UseAllCpuGroups> Element</span></span>
<span data-ttu-id="89320-103">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="89320-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="89320-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="89320-104">\<configuration></span></span>  
<span data-ttu-id="89320-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="89320-105">\<runtime></span></span>  
<span data-ttu-id="89320-106"><Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="89320-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89320-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89320-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89320-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89320-108">Attributes and Elements</span></span>  
 <span data-ttu-id="89320-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89320-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89320-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89320-110">Attributes</span></span>  
  
|<span data-ttu-id="89320-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89320-111">Attribute</span></span>|<span data-ttu-id="89320-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89320-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="89320-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="89320-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="89320-114">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="89320-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="89320-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89320-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="89320-116">Değer</span><span class="sxs-lookup"><span data-stu-id="89320-116">Value</span></span>|<span data-ttu-id="89320-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89320-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="89320-118">Çalışma zamanının yönetilen iş parçacıkları arasında birden fazla CPU grubu dağıtmaz.</span><span class="sxs-lookup"><span data-stu-id="89320-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="89320-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="89320-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="89320-120">Bilgisayarda birden fazla CPU grubu varsa çalışma zamanı yönetilen iş parçacıklarını birden çok CPU grupları arasında dağıtır ve [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğe etkin.</span><span class="sxs-lookup"><span data-stu-id="89320-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89320-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89320-121">Child Elements</span></span>  
 <span data-ttu-id="89320-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="89320-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89320-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89320-123">Parent Elements</span></span>  
  
|<span data-ttu-id="89320-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="89320-124">Element</span></span>|<span data-ttu-id="89320-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89320-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="89320-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="89320-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="89320-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="89320-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89320-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89320-128">Remarks</span></span>  
 <span data-ttu-id="89320-129">Bir bilgisayara birden fazla CPU grubu varsa, bu öğenin etkinleştirilmesi, çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmak neden olur.</span><span class="sxs-lookup"><span data-stu-id="89320-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="89320-130">Bu özelliği kullanmak için ayrıca etkinleştirmelisiniz [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi, çöp toplama için tüm CPU grupları genişletir ve tüm çekirdek oluştururken ve Yığınlar Dengeleme dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="89320-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="89320-131">Etkinleştirme [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi gerektiriyor etkinleştirme [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="89320-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="89320-132">Bu öğeler etkinleştirilmezse, etkinleştirme `<Thread_UseAllCpuGroups>` öğesi hiçbir etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="89320-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89320-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="89320-133">Example</span></span>  
 <span data-ttu-id="89320-134">Aşağıdaki örnek, birden çok CPU için desteğini nasıl etkinleştireceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="89320-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89320-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89320-135">See also</span></span>

- [<span data-ttu-id="89320-136">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="89320-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="89320-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="89320-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="89320-138">\<GCCpuGroup > öğesi</span><span class="sxs-lookup"><span data-stu-id="89320-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
