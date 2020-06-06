---
title: <Thread_UseAllCpuGroups> Öğesi
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115404"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="a2b8c-102">\<Thread_UseAllCpuGroups> Öğesi</span><span class="sxs-lookup"><span data-stu-id="a2b8c-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="a2b8c-103">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="a2b8c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2b8c-104">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2b8c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2b8c-105">Attributes and Elements</span></span>

<span data-ttu-id="a2b8c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2b8c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a2b8c-107">Attributes</span></span>

|<span data-ttu-id="a2b8c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a2b8c-108">Attribute</span></span>|<span data-ttu-id="a2b8c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2b8c-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a2b8c-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a2b8c-111">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-111">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="a2b8c-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a2b8c-112">enabled Attribute</span></span>

|<span data-ttu-id="a2b8c-113">Değer</span><span class="sxs-lookup"><span data-stu-id="a2b8c-113">Value</span></span>|<span data-ttu-id="a2b8c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2b8c-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="a2b8c-115">Çalışma zamanı, yönetilen iş parçacıklarını birden çok CPU grubu arasında dağıtmaz.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-115">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="a2b8c-116">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="a2b8c-117">Çalışma zamanı, yönetilen iş parçacıklarını birden çok CPU grubuna dağıtır ve bilgisayarda birden çok CPU grubu varsa ve [\<GCCpuGroup>](gccpugroup-element.md) öğesi etkinse.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-117">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a2b8c-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2b8c-118">Child Elements</span></span>

<span data-ttu-id="a2b8c-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a2b8c-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2b8c-120">Parent Elements</span></span>

|<span data-ttu-id="a2b8c-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a2b8c-121">Element</span></span>|<span data-ttu-id="a2b8c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2b8c-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a2b8c-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a2b8c-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a2b8c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2b8c-125">Remarks</span></span>

<span data-ttu-id="a2b8c-126">Bir bilgisayarda birden çok CPU grubu olduğunda, bu öğenin etkinleştirilmesi çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-126">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="a2b8c-127">Bu özelliği kullanmak için [\<GCCpuGroup>](gccpugroup-element.md) çöp toplamayı tüm CPU gruplarına genişleten ve Heap 'ler oluştururken ve dengeleyerek tüm çekirdekleri hesaba götüren öğesini de etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-127">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="a2b8c-128">Öğesinin etkinleştirilmesi için [\<GCCpuGroup>](gccpugroup-element.md) öğesini etkinleştirmeniz gerekir [\<gcServer>](gcserver-element.md) .</span><span class="sxs-lookup"><span data-stu-id="a2b8c-128">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="a2b8c-129">Bu öğeler etkinleştirilmemişse, `<Thread_UseAllCpuGroups>` öğesinin etkinleştirilmesi etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-129">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="a2b8c-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2b8c-130">Example</span></span>

<span data-ttu-id="a2b8c-131">Aşağıdaki örnekte, birden çok CPU grubu için desteğin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-131">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a2b8c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b8c-132">See also</span></span>

- [<span data-ttu-id="a2b8c-133">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="a2b8c-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a2b8c-134">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="a2b8c-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a2b8c-135">\<GCCpuGroup>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="a2b8c-135">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
