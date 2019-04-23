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
ms.openlocfilehash: 82bfe3b6e3107ff787716657dbf0b31dcadde911
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160166"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="bc35e-102">\<Yuva > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="bc35e-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="bc35e-103">Yuva işlemleri tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="bc35e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="bc35e-104">\<configuration></span></span>  
<span data-ttu-id="bc35e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="bc35e-105">\<system.net></span></span>  
<span data-ttu-id="bc35e-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="bc35e-106">\<settings></span></span>  
<span data-ttu-id="bc35e-107">\<Yuva ></span><span class="sxs-lookup"><span data-stu-id="bc35e-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc35e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc35e-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc35e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc35e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bc35e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc35e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc35e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc35e-111">Attributes</span></span>  
  
|<span data-ttu-id="bc35e-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="bc35e-112">**Attribute**</span></span>|<span data-ttu-id="bc35e-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bc35e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="bc35e-114">Yuva tamamlama bağlantı noktaları her zaman için Accept yöntemi çağrıları kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="bc35e-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="bc35e-116">Yuva tamamlama bağlantı noktaları her zaman Connect yöntem çağrıları için kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="bc35e-117">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="bc35e-118">Varsayılan belirtir <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> bir yuva için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="bc35e-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="bc35e-119">Varsayılan değer Windows sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bc35e-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc35e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc35e-120">Child Elements</span></span>  
 <span data-ttu-id="bc35e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc35e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc35e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc35e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bc35e-123">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="bc35e-123">**Element**</span></span>|<span data-ttu-id="bc35e-124">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bc35e-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bc35e-125">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="bc35e-125">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="bc35e-126">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bc35e-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc35e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc35e-127">Remarks</span></span>  
 <span data-ttu-id="bc35e-128">`alwaysUseCompletionPortsForAccept` Ve `alwaysUseCompletionPortsForConnect` öznitelikleri tamamlama bağlantı noktaları kullanımına ilişkin varsayılan davranışını belirtmek için kullanılan sınıfları tarafından <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span><span class="sxs-lookup"><span data-stu-id="bc35e-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="bc35e-129">Tamamlama bağlantı noktaları, yüksek performanslı sunucu uygulamaları için önerilir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="bc35e-130">İçin varsayılan değer `alwaysUseCompletionPortsForAccept` ve `alwaysUseCompletionPortsForConnect` öznitelikleri **false**.</span><span class="sxs-lookup"><span data-stu-id="bc35e-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="bc35e-131"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Geçerli değerini almak için kullanılan `alwaysUseCompletionPortsForAccept` ilgili yapılandırma dosyaları özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bc35e-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="bc35e-132"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Geçerli değerini almak için kullanılan `alwaysUseCompletionPortsForConnect` ilgili yapılandırma dosyaları özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bc35e-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="bc35e-133">`ipProtectionLevel` Özniteliği belirtir Varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> bir yuva için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="bc35e-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="bc35e-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Özelliği, belirtilen bir kapsam için bir IPv6 yuva için bir kısıtlama yapılandırması gibi adresleri aynı sitede yerel bir önek veya yerel bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc35e-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="bc35e-135">Bu seçenek, IPv6 yuvalarda erişim kısıtlaması için uygulamaları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="bc35e-136">Bu kısıtlamaların yeterlidir ve yerine kendisini dış saldırılarına karşı zorlaştırmak özel bir LAN üzerinde çalışan bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="bc35e-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="bc35e-137">Bu seçenek widens veya dinleme yuva, genel ve özel kullanıcılar uygun olduğunda veya gerektiği gibi aynı site için yalnızca erişimini etkinleştirme sınırsız erişim kapsamını daraltır.</span><span class="sxs-lookup"><span data-stu-id="bc35e-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="bc35e-138">Bu `ipProtectionLevel` özniteliğini yalnızca ilk gelen trafiği etkiler:</span><span class="sxs-lookup"><span data-stu-id="bc35e-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
