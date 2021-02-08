---
description: 'Daha fazla bilgi edinin: <GCCpuGroup> öğesi'
title: <GCCpuGroup> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: d4b3aa7084cbc2cb23b273bea95ffaec6e3a74d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786999"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="21463-103">\<GCCpuGroup> Öğesi</span><span class="sxs-lookup"><span data-stu-id="21463-103">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="21463-104">Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="21463-104">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="21463-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="21463-105">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21463-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21463-106">Attributes and Elements</span></span>

<span data-ttu-id="21463-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21463-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="21463-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21463-108">Attributes</span></span>

|<span data-ttu-id="21463-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="21463-109">Attribute</span></span>|<span data-ttu-id="21463-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21463-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="21463-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="21463-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="21463-112">Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="21463-112">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="21463-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="21463-113">enabled Attribute</span></span>

|<span data-ttu-id="21463-114">Değer</span><span class="sxs-lookup"><span data-stu-id="21463-114">Value</span></span>|<span data-ttu-id="21463-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21463-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="21463-116">Çöp toplama birden çok CPU grubunu desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="21463-116">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="21463-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="21463-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="21463-118">Çöp toplama, sunucu çöp toplama etkinse birden çok CPU grubunu destekler.</span><span class="sxs-lookup"><span data-stu-id="21463-118">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="21463-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21463-119">Child Elements</span></span>

<span data-ttu-id="21463-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="21463-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="21463-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21463-121">Parent Elements</span></span>

|<span data-ttu-id="21463-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="21463-122">Element</span></span>|<span data-ttu-id="21463-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21463-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="21463-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="21463-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="21463-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="21463-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="21463-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21463-126">Remarks</span></span>

<span data-ttu-id="21463-127">Bir bilgisayarda birden çok CPU grubu olduğunda ve sunucu çöp toplama özelliği etkin olduğunda (bkz. [\<gcServer>](gcserver-element.md) öğesi), bu öğenin tüm CPU gruplarında çöp toplamayı genişlettiğini ve Heap 'ler oluştururken ve bunları dengeleyerek tüm çekirdekleri hesaba getirecek şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="21463-127">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="21463-128">Bu öğe yalnızca çöp toplama iş parçacıkları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="21463-128">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="21463-129">Çalışma zamanının tüm CPU gruplarında Kullanıcı iş parçacıklarını dağıtmasını sağlamak için, öğesini de etkinleştirmeniz gerekir [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="21463-129">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="21463-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="21463-130">Example</span></span>

<span data-ttu-id="21463-131">Aşağıdaki örnekte, birden çok CPU grubu için çöp toplamanın nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="21463-131">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="21463-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21463-132">See also</span></span>

- [<span data-ttu-id="21463-133">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="21463-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="21463-134">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="21463-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="21463-135">Eşzamanlı atık toplamayı devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="21463-135">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="21463-136">İş istasyonu ve sunucu atık toplama</span><span class="sxs-lookup"><span data-stu-id="21463-136">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
