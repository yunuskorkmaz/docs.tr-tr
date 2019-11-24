---
title: <GCCpuGroup> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: ae9c96c9d49cf3f6be94da3f77b91423cab12e0b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430485"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="d0fe9-102">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="d0fe9-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="d0fe9-103">Specifies whether garbage collection supports multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="d0fe9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d0fe9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d0fe9-105">&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d0fe9-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d0fe9-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup>**</span><span class="sxs-lookup"><span data-stu-id="d0fe9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d0fe9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0fe9-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0fe9-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0fe9-108">Attributes and Elements</span></span>

<span data-ttu-id="d0fe9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0fe9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0fe9-110">Attributes</span></span>

|<span data-ttu-id="d0fe9-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0fe9-111">Attribute</span></span>|<span data-ttu-id="d0fe9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0fe9-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="d0fe9-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d0fe9-114">Specifies whether garbage collection supports multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="d0fe9-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0fe9-115">enabled Attribute</span></span>

|<span data-ttu-id="d0fe9-116">Değer</span><span class="sxs-lookup"><span data-stu-id="d0fe9-116">Value</span></span>|<span data-ttu-id="d0fe9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0fe9-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="d0fe9-118">Garbage collection does not support multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="d0fe9-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="d0fe9-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d0fe9-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0fe9-121">Child Elements</span></span>

<span data-ttu-id="d0fe9-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d0fe9-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0fe9-123">Parent Elements</span></span>

|<span data-ttu-id="d0fe9-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0fe9-124">Element</span></span>|<span data-ttu-id="d0fe9-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0fe9-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="d0fe9-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="d0fe9-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0fe9-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0fe9-128">Remarks</span></span>

<span data-ttu-id="d0fe9-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="d0fe9-130">This element applies only to garbage collection threads.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="d0fe9-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="d0fe9-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0fe9-132">Example</span></span>

<span data-ttu-id="d0fe9-133">The following example shows how to enable garbage collection for multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d0fe9-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0fe9-134">See also</span></span>

- [<span data-ttu-id="d0fe9-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d0fe9-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d0fe9-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d0fe9-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d0fe9-137">To disable concurrent garbage collection</span><span class="sxs-lookup"><span data-stu-id="d0fe9-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="d0fe9-138">Workstation and server garbage collection</span><span class="sxs-lookup"><span data-stu-id="d0fe9-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)
