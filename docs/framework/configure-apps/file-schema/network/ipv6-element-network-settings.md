---
title: '&lt;IPv6&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: 02ac6ecb372b1e902d65d4b35ef71fbf0ac093c4
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170126"
---
# <a name="ltipv6gt-element-network-settings"></a><span data-ttu-id="592b3-102">&lt;IPv6&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="592b3-102">&lt;ipv6&gt; Element (Network Settings)</span></span>
<span data-ttu-id="592b3-103">Internet Protokolü sürüm 6 (IPv6) sağlar eski üyeler alınan yanıtları <xref:System.Net.Dns> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="592b3-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="592b3-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="592b3-104">\<configuration></span></span>  
<span data-ttu-id="592b3-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="592b3-105">\<system.net></span></span>  
<span data-ttu-id="592b3-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="592b3-106">\<settings></span></span>  
<span data-ttu-id="592b3-107">\<IPv6 ></span><span class="sxs-lookup"><span data-stu-id="592b3-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="592b3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="592b3-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="592b3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="592b3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="592b3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="592b3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="592b3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="592b3-111">Attributes</span></span>  
  
|<span data-ttu-id="592b3-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="592b3-112">**Attribute**</span></span>|<span data-ttu-id="592b3-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="592b3-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="592b3-114">Belirtir olup olmadığını üyeleri <xref:System.Net.Dns> sınıfı Internet Protokolü sürüm 6 (IPv6) adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="592b3-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="592b3-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="592b3-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="592b3-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="592b3-116">Child Elements</span></span>  
 <span data-ttu-id="592b3-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="592b3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="592b3-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="592b3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="592b3-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="592b3-119">**Element**</span></span>|<span data-ttu-id="592b3-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="592b3-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="592b3-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="592b3-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="592b3-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="592b3-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="592b3-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="592b3-123">Remarks</span></span>  
 <span data-ttu-id="592b3-124">Bu ayar eski üyeler için IPv6 desteğini etkinleştirir <xref:System.Net.Dns> sınıfı: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, ve <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="592b3-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="592b3-125">Diğer üyeleriyle ilgili <xref:System.Net?displayProperty=nameWithType> ad alanı, IPv6 adresleri döndürülecek IPv6 işletim sistemi içinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="592b3-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="592b3-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="592b3-126">Configuration Files</span></span>  
 <span data-ttu-id="592b3-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="592b3-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="592b3-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="592b3-128">Example</span></span>  
 <span data-ttu-id="592b3-129">Aşağıdaki örnek için IPv6 desteğini nasıl etkinleştireceğinizi gösterir <xref:System.Net.Dns> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="592b3-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="592b3-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="592b3-130">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Dns?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="592b3-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="592b3-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
