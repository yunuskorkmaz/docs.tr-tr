---
title: '&lt;Yuva&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 995a89dd67664fd6a408f88f20f6837d2dbaaad4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsocketgt-element-network-settings"></a><span data-ttu-id="b6fa8-102">&lt;Yuva&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b6fa8-102">&lt;socket&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b6fa8-103">Yuva işlemleri tamamlama bağlantı noktalarını kullanacak olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="b6fa8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="b6fa8-104">\<configuration></span></span>  
<span data-ttu-id="b6fa8-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b6fa8-105">\<system.net></span></span>  
<span data-ttu-id="b6fa8-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="b6fa8-106">\<settings></span></span>  
<span data-ttu-id="b6fa8-107">\<Yuva ></span><span class="sxs-lookup"><span data-stu-id="b6fa8-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6fa8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6fa8-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6fa8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6fa8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b6fa8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6fa8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b6fa8-111">Attributes</span></span>  
  
|<span data-ttu-id="b6fa8-112">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="b6fa8-112">**Attribute**</span></span>|<span data-ttu-id="b6fa8-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b6fa8-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="b6fa8-114">Yuva her zaman tamamlama bağlantı noktalarını kabul yöntemi çağrıları için kullanılması gerekip gerekmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="b6fa8-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="b6fa8-116">Yuva her zaman tamamlama bağlantı noktalarını Bağlan yöntem çağrıları için kullanılması gerekip gerekmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="b6fa8-117">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="b6fa8-118">Varsayılan belirtir <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> yuva için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="b6fa8-119">Varsayılan değer Windows sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6fa8-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6fa8-120">Child Elements</span></span>  
 <span data-ttu-id="b6fa8-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6fa8-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6fa8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b6fa8-123">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="b6fa8-123">**Element**</span></span>|<span data-ttu-id="b6fa8-124">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b6fa8-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b6fa8-125">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="b6fa8-125">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="b6fa8-126">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6fa8-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6fa8-127">Remarks</span></span>  
 <span data-ttu-id="b6fa8-128">`alwaysUseCompletionPortsForAccept` Ve `alwaysUseCompletionPortsForConnect` öznitelikleri tamamlama bağlantı noktaları kullanımına ilişkin varsayılan davranışı belirtmek için tarafından kullanılan sınıfları <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="b6fa8-129">Tamamlama bağlantı noktaları, yüksek performanslı sunucu uygulamaları için önerilir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="b6fa8-130">İçin varsayılan değer `alwaysUseCompletionPortsForAccept` ve `alwaysUseCompletionPortsForConnect` öznitelikleri **false**.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="b6fa8-131"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Geçerli değerini almak için kullanılan `alwaysUseCompletionPortsForAccept` geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="b6fa8-132"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Geçerli değerini almak için kullanılan `alwaysUseCompletionPortsForConnect` geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="b6fa8-133">`ipProtectionLevel` Özniteliği belirtir. varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> yuva için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="b6fa8-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Özelliği, belirtilen kapsam için bir IPv6 yuva için bir kısıtlama yapılandırması gibi aynı adresleriyle site yerel öneki veya yerel bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="b6fa8-135">Bu seçenek, erişim kısıtlamaları IPv6 yuvalarda yerleştirmek uygulamaları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="b6fa8-136">Tür kısıtlamaları sadece ve yerine kendi dış saldırılara karşı sağlamlaştırmak özel bir LAN üzerinde çalışan bir uygulama etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="b6fa8-137">Bu seçenek widens veya dinleme yuva, ortak ve özel kullanıcılar uygun olduğunda veya yalnızca aynı sitede gerektiği için erişimi kısıtlamak etkinleştirme Kısıtlanmamış erişim kapsamını daraltır.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="b6fa8-138">Bu `ipProtectionLevel` özniteliği ayar, yalnızca ilk gelen trafiğe etkiler:</span><span class="sxs-lookup"><span data-stu-id="b6fa8-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
