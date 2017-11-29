---
title: "&lt;kaldırma&gt; öğesi olarak ayarlanıyor (ağ ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove elemment, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a87632ec9725aa24d085ca6c1bf1e54545b324fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-bypasslist-network-settings"></a><span data-ttu-id="c245e-102">&lt;kaldırma&gt; öğesi olarak ayarlanıyor (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="c245e-102">&lt;remove&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="c245e-103">Bir IP adresi veya DNS adı proxy atlama listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c245e-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>  
  
 <span data-ttu-id="c245e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c245e-104">\<configuration></span></span>  
<span data-ttu-id="c245e-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="c245e-105">\<system.net></span></span>  
<span data-ttu-id="c245e-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="c245e-106">\<defaultProxy></span></span>  
<span data-ttu-id="c245e-107">\<olarak ayarlanıyor ></span><span class="sxs-lookup"><span data-stu-id="c245e-107">\<bypasslist></span></span>  
<span data-ttu-id="c245e-108">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="c245e-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c245e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c245e-109">Syntax</span></span>  
  
```xml  
<remove   
  address="regular expression"   
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c245e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c245e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c245e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c245e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c245e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c245e-112">Attributes</span></span>  
  
|<span data-ttu-id="c245e-113">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="c245e-113">**Attribute**</span></span>|<span data-ttu-id="c245e-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c245e-114">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="c245e-115">Bir IP adresi veya DNS adı açıklayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="c245e-115">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c245e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c245e-116">Child Elements</span></span>  
 <span data-ttu-id="c245e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="c245e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c245e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c245e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c245e-119">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="c245e-119">**Element**</span></span>|<span data-ttu-id="c245e-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c245e-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c245e-121">olarak ayarlanıyor</span><span class="sxs-lookup"><span data-stu-id="c245e-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="c245e-122">Bir proxy kullanmayın adresleri açıklamak normal bir ifade kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c245e-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c245e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c245e-123">Remarks</span></span>  
 <span data-ttu-id="c245e-124">`remove` IP adreslerini veya DNS sunucu adları bir proxy sunucuyu atla adresleri listesinden açıklayan normal ifadeler öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c245e-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="c245e-125">Adresleri yapılandırma dosyası veya yapılandırma hiyerarşisindeki daha yüksek düzeyde önceden tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c245e-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="c245e-126">Değeri `address` özniteliği, bir IP adresi veya ana bilgisayar adlarını açıklar normal bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c245e-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="c245e-127">Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET framework normal ifadeleri](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c245e-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c245e-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="c245e-128">Configuration Files</span></span>  
 <span data-ttu-id="c245e-129">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c245e-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c245e-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="c245e-130">Example</span></span>  
 <span data-ttu-id="c245e-131">Aşağıdaki örnek adventure-works.com'u etki alanı için herhangi bir önceki tanımının kaldırır ve sonra contoso.com etki alanına atlama listesi ekler.</span><span class="sxs-lookup"><span data-stu-id="c245e-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove address="[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c245e-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c245e-132">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="c245e-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c245e-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
