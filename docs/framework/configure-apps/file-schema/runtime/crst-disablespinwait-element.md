---
title: < Crst_DisableSpinWait > öğesi
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a52dd671f1fbf6fda5bdc92c0935784181eb4b03
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663834"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="35ed7-102">\<Crst_DisableSpinWait > öğesi</span><span class="sxs-lookup"><span data-stu-id="35ed7-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="35ed7-103">Contentıon 'ın, önemli bir bölüm için bekleme için beklenip devre dışı bırakılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35ed7-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="35ed7-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="35ed7-104">\<configuration></span></span>  
<span data-ttu-id="35ed7-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="35ed7-105">\<runtime></span></span>  
<span data-ttu-id="35ed7-106">\<Crst_DisableSpinWait ></span><span class="sxs-lookup"><span data-stu-id="35ed7-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ed7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35ed7-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35ed7-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="35ed7-108">Attributes and Elements</span></span>

<span data-ttu-id="35ed7-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35ed7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35ed7-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="35ed7-110">Attributes</span></span>  
  
|<span data-ttu-id="35ed7-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="35ed7-111">Attribute</span></span>|<span data-ttu-id="35ed7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35ed7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35ed7-113">**etkinletir**</span><span class="sxs-lookup"><span data-stu-id="35ed7-113">**enabled**</span></span>|<span data-ttu-id="35ed7-114">Devam edildiğinde kritik bölümlerin dönmesi için bekleme devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35ed7-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="35ed7-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="35ed7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="35ed7-116">Değer</span><span class="sxs-lookup"><span data-stu-id="35ed7-116">Value</span></span>|<span data-ttu-id="35ed7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35ed7-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35ed7-118">1\.</span><span class="sxs-lookup"><span data-stu-id="35ed7-118">1</span></span>|<span data-ttu-id="35ed7-119">Beklemeyi devre dışı bırak-kritik bir bölüm alınamadığından bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="35ed7-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="35ed7-120">0</span><span class="sxs-lookup"><span data-stu-id="35ed7-120">0</span></span>|<span data-ttu-id="35ed7-121">Beklemeyi devre dışı bırakma-kritik bir bölüm alınamadığından bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="35ed7-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="35ed7-122">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="35ed7-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35ed7-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="35ed7-123">Child Elements</span></span>  
 <span data-ttu-id="35ed7-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="35ed7-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35ed7-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="35ed7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="35ed7-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="35ed7-126">Element</span></span>|<span data-ttu-id="35ed7-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35ed7-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="35ed7-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="35ed7-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="35ed7-129">Çeşitli çalışma zamanı yapılandırma ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="35ed7-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="35ed7-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="35ed7-130">Example</span></span>  

<span data-ttu-id="35ed7-131">Aşağıdaki örnek, contenbitirildiği zaman, kritik bölümlerde beklemeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="35ed7-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35ed7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35ed7-132">See also</span></span>

- [<span data-ttu-id="35ed7-133">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="35ed7-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="35ed7-134">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="35ed7-134">Configuration File Schema</span></span>](../index.md)
