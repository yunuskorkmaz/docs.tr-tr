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
ms.openlocfilehash: 7499d15f1d57887ffc3e78b83ed686c0c0f46cf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203528"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="85c0e-102">\<Temizle > bypasslist (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="85c0e-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="85c0e-103">Proxy atlama listesi temizler.</span><span class="sxs-lookup"><span data-stu-id="85c0e-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="85c0e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="85c0e-104">\<configuration></span></span>  
<span data-ttu-id="85c0e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="85c0e-105">\<system.net></span></span>  
<span data-ttu-id="85c0e-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="85c0e-106">\<defaultProxy></span></span>  
<span data-ttu-id="85c0e-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="85c0e-107">\<bypasslist></span></span>  
<span data-ttu-id="85c0e-108">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="85c0e-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c0e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85c0e-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85c0e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="85c0e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="85c0e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85c0e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85c0e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85c0e-112">Attributes</span></span>  
 <span data-ttu-id="85c0e-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="85c0e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="85c0e-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="85c0e-114">Child Elements</span></span>  
 <span data-ttu-id="85c0e-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="85c0e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85c0e-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="85c0e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="85c0e-117">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="85c0e-117">**Element**</span></span>|<span data-ttu-id="85c0e-118">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="85c0e-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="85c0e-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="85c0e-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="85c0e-120">Bir proxy sunucu kullanmaması adresleri açıklayan normal bir ifade kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="85c0e-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85c0e-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85c0e-121">Remarks</span></span>  
 <span data-ttu-id="85c0e-122">`clear` Öğesi atlama listesindeki tüm girişleri siler.</span><span class="sxs-lookup"><span data-stu-id="85c0e-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="85c0e-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="85c0e-123">Configuration Files</span></span>  
 <span data-ttu-id="85c0e-124">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="85c0e-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85c0e-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="85c0e-125">Example</span></span>  
 <span data-ttu-id="85c0e-126">Aşağıdaki örnek, atlama listesi temizler ve ardından iki adres atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="85c0e-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="85c0e-127">İlk contoso.com etki alanındaki tüm sunucular için proxy atlar; İkinci proxy 192.168 tüm sunucularıyla başlar, IP adresi için atlar.</span><span class="sxs-lookup"><span data-stu-id="85c0e-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="85c0e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85c0e-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="85c0e-129">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="85c0e-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
