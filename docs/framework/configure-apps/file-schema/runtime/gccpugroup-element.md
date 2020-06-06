---
title: <GCCpuGroup> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102898"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="5ddef-102">\<GCCpuGroup> Öğesi</span><span class="sxs-lookup"><span data-stu-id="5ddef-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="5ddef-103">Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ddef-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="5ddef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ddef-104">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ddef-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ddef-105">Attributes and Elements</span></span>

<span data-ttu-id="5ddef-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ddef-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ddef-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ddef-107">Attributes</span></span>

|<span data-ttu-id="5ddef-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ddef-108">Attribute</span></span>|<span data-ttu-id="5ddef-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ddef-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="5ddef-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5ddef-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="5ddef-111">Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ddef-111">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="5ddef-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ddef-112">enabled Attribute</span></span>

|<span data-ttu-id="5ddef-113">Değer</span><span class="sxs-lookup"><span data-stu-id="5ddef-113">Value</span></span>|<span data-ttu-id="5ddef-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ddef-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="5ddef-115">Çöp toplama birden çok CPU grubunu desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="5ddef-115">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="5ddef-116">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5ddef-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="5ddef-117">Çöp toplama, sunucu çöp toplama etkinse birden çok CPU grubunu destekler.</span><span class="sxs-lookup"><span data-stu-id="5ddef-117">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5ddef-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ddef-118">Child Elements</span></span>

<span data-ttu-id="5ddef-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ddef-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ddef-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ddef-120">Parent Elements</span></span>

|<span data-ttu-id="5ddef-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ddef-121">Element</span></span>|<span data-ttu-id="5ddef-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ddef-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="5ddef-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5ddef-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="5ddef-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5ddef-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ddef-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ddef-125">Remarks</span></span>

<span data-ttu-id="5ddef-126">Bir bilgisayarda birden çok CPU grubu olduğunda ve sunucu çöp toplama özelliği etkin olduğunda (bkz. [\<gcServer>](gcserver-element.md) öğesi), bu öğenin tüm CPU gruplarında çöp toplamayı genişlettiğini ve Heap 'ler oluştururken ve bunları dengeleyerek tüm çekirdekleri hesaba getirecek şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5ddef-126">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="5ddef-127">Bu öğe yalnızca çöp toplama iş parçacıkları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5ddef-127">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="5ddef-128">Çalışma zamanının tüm CPU gruplarında Kullanıcı iş parçacıklarını dağıtmasını sağlamak için, öğesini de etkinleştirmeniz gerekir [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="5ddef-128">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="5ddef-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ddef-129">Example</span></span>

<span data-ttu-id="5ddef-130">Aşağıdaki örnekte, birden çok CPU grubu için çöp toplamanın nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ddef-130">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5ddef-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ddef-131">See also</span></span>

- [<span data-ttu-id="5ddef-132">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="5ddef-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5ddef-133">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="5ddef-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5ddef-134">Eşzamanlı atık toplamayı devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="5ddef-134">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="5ddef-135">İş istasyonu ve sunucu atık toplama</span><span class="sxs-lookup"><span data-stu-id="5ddef-135">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
