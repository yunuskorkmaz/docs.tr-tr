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
ms.openlocfilehash: 44ef0b8e1b6dc6ad0efde6b26ad7d4700e06f2c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178339"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="6e515-102">\<ipv6> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6e515-102">\<ipv6> Element (Network Settings)</span></span>

<span data-ttu-id="6e515-103">, Sınıfın eski üyelerinden Internet Protokolü sürüm 6 (IPv6) yanıtlarını mümkün bir şekilde sunar <xref:System.Net.Dns> .</span><span class="sxs-lookup"><span data-stu-id="6e515-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**

## <a name="syntax"></a><span data-ttu-id="6e515-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e515-104">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e515-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e515-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6e515-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e515-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e515-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e515-107">Attributes</span></span>  
  
|<span data-ttu-id="6e515-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="6e515-108">**Attribute**</span></span>|<span data-ttu-id="6e515-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6e515-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="6e515-110"><xref:System.Net.Dns>Sınıfın üyelerinin Internet Protokolü sürüm 6 (IPv6) adresleri döndürmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e515-110">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="6e515-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="6e515-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e515-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e515-112">Child Elements</span></span>  

 <span data-ttu-id="6e515-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e515-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e515-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e515-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6e515-115">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="6e515-115">**Element**</span></span>|<span data-ttu-id="6e515-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6e515-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6e515-117">ayarlar</span><span class="sxs-lookup"><span data-stu-id="6e515-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="6e515-118">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="6e515-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e515-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e515-119">Remarks</span></span>  

 <span data-ttu-id="6e515-120">Bu ayar, sınıfının kullanılmayan üyeleri için IPv6 desteği sunar <xref:System.Net.Dns> : <xref:System.Net.Dns.BeginGetHostByName%2A> ,,, <xref:System.Net.Dns.BeginResolve%2A> <xref:System.Net.Dns.EndGetHostByName%2A> ,, <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.GetHostByName%2A> ve <xref:System.Net.Dns.Resolve%2A> .</span><span class="sxs-lookup"><span data-stu-id="6e515-120">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="6e515-121">Ad alanının diğer üyeleri için <xref:System.Net?displayProperty=nameWithType> , IPv6 adresleri işletim sisteminde IPv6 etkinse döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="6e515-121">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6e515-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6e515-122">Configuration Files</span></span>  

 <span data-ttu-id="6e515-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e515-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e515-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e515-124">Example</span></span>  

 <span data-ttu-id="6e515-125">Aşağıdaki örnekte, sınıfı için IPv6 desteğinin nasıl etkinleştirileceği gösterilmektedir <xref:System.Net.Dns> .</span><span class="sxs-lookup"><span data-stu-id="6e515-125">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e515-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e515-126">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6e515-127">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6e515-127">Network Settings Schema</span></span>](index.md)
