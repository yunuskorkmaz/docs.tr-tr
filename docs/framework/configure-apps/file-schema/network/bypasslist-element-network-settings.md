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
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154952"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="d5aeb-102">\<bypasslist> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="d5aeb-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="d5aeb-103">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="d5aeb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5aeb-104">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5aeb-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5aeb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d5aeb-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5aeb-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d5aeb-107">Attributes</span></span>  
 <span data-ttu-id="d5aeb-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d5aeb-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5aeb-109">Child Elements</span></span>  
  
|<span data-ttu-id="d5aeb-110">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="d5aeb-110">**Element**</span></span>|<span data-ttu-id="d5aeb-111">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d5aeb-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d5aeb-112">add</span><span class="sxs-lookup"><span data-stu-id="d5aeb-112">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="d5aeb-113">Proxy atlama listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-113">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="d5aeb-114">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="d5aeb-114">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="d5aeb-115">Atlama listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-115">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="d5aeb-116">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="d5aeb-116">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="d5aeb-117">Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-117">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d5aeb-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5aeb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d5aeb-119">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="d5aeb-119">**Element**</span></span>|<span data-ttu-id="d5aeb-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d5aeb-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d5aeb-121">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="d5aeb-121">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="d5aeb-122">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-122">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5aeb-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5aeb-123">Remarks</span></span>  
 <span data-ttu-id="d5aeb-124">Atlama listesi, <xref:System.Net.WebRequest> proxy sunucu aracılığıyla değil, doğrudan erişim sağlayan URI 'leri tanımlayan normal ifadeler içerir.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-124">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="d5aeb-125">Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-125">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="d5aeb-126">"[A-z] + \\ . contoso \\ . com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-126">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="d5aeb-127">Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için bir tutturucu ("$"): "[a-z] + \\ . contoso \\ . com $" kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-127">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="d5aeb-128">Normal ifadeler hakkında daha fazla bilgi için bkz.. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d5aeb-128">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d5aeb-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d5aeb-129">Configuration Files</span></span>  
 <span data-ttu-id="d5aeb-130">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5aeb-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5aeb-131">Example</span></span>  
 <span data-ttu-id="d5aeb-132">Aşağıdaki örnek atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-132">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="d5aeb-133">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresleri 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-133">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5aeb-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5aeb-134">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="d5aeb-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d5aeb-135">Network Settings Schema</span></span>](index.md)
