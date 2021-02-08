---
description: 'Hakkında daha fazla bilgi edinin: <Thread_UseAllCpuGroups> öğesi'
title: <Thread_UseAllCpuGroups> Öğesi
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: 3f11ba6855caab25bd261de71c80c78232f2690f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802417"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="83dbd-103">\<Thread_UseAllCpuGroups> Öğesi</span><span class="sxs-lookup"><span data-stu-id="83dbd-103">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="83dbd-104">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="83dbd-104">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="83dbd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="83dbd-105">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="83dbd-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="83dbd-106">Attributes and Elements</span></span>

<span data-ttu-id="83dbd-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83dbd-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="83dbd-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="83dbd-108">Attributes</span></span>

|<span data-ttu-id="83dbd-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="83dbd-109">Attribute</span></span>|<span data-ttu-id="83dbd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83dbd-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="83dbd-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="83dbd-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="83dbd-112">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="83dbd-112">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="83dbd-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="83dbd-113">enabled Attribute</span></span>

|<span data-ttu-id="83dbd-114">Değer</span><span class="sxs-lookup"><span data-stu-id="83dbd-114">Value</span></span>|<span data-ttu-id="83dbd-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83dbd-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="83dbd-116">Çalışma zamanı, yönetilen iş parçacıklarını birden çok CPU grubu arasında dağıtmaz.</span><span class="sxs-lookup"><span data-stu-id="83dbd-116">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="83dbd-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="83dbd-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="83dbd-118">Çalışma zamanı, yönetilen iş parçacıklarını birden çok CPU grubuna dağıtır ve bilgisayarda birden çok CPU grubu varsa ve [\<GCCpuGroup>](gccpugroup-element.md) öğesi etkinse.</span><span class="sxs-lookup"><span data-stu-id="83dbd-118">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="83dbd-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="83dbd-119">Child Elements</span></span>

<span data-ttu-id="83dbd-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="83dbd-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="83dbd-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="83dbd-121">Parent Elements</span></span>

|<span data-ttu-id="83dbd-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="83dbd-122">Element</span></span>|<span data-ttu-id="83dbd-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83dbd-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="83dbd-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="83dbd-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="83dbd-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="83dbd-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="83dbd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83dbd-126">Remarks</span></span>

<span data-ttu-id="83dbd-127">Bir bilgisayarda birden çok CPU grubu olduğunda, bu öğenin etkinleştirilmesi çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="83dbd-127">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="83dbd-128">Bu özelliği kullanmak için [\<GCCpuGroup>](gccpugroup-element.md) çöp toplamayı tüm CPU gruplarına genişleten ve Heap 'ler oluştururken ve dengeleyerek tüm çekirdekleri hesaba götüren öğesini de etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="83dbd-128">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="83dbd-129">Öğesinin etkinleştirilmesi için [\<GCCpuGroup>](gccpugroup-element.md) öğesini etkinleştirmeniz gerekir [\<gcServer>](gcserver-element.md) .</span><span class="sxs-lookup"><span data-stu-id="83dbd-129">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="83dbd-130">Bu öğeler etkinleştirilmemişse, `<Thread_UseAllCpuGroups>` öğesinin etkinleştirilmesi etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="83dbd-130">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="83dbd-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="83dbd-131">Example</span></span>

<span data-ttu-id="83dbd-132">Aşağıdaki örnekte, birden çok CPU grubu için desteğin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="83dbd-132">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="83dbd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83dbd-133">See also</span></span>

- [<span data-ttu-id="83dbd-134">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="83dbd-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="83dbd-135">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="83dbd-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="83dbd-136">\<GCCpuGroup> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="83dbd-136">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
