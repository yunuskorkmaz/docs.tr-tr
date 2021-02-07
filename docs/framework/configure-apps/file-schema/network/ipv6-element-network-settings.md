---
description: 'Daha fazla bilgi edinin: <ipv6> öğesi (ağ ayarları)'
title: <ipv6> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: 667acaebdb290140f67ea36020bb191cd1a44f34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698654"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="e1b41-103">\<ipv6> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="e1b41-103">\<ipv6> Element (Network Settings)</span></span>

<span data-ttu-id="e1b41-104">, Sınıfın eski üyelerinden Internet Protokolü sürüm 6 (IPv6) yanıtlarını mümkün bir şekilde sunar <xref:System.Net.Dns> .</span><span class="sxs-lookup"><span data-stu-id="e1b41-104">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**

## <a name="syntax"></a><span data-ttu-id="e1b41-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e1b41-105">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1b41-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1b41-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e1b41-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1b41-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1b41-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e1b41-108">Attributes</span></span>  
  
|<span data-ttu-id="e1b41-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="e1b41-109">**Attribute**</span></span>|<span data-ttu-id="e1b41-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e1b41-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="e1b41-111"><xref:System.Net.Dns>Sınıfın üyelerinin Internet Protokolü sürüm 6 (IPv6) adresleri döndürmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e1b41-111">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="e1b41-112">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e1b41-112">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1b41-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1b41-113">Child Elements</span></span>  

 <span data-ttu-id="e1b41-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e1b41-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1b41-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1b41-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e1b41-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="e1b41-116">**Element**</span></span>|<span data-ttu-id="e1b41-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e1b41-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e1b41-118">ayarlar</span><span class="sxs-lookup"><span data-stu-id="e1b41-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="e1b41-119">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="e1b41-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1b41-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1b41-120">Remarks</span></span>  

 <span data-ttu-id="e1b41-121">Bu ayar, sınıfının kullanılmayan üyeleri için IPv6 desteği sunar <xref:System.Net.Dns> : <xref:System.Net.Dns.BeginGetHostByName%2A> ,,, <xref:System.Net.Dns.BeginResolve%2A> <xref:System.Net.Dns.EndGetHostByName%2A> ,, <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.GetHostByName%2A> ve <xref:System.Net.Dns.Resolve%2A> .</span><span class="sxs-lookup"><span data-stu-id="e1b41-121">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="e1b41-122">Ad alanının diğer üyeleri için <xref:System.Net?displayProperty=nameWithType> , IPv6 adresleri işletim sisteminde IPv6 etkinse döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="e1b41-122">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e1b41-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e1b41-123">Configuration Files</span></span>  

 <span data-ttu-id="e1b41-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1b41-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1b41-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1b41-125">Example</span></span>  

 <span data-ttu-id="e1b41-126">Aşağıdaki örnekte, sınıfı için IPv6 desteğinin nasıl etkinleştirileceği gösterilmektedir <xref:System.Net.Dns> .</span><span class="sxs-lookup"><span data-stu-id="e1b41-126">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1b41-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1b41-127">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e1b41-128">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e1b41-128">Network Settings Schema</span></span>](index.md)
