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
ms.openlocfilehash: 839907d9339d459070fff12dbca22d3c2df5b020
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260625"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="d37f7-102">\<Ayarlar > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d37f7-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="d37f7-103">Temel ağ seçeneklerini yapılandırır <xref:System.Net?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d37f7-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="d37f7-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d37f7-104">\<configuration></span></span>  
<span data-ttu-id="d37f7-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d37f7-105">\<system.net></span></span>  
<span data-ttu-id="d37f7-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="d37f7-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d37f7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d37f7-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d37f7-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d37f7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d37f7-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d37f7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d37f7-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d37f7-110">Attributes</span></span>  
 <span data-ttu-id="d37f7-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d37f7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d37f7-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d37f7-112">Child Elements</span></span>  
  
|<span data-ttu-id="d37f7-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d37f7-113">Element</span></span>|<span data-ttu-id="d37f7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d37f7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d37f7-115">HttpListener</span><span class="sxs-lookup"><span data-stu-id="d37f7-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="d37f7-116">Tarafından kullanılan parametreler özelleştirir <xref:System.Net.HttpListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d37f7-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="d37f7-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="d37f7-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="d37f7-118">Web isteği parametreleri özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="d37f7-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="d37f7-119">IPv6</span><span class="sxs-lookup"><span data-stu-id="d37f7-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="d37f7-120">Internet Protokolü sürüm 6 (IPv6) sağlayan destekler.</span><span class="sxs-lookup"><span data-stu-id="d37f7-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="d37f7-121">\<performanceCounter > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d37f7-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="d37f7-122">Ağ performans sayaçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d37f7-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="d37f7-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="d37f7-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="d37f7-124">Ağ kaynaklarına bağlantılarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d37f7-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="d37f7-125">Yuva</span><span class="sxs-lookup"><span data-stu-id="d37f7-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="d37f7-126">Yuva işlemleri tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d37f7-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="d37f7-127">\<webProxyScript > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d37f7-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="d37f7-128">Web proxy'leri bulmak için kullanılan komut dosyası özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d37f7-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d37f7-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d37f7-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d37f7-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="d37f7-130">Element</span></span>|<span data-ttu-id="d37f7-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d37f7-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d37f7-132">System.NET</span><span class="sxs-lookup"><span data-stu-id="d37f7-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="d37f7-133">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d37f7-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d37f7-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d37f7-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d37f7-135">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d37f7-135">Configuration Files</span></span>  
 <span data-ttu-id="d37f7-136">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d37f7-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37f7-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d37f7-137">See also</span></span>
- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="d37f7-138">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d37f7-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
