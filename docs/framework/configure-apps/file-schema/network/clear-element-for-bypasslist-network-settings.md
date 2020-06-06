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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154939"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="f4a72-102">bypasslist için \<clear> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="f4a72-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="f4a72-103">Proxy atlama listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="f4a72-103">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="f4a72-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4a72-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4a72-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4a72-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f4a72-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4a72-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4a72-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4a72-107">Attributes</span></span>  
 <span data-ttu-id="f4a72-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="f4a72-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4a72-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4a72-109">Child Elements</span></span>  
 <span data-ttu-id="f4a72-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="f4a72-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4a72-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4a72-111">Parent Elements</span></span>  
  
|<span data-ttu-id="f4a72-112">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="f4a72-112">**Element**</span></span>|<span data-ttu-id="f4a72-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f4a72-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f4a72-114">BypassList</span><span class="sxs-lookup"><span data-stu-id="f4a72-114">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="f4a72-115">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4a72-115">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4a72-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4a72-116">Remarks</span></span>  
 <span data-ttu-id="f4a72-117">`clear`Öğesi atlama listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="f4a72-117">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f4a72-118">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f4a72-118">Configuration Files</span></span>  
 <span data-ttu-id="f4a72-119">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4a72-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4a72-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4a72-120">Example</span></span>  
 <span data-ttu-id="f4a72-121">Aşağıdaki örnek atlama listesini temizler ve atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="f4a72-121">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="f4a72-122">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresi 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="f4a72-122">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4a72-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4a72-123">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f4a72-124">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f4a72-124">Network Settings Schema</span></span>](index.md)
