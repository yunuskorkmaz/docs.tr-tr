---
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
ms.openlocfilehash: 1db0ba3b0a213de1175e6e0cee347753d2a413b7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699608"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="69048-102">BypassList için > öğesi eklemek \<(ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="69048-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="69048-103">Proxy atlama listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="69048-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[<span data-ttu-id="69048-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="69048-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="69048-105">[ **System. net >\<** &nbsp;&nbsp;](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="69048-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="69048-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultproxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="69048-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="69048-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<BypassList >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="69048-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="69048-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**</span><span class="sxs-lookup"><span data-stu-id="69048-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69048-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69048-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69048-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="69048-110">Attributes and Elements</span></span>  
 <span data-ttu-id="69048-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="69048-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69048-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="69048-112">Attributes</span></span>  
  
|<span data-ttu-id="69048-113">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="69048-113">**Attribute**</span></span>|<span data-ttu-id="69048-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="69048-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="69048-115">**adrestir**</span><span class="sxs-lookup"><span data-stu-id="69048-115">**address**</span></span>|<span data-ttu-id="69048-116">IP adresini veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="69048-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69048-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="69048-117">Child Elements</span></span>  
 <span data-ttu-id="69048-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="69048-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69048-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="69048-119">Parent Elements</span></span>  
  
|<span data-ttu-id="69048-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="69048-120">**Element**</span></span>|<span data-ttu-id="69048-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="69048-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="69048-122">BypassList</span><span class="sxs-lookup"><span data-stu-id="69048-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="69048-123">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="69048-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69048-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69048-124">Remarks</span></span>  
 <span data-ttu-id="69048-125">`add` öğesi, bir proxy sunucusunu atlayan adresler listesine IP adreslerini veya DNS sunucu adlarını açıklayan normal ifadeler ekler.</span><span class="sxs-lookup"><span data-stu-id="69048-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="69048-126">`address` özniteliğinin değeri bir IP adresi veya ana bilgisayar adı kümesini açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69048-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="69048-127">Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="69048-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="69048-128">"[A-z] +\\. contoso\\. com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="69048-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="69048-129">Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için, bir tutturucu ("$"): "[a-z] +\\. contoso\\. com $" kullanın.</span><span class="sxs-lookup"><span data-stu-id="69048-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="69048-130">Normal ifadeler hakkında daha fazla bilgi için bkz. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="69048-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="69048-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="69048-131">Configuration Files</span></span>  
 <span data-ttu-id="69048-132">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="69048-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69048-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="69048-133">Example</span></span>  
 <span data-ttu-id="69048-134">Aşağıdaki örnek atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="69048-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="69048-135">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresi 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="69048-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69048-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69048-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="69048-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="69048-137">Network Settings Schema</span></span>](index.md)
