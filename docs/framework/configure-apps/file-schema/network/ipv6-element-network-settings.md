---
title: "&lt;IPv6&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: dd5366b4110d9ec2290e2669919575e07e8ec98a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltipv6gt-element-network-settings"></a><span data-ttu-id="81bd1-102">&lt;IPv6&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="81bd1-102">&lt;ipv6&gt; Element (Network Settings)</span></span>
<span data-ttu-id="81bd1-103">Internet Protokolü sürüm 6 (IPv6) etkinleştirir eski üyeler yanıtlarının <xref:System.Net.Dns> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="81bd1-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="81bd1-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="81bd1-104">\<configuration></span></span>  
<span data-ttu-id="81bd1-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="81bd1-105">\<system.net></span></span>  
<span data-ttu-id="81bd1-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="81bd1-106">\<settings></span></span>  
<span data-ttu-id="81bd1-107">\<IPv6 ></span><span class="sxs-lookup"><span data-stu-id="81bd1-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81bd1-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81bd1-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81bd1-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="81bd1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="81bd1-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81bd1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81bd1-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81bd1-111">Attributes</span></span>  
  
|<span data-ttu-id="81bd1-112">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="81bd1-112">**Attribute**</span></span>|<span data-ttu-id="81bd1-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="81bd1-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="81bd1-114">Belirtir olup olmadığını üyeleri <xref:System.Net.Dns> sınıfı Internet Protokolü sürüm 6 (IPv6) adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="81bd1-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="81bd1-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="81bd1-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81bd1-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="81bd1-116">Child Elements</span></span>  
 <span data-ttu-id="81bd1-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="81bd1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81bd1-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="81bd1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="81bd1-119">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="81bd1-119">**Element**</span></span>|<span data-ttu-id="81bd1-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="81bd1-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="81bd1-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="81bd1-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="81bd1-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="81bd1-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81bd1-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81bd1-123">Remarks</span></span>  
 <span data-ttu-id="81bd1-124">Bu ayar eski üyeler IPv6 desteğini etkinleştirir <xref:System.Net.Dns> sınıfı: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, ve <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="81bd1-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="81bd1-125">Diğer üyeleriyle ilgili <xref:System.Net?displayProperty=nameWithType> ad alanı, IPv6 adreslerini döndürülüp döndürülmediğini IPv6 işletim sisteminde etkinleştirilirse.</span><span class="sxs-lookup"><span data-stu-id="81bd1-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="81bd1-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="81bd1-126">Configuration Files</span></span>  
 <span data-ttu-id="81bd1-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81bd1-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81bd1-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="81bd1-128">Example</span></span>  
 <span data-ttu-id="81bd1-129">Aşağıdaki örnek, IPv6 desteğini etkinleştirmek gösterilmiştir <xref:System.Net.Dns> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="81bd1-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="81bd1-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81bd1-130">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Dns?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="81bd1-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="81bd1-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
