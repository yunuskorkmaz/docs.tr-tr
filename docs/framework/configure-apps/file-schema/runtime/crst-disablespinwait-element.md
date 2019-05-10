---
title: < Crst_DisableSpinWait > öğesi
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f89f0558c11e229fef2ca3cd619e3c033f12c858
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754667"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="66258-102">\<Crst_DisableSpinWait > öğesi</span><span class="sxs-lookup"><span data-stu-id="66258-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="66258-103">Döndürme-waıtıng contended olduğunda önemli bir bölümü için devre dışı bırakılıp bırakılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="66258-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="66258-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="66258-104">\<configuration></span></span>  
<span data-ttu-id="66258-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="66258-105">\<runtime></span></span>  
<span data-ttu-id="66258-106">\<Crst_DisableSpinWait ></span><span class="sxs-lookup"><span data-stu-id="66258-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66258-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66258-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66258-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="66258-108">Attributes and Elements</span></span>

<span data-ttu-id="66258-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66258-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66258-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="66258-110">Attributes</span></span>  
  
|<span data-ttu-id="66258-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="66258-111">Attribute</span></span>|<span data-ttu-id="66258-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66258-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66258-113">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="66258-113">**enabled**</span></span>|<span data-ttu-id="66258-114">Döndürme-contended kritik bölümlere bekleniyor devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="66258-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="66258-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="66258-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="66258-116">Değer</span><span class="sxs-lookup"><span data-stu-id="66258-116">Value</span></span>|<span data-ttu-id="66258-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66258-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="66258-118">1.</span><span class="sxs-lookup"><span data-stu-id="66258-118">1</span></span>|<span data-ttu-id="66258-119">Kritik bir bölüm alınamıyor, döndürme bekleyen devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="66258-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="66258-120">0</span><span class="sxs-lookup"><span data-stu-id="66258-120">0</span></span>|<span data-ttu-id="66258-121">Kritik bir bölüm alınamıyor, döndürme bekleyen devre dışı bırakmayın.</span><span class="sxs-lookup"><span data-stu-id="66258-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="66258-122">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="66258-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66258-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="66258-123">Child Elements</span></span>  
 <span data-ttu-id="66258-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="66258-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66258-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="66258-125">Parent Elements</span></span>  
  
|<span data-ttu-id="66258-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="66258-126">Element</span></span>|<span data-ttu-id="66258-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66258-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="66258-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="66258-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="66258-129">Çeşitli çalışma zamanı yapılandırma ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="66258-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="66258-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="66258-130">Example</span></span>  

<span data-ttu-id="66258-131">Döndürme bekleme contended olduğunda önemli bölümleri aşağıdaki örnek devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="66258-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66258-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66258-132">See also</span></span>

- [<span data-ttu-id="66258-133">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="66258-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="66258-134">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="66258-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
