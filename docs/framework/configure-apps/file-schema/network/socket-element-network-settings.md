---
description: 'Daha fazla bilgi edinin: <socket> öğesi (ağ ayarları)'
title: <socket> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 564d6566bf6f6b1997b986cb6c0d85f841195e55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740138"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="e49a7-103">\<socket> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="e49a7-103">\<socket> Element (Network Settings)</span></span>

<span data-ttu-id="e49a7-104">Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-104">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="e49a7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e49a7-105">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e49a7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e49a7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e49a7-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e49a7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e49a7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e49a7-108">Attributes</span></span>  
  
|<span data-ttu-id="e49a7-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="e49a7-109">**Attribute**</span></span>|<span data-ttu-id="e49a7-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e49a7-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="e49a7-111">Yuvanın Yöntem çağrılarını kabul etmek için her zaman tamamlama bağlantı noktalarını kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-111">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="e49a7-112">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-112">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="e49a7-113">Yuvanın, bağlantı yöntemi çağrıları için her zaman tamamlama bağlantı noktaları kullanması gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-113">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="e49a7-114">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-114">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="e49a7-115"><xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>Yuva için kullanılacak varsayılanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-115">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="e49a7-116">Varsayılan değer, Windows sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e49a7-116">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e49a7-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e49a7-117">Child Elements</span></span>  

 <span data-ttu-id="e49a7-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e49a7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e49a7-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e49a7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e49a7-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="e49a7-120">**Element**</span></span>|<span data-ttu-id="e49a7-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e49a7-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e49a7-122">ayarlar</span><span class="sxs-lookup"><span data-stu-id="e49a7-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="e49a7-123">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="e49a7-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e49a7-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e49a7-124">Remarks</span></span>  

 <span data-ttu-id="e49a7-125">`alwaysUseCompletionPortsForAccept`Ve `alwaysUseCompletionPortsForConnect` öznitelikleri,. Namespace içindeki sınıflar tarafından tamamlama bağlantı noktalarının kullanımıyla ilgili varsayılan davranışı belirtmek için kullanılır <xref:System.Net.Sockets?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e49a7-125">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="e49a7-126">Tamamlanma bağlantı noktaları, yüksek performanslı sunucu uygulamaları için önerilir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-126">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="e49a7-127">Ve öznitelikleri için varsayılan değer `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="e49a7-127">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="e49a7-128">, <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> İlgili yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `alwaysUseCompletionPortsForAccept` .</span><span class="sxs-lookup"><span data-stu-id="e49a7-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="e49a7-129">, <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> İlgili yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `alwaysUseCompletionPortsForConnect` .</span><span class="sxs-lookup"><span data-stu-id="e49a7-129">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="e49a7-130">`ipProtectionLevel`Öznitelik, <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> bir yuva için kullanılacak varsayılan değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-130">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="e49a7-131"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Özelliği, aynı bağlantı yerel veya site yerel ön ekine sahip adresler gibi, IPv6 soketi için belirtilen kapsama yönelik bir kısıtlama yapılandırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e49a7-131">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="e49a7-132">Bu seçenek, uygulamaların IPv6 yuvaları üzerinde erişim kısıtlamaları yerleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e49a7-132">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="e49a7-133">Bu tür kısıtlamalar, özel bir LAN üzerinde çalışan bir uygulamanın kendisini dış saldırılara karşı tek ve robustly bir şekilde kendi kendine ister.</span><span class="sxs-lookup"><span data-stu-id="e49a7-133">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="e49a7-134">Bu seçenek, bir dinleme yuvasının kapsamını widens veya daraltır, uygun olduğunda genel ve özel kullanıcılardan Kısıtlanmamış erişimi etkinleştirir ya da gerektiğinde erişimi yalnızca aynı siteye kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="e49a7-134">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="e49a7-135">Bu `ipProtectionLevel` öznitelik ayarı yalnızca ilk gelen trafiği etkiler:</span><span class="sxs-lookup"><span data-stu-id="e49a7-135">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="e49a7-136">Bir yuvada gelen bağlantıları dinleyen bir TCP sunucusu.</span><span class="sxs-lookup"><span data-stu-id="e49a7-136">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="e49a7-137">Bir yuvada paket alan UDP uygulaması.</span><span class="sxs-lookup"><span data-stu-id="e49a7-137">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="e49a7-138">Bu yapılandırma ayarı, zaten kurulu olan TCP bağlantılarını etkilemez (trafik her iki yönde kısıtlanır) ve UDP paketleri gönderen bir uygulamayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="e49a7-138">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="e49a7-139">Öznitelik ayarı için olası değerler, `ipProtectionLevel` numaralandırmada belirtilen tanımlı koruma düzeylerine karşılık gelir ve <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="e49a7-139">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="e49a7-140">**Öznitelik değeri**</span><span class="sxs-lookup"><span data-stu-id="e49a7-140">**Attribute Value**</span></span>|<span data-ttu-id="e49a7-141">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e49a7-141">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="e49a7-142">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="e49a7-142">EdgeRestricted</span></span>|<span data-ttu-id="e49a7-143">IP koruma düzeyi kenar kısıtlanıyor.</span><span class="sxs-lookup"><span data-stu-id="e49a7-143">The IP protection level is edge restricted.</span></span> <span data-ttu-id="e49a7-144">Bu değer, Internet 'te çalışacak şekilde tasarlanan uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e49a7-144">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="e49a7-145">Bu ayar, Windows Teredo uygulamasını kullanarak ağ adresi çevirisi (NAT) çapraz geçişine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="e49a7-145">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="e49a7-146">Bu uygulamalar IPv4 güvenlik duvarlarını atlayabilir, bu nedenle uygulamaların açılan bağlantı noktasına yöneltilen Internet saldırılarına karşı sağlamlaştırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-146">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="e49a7-147">Windows Server 2003 ve Windows XP 'de, bir yuvada IP koruma düzeyi için varsayılan değer kenar kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="e49a7-147">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="e49a7-148">Kısıtlı</span><span class="sxs-lookup"><span data-stu-id="e49a7-148">Restricted</span></span>|<span data-ttu-id="e49a7-149">IP koruması düzeyi kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="e49a7-149">The IP protection level is restricted.</span></span> <span data-ttu-id="e49a7-150">Bu değer, Internet senaryoları uygulamayan intranet uygulamaları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e49a7-150">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="e49a7-151">Bu uygulamalar genellikle Internet stili saldırılara karşı sınanmamıştır veya sağlamlamazlar.</span><span class="sxs-lookup"><span data-stu-id="e49a7-151">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="e49a7-152">Bu ayar, alınan trafiği yalnızca bağlantı yerel ile sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="e49a7-152">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="e49a7-153">Sınırsız</span><span class="sxs-lookup"><span data-stu-id="e49a7-153">Unrestricted</span></span>|<span data-ttu-id="e49a7-154">IP koruması düzeyi Kısıtlanmamış.</span><span class="sxs-lookup"><span data-stu-id="e49a7-154">The IP protection level is unrestricted.</span></span> <span data-ttu-id="e49a7-155">Bu değer, Windows 'da yerleşik olarak bulunan IPv6 NAT çapraz geçiş özelliğinden faydalanan uygulamalar da dahil olmak üzere tasarlanan uygulamalar tarafından kullanılır (örneğin, Teredo).</span><span class="sxs-lookup"><span data-stu-id="e49a7-155">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="e49a7-156">Bu uygulamalar IPv4 güvenlik duvarlarını atlayabilir, bu nedenle uygulamaların açılan bağlantı noktasına yöneltilen Internet saldırılarına karşı sağlamlaştırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-156">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="e49a7-157">Windows Server 2008 R2 ve Windows Vista 'da, bir yuvada IP koruma düzeyi için varsayılan değer Kısıtlamasız olur.</span><span class="sxs-lookup"><span data-stu-id="e49a7-157">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="e49a7-158">Belirtilmemiş</span><span class="sxs-lookup"><span data-stu-id="e49a7-158">Unspecified</span></span>|<span data-ttu-id="e49a7-159">IP koruması düzeyi belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="e49a7-159">The IP protection level is unspecified.</span></span> <span data-ttu-id="e49a7-160">Windows 7 ve Windows Server 2008 R2 'de, bir yuvada IP koruma düzeyi için varsayılan değer belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="e49a7-160">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="e49a7-161">Öznitelik için varsayılan değer `ipProtectionLevel` **belirtilmemiş**.</span><span class="sxs-lookup"><span data-stu-id="e49a7-161">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="e49a7-162"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Özelliği, geçerli yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `ipProtectionLevel` .</span><span class="sxs-lookup"><span data-stu-id="e49a7-162">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e49a7-163">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e49a7-163">Configuration Files</span></span>  

 <span data-ttu-id="e49a7-164">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-164">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e49a7-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="e49a7-165">Example</span></span>  

 <span data-ttu-id="e49a7-166">Aşağıdaki örnek, tamamlama bağlantı noktalarının kullanılması gerektiğini ve varsayılan değer <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> Kısıtlanmamış olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e49a7-166">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e49a7-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e49a7-167">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="e49a7-168">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e49a7-168">Network Settings Schema</span></span>](index.md)