-   <span data-ttu-id="bc35e-139">Bir TCP yuva gelen bağlantıları için dinlemek sunucu.</span><span class="sxs-lookup"><span data-stu-id="bc35e-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
-   <span data-ttu-id="bc35e-140">Bir paketin bir yuvada alma bir UDP uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="bc35e-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="bc35e-141">Bu yapılandırma ayarının (her iki yönde trafik Kısıtlanmamış) önceden kurulmuş TCP bağlantıları etkilemez ve UDP paketlerini gönderen uygulama etkilemez.</span><span class="sxs-lookup"><span data-stu-id="bc35e-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="bc35e-142">Olası değerler için `ipProtectionLevel` özniteliğini karşılık gelen belirtilen tanımlı koruma düzeyleri ile <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> sabit listesi aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="bc35e-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="bc35e-143">**Öznitelik değeri**</span><span class="sxs-lookup"><span data-stu-id="bc35e-143">**Attribute Value**</span></span>|<span data-ttu-id="bc35e-144">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bc35e-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="bc35e-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="bc35e-145">EdgeRestricted</span></span>|<span data-ttu-id="bc35e-146">IP koruma düzeyi kısıtlı edge ' dir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="bc35e-147">Bu değer Internet üzerinden çalışmak üzere tasarlanmış uygulamalar tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="bc35e-148">Bu ayar Windows Teredo uygulamasını kullanarak ağ adresi çevirisi (NAT) geçişine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="bc35e-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="bc35e-149">Bu uygulamalar, uygulamalar, açık bağlantı noktalarından yönlendirilmiş Internet saldırılarına karşı sıkı gerekir böylece IPv4 güvenlik duvarları, atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="bc35e-150">Windows Server 2003 ve Windows XP'de bir yuvada IP koruma düzeyi için varsayılan değer edge kısıtlı ' dir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="bc35e-151">kısıtlı</span><span class="sxs-lookup"><span data-stu-id="bc35e-151">Restricted</span></span>|<span data-ttu-id="bc35e-152">IP koruma düzeyi sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="bc35e-152">The IP protection level is restricted.</span></span> <span data-ttu-id="bc35e-153">Bu değer olarak Internet senaryoları uygulamayan intranet uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc35e-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="bc35e-154">Bu uygulamalar genel olmayan test veya Internet stili saldırılarına karşı sıkı.</span><span class="sxs-lookup"><span data-stu-id="bc35e-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="bc35e-155">Bu ayar yalnızca bağlantı yerel alınan trafik sınırlar.</span><span class="sxs-lookup"><span data-stu-id="bc35e-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="bc35e-156">Sınırsız</span><span class="sxs-lookup"><span data-stu-id="bc35e-156">Unrestricted</span></span>|<span data-ttu-id="bc35e-157">IP koruma düzeyi kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="bc35e-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="bc35e-158">Bu değer yerleşik IPv6 NAT geçişi özelliklerini yararlanarak uygulamaları dahil olmak üzere Internet üzerinden çalışmak üzere tasarlanmış uygulamalar tarafından kullanılması halinde Windows (örneğin, Teredo).</span><span class="sxs-lookup"><span data-stu-id="bc35e-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="bc35e-159">Bu uygulamalar, uygulamalar, açık bağlantı noktalarından yönlendirilmiş Internet saldırılarına karşı sıkı gerekir böylece IPv4 güvenlik duvarları, atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="bc35e-160">Bir yuva IP koruma düzeyi için varsayılan değer, Windows Server 2008 R2 ve Windows Vista, kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="bc35e-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="bc35e-161">Belirtilmemiş</span><span class="sxs-lookup"><span data-stu-id="bc35e-161">Unspecified</span></span>|<span data-ttu-id="bc35e-162">IP koruma düzeyi belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="bc35e-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="bc35e-163">Windows 7 ve Windows Server 2008 R2 üzerinde bir yuvada IP koruma düzeyi için varsayılan değer belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="bc35e-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="bc35e-164">İçin varsayılan değer `ipProtectionLevel` özniteliği **belirtilmemiş**.</span><span class="sxs-lookup"><span data-stu-id="bc35e-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="bc35e-165"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Özelliği, geçerli değerini almak için kullanılabilir `ipProtectionLevel` geçerli yapılandırma dosyalarından özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bc35e-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bc35e-166">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="bc35e-166">Configuration Files</span></span>  
 <span data-ttu-id="bc35e-167">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc35e-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc35e-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc35e-168">Example</span></span>  
 <span data-ttu-id="bc35e-169">Aşağıdaki örnek nasıl tamamlama bağlantı noktalarının kullanılması gerektiğini belirtin ve bu gösterir. varsayılan <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> sınırsız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc35e-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc35e-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc35e-170">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="bc35e-171">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bc35e-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
