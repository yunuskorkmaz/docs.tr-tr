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
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155083"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="e6228-102">\<bypasslist (Ağ Ayarları) için> Öğesi ekle</span><span class="sxs-lookup"><span data-stu-id="e6228-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="e6228-103">Proxy bypass listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="e6228-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[<span data-ttu-id="e6228-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="e6228-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e6228-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e6228-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="e6228-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e6228-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="e6228-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e6228-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="e6228-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="e6228-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6228-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6228-109">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6228-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6228-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e6228-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6228-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6228-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6228-112">Attributes</span></span>  
  
|<span data-ttu-id="e6228-113">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="e6228-113">**Attribute**</span></span>|<span data-ttu-id="e6228-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e6228-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="e6228-115">**Adres**</span><span class="sxs-lookup"><span data-stu-id="e6228-115">**address**</span></span>|<span data-ttu-id="e6228-116">BIR IP adresi veya DNS adını açıklayan normal bir ifade.</span><span class="sxs-lookup"><span data-stu-id="e6228-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6228-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6228-117">Child Elements</span></span>  
 <span data-ttu-id="e6228-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e6228-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6228-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6228-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e6228-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="e6228-120">**Element**</span></span>|<span data-ttu-id="e6228-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e6228-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e6228-122">Bypasslist</span><span class="sxs-lookup"><span data-stu-id="e6228-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="e6228-123">Proxy kullanmayan adresleri açıklayan bir dizi düzenli ifade sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6228-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6228-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6228-124">Remarks</span></span>  
 <span data-ttu-id="e6228-125">Öğe, `add` ip adreslerini veya DNS sunucu adlarını açıklayan düzenli ifadeler ekler ve proxy sunucusunu atlayan adresler listesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="e6228-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="e6228-126">Öznitelik değeri `address` IP adresleri veya ana bilgisayar adları kümesi açıklayan normal bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6228-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="e6228-127">Bu öğe için düzenli bir ifade belirtirken dikkatli olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="e6228-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="e6228-128">Normal ifade "[a-z]+\\.contoso\\.com" contoso.com etki alanında herhangi bir ana bilgisayar eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanında herhangi bir ana bilgisayar eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e6228-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="e6228-129">Yalnızca contoso.com etki alanında bir ana bilgisayarla eşleştirmek için bir bağlantı ("$"): "[a-z]+\\.contoso\\.com$" kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6228-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="e6228-130">Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET Framework Düzenli İfadeler](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e6228-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e6228-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e6228-131">Configuration Files</span></span>  
 <span data-ttu-id="e6228-132">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6228-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6228-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6228-133">Example</span></span>  
 <span data-ttu-id="e6228-134">Aşağıdaki örnek, baypas listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="e6228-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="e6228-135">İlki, contoso.com etki alanında bulunan tüm sunucular için proxy'yi atlar; ikincisi, IP adresi 192.168 ile başlayan tüm sunucular için proxy'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="e6228-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6228-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6228-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e6228-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e6228-137">Network Settings Schema</span></span>](index.md)
