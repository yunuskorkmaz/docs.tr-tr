---
title: '&lt;GCCpuGroup&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25d083b730117a791fb8ab550b36f7b2e6c5f5be
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613719"
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="4a006-102">&lt;GCCpuGroup&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="4a006-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="4a006-103">Çöp toplama, birden fazla CPU grubu destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a006-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="4a006-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="4a006-104">\<configuration></span></span>  
<span data-ttu-id="4a006-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="4a006-105">\<runtime></span></span>  
<span data-ttu-id="4a006-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="4a006-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a006-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a006-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a006-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a006-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4a006-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a006-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a006-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4a006-110">Attributes</span></span>  
  
|<span data-ttu-id="4a006-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4a006-111">Attribute</span></span>|<span data-ttu-id="4a006-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a006-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4a006-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4a006-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4a006-114">Çöp toplama, birden fazla CPU grubu destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a006-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4a006-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4a006-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="4a006-116">Değer</span><span class="sxs-lookup"><span data-stu-id="4a006-116">Value</span></span>|<span data-ttu-id="4a006-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a006-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4a006-118">Çöp toplama, birden fazla CPU grubu desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="4a006-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="4a006-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4a006-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="4a006-120">Sunucu çöp toplama etkin olduğunda çöp toplama, birden fazla CPU grubu destekler.</span><span class="sxs-lookup"><span data-stu-id="4a006-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a006-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a006-121">Child Elements</span></span>  
 <span data-ttu-id="4a006-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="4a006-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a006-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a006-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4a006-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a006-124">Element</span></span>|<span data-ttu-id="4a006-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a006-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4a006-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4a006-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4a006-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4a006-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a006-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a006-128">Remarks</span></span>  
 <span data-ttu-id="4a006-129">Ne zaman bir bilgisayarda birden fazla CPU grubu ve sunucu çöp toplama etkin (bkz [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) öğe), bu öğenin etkinleştirilmesi, çöp toplama, tüm CPU grupları arasında genişletir ve tüm çekirdek içine alır hesabı oluştururken ve Yığınlar Dengeleme.</span><span class="sxs-lookup"><span data-stu-id="4a006-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a006-130">Bu öğe yalnızca çöp toplama iş parçacığı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a006-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="4a006-131">Kullanıcı iş parçacıklarını tüm CPU grupları arasında dağıtmak çalışma zamanını etkinleştirmek üzere, ayrıca etkinleştirmelisiniz [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a006-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a006-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a006-132">Example</span></span>  
 <span data-ttu-id="4a006-133">Aşağıdaki örnek, çöp toplama için birden fazla CPU grubu etkinleştirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a006-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a006-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a006-134">See Also</span></span>  
- [<span data-ttu-id="4a006-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4a006-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="4a006-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="4a006-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="4a006-137">Nasıl yapılır: Eş zamanlı çöp toplama devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="4a006-137">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
- [<span data-ttu-id="4a006-138">İş istasyonu ve sunucu çöp toplama</span><span class="sxs-lookup"><span data-stu-id="4a006-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
