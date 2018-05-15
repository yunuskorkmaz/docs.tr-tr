---
title: '&lt;Clear&gt; öğesi olarak ayarlanıyor (ağ ayarları) için'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9297b68a31117aabfa45328954ccb9c7cdac66c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="02228-102">&lt;Clear&gt; öğesi olarak ayarlanıyor (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="02228-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="02228-103">Proxy atlama listesi temizler.</span><span class="sxs-lookup"><span data-stu-id="02228-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="02228-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="02228-104">\<configuration></span></span>  
<span data-ttu-id="02228-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="02228-105">\<system.net></span></span>  
<span data-ttu-id="02228-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="02228-106">\<defaultProxy></span></span>  
<span data-ttu-id="02228-107">\<olarak ayarlanıyor ></span><span class="sxs-lookup"><span data-stu-id="02228-107">\<bypasslist></span></span>  
<span data-ttu-id="02228-108">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="02228-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02228-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02228-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02228-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="02228-110">Attributes and Elements</span></span>  
 <span data-ttu-id="02228-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02228-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02228-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02228-112">Attributes</span></span>  
 <span data-ttu-id="02228-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="02228-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02228-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="02228-114">Child Elements</span></span>  
 <span data-ttu-id="02228-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="02228-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02228-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="02228-116">Parent Elements</span></span>  
  
|<span data-ttu-id="02228-117">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="02228-117">**Element**</span></span>|<span data-ttu-id="02228-118">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="02228-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="02228-119">olarak ayarlanıyor</span><span class="sxs-lookup"><span data-stu-id="02228-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="02228-120">Bir proxy kullanmayın adresleri açıklamak normal bir ifade kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="02228-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02228-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02228-121">Remarks</span></span>  
 <span data-ttu-id="02228-122">`clear` Öğesi atlama listesindeki tüm girişleri siler.</span><span class="sxs-lookup"><span data-stu-id="02228-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="02228-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="02228-123">Configuration Files</span></span>  
 <span data-ttu-id="02228-124">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="02228-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02228-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="02228-125">Example</span></span>  
 <span data-ttu-id="02228-126">Aşağıdaki örnek atlama listesi temizler ve ardından iki adres atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="02228-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="02228-127">İlk contoso.com etki alanındaki tüm sunucular için proxy atlar; İkinci IP adresini başlar 192.168 olan tüm sunucular için proxy atlar.</span><span class="sxs-lookup"><span data-stu-id="02228-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02228-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02228-128">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="02228-129">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="02228-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
