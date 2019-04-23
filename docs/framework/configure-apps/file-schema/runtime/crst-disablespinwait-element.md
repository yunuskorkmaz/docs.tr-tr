---
title: < Crst_DisableSpinWait > öğesi
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cde26250db0b3d11c51a18b7ebd378953ae0958
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982177"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="68b87-102">\<Crst_DisableSpinWait > öğesi</span><span class="sxs-lookup"><span data-stu-id="68b87-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="68b87-103">Döndürme-waıtıng contended olduğunda önemli bir bölümü için devre dışı bırakılıp bırakılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="68b87-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span> \ 
  
 <span data-ttu-id="68b87-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="68b87-104">\<configuration></span></span>  
<span data-ttu-id="68b87-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="68b87-105">\<runtime></span></span>  
<span data-ttu-id="68b87-106">\<Crst_DisableSpinWait ></span><span class="sxs-lookup"><span data-stu-id="68b87-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b87-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68b87-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68b87-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="68b87-108">Attributes and Elements</span></span>

<span data-ttu-id="68b87-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68b87-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68b87-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="68b87-110">Attributes</span></span>  
  
|<span data-ttu-id="68b87-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="68b87-111">Attribute</span></span>|<span data-ttu-id="68b87-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68b87-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68b87-113">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="68b87-113">**enabled**</span></span>|<span data-ttu-id="68b87-114">Bunlar contended olduğunda döndürme-waıtıng kritik bölümler için etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="68b87-114">Specifies whether spin-waiting for critical sections is enabled when they are contended.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="68b87-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="68b87-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="68b87-116">Değer</span><span class="sxs-lookup"><span data-stu-id="68b87-116">Value</span></span>|<span data-ttu-id="68b87-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68b87-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68b87-118">1.</span><span class="sxs-lookup"><span data-stu-id="68b87-118">1</span></span>|<span data-ttu-id="68b87-119">Döndürme bekleme etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="68b87-119">Spin-waiting is enabled.</span></span>|  
|<span data-ttu-id="68b87-120">0</span><span class="sxs-lookup"><span data-stu-id="68b87-120">0</span></span>|<span data-ttu-id="68b87-121">Döndürme bekleyen devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="68b87-121">Spin-waiting is disabled.</span></span> <span data-ttu-id="68b87-122">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="68b87-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68b87-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="68b87-123">Child Elements</span></span>  
 <span data-ttu-id="68b87-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="68b87-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68b87-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="68b87-125">Parent Elements</span></span>  
  
|<span data-ttu-id="68b87-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="68b87-126">Element</span></span>|<span data-ttu-id="68b87-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68b87-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="68b87-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="68b87-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="68b87-129">Çeşitli çalışma zamanı yapılandırma ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="68b87-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="68b87-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="68b87-130">Example</span></span>  

<span data-ttu-id="68b87-131">Döndürme bekleme contended olduğunda önemli bölümleri aşağıdaki örnek devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="68b87-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="68b87-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68b87-132">See also</span></span>

- [<span data-ttu-id="68b87-133">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="68b87-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="68b87-134">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="68b87-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
