---
title: <GCCpuGroup> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102898"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="fd6c8-102">\<GCCpuGroup> Elemanı</span><span class="sxs-lookup"><span data-stu-id="fd6c8-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="fd6c8-103">Çöp toplamanın birden çok CPU gruplarını destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="fd6c8-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd6c8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fd6c8-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd6c8-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="fd6c8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span><span class="sxs-lookup"><span data-stu-id="fd6c8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fd6c8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd6c8-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd6c8-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd6c8-108">Attributes and Elements</span></span>

<span data-ttu-id="fd6c8-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd6c8-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd6c8-110">Attributes</span></span>

|<span data-ttu-id="fd6c8-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd6c8-111">Attribute</span></span>|<span data-ttu-id="fd6c8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd6c8-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="fd6c8-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fd6c8-114">Çöp toplamanın birden çok CPU gruplarını destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="fd6c8-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd6c8-115">enabled Attribute</span></span>

|<span data-ttu-id="fd6c8-116">Değer</span><span class="sxs-lookup"><span data-stu-id="fd6c8-116">Value</span></span>|<span data-ttu-id="fd6c8-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd6c8-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="fd6c8-118">Çöp toplama birden çok CPU gruplarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="fd6c8-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="fd6c8-120">Sunucu çöp toplama etkinse, çöp toplama birden çok CPU gruplarını destekler.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="fd6c8-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd6c8-121">Child Elements</span></span>

<span data-ttu-id="fd6c8-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fd6c8-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd6c8-123">Parent Elements</span></span>

|<span data-ttu-id="fd6c8-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd6c8-124">Element</span></span>|<span data-ttu-id="fd6c8-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd6c8-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="fd6c8-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="fd6c8-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fd6c8-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd6c8-128">Remarks</span></span>

<span data-ttu-id="fd6c8-129">Bir bilgisayarda birden çok CPU grubu olduğunda ve sunucu çöp toplama etkinleştirildiğinde [ \<(gcServer>](gcserver-element.md) öğesine bakın), bu öğenin tüm CPU gruplarında çöp toplamayı genişletmesini ve yığınoluştururken ve dengeleme yaparken tüm çekirdekleri hesaba katmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="fd6c8-130">Bu öğe yalnızca çöp toplama iş parçacıkları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="fd6c8-131">Kullanıcı iş parçacıklarını tüm CPU gruplarına dağıtmak için çalışma süresini etkinleştirmek için [ \<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) öğesini de etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="fd6c8-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd6c8-132">Example</span></span>

<span data-ttu-id="fd6c8-133">Aşağıdaki örnek, birden çok CPU grubu için çöp toplamanın nasıl etkinleştirilen gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="fd6c8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd6c8-134">See also</span></span>

- [<span data-ttu-id="fd6c8-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fd6c8-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fd6c8-136">Yapılandırma Dosya Şema</span><span class="sxs-lookup"><span data-stu-id="fd6c8-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fd6c8-137">Eşzamanlı çöp toplamayı devre dışı</span><span class="sxs-lookup"><span data-stu-id="fd6c8-137">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="fd6c8-138">İş istasyonu ve sunucu çöp toplama</span><span class="sxs-lookup"><span data-stu-id="fd6c8-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
