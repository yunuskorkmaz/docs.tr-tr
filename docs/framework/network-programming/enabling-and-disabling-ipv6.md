---
title: IPv6 Etkinleştirme ve Devre Dışı Bırakma
description: Bilgisayar veya uygulama için yapılandırma dosyasını değiştirme dahil olmak üzere IPv6 protokolünü kullanmayı etkinleştirmek için bu yapılandırma adımlarını izleyin.
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 7729647b09df20a98d5d639a641cb0a31f557330
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502619"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="ddfd7-103">IPv6 Etkinleştirme ve Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="ddfd7-103">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="ddfd7-104">IPv6 protokolünü kullanmak için, IPv6 'Yı destekleyen bir işletim sistemi sürümü çalıştırdığından ve işletim sisteminin ve ağ sınıflarının düzgün yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-104">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="ddfd7-105">Yapılandırma adımları</span><span class="sxs-lookup"><span data-stu-id="ddfd7-105">Configuration Steps</span></span>  
 <span data-ttu-id="ddfd7-106">Aşağıdaki tabloda çeşitli yapılandırma listelenmiştir</span><span class="sxs-lookup"><span data-stu-id="ddfd7-106">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="ddfd7-107">İşletim sistemi IPv6 etkin mi?</span><span class="sxs-lookup"><span data-stu-id="ddfd7-107">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="ddfd7-108">Ağ sınıfları IPv6-etkin mi?</span><span class="sxs-lookup"><span data-stu-id="ddfd7-108">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="ddfd7-109">Description</span><span class="sxs-lookup"><span data-stu-id="ddfd7-109">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="ddfd7-110">Hayır</span><span class="sxs-lookup"><span data-stu-id="ddfd7-110">No</span></span>|<span data-ttu-id="ddfd7-111">Hayır</span><span class="sxs-lookup"><span data-stu-id="ddfd7-111">No</span></span>|<span data-ttu-id="ddfd7-112">IPv6 adreslerini ayrıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-112">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="ddfd7-113">No</span><span class="sxs-lookup"><span data-stu-id="ddfd7-113">No</span></span>|<span data-ttu-id="ddfd7-114">Evet</span><span class="sxs-lookup"><span data-stu-id="ddfd7-114">Yes</span></span>|<span data-ttu-id="ddfd7-115">IPv6 adreslerini ayrıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-115">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="ddfd7-116">Evet</span><span class="sxs-lookup"><span data-stu-id="ddfd7-116">Yes</span></span>|<span data-ttu-id="ddfd7-117">No</span><span class="sxs-lookup"><span data-stu-id="ddfd7-117">No</span></span>|<span data-ttu-id="ddfd7-118">, Bilinen olarak işaretlenmemiş ad çözümleme yöntemlerini kullanarak IPv6 adreslerini ayrıştırıp adresleri çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-118">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="ddfd7-119">Yes</span><span class="sxs-lookup"><span data-stu-id="ddfd7-119">Yes</span></span>|<span data-ttu-id="ddfd7-120">Yes</span><span class="sxs-lookup"><span data-stu-id="ddfd7-120">Yes</span></span>|<span data-ttu-id="ddfd7-121">, Artık kullanılmıyor olarak işaretlenenler dahil tüm yöntemleri kullanarak IPv6 adreslerini ayrıştırıp çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-121">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="ddfd7-122">System.Net ad alanındaki tüm sınıfların IPv6 desteğini etkinleştirmek için, bilgisayar yapılandırma dosyasını veya uygulamanın yapılandırma dosyasını değiştirmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-122">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="ddfd7-123">Bir uygulamanın yapılandırma dosyası, bilgisayar yapılandırma dosyasına göre önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-123">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="ddfd7-124">*Machine. config*bilgisayar yapılandırma dosyasının nasıl değiştirileceği hakkında bir örnek Için, IPv6 desteğinin etkinleştirilmesi için bkz. [IPv6 desteğini etkinleştirmek Için bilgisayar yapılandırma dosyasını değiştirme](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="ddfd7-124">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="ddfd7-125">Ayrıca, işletim sistemi için IPv6 desteğinin etkinleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-125">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="ddfd7-126">.NET Framework yapılandırma dosyasında aşağıdaki şekilde ayarlanmış bir yapılandırma anahtarı vardır</span><span class="sxs-lookup"><span data-stu-id="ddfd7-126">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
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
  
 <span data-ttu-id="ddfd7-127">.NET Framework sürüm 1,1 ve önceki sürümlerde **IPv6 etkin** yapılandırma anahtarının değeri, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyelerinin IPv6 adresleri döndürmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-127">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="ddfd7-128">.NET Framework sürüm 2,0 ve üzeri için, Windows IPv6 'yı destekliyorsa, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyeleri (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi) bir sınırlamaya sahip IPv6 adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-128">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="ddfd7-129">Kullanılmayan DNS üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) IPv6 etkin ayarının yapılandırma dosyasındaki değeri okur ve tanır.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-129">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddfd7-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddfd7-130">See also</span></span>

- [<span data-ttu-id="ddfd7-131">Internet Protokolü sürüm 6</span><span class="sxs-lookup"><span data-stu-id="ddfd7-131">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="ddfd7-132">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="ddfd7-132">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="ddfd7-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ddfd7-133">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="ddfd7-134">\<ipv6>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="ddfd7-134">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
