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
ms.openlocfilehash: c25477c2c99be66b34b07e1f7e50115bfa8d14e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154939"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="c1fd3-102">\<bypasslist (Ağ Ayarları) için açık> Öğesi</span><span class="sxs-lookup"><span data-stu-id="c1fd3-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="c1fd3-103">Proxy bypass listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-103">Clears the proxy bypass list.</span></span>  
  
<span data-ttu-id="c1fd3-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1fd3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c1fd3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c1fd3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="c1fd3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c1fd3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="c1fd3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c1fd3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>\
<span data-ttu-id="c1fd3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<açık>**</span><span class="sxs-lookup"><span data-stu-id="c1fd3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c1fd3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1fd3-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1fd3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1fd3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c1fd3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1fd3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1fd3-112">Attributes</span></span>  
 <span data-ttu-id="c1fd3-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c1fd3-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1fd3-114">Child Elements</span></span>  
 <span data-ttu-id="c1fd3-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1fd3-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1fd3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c1fd3-117">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="c1fd3-117">**Element**</span></span>|<span data-ttu-id="c1fd3-118">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c1fd3-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c1fd3-119">Bypasslist</span><span class="sxs-lookup"><span data-stu-id="c1fd3-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="c1fd3-120">Proxy kullanmayan adresleri açıklayan bir dizi düzenli ifade sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1fd3-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1fd3-121">Remarks</span></span>  
 <span data-ttu-id="c1fd3-122">Öğe, `clear` tüm girişleri baypas listesinden temizler.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c1fd3-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="c1fd3-123">Configuration Files</span></span>  
 <span data-ttu-id="c1fd3-124">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1fd3-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1fd3-125">Example</span></span>  
 <span data-ttu-id="c1fd3-126">Aşağıdaki örnek, baypas listesini temizler ve sonra bypass listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="c1fd3-127">İlki, contoso.com etki alanında bulunan tüm sunucular için proxy'yi atlar; ikincisi, IP adresi 192.168 ile başlayan tüm sunucular için proxy'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1fd3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1fd3-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="c1fd3-129">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c1fd3-129">Network Settings Schema</span></span>](index.md)
