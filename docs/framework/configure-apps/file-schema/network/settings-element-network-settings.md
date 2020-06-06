---
title: <settings> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: d510c445c585a36005ed415b14188efc4be03984
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089114"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="4e8b5-102">\<settings> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="4e8b5-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="4e8b5-103">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4e8b5-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="4e8b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e8b5-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e8b5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e8b5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4e8b5-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e8b5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4e8b5-107">Attributes</span></span>  
 <span data-ttu-id="4e8b5-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4e8b5-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e8b5-109">Child Elements</span></span>  
  
|<span data-ttu-id="4e8b5-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="4e8b5-110">Element</span></span>|<span data-ttu-id="4e8b5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e8b5-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e8b5-112">httpListener</span><span class="sxs-lookup"><span data-stu-id="4e8b5-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="4e8b5-113">Sınıf tarafından kullanılan parametreleri özelleştirir <xref:System.Net.HttpListener> .</span><span class="sxs-lookup"><span data-stu-id="4e8b5-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="4e8b5-114">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="4e8b5-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="4e8b5-115">Web isteği parametrelerini özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="4e8b5-116">IPv6</span><span class="sxs-lookup"><span data-stu-id="4e8b5-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="4e8b5-117">Internet Protokolü sürüm 6 (IPv6) desteğini sunar.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="4e8b5-118">\<performanceCounter>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="4e8b5-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="4e8b5-119">Ağ performans sayaçlarını etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="4e8b5-120">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="4e8b5-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="4e8b5-121">Ağ kaynaklarına bağlantıları yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="4e8b5-122">yuvasının</span><span class="sxs-lookup"><span data-stu-id="4e8b5-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="4e8b5-123">Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="4e8b5-124">\<webProxyScript>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="4e8b5-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="4e8b5-125">Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4e8b5-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e8b5-126">Parent Elements</span></span>  
  
|<span data-ttu-id="4e8b5-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="4e8b5-127">Element</span></span>|<span data-ttu-id="4e8b5-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e8b5-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e8b5-129">system.net</span><span class="sxs-lookup"><span data-stu-id="4e8b5-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="4e8b5-130">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e8b5-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e8b5-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4e8b5-132">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4e8b5-132">Configuration Files</span></span>  
 <span data-ttu-id="4e8b5-133">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e8b5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e8b5-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="4e8b5-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4e8b5-135">Network Settings Schema</span></span>](index.md)
