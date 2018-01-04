---
title: "Internet Protokolü sürüm 6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 333fbb452cb1f24b5e62d1106eff4560b26267b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="b2e86-102">Internet Protokolü sürüm 6</span><span class="sxs-lookup"><span data-stu-id="b2e86-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="b2e86-103">Internet Protokolü sürüm 6 (IPv6), standart protokol ağ katmanı Internet için yeni bir paketidir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="b2e86-104">IPv6 adresi tükenmesi, güvenlik, otomatik yapılandırma, genişletilebilirlik ve benzeri şekilde ile birçok geçerli sürümü (IPv4 olarak bilinir) Internet Protokolü paketi, sorunu çözmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b2e86-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="b2e86-105">IPv6 yeni tür uygulamaların, eşler arası ve mobil uygulamaları dahil olmak üzere etkinleştirmek için Internet özelliklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="b2e86-106">Geçerli IPv4 protokolünün ana sorunları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b2e86-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
-   <span data-ttu-id="b2e86-107">Hızlı tükenmesi adres alanı.</span><span class="sxs-lookup"><span data-stu-id="b2e86-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="b2e86-108">Bu, tek bir ortak IP adresi için birden çok özel adres eşlenen ağ adres çevirileri (NAT) kullanımını açmıştır.</span><span class="sxs-lookup"><span data-stu-id="b2e86-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="b2e86-109">Bu düzenek tarafından oluşturulan ana sorunları ek yükü ve uçtan uca bağlantı işliyor.</span><span class="sxs-lookup"><span data-stu-id="b2e86-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
-   <span data-ttu-id="b2e86-110">Hiyerarşi destek eksikliği.</span><span class="sxs-lookup"><span data-stu-id="b2e86-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="b2e86-111">Bunun devralınan önceden tanımlanmış sınıf düzenlemesi nedeniyle IPv4 doğru hiyerarşik desteğini azaltır.</span><span class="sxs-lookup"><span data-stu-id="b2e86-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="b2e86-112">IP adresleri, ağ topolojisini gerçekten eşlemeleri şekilde yapısı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="b2e86-113">Bu önemli tasarım kusur Internet üzerindeki herhangi bir yere IPv4 paketlerini iletmek büyük yönlendirme tablolarını gereksinimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2e86-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
-   <span data-ttu-id="b2e86-114">Karmaşık ağ yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="b2e86-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="b2e86-115">IPv4 ile adresleri statik olarak atanmalıdır veya DHCP gibi yapılandırma protokolünü kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b2e86-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="b2e86-116">İdeal bir durumda konakları DHCP altyapı yönetimini yararlanmayı sahip.</span><span class="sxs-lookup"><span data-stu-id="b2e86-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="b2e86-117">Bunun yerine, bunlar kendilerini bunlar bulunduğu ağ kesiminde göre yapılandırmanız mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b2e86-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
-   <span data-ttu-id="b2e86-118">Yerleşik kimlik doğrulama ve gizliliği eksiği.</span><span class="sxs-lookup"><span data-stu-id="b2e86-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="b2e86-119">IPv4 kimlik doğrulaması veya alışverişi verilerin şifrelenmesini sağlayan herhangi bir mekanizma için desteği gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b2e86-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="b2e86-120">Bu, IPv6 ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-120">This changes with IPv6.</span></span> <span data-ttu-id="b2e86-121">Internet Protokolü güvenliği (IPSec) IPv6 desteği gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="b2e86-122">Yeni bir protokolü paketi, aşağıdaki temel gereksinimleri karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="b2e86-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
-   <span data-ttu-id="b2e86-123">Büyük ölçekli Yönlendirme ve düşük yükü ile adresleme.</span><span class="sxs-lookup"><span data-stu-id="b2e86-123">Large-scale routing and addressing with low overhead.</span></span>  
  
-   <span data-ttu-id="b2e86-124">Otomatik yapılandırma çeşitli bağlantı durumlar için.</span><span class="sxs-lookup"><span data-stu-id="b2e86-124">Auto-configuration for various connecting situations.</span></span>  
  
-   <span data-ttu-id="b2e86-125">Yerleşik kimlik doğrulama ve gizliliği.</span><span class="sxs-lookup"><span data-stu-id="b2e86-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="b2e86-126">Daha fazla bilgi için bkz: [IPv6 adresleme](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 yönlendirme](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 otomatik yapılandırma](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [etkinleştirme ve devre dışı bırakma IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), ve [Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayarı yapılandırma dosyasını değiştirme](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="b2e86-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="b2e86-127">Referanslar</span><span class="sxs-lookup"><span data-stu-id="b2e86-127">References</span></span>  
 <span data-ttu-id="b2e86-128">Internet Engineering Task Force sitede bulabilirsiniz seçili RFC belgeleri aşağıda verilmiştir ([http://www.ietf.org](http://www.ietf.org/)):</span><span class="sxs-lookup"><span data-stu-id="b2e86-128">The following are selected RFC documents that you can find at the Internet Engineering Task Force site ([http://www.ietf.org](http://www.ietf.org/)):</span></span>  
  
-   <span data-ttu-id="b2e86-129">RFC 1287, gelecekteki Internet mimarisinin bulunun.</span><span class="sxs-lookup"><span data-stu-id="b2e86-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
-   <span data-ttu-id="b2e86-130">RFC 1454, IP sonraki sürümü teklifleri karşılaştırması.</span><span class="sxs-lookup"><span data-stu-id="b2e86-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
-   <span data-ttu-id="b2e86-131">RFC 2373, IP sürüm 6 Adresleme Mimarisi.</span><span class="sxs-lookup"><span data-stu-id="b2e86-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
-   <span data-ttu-id="b2e86-132">RFC 2374, bir IPv6 toplanabilir genel tek noktaya yayın adresi biçimi.</span><span class="sxs-lookup"><span data-stu-id="b2e86-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="b2e86-133">Üzerinde IPv6 ilgili bilgiler de bulabilirsiniz [IPv6 alanı TechNet'te](http://go.microsoft.com/fwlink/?LinkID=179658).</span><span class="sxs-lookup"><span data-stu-id="b2e86-133">You can also find IPv6-related information on the [IPv6 area on Technet](http://go.microsoft.com/fwlink/?LinkID=179658).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e86-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2e86-134">See Also</span></span>  
 [<span data-ttu-id="b2e86-135">IPv6 yuva örnek</span><span class="sxs-lookup"><span data-stu-id="b2e86-135">IPv6 Sockets Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179568)  
 [<span data-ttu-id="b2e86-136">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="b2e86-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="b2e86-137">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="b2e86-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
