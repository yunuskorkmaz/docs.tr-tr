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
ms.openlocfilehash: e5305d9aed09b6c4d1ad4201e5e08e007a14c7c0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664193"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="cfddb-102">\<BypassList için > öğesini temizle (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="cfddb-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="cfddb-103">Proxy atlama listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="cfddb-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="cfddb-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="cfddb-104">\<configuration></span></span>  
<span data-ttu-id="cfddb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cfddb-105">\<system.net></span></span>  
<span data-ttu-id="cfddb-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="cfddb-106">\<defaultProxy></span></span>  
<span data-ttu-id="cfddb-107">\<BypassList ></span><span class="sxs-lookup"><span data-stu-id="cfddb-107">\<bypasslist></span></span>  
<span data-ttu-id="cfddb-108">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="cfddb-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfddb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfddb-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfddb-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfddb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cfddb-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cfddb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfddb-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cfddb-112">Attributes</span></span>  
 <span data-ttu-id="cfddb-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="cfddb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cfddb-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfddb-114">Child Elements</span></span>  
 <span data-ttu-id="cfddb-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="cfddb-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cfddb-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfddb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cfddb-117">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="cfddb-117">**Element**</span></span>|<span data-ttu-id="cfddb-118">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="cfddb-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cfddb-119">BypassList</span><span class="sxs-lookup"><span data-stu-id="cfddb-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="cfddb-120">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfddb-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfddb-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfddb-121">Remarks</span></span>  
 <span data-ttu-id="cfddb-122">`clear` Öğesi atlama listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="cfddb-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cfddb-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="cfddb-123">Configuration Files</span></span>  
 <span data-ttu-id="cfddb-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cfddb-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfddb-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="cfddb-125">Example</span></span>  
 <span data-ttu-id="cfddb-126">Aşağıdaki örnek atlama listesini temizler ve atlama listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="cfddb-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="cfddb-127">İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresi 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="cfddb-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cfddb-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfddb-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="cfddb-129">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cfddb-129">Network Settings Schema</span></span>](index.md)
