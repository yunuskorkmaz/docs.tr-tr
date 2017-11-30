---
title: "&lt;Thread_UseAllCpuGroups&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 187e391acf3b80a5ae2dfe795c4a3b397af815ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltthreaduseallcpugroupsgt-element"></a><span data-ttu-id="b498b-102">&lt;Thread_UseAllCpuGroups&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="b498b-102">&lt;Thread_UseAllCpuGroups&gt; Element</span></span>
<span data-ttu-id="b498b-103">Çalışma zamanı, tüm CPU gruplarında yönetilen iş parçacığı dağıtır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b498b-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="b498b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="b498b-104">\<configuration></span></span>  
<span data-ttu-id="b498b-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="b498b-105">\<runtime></span></span>  
<span data-ttu-id="b498b-106">< Thread_UseAllCpuGroups ></span><span class="sxs-lookup"><span data-stu-id="b498b-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b498b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b498b-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b498b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b498b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b498b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b498b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b498b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b498b-110">Attributes</span></span>  
  
|<span data-ttu-id="b498b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b498b-111">Attribute</span></span>|<span data-ttu-id="b498b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b498b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b498b-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b498b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b498b-114">Çalışma zamanı, tüm CPU gruplarında yönetilen iş parçacığı dağıtır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b498b-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b498b-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b498b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b498b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="b498b-116">Value</span></span>|<span data-ttu-id="b498b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b498b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b498b-118">Çalışma zamanı yönetilen iş parçacığı birden çok CPU gruplarında dağıtmaz.</span><span class="sxs-lookup"><span data-stu-id="b498b-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="b498b-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b498b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b498b-120">Bilgisayarda birden çok CPU grupları varsa çalışma zamanı yönetilen iş parçacığı birden çok CPU grubu içinde dağıtır ve [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi etkindir.</span><span class="sxs-lookup"><span data-stu-id="b498b-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b498b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b498b-121">Child Elements</span></span>  
 <span data-ttu-id="b498b-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="b498b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b498b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b498b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b498b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b498b-124">Element</span></span>|<span data-ttu-id="b498b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b498b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b498b-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b498b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b498b-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="b498b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b498b-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b498b-128">Remarks</span></span>  
 <span data-ttu-id="b498b-129">Bir bilgisayarda birden çok CPU grubu olduğunda, bu öğe etkinleştirme yönetilen iş parçacığı tüm CPU gruplarında dağıtmak çalışma zamanı neden olur.</span><span class="sxs-lookup"><span data-stu-id="b498b-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="b498b-130">Bu özelliği kullanmak için da etkinleştirmeniz gerekir [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi, tüm CPU gruplarına çöp toplama genişleten ve tüm çekirdek oluştururken ve yığın Dengeleme dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="b498b-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="b498b-131">Etkinleştirme [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi gerektiriyor etkinleştirme [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="b498b-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="b498b-132">Bu öğeleri etkinleştirilmezse, etkinleştirme `<Thread_UseAllCpuGroups>` öğesi etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b498b-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b498b-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="b498b-133">Example</span></span>  
 <span data-ttu-id="b498b-134">Aşağıdaki örnek, birden çok CPU grupları desteğini etkinleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b498b-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b498b-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b498b-135">See Also</span></span>  
 [<span data-ttu-id="b498b-136">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b498b-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="b498b-137">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="b498b-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="b498b-138">\<GCCpuGroup > öğesi</span><span class="sxs-lookup"><span data-stu-id="b498b-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
