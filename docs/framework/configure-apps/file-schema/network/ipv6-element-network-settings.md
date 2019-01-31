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
ms.openlocfilehash: 708604c782690efa631e4eab0aa62c1c0b1f657b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279701"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="bd243-102">\<IPv6 > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="bd243-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="bd243-103">Internet Protokolü sürüm 6 (IPv6) sağlar eski üyeler alınan yanıtları <xref:System.Net.Dns> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bd243-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="bd243-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="bd243-104">\<configuration></span></span>  
<span data-ttu-id="bd243-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="bd243-105">\<system.net></span></span>  
<span data-ttu-id="bd243-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="bd243-106">\<settings></span></span>  
<span data-ttu-id="bd243-107">\<IPv6 ></span><span class="sxs-lookup"><span data-stu-id="bd243-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd243-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd243-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd243-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd243-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bd243-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd243-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd243-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd243-111">Attributes</span></span>  
  
|<span data-ttu-id="bd243-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="bd243-112">**Attribute**</span></span>|<span data-ttu-id="bd243-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bd243-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="bd243-114">Belirtir olup olmadığını üyeleri <xref:System.Net.Dns> sınıfı Internet Protokolü sürüm 6 (IPv6) adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bd243-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="bd243-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="bd243-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd243-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd243-116">Child Elements</span></span>  
 <span data-ttu-id="bd243-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd243-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd243-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd243-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bd243-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="bd243-119">**Element**</span></span>|<span data-ttu-id="bd243-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bd243-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bd243-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="bd243-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="bd243-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bd243-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd243-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd243-123">Remarks</span></span>  
 <span data-ttu-id="bd243-124">Bu ayar eski üyeler için IPv6 desteğini etkinleştirir <xref:System.Net.Dns> sınıfı: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, ve <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd243-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="bd243-125">Diğer üyeleriyle ilgili <xref:System.Net?displayProperty=nameWithType> ad alanı, IPv6 adresleri döndürülecek IPv6 işletim sistemi içinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bd243-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bd243-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="bd243-126">Configuration Files</span></span>  
 <span data-ttu-id="bd243-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd243-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd243-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd243-128">Example</span></span>  
 <span data-ttu-id="bd243-129">Aşağıdaki örnek için IPv6 desteğini nasıl etkinleştireceğinizi gösterir <xref:System.Net.Dns> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bd243-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd243-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd243-130">See also</span></span>
- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bd243-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bd243-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
