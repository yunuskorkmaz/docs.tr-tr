---
description: 'Hakkında daha fazla bilgi edinin: <Crst_DisableSpinWait> öğesi'
title: <Crst_DisableSpinWait> öğesi
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: fca6fed2dabc3d1319ad030bb13bbb35a561b9aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795111"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="05d06-103">\<Crst_DisableSpinWait> öğesi</span><span class="sxs-lookup"><span data-stu-id="05d06-103">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="05d06-104">Contentıon 'ın, önemli bir bölüm için bekleme için beklenip devre dışı bırakılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="05d06-104">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="05d06-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="05d06-105">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05d06-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="05d06-106">Attributes and Elements</span></span>

<span data-ttu-id="05d06-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05d06-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05d06-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="05d06-108">Attributes</span></span>  
  
|<span data-ttu-id="05d06-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="05d06-109">Attribute</span></span>|<span data-ttu-id="05d06-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05d06-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05d06-111">**etkinletir**</span><span class="sxs-lookup"><span data-stu-id="05d06-111">**enabled**</span></span>|<span data-ttu-id="05d06-112">Devam edildiğinde kritik bölümlerin dönmesi için bekleme devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="05d06-112">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="05d06-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="05d06-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="05d06-114">Değer</span><span class="sxs-lookup"><span data-stu-id="05d06-114">Value</span></span>|<span data-ttu-id="05d06-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05d06-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05d06-116">1</span><span class="sxs-lookup"><span data-stu-id="05d06-116">1</span></span>|<span data-ttu-id="05d06-117">Beklemeyi devre dışı bırak-kritik bir bölüm alınamadığından bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="05d06-117">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="05d06-118">0</span><span class="sxs-lookup"><span data-stu-id="05d06-118">0</span></span>|<span data-ttu-id="05d06-119">Beklemeyi devre dışı bırakma-kritik bir bölüm alınamadığından bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="05d06-119">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="05d06-120">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="05d06-120">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05d06-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="05d06-121">Child Elements</span></span>  

 <span data-ttu-id="05d06-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="05d06-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05d06-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="05d06-123">Parent Elements</span></span>  
  
|<span data-ttu-id="05d06-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="05d06-124">Element</span></span>|<span data-ttu-id="05d06-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05d06-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="05d06-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="05d06-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="05d06-127">Çeşitli çalışma zamanı yapılandırma ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="05d06-127">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05d06-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="05d06-128">Example</span></span>  

<span data-ttu-id="05d06-129">Aşağıdaki örnek, contenbitirildiği zaman, kritik bölümlerde beklemeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="05d06-129">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05d06-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05d06-130">See also</span></span>

- [<span data-ttu-id="05d06-131">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="05d06-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="05d06-132">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="05d06-132">Configuration File Schema</span></span>](../index.md)
