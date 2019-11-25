---
title: <socket> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 0e2b369eccfbc658a790ef61a961315a88361669
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089082"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="5f478-102">\<yuva > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5f478-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="5f478-103">Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f478-103">Specifies whether socket operations use completion ports.</span></span>  

<span data-ttu-id="5f478-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5f478-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5f478-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="5f478-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="5f478-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ayarları >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5f478-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="5f478-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<yuva >**</span><span class="sxs-lookup"><span data-stu-id="5f478-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5f478-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f478-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f478-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f478-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5f478-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f478-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f478-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5f478-111">Attributes</span></span>  
  
|<span data-ttu-id="5f478-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="5f478-112">**Attribute**</span></span>|<span data-ttu-id="5f478-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5f478-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="5f478-114">Yuvanın Yöntem çağrılarını kabul etmek için her zaman tamamlama bağlantı noktalarını kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f478-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="5f478-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5f478-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="5f478-116">Yuvanın, bağlantı yöntemi çağrıları için her zaman tamamlama bağlantı noktaları kullanması gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f478-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="5f478-117">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5f478-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="5f478-118">Yuva için kullanılacak varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f478-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="5f478-119">Varsayılan değer, Windows sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5f478-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f478-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f478-120">Child Elements</span></span>  
 <span data-ttu-id="5f478-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f478-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f478-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f478-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5f478-123">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5f478-123">**Element**</span></span>|<span data-ttu-id="5f478-124">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5f478-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5f478-125">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="5f478-125">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="5f478-126"><xref:System.Net> ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5f478-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f478-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f478-127">Remarks</span></span>  
 <span data-ttu-id="5f478-128">`alwaysUseCompletionPortsForAccept` ve `alwaysUseCompletionPortsForConnect` öznitelikleri, <xref:System.Net.Sockets?displayProperty=nameWithType>. Namespace içindeki sınıflar tarafından tamamlama bağlantı noktalarının kullanımıyla ilgili varsayılan davranışı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f478-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="5f478-129">Tamamlanma bağlantı noktaları, yüksek performanslı sunucu uygulamaları için önerilir.</span><span class="sxs-lookup"><span data-stu-id="5f478-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="5f478-130">`alwaysUseCompletionPortsForAccept` ve `alwaysUseCompletionPortsForConnect` öznitelikleri için varsayılan değer **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="5f478-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="5f478-131"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>, uygun yapılandırma dosyalarından `alwaysUseCompletionPortsForAccept` özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f478-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="5f478-132"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>, uygun yapılandırma dosyalarından `alwaysUseCompletionPortsForConnect` özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f478-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="5f478-133">`ipProtectionLevel` özniteliği, bir yuva için kullanılacak varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f478-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="5f478-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> özelliği, aynı bağlantı yerel veya site yerel ön ekine sahip adresler gibi, IPv6 soketi için belirtilen kapsama yönelik bir kısıtlama yapılandırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f478-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="5f478-135">Bu seçenek, uygulamaların IPv6 yuvaları üzerinde erişim kısıtlamaları yerleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f478-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="5f478-136">Bu tür kısıtlamalar, özel bir LAN üzerinde çalışan bir uygulamanın kendisini dış saldırılara karşı tek ve robustly bir şekilde kendi kendine ister.</span><span class="sxs-lookup"><span data-stu-id="5f478-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="5f478-137">Bu seçenek, bir dinleme yuvasının kapsamını widens veya daraltır, uygun olduğunda genel ve özel kullanıcılardan Kısıtlanmamış erişimi etkinleştirir ya da gerektiğinde erişimi yalnızca aynı siteye kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="5f478-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="5f478-138">Bu `ipProtectionLevel` özniteliği ayarı yalnızca ilk gelen trafiği etkiler:</span><span class="sxs-lookup"><span data-stu-id="5f478-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="5f478-139">Bir yuvada gelen bağlantıları dinleyen bir TCP sunucusu.</span><span class="sxs-lookup"><span data-stu-id="5f478-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="5f478-140">Bir yuvada paket alan UDP uygulaması.</span><span class="sxs-lookup"><span data-stu-id="5f478-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="5f478-141">Bu yapılandırma ayarı, zaten kurulu olan TCP bağlantılarını etkilemez (trafik her iki yönde kısıtlanır) ve UDP paketleri gönderen bir uygulamayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="5f478-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="5f478-142">`ipProtectionLevel` öznitelik ayarı için olası değerler, <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> numaralandırmasında belirtilen tanımlı koruma düzeylerine karşılık gelir:</span><span class="sxs-lookup"><span data-stu-id="5f478-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="5f478-143">**Öznitelik değeri**</span><span class="sxs-lookup"><span data-stu-id="5f478-143">**Attribute Value**</span></span>|<span data-ttu-id="5f478-144">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5f478-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="5f478-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="5f478-145">EdgeRestricted</span></span>|<span data-ttu-id="5f478-146">IP koruma düzeyi kenar kısıtlanıyor.</span><span class="sxs-lookup"><span data-stu-id="5f478-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="5f478-147">Bu değer, Internet 'te çalışacak şekilde tasarlanan uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f478-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="5f478-148">Bu ayar, Windows Teredo uygulamasını kullanarak ağ adresi çevirisi (NAT) çapraz geçişine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="5f478-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="5f478-149">Bu uygulamalar IPv4 güvenlik duvarlarını atlayabilir, bu nedenle uygulamaların açılan bağlantı noktasına yöneltilen Internet saldırılarına karşı sağlamlaştırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f478-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="5f478-150">Windows Server 2003 ve Windows XP 'de, bir yuvada IP koruma düzeyi için varsayılan değer kenar kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="5f478-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="5f478-151">Dığından</span><span class="sxs-lookup"><span data-stu-id="5f478-151">Restricted</span></span>|<span data-ttu-id="5f478-152">IP koruması düzeyi kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="5f478-152">The IP protection level is restricted.</span></span> <span data-ttu-id="5f478-153">Bu değer, Internet senaryoları uygulamayan intranet uygulamaları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f478-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="5f478-154">Bu uygulamalar genellikle Internet stili saldırılara karşı sınanmamıştır veya sağlamlamazlar.</span><span class="sxs-lookup"><span data-stu-id="5f478-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="5f478-155">Bu ayar, alınan trafiği yalnızca bağlantı yerel ile sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="5f478-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="5f478-156">Edin</span><span class="sxs-lookup"><span data-stu-id="5f478-156">Unrestricted</span></span>|<span data-ttu-id="5f478-157">IP koruması düzeyi Kısıtlanmamış.</span><span class="sxs-lookup"><span data-stu-id="5f478-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="5f478-158">Bu değer, Windows 'da yerleşik olarak bulunan IPv6 NAT çapraz geçiş özelliğinden faydalanan uygulamalar da dahil olmak üzere tasarlanan uygulamalar tarafından kullanılır (örneğin, Teredo).</span><span class="sxs-lookup"><span data-stu-id="5f478-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="5f478-159">Bu uygulamalar IPv4 güvenlik duvarlarını atlayabilir, bu nedenle uygulamaların açılan bağlantı noktasına yöneltilen Internet saldırılarına karşı sağlamlaştırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f478-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="5f478-160">Windows Server 2008 R2 ve Windows Vista 'da, bir yuvada IP koruma düzeyi için varsayılan değer Kısıtlamasız olur.</span><span class="sxs-lookup"><span data-stu-id="5f478-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="5f478-161">Memesi</span><span class="sxs-lookup"><span data-stu-id="5f478-161">Unspecified</span></span>|<span data-ttu-id="5f478-162">IP koruması düzeyi belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="5f478-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="5f478-163">Windows 7 ve Windows Server 2008 R2 'de, bir yuvada IP koruma düzeyi için varsayılan değer belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="5f478-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="5f478-164">`ipProtectionLevel` özniteliği için varsayılan değer **belirtilmemiş**.</span><span class="sxs-lookup"><span data-stu-id="5f478-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="5f478-165"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> özelliği, uygun yapılandırma dosyalarından `ipProtectionLevel` özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f478-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5f478-166">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5f478-166">Configuration Files</span></span>  
 <span data-ttu-id="5f478-167">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f478-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f478-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f478-168">Example</span></span>  
 <span data-ttu-id="5f478-169">Aşağıdaki örnek, bu tamamlama bağlantı noktalarının nasıl kullanılacağını ve varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> sınırsız olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f478-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f478-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f478-170">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="5f478-171">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5f478-171">Network Settings Schema</span></span>](index.md)
