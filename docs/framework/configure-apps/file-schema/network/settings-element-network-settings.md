---
description: 'Daha fazla bilgi edinin: <settings> öğesi (ağ ayarları)'
title: <settings> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: e6ed242e68ac9a9e2c20067d66681bbcd51fcc50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712980"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="4a3ac-103">\<settings> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="4a3ac-103">\<settings> Element (Network Settings)</span></span>

<span data-ttu-id="4a3ac-104">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4a3ac-104">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="4a3ac-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a3ac-105">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a3ac-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a3ac-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4a3ac-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a3ac-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4a3ac-108">Attributes</span></span>  

 <span data-ttu-id="4a3ac-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a3ac-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a3ac-110">Child Elements</span></span>  
  
|<span data-ttu-id="4a3ac-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a3ac-111">Element</span></span>|<span data-ttu-id="4a3ac-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a3ac-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a3ac-113">httpListener</span><span class="sxs-lookup"><span data-stu-id="4a3ac-113">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="4a3ac-114">Sınıf tarafından kullanılan parametreleri özelleştirir <xref:System.Net.HttpListener> .</span><span class="sxs-lookup"><span data-stu-id="4a3ac-114">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="4a3ac-115">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="4a3ac-115">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="4a3ac-116">Web isteği parametrelerini özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-116">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="4a3ac-117">IPv6</span><span class="sxs-lookup"><span data-stu-id="4a3ac-117">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="4a3ac-118">Internet Protokolü sürüm 6 (IPv6) desteğini sunar.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-118">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="4a3ac-119">\<performanceCounter> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="4a3ac-119">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="4a3ac-120">Ağ performans sayaçlarını etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-120">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="4a3ac-121">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="4a3ac-121">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="4a3ac-122">Ağ kaynaklarına bağlantıları yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-122">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="4a3ac-123">yuvasının</span><span class="sxs-lookup"><span data-stu-id="4a3ac-123">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="4a3ac-124">Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-124">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="4a3ac-125">\<webProxyScript> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="4a3ac-125">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="4a3ac-126">Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-126">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a3ac-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a3ac-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4a3ac-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a3ac-128">Element</span></span>|<span data-ttu-id="4a3ac-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a3ac-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a3ac-130">system.net</span><span class="sxs-lookup"><span data-stu-id="4a3ac-130">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="4a3ac-131">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-131">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a3ac-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a3ac-132">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4a3ac-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4a3ac-133">Configuration Files</span></span>  

 <span data-ttu-id="4a3ac-134">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3ac-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-135">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="4a3ac-136">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4a3ac-136">Network Settings Schema</span></span>](index.md)
