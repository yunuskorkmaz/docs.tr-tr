---
title: Internet Protokolü sürüm 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8842bb47ad32ae1e26eaa503398ea91afb7fd1dd
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003209"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="3ca11-102">Internet Protokolü sürüm 6</span><span class="sxs-lookup"><span data-stu-id="3ca11-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="3ca11-103">Internet Protokolü sürüm 6 (IPv6) yeni bir Internet'e ağ katmanı standart protokoller paketidir.</span><span class="sxs-lookup"><span data-stu-id="3ca11-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="3ca11-104">IPv6 adres tükenmesi, güvenlik, otomatik yapılandırma, genişletilebilirlik ve benzeri için haklısın ile birçok (IPv4 olarak bilinir) Internet Protokolü paketinin geçerli sürümü, sorunu çözmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ca11-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="3ca11-105">IPv6, yeni türde uygulamalar, eşler arası ile mobil uygulamalar dahil olmak üzere etkinleştirmek için yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="3ca11-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="3ca11-106">Geçerli IPv4 protokolünün ana sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3ca11-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
-   <span data-ttu-id="3ca11-107">Hızlı tükenmesi adres alanı.</span><span class="sxs-lookup"><span data-stu-id="3ca11-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="3ca11-108">Bu, tek bir genel IP adresi için birden çok özel adresleri eşlenen ağ adres çevirileri (NAT) kullanımını açmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ca11-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="3ca11-109">Bu mekanizma tarafından oluşturulmuş ana sorunu işlem ek yükü ve uçtan uca bağlantısının olmaması.</span><span class="sxs-lookup"><span data-stu-id="3ca11-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
-   <span data-ttu-id="3ca11-110">Hiyerarşi desteği eksikliği.</span><span class="sxs-lookup"><span data-stu-id="3ca11-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="3ca11-111">Önceden tanımlanmış devralınan sınıf kuruluşunu nedeniyle IPv4 true hiyerarşik dönülemiyor.</span><span class="sxs-lookup"><span data-stu-id="3ca11-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="3ca11-112">IP adresleri, ağ topolojisini gerçekten eşleyen bir şekilde yapı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="3ca11-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="3ca11-113">Bu önemli bir tasarım kusurunu Internet üzerindeki herhangi bir konuma IPv4 paketlerini iletmek büyük yönlendirme tablolarını gereksinimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ca11-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
-   <span data-ttu-id="3ca11-114">Karmaşık ağ yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="3ca11-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="3ca11-115">IPv4 ile adresi statik olarak atanması gerekir veya DHCP gibi bir Yapılandırma Protokolü kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3ca11-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="3ca11-116">İdeal durumda, konaklar üzerinde DHCP altyapı yönetimini kullanan girmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3ca11-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="3ca11-117">Bunun yerine, bunlar bulunduğu oldukları ağ kesiminde tabanlı ağınıza ağı kendileri yapılandırmak mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="3ca11-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
-   <span data-ttu-id="3ca11-118">Yerleşik kimlik doğrulama ve gizliliği eksiği.</span><span class="sxs-lookup"><span data-stu-id="3ca11-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="3ca11-119">IPv4 destek kimlik doğrulaması veya alışverişi olur verilerin şifrelenmesini sağlayan bir mekanizma gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="3ca11-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="3ca11-120">Bu, IPv6 ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3ca11-120">This changes with IPv6.</span></span> <span data-ttu-id="3ca11-121">Internet Protokolü güvenliği (IPSec), bir IPv6 desteği gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="3ca11-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="3ca11-122">Yeni bir protokolü paketi aşağıdaki temel gereksinimleri karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="3ca11-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
-   <span data-ttu-id="3ca11-123">Büyük ölçekli Yönlendirme ve düşük yüklerle ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="3ca11-123">Large-scale routing and addressing with low overhead.</span></span>  
  
-   <span data-ttu-id="3ca11-124">Otomatik yapılandırma için çeşitli bağlantı durumlarda.</span><span class="sxs-lookup"><span data-stu-id="3ca11-124">Auto-configuration for various connecting situations.</span></span>  
  
-   <span data-ttu-id="3ca11-125">Yerleşik kimlik doğrulama ve gizliliği.</span><span class="sxs-lookup"><span data-stu-id="3ca11-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="3ca11-126">Daha fazla bilgi için [IPv6 adresleme](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 yönlendirme](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 otomatik yapılandırma](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [etkinleştirme ve devre dışı bırakma IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), ve [Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="3ca11-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="3ca11-127">Referanslar</span><span class="sxs-lookup"><span data-stu-id="3ca11-127">References</span></span>  
 <span data-ttu-id="3ca11-128">Internet Engineering Task Force sitesinde bulabilirsiniz seçili RFC belgeleri aşağıda verilmiştir ([http://www.ietf.org](http://www.ietf.org/)):</span><span class="sxs-lookup"><span data-stu-id="3ca11-128">The following are selected RFC documents that you can find at the Internet Engineering Task Force site ([http://www.ietf.org](http://www.ietf.org/)):</span></span>  
  
-   <span data-ttu-id="3ca11-129">RFC 1287, doğrultusunda gelecekteki Internet mimarisi.</span><span class="sxs-lookup"><span data-stu-id="3ca11-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
-   <span data-ttu-id="3ca11-130">RFC 1454, IP'ın sonraki sürümü için teklifleri karşılaştırması.</span><span class="sxs-lookup"><span data-stu-id="3ca11-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
-   <span data-ttu-id="3ca11-131">RFC 2373, IP sürümü 6 Adresleme Mimarisi.</span><span class="sxs-lookup"><span data-stu-id="3ca11-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
-   <span data-ttu-id="3ca11-132">RFC 2374, IPv6 toplanabilir genel tek noktaya yayın adresi biçimi.</span><span class="sxs-lookup"><span data-stu-id="3ca11-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="3ca11-133">Üzerinde IPv6 ilgili bilgiler bulabilirsiniz [IPv6 alan TechNet'teki](http://go.microsoft.com/fwlink/?LinkID=179658).</span><span class="sxs-lookup"><span data-stu-id="3ca11-133">You can also find IPv6-related information on the [IPv6 area on Technet](http://go.microsoft.com/fwlink/?LinkID=179658).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca11-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ca11-134">See Also</span></span>  
 <span data-ttu-id="3ca11-135">[IPv6 yuva örnek](https://msdn.microsoft.com/library/ms180981(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="3ca11-135">[IPv6 Sockets Sample](https://msdn.microsoft.com/library/ms180981(v=vs.85).aspx)</span></span>  
 [<span data-ttu-id="3ca11-136">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3ca11-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="3ca11-137">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="3ca11-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
