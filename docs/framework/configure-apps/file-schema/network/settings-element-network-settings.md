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
ms.openlocfilehash: ba08f630dc602c950da309bf29482d85b41af7ef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697692"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="b47fd-102">\<settings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b47fd-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="b47fd-103">@No__t-0 ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b47fd-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
[<span data-ttu-id="b47fd-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="b47fd-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b47fd-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b47fd-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="b47fd-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<settings >**</span><span class="sxs-lookup"><span data-stu-id="b47fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b47fd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b47fd-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b47fd-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b47fd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b47fd-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b47fd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b47fd-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b47fd-110">Attributes</span></span>  
 <span data-ttu-id="b47fd-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="b47fd-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b47fd-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b47fd-112">Child Elements</span></span>  
  
|<span data-ttu-id="b47fd-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="b47fd-113">Element</span></span>|<span data-ttu-id="b47fd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b47fd-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b47fd-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="b47fd-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="b47fd-116">@No__t-0 sınıfı tarafından kullanılan parametreleri özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="b47fd-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="b47fd-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="b47fd-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="b47fd-118">Web isteği parametrelerini özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="b47fd-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="b47fd-119">IPv6</span><span class="sxs-lookup"><span data-stu-id="b47fd-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="b47fd-120">Internet Protokolü sürüm 6 (IPv6) desteğini sunar.</span><span class="sxs-lookup"><span data-stu-id="b47fd-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="b47fd-121">\<performanceCounter > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b47fd-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="b47fd-122">Ağ performans sayaçlarını etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b47fd-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="b47fd-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="b47fd-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="b47fd-124">Ağ kaynaklarına bağlantıları yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b47fd-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="b47fd-125">yuvasının</span><span class="sxs-lookup"><span data-stu-id="b47fd-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="b47fd-126">Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b47fd-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="b47fd-127">\<webProxyScript > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b47fd-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="b47fd-128">Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b47fd-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b47fd-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b47fd-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b47fd-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="b47fd-130">Element</span></span>|<span data-ttu-id="b47fd-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b47fd-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b47fd-132">system.net</span><span class="sxs-lookup"><span data-stu-id="b47fd-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b47fd-133">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="b47fd-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b47fd-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b47fd-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b47fd-135">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="b47fd-135">Configuration Files</span></span>  
 <span data-ttu-id="b47fd-136">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b47fd-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b47fd-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b47fd-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="b47fd-138">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b47fd-138">Network Settings Schema</span></span>](index.md)
