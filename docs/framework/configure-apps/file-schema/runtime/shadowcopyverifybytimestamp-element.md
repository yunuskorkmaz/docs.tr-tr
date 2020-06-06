---
title: <shadowCopyVerifyByTimestamp> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115734"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="e00a8-102">\<shadowCopyVerifyByTimestamp> Öğesi</span><span class="sxs-lookup"><span data-stu-id="e00a8-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="e00a8-103">Gölge kopyalamanın .NET Framework 4 ' te tanıtılan varsayılan başlangıç davranışını kullanıp kullanmadığını veya .NET Framework önceki sürümlerinin başlangıç davranışına geri dönmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e00a8-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="e00a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e00a8-104">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e00a8-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e00a8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e00a8-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e00a8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e00a8-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e00a8-107">Attributes</span></span>  
  
|<span data-ttu-id="e00a8-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e00a8-108">Attribute</span></span>|<span data-ttu-id="e00a8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e00a8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e00a8-110">enabled</span><span class="sxs-lookup"><span data-stu-id="e00a8-110">enabled</span></span>|<span data-ttu-id="e00a8-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e00a8-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e00a8-112">Derlemeyi gölge kopyalamadan önce bir derlemenin güncelleştirilip güncelleştirilmediğini anlamak için, gölge kopyalamayı kullanan uygulama etki alanlarının derleme zaman damgalarını karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="e00a8-112">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e00a8-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e00a8-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="e00a8-114">Değer</span><span class="sxs-lookup"><span data-stu-id="e00a8-114">Value</span></span>|<span data-ttu-id="e00a8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e00a8-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e00a8-116">true</span><span class="sxs-lookup"><span data-stu-id="e00a8-116">true</span></span>|<span data-ttu-id="e00a8-117">Başlangıçta, yalnızca gölge kopya dizinine son kopyalandıklarından bu yana güncelleştirilmiş derlemeleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="e00a8-117">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="e00a8-118">.NET Framework 4 için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="e00a8-118">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="e00a8-119">yanlış</span><span class="sxs-lookup"><span data-stu-id="e00a8-119">false</span></span>|<span data-ttu-id="e00a8-120">Başlangıçtaki tüm dosyaları kopyalamak için .NET Framework önceki sürümlerinin başlangıç davranışına geri döner.</span><span class="sxs-lookup"><span data-stu-id="e00a8-120">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e00a8-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e00a8-121">Child Elements</span></span>  
 <span data-ttu-id="e00a8-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="e00a8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e00a8-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e00a8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e00a8-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e00a8-124">Element</span></span>|<span data-ttu-id="e00a8-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e00a8-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e00a8-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e00a8-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e00a8-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e00a8-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e00a8-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e00a8-128">Remarks</span></span>  
 <span data-ttu-id="e00a8-129">.NET Framework 4 ' te başlayarak, derlemeler yalnızca, zaman damgaları, gölge kopya dizinine en son kopyalandıklarından bu yana değiştirildikleri belirtilmişse gölge olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="e00a8-129">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="e00a8-130">Bu, gölge kopyalama [derlemeler](../../../app-domains/shadow-copy-assemblies.md)' de açıklandığı gibi, gölge kopyalamayı kullanan birçok uygulama için başlangıç zamanlarını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="e00a8-130">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="e00a8-131">Yüksek oranda yüzdesi ve derleme güncelleştirmelerinin sıklığı olan uygulamalar bu değişiklikten daha fazla avantaj sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e00a8-131">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="e00a8-132">Bu durumda, .NET Framework önceki sürümlerinin davranışını geri yüklemek için bu öğeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e00a8-132">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e00a8-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="e00a8-133">Example</span></span>  
 <span data-ttu-id="e00a8-134">Aşağıdaki örnek, .NET Framework 4 ' te gölge kopyalamanın varsayılan başlatma davranışının nasıl devre dışı bırakılacağını ve .NET Framework önceki sürümlerinin başlangıç davranışına geri dönmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e00a8-134">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e00a8-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e00a8-135">See also</span></span>

- [<span data-ttu-id="e00a8-136">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e00a8-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e00a8-137">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e00a8-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e00a8-138">Gölge Kopyalama Derlemeleri</span><span class="sxs-lookup"><span data-stu-id="e00a8-138">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
