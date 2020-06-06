---
title: <Crst_DisableSpinWait> öğesi
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 0683081183081e249b2a9c89e1a6a15f638fb339
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117645"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="3e503-102">\<Crst_DisableSpinWait> öğesi</span><span class="sxs-lookup"><span data-stu-id="3e503-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="3e503-103">Contentıon 'ın, önemli bir bölüm için bekleme için beklenip devre dışı bırakılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e503-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="3e503-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e503-104">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e503-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e503-105">Attributes and Elements</span></span>

<span data-ttu-id="3e503-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e503-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e503-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e503-107">Attributes</span></span>  
  
|<span data-ttu-id="3e503-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e503-108">Attribute</span></span>|<span data-ttu-id="3e503-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e503-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e503-110">**etkinletir**</span><span class="sxs-lookup"><span data-stu-id="3e503-110">**enabled**</span></span>|<span data-ttu-id="3e503-111">Devam edildiğinde kritik bölümlerin dönmesi için bekleme devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e503-111">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3e503-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e503-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="3e503-113">Değer</span><span class="sxs-lookup"><span data-stu-id="3e503-113">Value</span></span>|<span data-ttu-id="3e503-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e503-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e503-115">1</span><span class="sxs-lookup"><span data-stu-id="3e503-115">1</span></span>|<span data-ttu-id="3e503-116">Beklemeyi devre dışı bırak-kritik bir bölüm alınamadığından bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="3e503-116">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="3e503-117">0</span><span class="sxs-lookup"><span data-stu-id="3e503-117">0</span></span>|<span data-ttu-id="3e503-118">Beklemeyi devre dışı bırakma-kritik bir bölüm alınamadığından bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="3e503-118">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="3e503-119">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="3e503-119">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e503-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e503-120">Child Elements</span></span>  
 <span data-ttu-id="3e503-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="3e503-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e503-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e503-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3e503-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e503-123">Element</span></span>|<span data-ttu-id="3e503-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e503-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3e503-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3e503-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3e503-126">Çeşitli çalışma zamanı yapılandırma ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3e503-126">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3e503-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e503-127">Example</span></span>  

<span data-ttu-id="3e503-128">Aşağıdaki örnek, contenbitirildiği zaman, kritik bölümlerde beklemeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3e503-128">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e503-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e503-129">See also</span></span>

- [<span data-ttu-id="3e503-130">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="3e503-130">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3e503-131">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="3e503-131">Configuration File Schema</span></span>](../index.md)
