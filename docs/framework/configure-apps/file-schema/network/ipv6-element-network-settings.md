---
title: <ipv6> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: c16949171d082bd02abb0a02db83c2e71c2f17df
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088129"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="b6bb0-102">\<IPv6 > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b6bb0-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="b6bb0-103"><xref:System.Net.Dns> sınıfının kullanılmayan üyelerinden Internet Protokolü sürüm 6 (IPv6) yanıtlarını mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

<span data-ttu-id="b6bb0-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b6bb0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b6bb0-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="b6bb0-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="b6bb0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ayarları >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b6bb0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="b6bb0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ıpv6 >**</span><span class="sxs-lookup"><span data-stu-id="b6bb0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b6bb0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6bb0-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6bb0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6bb0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b6bb0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6bb0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b6bb0-111">Attributes</span></span>  
  
|<span data-ttu-id="b6bb0-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="b6bb0-112">**Attribute**</span></span>|<span data-ttu-id="b6bb0-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b6bb0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="b6bb0-114"><xref:System.Net.Dns> sınıfının üyelerinin Internet Protokolü sürüm 6 (IPv6) adreslerini döndürmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="b6bb0-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6bb0-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6bb0-116">Child Elements</span></span>  
 <span data-ttu-id="b6bb0-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6bb0-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6bb0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b6bb0-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="b6bb0-119">**Element**</span></span>|<span data-ttu-id="b6bb0-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b6bb0-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b6bb0-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="b6bb0-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b6bb0-122"><xref:System.Net> ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6bb0-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6bb0-123">Remarks</span></span>  
 <span data-ttu-id="b6bb0-124">Bu ayar <xref:System.Net.Dns> sınıfının kullanılmayan üyeleri için IPv6 desteği sunar: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>ve <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="b6bb0-125"><xref:System.Net?displayProperty=nameWithType> ad alanının diğer üyeleri için, IPv6 adresleri işletim sisteminde IPv6 etkinse döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b6bb0-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="b6bb0-126">Configuration Files</span></span>  
 <span data-ttu-id="b6bb0-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6bb0-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6bb0-128">Example</span></span>  
 <span data-ttu-id="b6bb0-129">Aşağıdaki örnek, <xref:System.Net.Dns> sınıfı için IPv6 desteğinin nasıl etkinleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6bb0-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6bb0-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b6bb0-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b6bb0-131">Network Settings Schema</span></span>](index.md)
