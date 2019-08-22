---
title: <bypasslist> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 10d2a025096579c6bed64f82cc955deb0542717c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664197"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="fd99d-102">\<BypassList > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="fd99d-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="fd99d-103">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd99d-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="fd99d-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="fd99d-104">\<configuration></span></span>  
<span data-ttu-id="fd99d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fd99d-105">\<system.net></span></span>  
<span data-ttu-id="fd99d-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="fd99d-106">\<defaultProxy></span></span>  
<span data-ttu-id="fd99d-107">\<BypassList ></span><span class="sxs-lookup"><span data-stu-id="fd99d-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd99d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd99d-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd99d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd99d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fd99d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd99d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd99d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd99d-111">Attributes</span></span>  
 <span data-ttu-id="fd99d-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd99d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fd99d-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd99d-113">Child Elements</span></span>  
  
|<span data-ttu-id="fd99d-114">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="fd99d-114">**Element**</span></span>|<span data-ttu-id="fd99d-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fd99d-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fd99d-116">add</span><span class="sxs-lookup"><span data-stu-id="fd99d-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="fd99d-117">Proxy atlama listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="fd99d-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="fd99d-118">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="fd99d-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="fd99d-119">Atlama listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="fd99d-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="fd99d-120">remove</span><span class="sxs-lookup"><span data-stu-id="fd99d-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="fd99d-121">Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fd99d-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd99d-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd99d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fd99d-123">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="fd99d-123">**Element**</span></span>|<span data-ttu-id="fd99d-124">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fd99d-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fd99d-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="fd99d-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="fd99d-126">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fd99d-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd99d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd99d-127">Remarks</span></span>  
 <span data-ttu-id="fd99d-128">Atlama listesi, proxy sunucu aracılığıyla değil, doğrudan erişim <xref:System.Net.WebRequest> sağlayan URI 'leri tanımlayan normal ifadeler içerir.</span><span class="sxs-lookup"><span data-stu-id="fd99d-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="fd99d-129">Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd99d-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="fd99d-130">"[A-z] +\\. contoso\\. com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="fd99d-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="fd99d-131">Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için bir tutturucu ("$"): "[a-z] +\\. contoso\\. com $" kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd99d-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="fd99d-132">Normal ifadeler hakkında daha fazla bilgi için bkz. [Normal ifadeleri .NET Framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fd99d-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fd99d-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="fd99d-133">Configuration Files</span></span>  
 <span data-ttu-id="fd99d-134">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd99d-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd99d-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd99d-135">Example</span></span>  
 <span data-ttu-id="fd99d-136">Aşağıdaki örnek atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="fd99d-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="fd99d-137">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresleri 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="fd99d-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd99d-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd99d-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="fd99d-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fd99d-139">Network Settings Schema</span></span>](index.md)