-   <span data-ttu-id="b6fa8-139">Bir yuvada gelen bağlantılar için dinleme TCP sunucu.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
-   <span data-ttu-id="b6fa8-140">Paket bir yuvada alma UDP uygulama.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="b6fa8-141">Bu yapılandırma ayarının (her iki yönde trafik Kısıtlanmamış) zaten oluşturulmuş TCP bağlantılarını etkilemez ve UDP paketlerini gönderen uygulama etkilemez.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="b6fa8-142">Olası değerler için `ipProtectionLevel` özniteliğinin ayarına karşılık gelen belirtilen tanımlanan koruma düzeyleri ile <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> şekilde numaralandırma:</span><span class="sxs-lookup"><span data-stu-id="b6fa8-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="b6fa8-143">**Öznitelik değeri**</span><span class="sxs-lookup"><span data-stu-id="b6fa8-143">**Attribute Value**</span></span>|<span data-ttu-id="b6fa8-144">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b6fa8-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="b6fa8-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="b6fa8-145">EdgeRestricted</span></span>|<span data-ttu-id="b6fa8-146">IP koruma düzeyi kenar sınırlı olur.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="b6fa8-147">Bu değer Internet üzerinden çalışmak için tasarlanmış uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="b6fa8-148">Bu ayar Windows Teredo uygulamasını kullanarak ağ adresi çevirisi (NAT) geçişine izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="b6fa8-149">Açılan bağlantı noktasına yönelik Internet saldırılarına karşı uygulamalar sıkı gerekir böylece bu uygulamaları IPv4 güvenlik duvarları, atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="b6fa8-150">Windows Server 2003 ve Windows XP üzerinde bir yuvada IP koruma düzeyi için varsayılan değer kısıtlanmış kenar ' dir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="b6fa8-151">Sınırlı</span><span class="sxs-lookup"><span data-stu-id="b6fa8-151">Restricted</span></span>|<span data-ttu-id="b6fa8-152">IP koruma düzeyi sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-152">The IP protection level is restricted.</span></span> <span data-ttu-id="b6fa8-153">Bu değer Internet senaryoları kullanılmaz intranet uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="b6fa8-154">Bu uygulamalar genellikle değil test veya Internet stili saldırılarına karşı sıkı.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="b6fa8-155">Bu ayar yalnızca bağlantı yerel alınan trafiğini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="b6fa8-156">Sınırsız</span><span class="sxs-lookup"><span data-stu-id="b6fa8-156">Unrestricted</span></span>|<span data-ttu-id="b6fa8-157">IP koruma düzeyi kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="b6fa8-158">Bu değer yerleşik IPv6 NAT geçişi özelliklerini yararlanarak uygulamalar dahil olmak üzere, Internet üzerinden çalışmak için tasarlanmış uygulamalar tarafından kullanılması halinde Windows (örneğin, Teredo).</span><span class="sxs-lookup"><span data-stu-id="b6fa8-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="b6fa8-159">Açılan bağlantı noktasına yönelik Internet saldırılarına karşı uygulamalar sıkı gerekir böylece bu uygulamaları IPv4 güvenlik duvarları, atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="b6fa8-160">Windows Server 2008 R2 ve Windows Vista üzerinde bir yuvada IP koruma düzeyi için varsayılan değer kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="b6fa8-161">Belirtilmemiş</span><span class="sxs-lookup"><span data-stu-id="b6fa8-161">Unspecified</span></span>|<span data-ttu-id="b6fa8-162">IP koruma düzeyi belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="b6fa8-163">Windows 7 ve Windows Server 2008 R2 üzerinde bir yuvada IP koruma düzeyi için varsayılan değer belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="b6fa8-164">İçin varsayılan değer `ipProtectionLevel` özniteliği **belirtilmemiş**.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="b6fa8-165"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Özelliği, geçerli değerini almak için kullanılabilir `ipProtectionLevel` geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b6fa8-166">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="b6fa8-166">Configuration Files</span></span>  
 <span data-ttu-id="b6fa8-167">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6fa8-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6fa8-168">Example</span></span>  
 <span data-ttu-id="b6fa8-169">Aşağıdaki örnek, tamamlama bağlantı noktalarının kullanılacağını belirtin ve sonra gösterir varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> Kısıtlanmamış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6fa8-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6fa8-170">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [<span data-ttu-id="b6fa8-171">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b6fa8-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
