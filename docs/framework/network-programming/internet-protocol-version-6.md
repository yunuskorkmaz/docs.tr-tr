---
title: İnternet Protokolü Sürüm 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 135d87f126dcdb9689c23adbaaa4786bc69a3e09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642327"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="23ce6-102">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="23ce6-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="23ce6-103">Internet Protokolü sürüm 6 (IPv6) yeni bir Internet'e ağ katmanı standart protokoller paketidir.</span><span class="sxs-lookup"><span data-stu-id="23ce6-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="23ce6-104">IPv6 adres tükenmesi, güvenlik, otomatik yapılandırma, genişletilebilirlik ve benzeri için haklısın ile birçok (IPv4 olarak bilinir) Internet Protokolü paketinin geçerli sürümü, sorunu çözmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="23ce6-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="23ce6-105">IPv6, yeni türde uygulamalar, eşler arası ile mobil uygulamalar dahil olmak üzere etkinleştirmek için yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="23ce6-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="23ce6-106">Geçerli IPv4 protokolünün ana sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="23ce6-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="23ce6-107">Hızlı tükenmesi adres alanı.</span><span class="sxs-lookup"><span data-stu-id="23ce6-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="23ce6-108">Bu, tek bir genel IP adresi için birden çok özel adresleri eşlenen ağ adres çevirileri (NAT) kullanımını açmıştır.</span><span class="sxs-lookup"><span data-stu-id="23ce6-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="23ce6-109">Bu mekanizma tarafından oluşturulmuş ana sorunu işlem ek yükü ve uçtan uca bağlantısının olmaması.</span><span class="sxs-lookup"><span data-stu-id="23ce6-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="23ce6-110">Hiyerarşi desteği eksikliği.</span><span class="sxs-lookup"><span data-stu-id="23ce6-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="23ce6-111">Önceden tanımlanmış devralınan sınıf kuruluşunu nedeniyle IPv4 true hiyerarşik dönülemiyor.</span><span class="sxs-lookup"><span data-stu-id="23ce6-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="23ce6-112">IP adresleri, ağ topolojisini gerçekten eşleyen bir şekilde yapı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="23ce6-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="23ce6-113">Bu önemli bir tasarım kusurunu Internet üzerindeki herhangi bir konuma IPv4 paketlerini iletmek büyük yönlendirme tablolarını gereksinimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23ce6-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="23ce6-114">Karmaşık ağ yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="23ce6-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="23ce6-115">IPv4 ile adresi statik olarak atanması gerekir veya DHCP gibi bir Yapılandırma Protokolü kullanarak.</span><span class="sxs-lookup"><span data-stu-id="23ce6-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="23ce6-116">İdeal durumda, konaklar üzerinde DHCP altyapı yönetimini kullanan girmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="23ce6-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="23ce6-117">Bunun yerine, bunlar bulunduğu oldukları ağ kesiminde tabanlı ağınıza ağı kendileri yapılandırmak mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="23ce6-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="23ce6-118">Yerleşik kimlik doğrulama ve gizliliği eksiği.</span><span class="sxs-lookup"><span data-stu-id="23ce6-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="23ce6-119">IPv4 destek kimlik doğrulaması veya alışverişi olur verilerin şifrelenmesini sağlayan bir mekanizma gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="23ce6-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="23ce6-120">Bu, IPv6 ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="23ce6-120">This changes with IPv6.</span></span> <span data-ttu-id="23ce6-121">Internet Protokolü güvenliği (IPSec), bir IPv6 desteği gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="23ce6-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="23ce6-122">Yeni bir protokolü paketi aşağıdaki temel gereksinimleri karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="23ce6-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="23ce6-123">Büyük ölçekli Yönlendirme ve düşük yüklerle ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="23ce6-123">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="23ce6-124">Otomatik yapılandırma için çeşitli bağlantı durumlarda.</span><span class="sxs-lookup"><span data-stu-id="23ce6-124">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="23ce6-125">Yerleşik kimlik doğrulama ve gizliliği.</span><span class="sxs-lookup"><span data-stu-id="23ce6-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="23ce6-126">Daha fazla bilgi için [IPv6 adresleme](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 yönlendirme](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 otomatik yapılandırma](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [etkinleştirme ve devre dışı bırakma IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), ve [Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="23ce6-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="23ce6-127">Referanslar</span><span class="sxs-lookup"><span data-stu-id="23ce6-127">References</span></span>  
 <span data-ttu-id="23ce6-128">Konumunda bulabilirsiniz seçili RFC belgeleri aşağıda verilmiştir [Internet Engineering Task Force (IETF)](https://www.ietf.org/) Web sitesi:</span><span class="sxs-lookup"><span data-stu-id="23ce6-128">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="23ce6-129">RFC 1287, doğrultusunda gelecekteki Internet mimarisi.</span><span class="sxs-lookup"><span data-stu-id="23ce6-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="23ce6-130">RFC 1454, IP'ın sonraki sürümü için teklifleri karşılaştırması.</span><span class="sxs-lookup"><span data-stu-id="23ce6-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="23ce6-131">RFC 2373, IP sürümü 6 Adresleme Mimarisi.</span><span class="sxs-lookup"><span data-stu-id="23ce6-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="23ce6-132">RFC 2374, IPv6 toplanabilir genel tek noktaya yayın adresi biçimi.</span><span class="sxs-lookup"><span data-stu-id="23ce6-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="23ce6-133">Üzerinde IPv6 ilgili bilgiler bulabilirsiniz [IP sürüm 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span><span class="sxs-lookup"><span data-stu-id="23ce6-133">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ce6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23ce6-134">See also</span></span>

- [<span data-ttu-id="23ce6-135">IPv6 yuva örnek</span><span class="sxs-lookup"><span data-stu-id="23ce6-135">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="23ce6-136">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="23ce6-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
- [<span data-ttu-id="23ce6-137">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="23ce6-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
