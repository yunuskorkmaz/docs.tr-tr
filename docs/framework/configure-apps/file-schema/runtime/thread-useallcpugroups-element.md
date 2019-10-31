---
title: <Thread_UseAllCpuGroups> Öğesi
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115404"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="49e14-102">\<Thread_UseAllCpuGroups > öğesi</span><span class="sxs-lookup"><span data-stu-id="49e14-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="49e14-103">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="49e14-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="49e14-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="49e14-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="49e14-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="49e14-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="49e14-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups >**</span><span class="sxs-lookup"><span data-stu-id="49e14-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="49e14-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49e14-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49e14-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="49e14-108">Attributes and Elements</span></span>

<span data-ttu-id="49e14-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49e14-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="49e14-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="49e14-110">Attributes</span></span>

|<span data-ttu-id="49e14-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="49e14-111">Attribute</span></span>|<span data-ttu-id="49e14-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49e14-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="49e14-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="49e14-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="49e14-114">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="49e14-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="49e14-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="49e14-115">enabled Attribute</span></span>

|<span data-ttu-id="49e14-116">Değer</span><span class="sxs-lookup"><span data-stu-id="49e14-116">Value</span></span>|<span data-ttu-id="49e14-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49e14-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="49e14-118">Çalışma zamanı, yönetilen iş parçacıklarını birden çok CPU grubu arasında dağıtmaz.</span><span class="sxs-lookup"><span data-stu-id="49e14-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="49e14-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="49e14-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="49e14-120">Bilgisayarın birden çok CPU grubu varsa ve [\<GCCpuGroup >](gccpugroup-element.md) öğesi etkinse, çalışma zamanı yönetilen iş parçacıklarını bırden çok CPU grubu arasında dağıtır.</span><span class="sxs-lookup"><span data-stu-id="49e14-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="49e14-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="49e14-121">Child Elements</span></span>

<span data-ttu-id="49e14-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="49e14-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="49e14-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="49e14-123">Parent Elements</span></span>

|<span data-ttu-id="49e14-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="49e14-124">Element</span></span>|<span data-ttu-id="49e14-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49e14-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="49e14-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="49e14-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="49e14-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="49e14-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="49e14-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49e14-128">Remarks</span></span>

<span data-ttu-id="49e14-129">Bir bilgisayarda birden çok CPU grubu olduğunda, bu öğenin etkinleştirilmesi çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="49e14-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="49e14-130">Bu özelliği kullanmak için çöp toplamayı tüm CPU gruplarına genişleten [\<GCCpuGroup >](gccpugroup-element.md) öğesini etkinleştirmeniz ve Heap 'ler oluştururken ve bunları dengeleyerek tüm çekirdekleri hesaba almalısınız.</span><span class="sxs-lookup"><span data-stu-id="49e14-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="49e14-131">[\<GCCpuGroup >](gccpugroup-element.md) öğesinin etkinleştirilmesi [\<gcServer >](gcserver-element.md) öğesinin etkinleştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="49e14-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="49e14-132">Bu öğeler etkinleştirilmemişse `<Thread_UseAllCpuGroups>` öğesinin etkinleştirilmesi etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="49e14-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="49e14-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="49e14-133">Example</span></span>

<span data-ttu-id="49e14-134">Aşağıdaki örnekte, birden çok CPU grubu için desteğin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="49e14-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="49e14-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49e14-135">See also</span></span>

- [<span data-ttu-id="49e14-136">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="49e14-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="49e14-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="49e14-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="49e14-138">\<GCCpuGroup > öğesi</span><span class="sxs-lookup"><span data-stu-id="49e14-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
