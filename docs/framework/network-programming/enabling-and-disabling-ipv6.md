---
title: IPv6 Etkinleştirme ve Devre Dışı Bırakma
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048570"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="bc20d-102">IPv6 Etkinleştirme ve Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="bc20d-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="bc20d-103">IPv6 protokolünü kullanmak için, IPv6'yı destekleyen işletim sisteminin bir sürümünü çalıştırdığınızdan emin olun ve işletim sistemi ve ağ sınıflarının düzgün şekilde yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="bc20d-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="bc20d-104">Yapılandırma Adımları</span><span class="sxs-lookup"><span data-stu-id="bc20d-104">Configuration Steps</span></span>  
 <span data-ttu-id="bc20d-105">Aşağıdaki tabloda çeşitli yapılandırmalar listele</span><span class="sxs-lookup"><span data-stu-id="bc20d-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="bc20d-106">İşletim sistemi IPv6 etkin?</span><span class="sxs-lookup"><span data-stu-id="bc20d-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="bc20d-107">Ağ sınıfları IPv6 etkin?</span><span class="sxs-lookup"><span data-stu-id="bc20d-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="bc20d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc20d-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="bc20d-109">Hayır</span><span class="sxs-lookup"><span data-stu-id="bc20d-109">No</span></span>|<span data-ttu-id="bc20d-110">Hayır</span><span class="sxs-lookup"><span data-stu-id="bc20d-110">No</span></span>|<span data-ttu-id="bc20d-111">IPv6 adreslerini ayrışdırabilir.</span><span class="sxs-lookup"><span data-stu-id="bc20d-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="bc20d-112">Hayır</span><span class="sxs-lookup"><span data-stu-id="bc20d-112">No</span></span>|<span data-ttu-id="bc20d-113">Evet</span><span class="sxs-lookup"><span data-stu-id="bc20d-113">Yes</span></span>|<span data-ttu-id="bc20d-114">IPv6 adreslerini ayrışdırabilir.</span><span class="sxs-lookup"><span data-stu-id="bc20d-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="bc20d-115">Evet</span><span class="sxs-lookup"><span data-stu-id="bc20d-115">Yes</span></span>|<span data-ttu-id="bc20d-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="bc20d-116">No</span></span>|<span data-ttu-id="bc20d-117">IPv6 adreslerini ayrışdırabilir ve iPv6 adreslerini eski işaretlenmemiş ad çözümleme yöntemlerini kullanarak çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bc20d-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="bc20d-118">Evet</span><span class="sxs-lookup"><span data-stu-id="bc20d-118">Yes</span></span>|<span data-ttu-id="bc20d-119">Evet</span><span class="sxs-lookup"><span data-stu-id="bc20d-119">Yes</span></span>|<span data-ttu-id="bc20d-120">IPv6 adreslerini, eski işaretlenmiş olanlar da dahil olmak üzere tüm yöntemleri kullanarak ayrıştabilir ve çözebilir.</span><span class="sxs-lookup"><span data-stu-id="bc20d-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="bc20d-121">System.Net ad alanındaki tüm sınıflar için IPv6 desteğini etkinleştirmek için, bilgisayar yapılandırma dosyasını veya uygulama nın yapılandırma dosyasını değiştirmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bc20d-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="bc20d-122">Bir uygulamanın yapılandırma dosyasının bilgisayar yapılandırma dosyasından önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="bc20d-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="bc20d-123">Bilgisayar yapılandırma dosyası, *machine.config,* Ipv6 desteği sağlamak için nasıl değiştirin bir örnek için [bkz.](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)</span><span class="sxs-lookup"><span data-stu-id="bc20d-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="bc20d-124">Ayrıca, işletim sistemi için IPv6 desteğinin etkin olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="bc20d-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="bc20d-125">.NET Framework'ün bir yapılandırma dosyasında aşağıdaki gibi ayarlanmış bir yapılandırma anahtarı vardır</span><span class="sxs-lookup"><span data-stu-id="bc20d-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
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
  
 <span data-ttu-id="bc20d-126">.NET Framework sürüm 1.1 ve daha önceki sürümiçin, **ipv6 etkinleştirilmiş** <xref:System.Net.Dns?displayProperty=nameWithType> yapılandırma anahtarının değeri, sınıf üyelerinin IPv6 adreslerini döndürüp döndürmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc20d-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="bc20d-127">.NET Framework sürüm 2.0 ve sonrası için, Windows IPv6'yı destekliyorsa, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyeleri (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntem) IPv6 adreslerini tek bir sınırlamayla döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="bc20d-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="bc20d-128">DNS'nin <xref:System.Net.Dns?displayProperty=nameWithType> eski üyeleri (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntem) ipv6 etkin ayar için yapılandırma dosyasındaki değeri okur ve tanır.</span><span class="sxs-lookup"><span data-stu-id="bc20d-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc20d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc20d-129">See also</span></span>

- [<span data-ttu-id="bc20d-130">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="bc20d-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="bc20d-131">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="bc20d-131">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="bc20d-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bc20d-132">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="bc20d-133">\<ipv6> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="bc20d-133">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
