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
ms.openlocfilehash: 12797e2f06d03aacd81700eae57d5776c1a6f354
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663989"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="cfb48-102">\<Settings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="cfb48-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="cfb48-103"><xref:System.Net?displayProperty=nameWithType> Ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="cfb48-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="cfb48-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="cfb48-104">\<configuration></span></span>  
<span data-ttu-id="cfb48-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cfb48-105">\<system.net></span></span>  
<span data-ttu-id="cfb48-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="cfb48-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb48-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfb48-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfb48-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfb48-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cfb48-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cfb48-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfb48-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cfb48-110">Attributes</span></span>  
 <span data-ttu-id="cfb48-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="cfb48-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cfb48-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfb48-112">Child Elements</span></span>  
  
|<span data-ttu-id="cfb48-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="cfb48-113">Element</span></span>|<span data-ttu-id="cfb48-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfb48-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfb48-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="cfb48-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="cfb48-116"><xref:System.Net.HttpListener> Sınıf tarafından kullanılan parametreleri özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="cfb48-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="cfb48-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="cfb48-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="cfb48-118">Web isteği parametrelerini özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="cfb48-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="cfb48-119">IPv6</span><span class="sxs-lookup"><span data-stu-id="cfb48-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="cfb48-120">Internet Protokolü sürüm 6 (IPv6) desteğini sunar.</span><span class="sxs-lookup"><span data-stu-id="cfb48-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="cfb48-121">\<performanceCounter > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="cfb48-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="cfb48-122">Ağ performans sayaçlarını etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cfb48-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="cfb48-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="cfb48-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="cfb48-124">Ağ kaynaklarına bağlantıları yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="cfb48-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="cfb48-125">yuvasının</span><span class="sxs-lookup"><span data-stu-id="cfb48-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="cfb48-126">Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cfb48-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="cfb48-127">\<webProxyScript > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="cfb48-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="cfb48-128">Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="cfb48-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cfb48-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfb48-129">Parent Elements</span></span>  
  
|<span data-ttu-id="cfb48-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="cfb48-130">Element</span></span>|<span data-ttu-id="cfb48-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfb48-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfb48-132">system.net</span><span class="sxs-lookup"><span data-stu-id="cfb48-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="cfb48-133">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="cfb48-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfb48-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfb48-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cfb48-135">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="cfb48-135">Configuration Files</span></span>  
 <span data-ttu-id="cfb48-136">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cfb48-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb48-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfb48-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="cfb48-138">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cfb48-138">Network Settings Schema</span></span>](index.md)
