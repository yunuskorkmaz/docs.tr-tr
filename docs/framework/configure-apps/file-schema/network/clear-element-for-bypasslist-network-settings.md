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
ms.openlocfilehash: 96cef2dff3156e49a93be818230c83370dab5264
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185867"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="364ed-102">bypasslist için \<clear> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="364ed-102">\<clear> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="364ed-103">Proxy atlama listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="364ed-103">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="364ed-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="364ed-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="364ed-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="364ed-105">Attributes and Elements</span></span>  

 <span data-ttu-id="364ed-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="364ed-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="364ed-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="364ed-107">Attributes</span></span>  

 <span data-ttu-id="364ed-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="364ed-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="364ed-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="364ed-109">Child Elements</span></span>  

 <span data-ttu-id="364ed-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="364ed-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="364ed-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="364ed-111">Parent Elements</span></span>  
  
|<span data-ttu-id="364ed-112">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="364ed-112">**Element**</span></span>|<span data-ttu-id="364ed-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="364ed-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="364ed-114">BypassList</span><span class="sxs-lookup"><span data-stu-id="364ed-114">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="364ed-115">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="364ed-115">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="364ed-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="364ed-116">Remarks</span></span>  

 <span data-ttu-id="364ed-117">`clear`Öğesi atlama listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="364ed-117">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="364ed-118">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="364ed-118">Configuration Files</span></span>  

 <span data-ttu-id="364ed-119">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="364ed-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="364ed-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="364ed-120">Example</span></span>  

 <span data-ttu-id="364ed-121">Aşağıdaki örnek atlama listesini temizler ve atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="364ed-121">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="364ed-122">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresi 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="364ed-122">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="364ed-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="364ed-123">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="364ed-124">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="364ed-124">Network Settings Schema</span></span>](index.md)
