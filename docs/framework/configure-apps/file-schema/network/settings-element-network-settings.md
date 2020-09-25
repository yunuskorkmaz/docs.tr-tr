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
ms.openlocfilehash: c5fe0b9eccd1c429c0041fcfab06b0cc20a20aa2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167281"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="0bf34-102">\<settings> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="0bf34-102">\<settings> Element (Network Settings)</span></span>

<span data-ttu-id="0bf34-103">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0bf34-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="0bf34-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0bf34-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bf34-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bf34-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0bf34-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bf34-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bf34-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0bf34-107">Attributes</span></span>  

 <span data-ttu-id="0bf34-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="0bf34-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0bf34-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bf34-109">Child Elements</span></span>  
  
|<span data-ttu-id="0bf34-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="0bf34-110">Element</span></span>|<span data-ttu-id="0bf34-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bf34-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bf34-112">httpListener</span><span class="sxs-lookup"><span data-stu-id="0bf34-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="0bf34-113">Sınıf tarafından kullanılan parametreleri özelleştirir <xref:System.Net.HttpListener> .</span><span class="sxs-lookup"><span data-stu-id="0bf34-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="0bf34-114">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="0bf34-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="0bf34-115">Web isteği parametrelerini özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="0bf34-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="0bf34-116">IPv6</span><span class="sxs-lookup"><span data-stu-id="0bf34-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="0bf34-117">Internet Protokolü sürüm 6 (IPv6) desteğini sunar.</span><span class="sxs-lookup"><span data-stu-id="0bf34-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="0bf34-118">\<performanceCounter> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="0bf34-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="0bf34-119">Ağ performans sayaçlarını etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0bf34-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="0bf34-120">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="0bf34-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="0bf34-121">Ağ kaynaklarına bağlantıları yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0bf34-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="0bf34-122">yuvasının</span><span class="sxs-lookup"><span data-stu-id="0bf34-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="0bf34-123">Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bf34-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="0bf34-124">\<webProxyScript> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="0bf34-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="0bf34-125">Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0bf34-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0bf34-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bf34-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0bf34-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="0bf34-127">Element</span></span>|<span data-ttu-id="0bf34-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bf34-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bf34-129">system.net</span><span class="sxs-lookup"><span data-stu-id="0bf34-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="0bf34-130">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="0bf34-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bf34-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0bf34-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0bf34-132">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="0bf34-132">Configuration Files</span></span>  

 <span data-ttu-id="0bf34-133">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0bf34-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf34-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bf34-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="0bf34-135">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="0bf34-135">Network Settings Schema</span></span>](index.md)
