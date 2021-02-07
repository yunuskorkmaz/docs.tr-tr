---
description: 'Hakkında daha fazla bilgi edinin: <clear> BypassList için öğesi (ağ ayarları)'
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
ms.openlocfilehash: 4ddb66c837c55391a19826c44c6df7a3e88c8e0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729907"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="51635-103">bypasslist için \<clear> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="51635-103">\<clear> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="51635-104">Proxy atlama listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="51635-104">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="51635-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="51635-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51635-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="51635-106">Attributes and Elements</span></span>  

 <span data-ttu-id="51635-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="51635-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51635-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="51635-108">Attributes</span></span>  

 <span data-ttu-id="51635-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="51635-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="51635-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="51635-110">Child Elements</span></span>  

 <span data-ttu-id="51635-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="51635-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51635-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="51635-112">Parent Elements</span></span>  
  
|<span data-ttu-id="51635-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="51635-113">**Element**</span></span>|<span data-ttu-id="51635-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="51635-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="51635-115">BypassList</span><span class="sxs-lookup"><span data-stu-id="51635-115">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="51635-116">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="51635-116">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51635-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51635-117">Remarks</span></span>  

 <span data-ttu-id="51635-118">`clear`Öğesi atlama listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="51635-118">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="51635-119">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="51635-119">Configuration Files</span></span>  

 <span data-ttu-id="51635-120">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51635-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51635-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="51635-121">Example</span></span>  

 <span data-ttu-id="51635-122">Aşağıdaki örnek atlama listesini temizler ve atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="51635-122">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="51635-123">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresi 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="51635-123">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51635-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51635-124">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="51635-125">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="51635-125">Network Settings Schema</span></span>](index.md)
