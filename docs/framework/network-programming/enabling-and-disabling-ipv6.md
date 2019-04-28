---
title: IPv6 Etkinleştirme ve Devre Dışı Bırakma
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 73dee0cb57674c8a2fa4ba2246162870ab1e3a10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643107"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="f81d8-102">IPv6 Etkinleştirme ve Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="f81d8-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="f81d8-103">IPv6 protokolü kullanmak için bir IPv6 destekleyen bir işletim sistemi sürümünü çalıştırdığından emin olun ve işletim sistemi ve ağ sınıfları düzgün yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f81d8-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="f81d8-104">Yapılandırma adımları</span><span class="sxs-lookup"><span data-stu-id="f81d8-104">Configuration Steps</span></span>  
 <span data-ttu-id="f81d8-105">Aşağıdaki tabloda çeşitli yapılandırmalarını listeler</span><span class="sxs-lookup"><span data-stu-id="f81d8-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="f81d8-106">İşletim sistemi IPv6 özellikli?</span><span class="sxs-lookup"><span data-stu-id="f81d8-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="f81d8-107">Ağ, IPv6 özellikli sınıfları?</span><span class="sxs-lookup"><span data-stu-id="f81d8-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="f81d8-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f81d8-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="f81d8-109">Hayır</span><span class="sxs-lookup"><span data-stu-id="f81d8-109">No</span></span>|<span data-ttu-id="f81d8-110">Hayır</span><span class="sxs-lookup"><span data-stu-id="f81d8-110">No</span></span>|<span data-ttu-id="f81d8-111">IPv6 adresleri ayrıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f81d8-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="f81d8-112">Hayır</span><span class="sxs-lookup"><span data-stu-id="f81d8-112">No</span></span>|<span data-ttu-id="f81d8-113">Evet</span><span class="sxs-lookup"><span data-stu-id="f81d8-113">Yes</span></span>|<span data-ttu-id="f81d8-114">IPv6 adresleri ayrıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f81d8-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="f81d8-115">Evet</span><span class="sxs-lookup"><span data-stu-id="f81d8-115">Yes</span></span>|<span data-ttu-id="f81d8-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="f81d8-116">No</span></span>|<span data-ttu-id="f81d8-117">IPv6 adresleri ayrıştırabilir ve eski işaretlenmemiş ad çözümleme yöntemleri kullanarak IPv6 adresleri çözümlemek.</span><span class="sxs-lookup"><span data-stu-id="f81d8-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="f81d8-118">Evet</span><span class="sxs-lookup"><span data-stu-id="f81d8-118">Yes</span></span>|<span data-ttu-id="f81d8-119">Evet</span><span class="sxs-lookup"><span data-stu-id="f81d8-119">Yes</span></span>|<span data-ttu-id="f81d8-120">Ayrıştırabilir ve IPv6 adresleri artık kullanılmıyor olarak işaretlendiğinden dahil olmak üzere tüm yöntemleri kullanarak çözün.</span><span class="sxs-lookup"><span data-stu-id="f81d8-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="f81d8-121">System.Net ad alanındaki tüm sınıflar için IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyası veya uygulama için yapılandırma dosyasını değiştirmeniz gerekir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f81d8-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="f81d8-122">Bir uygulama yapılandırma dosyası, bilgisayar yapılandırma dosyası üzerinde önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f81d8-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="f81d8-123">Bilgisayar yapılandırma dosyasını değiştirme ilişkin bir örnek için *machine.config*, etkinleştirmek için IPv6 desteği bkz [nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="f81d8-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="f81d8-124">Ayrıca, IPv6 desteği için işletim sistemi etkinleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f81d8-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="f81d8-125">.NET Framework sahip bir yapılandırma dosyasında şu şekilde ayarlanan bir yapılandırma anahtarı</span><span class="sxs-lookup"><span data-stu-id="f81d8-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 <span data-ttu-id="f81d8-126">.NET Framework sürüm 1.1 ve önceki değerini **IPv6 etkin** yapılandırma anahtarı belirtir olup olmadığını üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıf, IPv6 adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f81d8-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="f81d8-127">.NET Framework sürüm 2.0 ve üzeri, Windows IPv6 sonra üyeleri destekliyorsa <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi), tek bir kısıtlama olmaksızın IPv6 adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f81d8-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="f81d8-128">Geçersiz DNS üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) okuyun ve yapılandırma dosyasında IPv6 etkin ayarı için değer tanınamıyor.</span><span class="sxs-lookup"><span data-stu-id="f81d8-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81d8-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f81d8-129">See also</span></span>

- [<span data-ttu-id="f81d8-130">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="f81d8-130">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [<span data-ttu-id="f81d8-131">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="f81d8-131">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
- [<span data-ttu-id="f81d8-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f81d8-132">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="f81d8-133">\<IPv6 > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="f81d8-133">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
