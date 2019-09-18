---
title: IPv6 Etkinleştirme ve Devre Dışı Bırakma
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048570"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="d3b9e-102">IPv6 Etkinleştirme ve Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="d3b9e-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="d3b9e-103">IPv6 protokolünü kullanmak için, IPv6 'Yı destekleyen bir işletim sistemi sürümü çalıştırdığından ve işletim sisteminin ve ağ sınıflarının düzgün yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="d3b9e-104">Yapılandırma adımları</span><span class="sxs-lookup"><span data-stu-id="d3b9e-104">Configuration Steps</span></span>  
 <span data-ttu-id="d3b9e-105">Aşağıdaki tabloda çeşitli yapılandırma listelenmiştir</span><span class="sxs-lookup"><span data-stu-id="d3b9e-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="d3b9e-106">İşletim sistemi IPv6 etkin mi?</span><span class="sxs-lookup"><span data-stu-id="d3b9e-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="d3b9e-107">Ağ sınıfları IPv6-etkin mi?</span><span class="sxs-lookup"><span data-stu-id="d3b9e-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="d3b9e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3b9e-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="d3b9e-109">Hayır</span><span class="sxs-lookup"><span data-stu-id="d3b9e-109">No</span></span>|<span data-ttu-id="d3b9e-110">Hayır</span><span class="sxs-lookup"><span data-stu-id="d3b9e-110">No</span></span>|<span data-ttu-id="d3b9e-111">IPv6 adreslerini ayrıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="d3b9e-112">Hayır</span><span class="sxs-lookup"><span data-stu-id="d3b9e-112">No</span></span>|<span data-ttu-id="d3b9e-113">Evet</span><span class="sxs-lookup"><span data-stu-id="d3b9e-113">Yes</span></span>|<span data-ttu-id="d3b9e-114">IPv6 adreslerini ayrıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="d3b9e-115">Evet</span><span class="sxs-lookup"><span data-stu-id="d3b9e-115">Yes</span></span>|<span data-ttu-id="d3b9e-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="d3b9e-116">No</span></span>|<span data-ttu-id="d3b9e-117">, Bilinen olarak işaretlenmemiş ad çözümleme yöntemlerini kullanarak IPv6 adreslerini ayrıştırıp adresleri çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="d3b9e-118">Evet</span><span class="sxs-lookup"><span data-stu-id="d3b9e-118">Yes</span></span>|<span data-ttu-id="d3b9e-119">Evet</span><span class="sxs-lookup"><span data-stu-id="d3b9e-119">Yes</span></span>|<span data-ttu-id="d3b9e-120">, Artık kullanılmıyor olarak işaretlenenler dahil tüm yöntemleri kullanarak IPv6 adreslerini ayrıştırıp çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="d3b9e-121">System.Net ad alanındaki tüm sınıfların IPv6 desteğini etkinleştirmek için, bilgisayar yapılandırma dosyasını veya uygulamanın yapılandırma dosyasını değiştirmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="d3b9e-122">Bir uygulamanın yapılandırma dosyası, bilgisayar yapılandırma dosyasına göre önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="d3b9e-123">Bilgisayar yapılandırma dosyasının, *Machine. config*, IPv6 desteğinin etkinleştirilmesi için nasıl değiştirileceği hakkında bir örnek için bkz [. nasıl yapılır: IPv6 desteğini](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)etkinleştirmek Için bilgisayar yapılandırma dosyasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="d3b9e-124">Ayrıca, işletim sistemi için IPv6 desteğinin etkinleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="d3b9e-125">.NET Framework yapılandırma dosyasında aşağıdaki şekilde ayarlanmış bir yapılandırma anahtarı vardır</span><span class="sxs-lookup"><span data-stu-id="d3b9e-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
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
  
 <span data-ttu-id="d3b9e-126">.NET Framework sürüm 1,1 ve önceki sürümlerde **IPv6 etkin** yapılandırma anahtarının değeri, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyelerinin IPv6 adresleri döndürmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="d3b9e-127">.NET Framework sürüm 2,0 ve üzeri için, Windows IPv6 'yı destekliyorsa, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyeleri (örneğin <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> , yöntemi) bir sınırlamaya sahip IPv6 adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="d3b9e-128">Kullanılmayan DNS <xref:System.Net.Dns?displayProperty=nameWithType> üyeleri (örneğin <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> , yöntemi) IPv6 etkin ayarının yapılandırma dosyasındaki değeri okur ve tanır.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b9e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3b9e-129">See also</span></span>

- [<span data-ttu-id="d3b9e-130">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="d3b9e-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="d3b9e-131">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="d3b9e-131">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="d3b9e-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d3b9e-132">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="d3b9e-133">\<IPv6 > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d3b9e-133">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
