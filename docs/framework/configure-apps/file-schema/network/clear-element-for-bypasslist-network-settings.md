---
title: '&lt;Temizle&gt; bypasslist (ağ ayarları) için'
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
ms.openlocfilehash: 840833f2752115cb5f5639a25daf05bcbff3d452
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720921"
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="8d63c-102">&lt;Temizle&gt; bypasslist (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="8d63c-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="8d63c-103">Proxy atlama listesi temizler.</span><span class="sxs-lookup"><span data-stu-id="8d63c-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="8d63c-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8d63c-104">\<configuration></span></span>  
<span data-ttu-id="8d63c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8d63c-105">\<system.net></span></span>  
<span data-ttu-id="8d63c-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="8d63c-106">\<defaultProxy></span></span>  
<span data-ttu-id="8d63c-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="8d63c-107">\<bypasslist></span></span>  
<span data-ttu-id="8d63c-108">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="8d63c-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d63c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d63c-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d63c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d63c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8d63c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d63c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d63c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8d63c-112">Attributes</span></span>  
 <span data-ttu-id="8d63c-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="8d63c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d63c-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d63c-114">Child Elements</span></span>  
 <span data-ttu-id="8d63c-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="8d63c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d63c-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d63c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8d63c-117">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="8d63c-117">**Element**</span></span>|<span data-ttu-id="8d63c-118">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8d63c-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8d63c-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="8d63c-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="8d63c-120">Bir proxy sunucu kullanmaması adresleri açıklayan normal bir ifade kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d63c-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d63c-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d63c-121">Remarks</span></span>  
 <span data-ttu-id="8d63c-122">`clear` Öğesi atlama listesindeki tüm girişleri siler.</span><span class="sxs-lookup"><span data-stu-id="8d63c-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8d63c-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="8d63c-123">Configuration Files</span></span>  
 <span data-ttu-id="8d63c-124">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d63c-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d63c-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d63c-125">Example</span></span>  
 <span data-ttu-id="8d63c-126">Aşağıdaki örnek, atlama listesi temizler ve ardından iki adres atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="8d63c-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="8d63c-127">İlk contoso.com etki alanındaki tüm sunucular için proxy atlar; İkinci proxy 192.168 tüm sunucularıyla başlar, IP adresi için atlar.</span><span class="sxs-lookup"><span data-stu-id="8d63c-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d63c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d63c-128">See also</span></span>
- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="8d63c-129">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8d63c-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
