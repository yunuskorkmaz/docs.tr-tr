---
title: Etkinleştirme ve IPv6 devre dışı bırakma
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b018d646816bda96945a440a890da20b81b1cbbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393938"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="2c445-102">Etkinleştirme ve IPv6 devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="2c445-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="2c445-103">IPv6 protokolünü kullanmak için bir IPv6'yı destekleyen işletim sistemi sürümünü çalıştırdığından emin olun ve işletim sistemi ve ağ sınıfları düzgün yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2c445-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="2c445-104">Yapılandırma adımları</span><span class="sxs-lookup"><span data-stu-id="2c445-104">Configuration Steps</span></span>  
 <span data-ttu-id="2c445-105">Aşağıdaki tabloda çeşitli yapılandırmaları listeler</span><span class="sxs-lookup"><span data-stu-id="2c445-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="2c445-106">İşletim sistemi IPv6 etkinleştirilmiş mi?</span><span class="sxs-lookup"><span data-stu-id="2c445-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="2c445-107">Ağ, IPv6 özellikli sınıfları?</span><span class="sxs-lookup"><span data-stu-id="2c445-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="2c445-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c445-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="2c445-109">Hayır</span><span class="sxs-lookup"><span data-stu-id="2c445-109">No</span></span>|<span data-ttu-id="2c445-110">Hayır</span><span class="sxs-lookup"><span data-stu-id="2c445-110">No</span></span>|<span data-ttu-id="2c445-111">IPv6 adresleri ayrıştıramıyor.</span><span class="sxs-lookup"><span data-stu-id="2c445-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="2c445-112">Hayır</span><span class="sxs-lookup"><span data-stu-id="2c445-112">No</span></span>|<span data-ttu-id="2c445-113">Evet</span><span class="sxs-lookup"><span data-stu-id="2c445-113">Yes</span></span>|<span data-ttu-id="2c445-114">IPv6 adresleri ayrıştıramıyor.</span><span class="sxs-lookup"><span data-stu-id="2c445-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="2c445-115">Evet</span><span class="sxs-lookup"><span data-stu-id="2c445-115">Yes</span></span>|<span data-ttu-id="2c445-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="2c445-116">No</span></span>|<span data-ttu-id="2c445-117">IPv6 adresleri ayrıştırabilir ve ad çözümleme yöntemleri geçersiz işaretlenmemiş kullanarak IPv6 adresleri çözümleyecek.</span><span class="sxs-lookup"><span data-stu-id="2c445-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="2c445-118">Evet</span><span class="sxs-lookup"><span data-stu-id="2c445-118">Yes</span></span>|<span data-ttu-id="2c445-119">Evet</span><span class="sxs-lookup"><span data-stu-id="2c445-119">Yes</span></span>|<span data-ttu-id="2c445-120">Ayrıştırılamıyor ve geçersiz olarak işaretlenmiş dahil olmak üzere tüm yöntemleri kullanarak IPv6 adresleri çözümleyecek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c445-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="2c445-121">System.Net ad alanındaki tüm sınıfları IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyası veya uygulama için yapılandırma dosyası değiştirmelisiniz olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2c445-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="2c445-122">Bir uygulama için yapılandırma dosyası bilgisayar yapılandırma dosyası önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2c445-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="2c445-123">Bilgisayar yapılandırma dosyasını değiştirme konusunda bir örnek için *machine.config*, etkinleştirmek için IPv6 desteği bkz [nasıl yapılır: IPv6'yı destekleyen etkinleştirmek için bilgisayarı yapılandırma dosyasını değiştirme](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="2c445-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="2c445-124">Ayrıca, IPv6 desteği için işletim sistemini etkinleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2c445-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="2c445-125">.NET Framework yapılandırma dosyasında aşağıdaki gibi ayarlayın yapılandırma anahtarı sahiptir</span><span class="sxs-lookup"><span data-stu-id="2c445-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 <span data-ttu-id="2c445-126">.NET Framework sürüm 1.1 ve önceki değeri için **etkin IPv6** yapılandırma anahtarı belirtir olup olmadığını üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı IPv6 adresleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2c445-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="2c445-127">.NET Framework sürüm 2.0 ve daha sonra Windows IPv6 sonra üyeleri destekliyorsa için <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi), IPv6 adresleriyle bir sınırlama döndürür.</span><span class="sxs-lookup"><span data-stu-id="2c445-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="2c445-128">Eski DNS üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) okuma ve yapılandırma dosyasındaki IPv6 etkin ayarı için değer algılar.</span><span class="sxs-lookup"><span data-stu-id="2c445-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c445-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c445-129">See Also</span></span>  
 [<span data-ttu-id="2c445-130">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="2c445-130">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="2c445-131">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="2c445-131">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)  
 [<span data-ttu-id="2c445-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2c445-132">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="2c445-133">\<IPv6 > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="2c445-133">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
