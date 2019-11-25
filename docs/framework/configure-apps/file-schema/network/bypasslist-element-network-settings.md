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
ms.openlocfilehash: 7a6c1282c9ca8381d2dbb21ffdc82f95732c42b3
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087519"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="54ee2-102">\<BypassList > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="54ee2-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="54ee2-103">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="54ee2-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="54ee2-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="54ee2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="54ee2-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="54ee2-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="54ee2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="54ee2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="54ee2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<BypassList >**</span><span class="sxs-lookup"><span data-stu-id="54ee2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="54ee2-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54ee2-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54ee2-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="54ee2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="54ee2-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54ee2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54ee2-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="54ee2-111">Attributes</span></span>  
 <span data-ttu-id="54ee2-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="54ee2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54ee2-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="54ee2-113">Child Elements</span></span>  
  
|<span data-ttu-id="54ee2-114">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="54ee2-114">**Element**</span></span>|<span data-ttu-id="54ee2-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="54ee2-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="54ee2-116">add</span><span class="sxs-lookup"><span data-stu-id="54ee2-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="54ee2-117">Proxy atlama listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="54ee2-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="54ee2-118">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="54ee2-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="54ee2-119">Atlama listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="54ee2-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="54ee2-120">remove</span><span class="sxs-lookup"><span data-stu-id="54ee2-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="54ee2-121">Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="54ee2-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54ee2-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="54ee2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="54ee2-123">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="54ee2-123">**Element**</span></span>|<span data-ttu-id="54ee2-124">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="54ee2-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="54ee2-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="54ee2-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="54ee2-126">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="54ee2-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54ee2-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54ee2-127">Remarks</span></span>  
 <span data-ttu-id="54ee2-128">Atlama listesi, yalnızca proxy sunucu yerine, örneklere erişen <xref:System.Net.WebRequest> URI 'Leri tanımlayan normal ifadeler içerir.</span><span class="sxs-lookup"><span data-stu-id="54ee2-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="54ee2-129">Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="54ee2-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="54ee2-130">"[A-z] +\\. contoso\\. com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="54ee2-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="54ee2-131">Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için, bir tutturucu ("$"): "[a-z] +\\. contoso\\. com $" kullanın.</span><span class="sxs-lookup"><span data-stu-id="54ee2-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="54ee2-132">Normal ifadeler hakkında daha fazla bilgi için bkz. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="54ee2-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="54ee2-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="54ee2-133">Configuration Files</span></span>  
 <span data-ttu-id="54ee2-134">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54ee2-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54ee2-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="54ee2-135">Example</span></span>  
 <span data-ttu-id="54ee2-136">Aşağıdaki örnek atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="54ee2-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="54ee2-137">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresleri 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="54ee2-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54ee2-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54ee2-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="54ee2-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="54ee2-139">Network Settings Schema</span></span>](index.md)
