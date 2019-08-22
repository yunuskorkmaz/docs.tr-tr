---
title: <Thread_UseAllCpuGroups> Öğesi
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9ee6bdb7094ea2bc9e283e331c0f6ad9b68e4f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663419"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="45fa5-102">\<Thread_UseAllCpuGroups > öğesi</span><span class="sxs-lookup"><span data-stu-id="45fa5-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="45fa5-103">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45fa5-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="45fa5-104">\<Yapılandırma > </span><span class="sxs-lookup"><span data-stu-id="45fa5-104">\<configuration></span></span>\
<span data-ttu-id="45fa5-105">\<çalışma zamanı > </span><span class="sxs-lookup"><span data-stu-id="45fa5-105">\<runtime></span></span>\
<span data-ttu-id="45fa5-106">\<Thread_UseAllCpuGroups ></span><span class="sxs-lookup"><span data-stu-id="45fa5-106">\<Thread_UseAllCpuGroups></span></span>

## <a name="syntax"></a><span data-ttu-id="45fa5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45fa5-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="45fa5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="45fa5-108">Attributes and Elements</span></span>

<span data-ttu-id="45fa5-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45fa5-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="45fa5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45fa5-110">Attributes</span></span>

|<span data-ttu-id="45fa5-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="45fa5-111">Attribute</span></span>|<span data-ttu-id="45fa5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45fa5-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="45fa5-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="45fa5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="45fa5-114">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45fa5-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="45fa5-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="45fa5-115">enabled Attribute</span></span>

|<span data-ttu-id="45fa5-116">Değer</span><span class="sxs-lookup"><span data-stu-id="45fa5-116">Value</span></span>|<span data-ttu-id="45fa5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45fa5-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="45fa5-118">Çalışma zamanı, yönetilen iş parçacıklarını birden çok CPU grubu arasında dağıtmaz.</span><span class="sxs-lookup"><span data-stu-id="45fa5-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="45fa5-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="45fa5-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="45fa5-120">Bilgisayarın birden çok CPU grubu varsa ve [ \<GCCpuGroup >](gccpugroup-element.md) öğesi etkinse, çalışma zamanı yönetilen iş parçacıklarını birden çok CPU grubuna dağıtır.</span><span class="sxs-lookup"><span data-stu-id="45fa5-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="45fa5-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="45fa5-121">Child Elements</span></span>

<span data-ttu-id="45fa5-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="45fa5-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="45fa5-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="45fa5-123">Parent Elements</span></span>

|<span data-ttu-id="45fa5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="45fa5-124">Element</span></span>|<span data-ttu-id="45fa5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45fa5-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="45fa5-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="45fa5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="45fa5-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="45fa5-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="45fa5-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45fa5-128">Remarks</span></span>

<span data-ttu-id="45fa5-129">Bir bilgisayarda birden çok CPU grubu olduğunda, bu öğenin etkinleştirilmesi çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="45fa5-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="45fa5-130">Bu özelliği kullanmak için, atık toplamayı tüm CPU gruplarına genişleten ve Heap 'ler oluştururken ve dengeleyerek tüm çekirdekleri hesaba götüren [ \<GCCpuGroup >](gccpugroup-element.md) öğesini de etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="45fa5-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="45fa5-131">GCCpuGroup > öğesinin etkinleştirilmesi, [gcServer > öğesinin etkinleştirilmesini gerektirir. \<](gcserver-element.md) [ \<](gccpugroup-element.md)</span><span class="sxs-lookup"><span data-stu-id="45fa5-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="45fa5-132">Bu öğeler etkinleştirilmemişse, `<Thread_UseAllCpuGroups>` öğesinin etkinleştirilmesi etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="45fa5-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="45fa5-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="45fa5-133">Example</span></span>

<span data-ttu-id="45fa5-134">Aşağıdaki örnekte, birden çok CPU grubu için desteğin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="45fa5-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="45fa5-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45fa5-135">See also</span></span>

- [<span data-ttu-id="45fa5-136">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="45fa5-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="45fa5-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="45fa5-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="45fa5-138">\<GCCpuGroup > öğesi</span><span class="sxs-lookup"><span data-stu-id="45fa5-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
