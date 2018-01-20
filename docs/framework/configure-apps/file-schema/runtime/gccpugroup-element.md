---
title: '&lt;GCCpuGroup&gt; Element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dcead28d7bf66e0626a0108015add4f22c5fa476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="926e6-102">&lt;GCCpuGroup&gt; Element</span><span class="sxs-lookup"><span data-stu-id="926e6-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="926e6-103">Çöp toplama birden çok CPU grupları destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="926e6-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="926e6-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="926e6-104">\<configuration></span></span>  
<span data-ttu-id="926e6-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="926e6-105">\<runtime></span></span>  
<span data-ttu-id="926e6-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="926e6-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="926e6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="926e6-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="926e6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="926e6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="926e6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="926e6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="926e6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="926e6-110">Attributes</span></span>  
  
|<span data-ttu-id="926e6-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="926e6-111">Attribute</span></span>|<span data-ttu-id="926e6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="926e6-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="926e6-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="926e6-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="926e6-114">Çöp toplama birden çok CPU grupları destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="926e6-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="926e6-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="926e6-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="926e6-116">Değer</span><span class="sxs-lookup"><span data-stu-id="926e6-116">Value</span></span>|<span data-ttu-id="926e6-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="926e6-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="926e6-118">Çöp toplama birden çok CPU grupları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="926e6-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="926e6-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="926e6-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="926e6-120">Sunucu çöp toplama etkinse, atık toplama birden çok CPU gruplarını destekler.</span><span class="sxs-lookup"><span data-stu-id="926e6-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="926e6-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="926e6-121">Child Elements</span></span>  
 <span data-ttu-id="926e6-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="926e6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="926e6-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="926e6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="926e6-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="926e6-124">Element</span></span>|<span data-ttu-id="926e6-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="926e6-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="926e6-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="926e6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="926e6-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="926e6-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="926e6-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="926e6-128">Remarks</span></span>  
 <span data-ttu-id="926e6-129">Ne zaman birden çok CPU grubu olan bir bilgisayarda ve sunucu çöp toplama etkin (bkz [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) öğesi), bu öğe etkinleştirme çöp toplama tüm CPU gruplarında genişletir ve tüm çekirdek içine alır hesap oluştururken ve yığın Dengeleme.</span><span class="sxs-lookup"><span data-stu-id="926e6-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="926e6-130">Bu öğe yalnızca atık toplama iş parçacığı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="926e6-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="926e6-131">Kullanıcı iş parçacıkları tüm CPU gruplarında dağıtmak çalışma zamanı etkinleştirmek için da etkinleştirmeniz gerekir [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="926e6-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="926e6-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="926e6-132">Example</span></span>  
 <span data-ttu-id="926e6-133">Aşağıdaki örnek, birden çok CPU grupları atık toplamayı etkinleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="926e6-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="926e6-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="926e6-134">See Also</span></span>  
 [<span data-ttu-id="926e6-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="926e6-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="926e6-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="926e6-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="926e6-137">Nasıl yapılır: eş zamanlı çöp toplama devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="926e6-137">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [<span data-ttu-id="926e6-138">İş istasyonu ve sunucu çöp toplama</span><span class="sxs-lookup"><span data-stu-id="926e6-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
