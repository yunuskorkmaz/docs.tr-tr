---
title: '&lt;kaldırma&gt; bypasslist (ağ ayarları) için'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove elemment, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: c9db8cc2cf05987db97f28d7f97967f5bb52404e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625672"
---
# <a name="ltremovegt-element-for-bypasslist-network-settings"></a><span data-ttu-id="3b881-102">&lt;kaldırma&gt; bypasslist (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="3b881-102">&lt;remove&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="3b881-103">Bir IP adresi veya DNS adı proxy atlama listeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3b881-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>  
  
 <span data-ttu-id="3b881-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3b881-104">\<configuration></span></span>  
<span data-ttu-id="3b881-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3b881-105">\<system.net></span></span>  
<span data-ttu-id="3b881-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="3b881-106">\<defaultProxy></span></span>  
<span data-ttu-id="3b881-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="3b881-107">\<bypasslist></span></span>  
<span data-ttu-id="3b881-108">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="3b881-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b881-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b881-109">Syntax</span></span>  
  
```xml  
<remove   
  address="regular expression"   
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b881-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b881-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3b881-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b881-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b881-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b881-112">Attributes</span></span>  
  
|<span data-ttu-id="3b881-113">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="3b881-113">**Attribute**</span></span>|<span data-ttu-id="3b881-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3b881-114">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="3b881-115">Bir IP adresi veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="3b881-115">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b881-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b881-116">Child Elements</span></span>  
 <span data-ttu-id="3b881-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="3b881-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b881-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b881-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3b881-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="3b881-119">**Element**</span></span>|<span data-ttu-id="3b881-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3b881-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3b881-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="3b881-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="3b881-122">Bir proxy sunucu kullanmaması adresleri açıklayan normal bir ifade kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b881-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b881-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b881-123">Remarks</span></span>  
 <span data-ttu-id="3b881-124">`remove` Öğeyi normal ifadeler IP adresi veya DNS sunucu adları bir ara sunucu atlama adresleri listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3b881-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="3b881-125">Adresler, yapılandırma dosyasında ya da daha yüksek bir düzeyde yapılandırma hiyerarşideki daha önce tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="3b881-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="3b881-126">Değeri `address` öznitelik, bir dizi IP adresi veya ana bilgisayar adları açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b881-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="3b881-127">Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET framework normal ifadelerinde](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3b881-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3b881-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="3b881-128">Configuration Files</span></span>  
 <span data-ttu-id="3b881-129">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b881-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b881-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b881-130">Example</span></span>  
 <span data-ttu-id="3b881-131">Aşağıdaki örnek, adventure works.com'u etki alanı için herhangi bir önceki tanım kaldırır ve sonra contoso.com etki alanına atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="3b881-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b881-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b881-132">See also</span></span>
- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="3b881-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3b881-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
