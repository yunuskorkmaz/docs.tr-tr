---
title: '&lt;ekleme&gt; öğesi olarak ayarlanıyor (ağ ayarları) için'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d786d4fd7e6663649408b36fb518db06063ef916
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a><span data-ttu-id="c5b21-102">&lt;ekleme&gt; öğesi olarak ayarlanıyor (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="c5b21-102">&lt;add&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="c5b21-103">Bir IP adresi veya DNS adı proxy atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="c5b21-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="c5b21-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c5b21-104">\<configuration></span></span>  
<span data-ttu-id="c5b21-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c5b21-105">\<system.net></span></span>  
<span data-ttu-id="c5b21-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="c5b21-106">\<defaultProxy></span></span>  
<span data-ttu-id="c5b21-107">\<olarak ayarlanıyor ></span><span class="sxs-lookup"><span data-stu-id="c5b21-107">\<bypasslist></span></span>  
<span data-ttu-id="c5b21-108">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="c5b21-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b21-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5b21-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5b21-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5b21-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c5b21-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5b21-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5b21-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5b21-112">Attributes</span></span>  
  
|<span data-ttu-id="c5b21-113">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="c5b21-113">**Attribute**</span></span>|<span data-ttu-id="c5b21-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c5b21-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="c5b21-115">**Adres**</span><span class="sxs-lookup"><span data-stu-id="c5b21-115">**address**</span></span>|<span data-ttu-id="c5b21-116">Bir IP adresi veya DNS adı açıklayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="c5b21-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5b21-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5b21-117">Child Elements</span></span>  
 <span data-ttu-id="c5b21-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5b21-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5b21-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5b21-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c5b21-120">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="c5b21-120">**Element**</span></span>|<span data-ttu-id="c5b21-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c5b21-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c5b21-122">olarak ayarlanıyor</span><span class="sxs-lookup"><span data-stu-id="c5b21-122">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="c5b21-123">Bir proxy kullanmayın adresleri açıklamak normal bir ifade kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5b21-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5b21-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5b21-124">Remarks</span></span>  
 <span data-ttu-id="c5b21-125">`add` Öğesi IP adreslerini veya DNS sunucu adları için proxy sunucuyu atla adresleri listesi açıklayan normal ifadeler ekler.</span><span class="sxs-lookup"><span data-stu-id="c5b21-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="c5b21-126">Değeri `address` özniteliği, bir IP adresi veya ana bilgisayar adlarını açıklar normal bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5b21-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="c5b21-127">Bu öğe için normal bir ifade belirtirken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5b21-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="c5b21-128">Normal ifade "[a-z] +\\.contoso\\.com" barındıran tüm contoso.com etki alanı, ancak bunu eşleşmeleri ayrıca contoso.com.cpandl.com etki alanındaki herhangi bir ana eşleşir.</span><span class="sxs-lookup"><span data-stu-id="c5b21-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="c5b21-129">Yalnızca bir ana bilgisayar contoso.com etki alanındaki eşleştirmek için bir yer işareti ("$") kullanın: "[a-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="c5b21-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="c5b21-130">Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET framework normal ifadeleri](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c5b21-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c5b21-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="c5b21-131">Configuration Files</span></span>  
 <span data-ttu-id="c5b21-132">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5b21-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5b21-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5b21-133">Example</span></span>  
 <span data-ttu-id="c5b21-134">Aşağıdaki örnekte iki adres atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="c5b21-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="c5b21-135">İlk contoso.com etki alanındaki tüm sunucular için proxy atlar; İkinci IP adresini başlar 192.168 olan tüm sunucular için proxy atlar.</span><span class="sxs-lookup"><span data-stu-id="c5b21-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5b21-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5b21-136">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="c5b21-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c5b21-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
