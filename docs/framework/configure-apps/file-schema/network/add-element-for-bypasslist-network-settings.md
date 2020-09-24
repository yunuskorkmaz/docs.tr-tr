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
ms.openlocfilehash: 927a43f352fd776d9e6ba52ebea6ba2a1ccd4d48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149497"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="66459-102">bypasslist için \<add> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="66459-102">\<add> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="66459-103">Proxy atlama listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="66459-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="66459-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="66459-104">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66459-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="66459-105">Attributes and Elements</span></span>  

 <span data-ttu-id="66459-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66459-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66459-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="66459-107">Attributes</span></span>  
  
|<span data-ttu-id="66459-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="66459-108">**Attribute**</span></span>|<span data-ttu-id="66459-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="66459-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="66459-110">**adrestir**</span><span class="sxs-lookup"><span data-stu-id="66459-110">**address**</span></span>|<span data-ttu-id="66459-111">IP adresini veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="66459-111">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66459-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="66459-112">Child Elements</span></span>  

 <span data-ttu-id="66459-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="66459-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66459-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="66459-114">Parent Elements</span></span>  
  
|<span data-ttu-id="66459-115">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="66459-115">**Element**</span></span>|<span data-ttu-id="66459-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="66459-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="66459-117">BypassList</span><span class="sxs-lookup"><span data-stu-id="66459-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="66459-118">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="66459-118">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66459-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66459-119">Remarks</span></span>  

 <span data-ttu-id="66459-120">`add`Öğesi, IP adreslerini veya DNS sunucu adlarını bir proxy sunucusunu atlayan adresler listesine açıklayan normal ifadeler ekler.</span><span class="sxs-lookup"><span data-stu-id="66459-120">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="66459-121">`address`Özniteliğin değeri BIR IP adresi veya ana bilgisayar adı kümesini açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66459-121">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="66459-122">Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="66459-122">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="66459-123">"[A-z] + \\ . contoso \\ . com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="66459-123">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="66459-124">Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için bir tutturucu ("$"): "[a-z] + \\ . contoso \\ . com $" kullanın.</span><span class="sxs-lookup"><span data-stu-id="66459-124">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="66459-125">Normal ifadeler hakkında daha fazla bilgi için bkz.. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="66459-125">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="66459-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="66459-126">Configuration Files</span></span>  

 <span data-ttu-id="66459-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66459-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66459-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="66459-128">Example</span></span>  

 <span data-ttu-id="66459-129">Aşağıdaki örnek atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="66459-129">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="66459-130">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresi 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="66459-130">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66459-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66459-131">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="66459-132">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="66459-132">Network Settings Schema</span></span>](index.md)
