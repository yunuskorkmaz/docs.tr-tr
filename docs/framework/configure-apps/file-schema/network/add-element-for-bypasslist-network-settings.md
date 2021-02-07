---
description: 'Hakkında daha fazla bilgi edinin: <add> BypassList için öğesi (ağ ayarları)'
title: bypasslist için <add> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 6bbd42cdf5d3b9bc31326b619cde96cfac0c755a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698641"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="a714a-103">bypasslist için \<add> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="a714a-103">\<add> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="a714a-104">Proxy atlama listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="a714a-104">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="a714a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a714a-105">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a714a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a714a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a714a-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a714a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a714a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a714a-108">Attributes</span></span>  
  
|<span data-ttu-id="a714a-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="a714a-109">**Attribute**</span></span>|<span data-ttu-id="a714a-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a714a-110">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="a714a-111">**adrestir**</span><span class="sxs-lookup"><span data-stu-id="a714a-111">**address**</span></span>|<span data-ttu-id="a714a-112">IP adresini veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="a714a-112">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a714a-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a714a-113">Child Elements</span></span>  

 <span data-ttu-id="a714a-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="a714a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a714a-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a714a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a714a-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="a714a-116">**Element**</span></span>|<span data-ttu-id="a714a-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a714a-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a714a-118">BypassList</span><span class="sxs-lookup"><span data-stu-id="a714a-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="a714a-119">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a714a-119">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a714a-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a714a-120">Remarks</span></span>  

 <span data-ttu-id="a714a-121">`add`Öğesi, IP adreslerini veya DNS sunucu adlarını bir proxy sunucusunu atlayan adresler listesine açıklayan normal ifadeler ekler.</span><span class="sxs-lookup"><span data-stu-id="a714a-121">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="a714a-122">`address`Özniteliğin değeri BIR IP adresi veya ana bilgisayar adı kümesini açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a714a-122">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="a714a-123">Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a714a-123">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="a714a-124">"[A-z] + \\ . contoso \\ . com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="a714a-124">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="a714a-125">Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için bir tutturucu ("$"): "[a-z] + \\ . contoso \\ . com $" kullanın.</span><span class="sxs-lookup"><span data-stu-id="a714a-125">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="a714a-126">Normal ifadeler hakkında daha fazla bilgi için bkz.. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a714a-126">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a714a-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a714a-127">Configuration Files</span></span>  

 <span data-ttu-id="a714a-128">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a714a-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a714a-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a714a-129">Example</span></span>  

 <span data-ttu-id="a714a-130">Aşağıdaki örnek atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="a714a-130">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="a714a-131">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresi 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="a714a-131">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a714a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a714a-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a714a-133">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="a714a-133">Network Settings Schema</span></span>](index.md)
