---
title: <bypasslist> Öğesi (Ağ Ayarları)
description: <bypasslist>Ağ ayarları öğesi, .NET Framework proxy kullanmayan adresleri tanımlayan bir dizi normal ifade sağlar.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 58cdcf046b2a5a292493c5704739b22aa4ec4f17
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178417"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="e67c1-103">\<bypasslist> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="e67c1-103">\<bypasslist> Element (Network Settings)</span></span>

<span data-ttu-id="e67c1-104">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e67c1-104">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="e67c1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e67c1-105">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e67c1-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e67c1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e67c1-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e67c1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e67c1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e67c1-108">Attributes</span></span>  

 <span data-ttu-id="e67c1-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="e67c1-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e67c1-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e67c1-110">Child Elements</span></span>  
  
|<span data-ttu-id="e67c1-111">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="e67c1-111">**Element**</span></span>|<span data-ttu-id="e67c1-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e67c1-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e67c1-113">add</span><span class="sxs-lookup"><span data-stu-id="e67c1-113">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="e67c1-114">Proxy atlama listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="e67c1-114">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="e67c1-115">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="e67c1-115">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="e67c1-116">Atlama listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="e67c1-116">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="e67c1-117">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="e67c1-117">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="e67c1-118">Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e67c1-118">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e67c1-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e67c1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e67c1-120">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="e67c1-120">**Element**</span></span>|<span data-ttu-id="e67c1-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e67c1-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e67c1-122">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="e67c1-122">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="e67c1-123">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e67c1-123">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e67c1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e67c1-124">Remarks</span></span>  

 <span data-ttu-id="e67c1-125">Atlama listesi, <xref:System.Net.WebRequest> proxy sunucu aracılığıyla değil, doğrudan erişim sağlayan URI 'leri tanımlayan normal ifadeler içerir.</span><span class="sxs-lookup"><span data-stu-id="e67c1-125">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="e67c1-126">Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e67c1-126">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="e67c1-127">"[A-z] + \\ . contoso \\ . com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e67c1-127">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="e67c1-128">Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için bir tutturucu ("$"): "[a-z] + \\ . contoso \\ . com $" kullanın.</span><span class="sxs-lookup"><span data-stu-id="e67c1-128">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="e67c1-129">Normal ifadeler hakkında daha fazla bilgi için bkz.. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e67c1-129">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e67c1-130">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e67c1-130">Configuration Files</span></span>  

 <span data-ttu-id="e67c1-131">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e67c1-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e67c1-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="e67c1-132">Example</span></span>  

 <span data-ttu-id="e67c1-133">Aşağıdaki örnek atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="e67c1-133">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="e67c1-134">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresleri 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="e67c1-134">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e67c1-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e67c1-135">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e67c1-136">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e67c1-136">Network Settings Schema</span></span>](index.md)
