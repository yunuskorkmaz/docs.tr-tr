---
title: bypasslist için <clear> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 4d078dac14103560423bfccdd4a1717031e7a60f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699506"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="cead5-102">BypassList için \<clear > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="cead5-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="cead5-103">Proxy atlama listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="cead5-103">Clears the proxy bypass list.</span></span>  
  
[<span data-ttu-id="cead5-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="cead5-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cead5-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cead5-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="cead5-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cead5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="cead5-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cead5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="cead5-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="cead5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cead5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cead5-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cead5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cead5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cead5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cead5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cead5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cead5-112">Attributes</span></span>  
 <span data-ttu-id="cead5-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="cead5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cead5-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cead5-114">Child Elements</span></span>  
 <span data-ttu-id="cead5-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="cead5-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cead5-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cead5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cead5-117">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="cead5-117">**Element**</span></span>|<span data-ttu-id="cead5-118">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="cead5-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cead5-119">BypassList</span><span class="sxs-lookup"><span data-stu-id="cead5-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="cead5-120">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cead5-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cead5-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cead5-121">Remarks</span></span>  
 <span data-ttu-id="cead5-122">@No__t-0 öğesi atlama listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="cead5-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cead5-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="cead5-123">Configuration Files</span></span>  
 <span data-ttu-id="cead5-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cead5-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cead5-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="cead5-125">Example</span></span>  
 <span data-ttu-id="cead5-126">Aşağıdaki örnek atlama listesini temizler ve atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="cead5-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="cead5-127">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresi 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="cead5-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="cead5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cead5-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="cead5-129">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cead5-129">Network Settings Schema</span></span>](index.md)
