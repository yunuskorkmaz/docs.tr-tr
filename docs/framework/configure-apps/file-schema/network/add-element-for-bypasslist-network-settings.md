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
ms.openlocfilehash: da234402c6ec7e2c1f85e4bd674517b1147f0d18
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927491"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="b698a-102">\<BypassList için > öğesi Ekle (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b698a-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="b698a-103">Proxy atlama listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="b698a-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="b698a-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="b698a-104">\<configuration></span></span>  
<span data-ttu-id="b698a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b698a-105">\<system.net></span></span>  
<span data-ttu-id="b698a-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="b698a-106">\<defaultProxy></span></span>  
<span data-ttu-id="b698a-107">\<BypassList ></span><span class="sxs-lookup"><span data-stu-id="b698a-107">\<bypasslist></span></span>  
<span data-ttu-id="b698a-108">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="b698a-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b698a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b698a-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b698a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b698a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b698a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b698a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b698a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b698a-112">Attributes</span></span>  
  
|<span data-ttu-id="b698a-113">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="b698a-113">**Attribute**</span></span>|<span data-ttu-id="b698a-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b698a-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="b698a-115">**adrestir**</span><span class="sxs-lookup"><span data-stu-id="b698a-115">**address**</span></span>|<span data-ttu-id="b698a-116">IP adresini veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="b698a-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b698a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b698a-117">Child Elements</span></span>  
 <span data-ttu-id="b698a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="b698a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b698a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b698a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b698a-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="b698a-120">**Element**</span></span>|<span data-ttu-id="b698a-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b698a-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b698a-122">BypassList</span><span class="sxs-lookup"><span data-stu-id="b698a-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="b698a-123">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b698a-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b698a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b698a-124">Remarks</span></span>  
 <span data-ttu-id="b698a-125">Öğesi `add` , IP adreslerini veya DNS sunucu adlarını bir proxy sunucusunu atlayan adresler listesine açıklayan normal ifadeler ekler.</span><span class="sxs-lookup"><span data-stu-id="b698a-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="b698a-126">`address` Özniteliğin değeri bir IP adresi veya ana bilgisayar adı kümesini açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b698a-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="b698a-127">Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b698a-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="b698a-128">"[A-z] +\\. contoso\\. com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="b698a-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="b698a-129">Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için bir tutturucu ("$"): "[a-z] +\\. contoso\\. com $" kullanın.</span><span class="sxs-lookup"><span data-stu-id="b698a-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="b698a-130">Normal ifadeler hakkında daha fazla bilgi için bkz. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b698a-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b698a-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="b698a-131">Configuration Files</span></span>  
 <span data-ttu-id="b698a-132">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b698a-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b698a-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="b698a-133">Example</span></span>  
 <span data-ttu-id="b698a-134">Aşağıdaki örnek atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="b698a-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="b698a-135">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresi 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="b698a-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b698a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b698a-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="b698a-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b698a-137">Network Settings Schema</span></span>](index.md)
