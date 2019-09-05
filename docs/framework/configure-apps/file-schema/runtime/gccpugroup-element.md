---
title: <GCCpuGroup> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ff646f13c5619b0bfca1b61c86013a981c274e3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252558"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="7d0ca-102">\<GCCpuGroup > öğesi</span><span class="sxs-lookup"><span data-stu-id="7d0ca-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="7d0ca-103">Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="7d0ca-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d0ca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7d0ca-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d0ca-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7d0ca-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup>**</span><span class="sxs-lookup"><span data-stu-id="7d0ca-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="7d0ca-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d0ca-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d0ca-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d0ca-108">Attributes and Elements</span></span>

<span data-ttu-id="7d0ca-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d0ca-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d0ca-110">Attributes</span></span>

|<span data-ttu-id="7d0ca-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7d0ca-111">Attribute</span></span>|<span data-ttu-id="7d0ca-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d0ca-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="7d0ca-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7d0ca-114">Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="7d0ca-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7d0ca-115">enabled Attribute</span></span>

|<span data-ttu-id="7d0ca-116">Değer</span><span class="sxs-lookup"><span data-stu-id="7d0ca-116">Value</span></span>|<span data-ttu-id="7d0ca-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d0ca-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="7d0ca-118">Çöp toplama birden çok CPU grubunu desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="7d0ca-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="7d0ca-120">Çöp toplama, sunucu çöp toplama etkinse birden çok CPU grubunu destekler.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7d0ca-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d0ca-121">Child Elements</span></span>

<span data-ttu-id="7d0ca-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7d0ca-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d0ca-123">Parent Elements</span></span>

|<span data-ttu-id="7d0ca-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d0ca-124">Element</span></span>|<span data-ttu-id="7d0ca-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d0ca-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="7d0ca-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="7d0ca-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7d0ca-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d0ca-128">Remarks</span></span>

<span data-ttu-id="7d0ca-129">Bir bilgisayarda birden çok CPU grubu olduğunda ve sunucu çöp toplama özelliği etkin olduğunda (bkz. [ \<gcServer >](gcserver-element.md) öğesi), bu öğenin tüm CPU gruplarında çöp toplamayı genişlettiği ve ve oluştururken tüm çekirdekleri hesaba ayırır Heap 'ler dengeleniyor.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="7d0ca-130">Bu öğe yalnızca çöp toplama iş parçacıkları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="7d0ca-131">Çalışma zamanının tüm CPU gruplarında Kullanıcı iş parçacıklarını dağıtmasını sağlamak için, [ \<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md) öğesini de etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="7d0ca-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d0ca-132">Example</span></span>

<span data-ttu-id="7d0ca-133">Aşağıdaki örnekte, birden çok CPU grubu için çöp toplamanın nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="7d0ca-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d0ca-134">See also</span></span>

- [<span data-ttu-id="7d0ca-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7d0ca-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7d0ca-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="7d0ca-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7d0ca-137">Eşzamanlı atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="7d0ca-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="7d0ca-138">İş istasyonu ve sunucu atık toplama</span><span class="sxs-lookup"><span data-stu-id="7d0ca-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
