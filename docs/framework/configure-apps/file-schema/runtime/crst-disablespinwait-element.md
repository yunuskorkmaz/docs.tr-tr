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
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704836"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="45e2a-102">\<Crst_DisableSpinWait > öğesi</span><span class="sxs-lookup"><span data-stu-id="45e2a-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="45e2a-103">Döndürme-waıtıng contended olduğunda önemli bir bölümü için devre dışı bırakılıp bırakılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45e2a-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span> \ 
  
 <span data-ttu-id="45e2a-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="45e2a-104">\<configuration></span></span>  
<span data-ttu-id="45e2a-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="45e2a-105">\<runtime></span></span>  
<span data-ttu-id="45e2a-106">\<Crst_DisableSpinWait ></span><span class="sxs-lookup"><span data-stu-id="45e2a-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e2a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45e2a-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45e2a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="45e2a-108">Attributes and Elements</span></span>

<span data-ttu-id="45e2a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45e2a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45e2a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45e2a-110">Attributes</span></span>  
  
|<span data-ttu-id="45e2a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="45e2a-111">Attribute</span></span>|<span data-ttu-id="45e2a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45e2a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45e2a-113">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="45e2a-113">**enabled**</span></span>|<span data-ttu-id="45e2a-114">Bunlar contended olduğunda döndürme-waıtıng kritik bölümler için etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="45e2a-114">Specifies whether spin-waiting for critical sections is enabled when they are contended.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="45e2a-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="45e2a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="45e2a-116">Değer</span><span class="sxs-lookup"><span data-stu-id="45e2a-116">Value</span></span>|<span data-ttu-id="45e2a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45e2a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45e2a-118">1.</span><span class="sxs-lookup"><span data-stu-id="45e2a-118">1</span></span>|<span data-ttu-id="45e2a-119">Döndürme bekleme etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="45e2a-119">Spin-waiting is enabled.</span></span>|  
|<span data-ttu-id="45e2a-120">0</span><span class="sxs-lookup"><span data-stu-id="45e2a-120">0</span></span>|<span data-ttu-id="45e2a-121">Döndürme bekleyen devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="45e2a-121">Spin-waiting is disabled.</span></span> <span data-ttu-id="45e2a-122">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="45e2a-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45e2a-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="45e2a-123">Child Elements</span></span>  
 <span data-ttu-id="45e2a-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="45e2a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45e2a-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="45e2a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="45e2a-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="45e2a-126">Element</span></span>|<span data-ttu-id="45e2a-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45e2a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="45e2a-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="45e2a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="45e2a-129">Çeşitli çalışma zamanı yapılandırma ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="45e2a-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45e2a-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="45e2a-130">Example</span></span>  

<span data-ttu-id="45e2a-131">Döndürme bekleme contended olduğunda önemli bölümleri aşağıdaki örnek devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="45e2a-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45e2a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45e2a-132">See also</span></span>

- [<span data-ttu-id="45e2a-133">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="45e2a-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="45e2a-134">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="45e2a-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
