---
title: İnternet Protokolü Sürüm 6
description: IPv6 protokolünü ve IPv4 'den farklı olduğunu öğrenin. .NET Framework uygulamalar IPv6 'yı destekler, ancak yapılandırma gerektirebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: dd8b0b26e449fba7479d2678aff25ed49e721a90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502398"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="588c7-104">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="588c7-104">Internet Protocol Version 6</span></span>
<span data-ttu-id="588c7-105">Internet Protokolü sürüm 6 (IPv6), Internet ağ katmanı için yeni bir standart protokoller paketidir.</span><span class="sxs-lookup"><span data-stu-id="588c7-105">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="588c7-106">IPv6, Internet Protokolü paketi 'nin geçerli sürümünün (IPv4 olarak bilinir), aşalım, güvenlik, otomatik yapılandırma, genişletilebilirlik vb. gibi birçok sorununu çözmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="588c7-106">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="588c7-107">IPv6, eşler arası ve mobil uygulamalar da dahil olmak üzere yeni uygulama türlerini etkinleştirmek için Internet 'in yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="588c7-107">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="588c7-108">Geçerli IPv4 protokolünün başlıca sorunları aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="588c7-108">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="588c7-109">Adres alanının hızlı bir şekilde çıkarılması.</span><span class="sxs-lookup"><span data-stu-id="588c7-109">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="588c7-110">Bu, birden çok özel adresi tek bir genel IP adresine eşleyen ağ adresi çeviricileri (NAT) kullanımına yol açmıştır.</span><span class="sxs-lookup"><span data-stu-id="588c7-110">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="588c7-111">Bu mekanizma tarafından oluşturulan başlıca sorunlar, ek yükü ve uçtan uca bağlantının eksikliğinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="588c7-111">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="588c7-112">Hiyerarşi desteğinin bulunmaması.</span><span class="sxs-lookup"><span data-stu-id="588c7-112">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="588c7-113">Devralınan önceden tanımlanmış sınıf kuruluşunda, IPv4 gerçek hiyerarşik desteğe sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="588c7-113">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="588c7-114">IP adreslerini gerçekten ağ topolojisini eşleyen bir şekilde yapılandırmak olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="588c7-114">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="588c7-115">Bu önemli tasarım kusuru, Internet 'teki herhangi bir konuma IPv4 paketleri sunmaya yönelik büyük yönlendirme tablolarına yönelik ihtiyacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="588c7-115">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="588c7-116">Karmaşık ağ yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="588c7-116">Complex network configuration.</span></span>  
  
     <span data-ttu-id="588c7-117">IPv4 ile adreslerin statik olarak atanması veya DHCP gibi bir yapılandırma Protokolü kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="588c7-117">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="588c7-118">İdeal bir durumda, konaklar bir DHCP altyapısının yönetimine güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="588c7-118">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="588c7-119">Bunun yerine kendilerini bulundukları ağ kesimine göre yapılandırabilirler.</span><span class="sxs-lookup"><span data-stu-id="588c7-119">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="588c7-120">Yerleşik kimlik doğrulaması ve gizlilik eksikliği yok.</span><span class="sxs-lookup"><span data-stu-id="588c7-120">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="588c7-121">IPv4, değiştirilen verilerin kimlik doğrulaması veya şifrelemesini sağlayan herhangi bir mekanizma için destek gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="588c7-121">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="588c7-122">Bu, IPv6 ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="588c7-122">This changes with IPv6.</span></span> <span data-ttu-id="588c7-123">Internet Protokolü güvenliği (IPSec) bir IPv6 destek gereksinimidir.</span><span class="sxs-lookup"><span data-stu-id="588c7-123">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="588c7-124">Yeni bir protokol paketinin aşağıdaki temel gereksinimleri karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="588c7-124">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="588c7-125">Düşük ek yüklerle büyük ölçekli yönlendirme ve adresleme.</span><span class="sxs-lookup"><span data-stu-id="588c7-125">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="588c7-126">Çeşitli bağlama durumları için otomatik yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="588c7-126">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="588c7-127">Yerleşik kimlik doğrulaması ve gizlilik.</span><span class="sxs-lookup"><span data-stu-id="588c7-127">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="588c7-128">Daha fazla bilgi için bkz. [IPv6 adresleme](ipv6-addressing.md), [IPv6 yönlendirme](ipv6-routing.md), [IPv6 otomatik yapılandırma](ipv6-auto-configuration.md), [IPv6 'Yı etkinleştirme ve devre dışı bırakma](enabling-and-disabling-ipv6.md)ve [nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="588c7-128">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="588c7-129">Başvurular</span><span class="sxs-lookup"><span data-stu-id="588c7-129">References</span></span>  
 <span data-ttu-id="588c7-130">Aşağıda, [Internet Mühendisliği görev gücü (IETF)](https://www.ietf.org/) Web SITESINDE bulabileceğiniz RFC belgelerinin seçildiği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="588c7-130">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="588c7-131">RFC 1287, gelecekteki Internet mimarisine doğru.</span><span class="sxs-lookup"><span data-stu-id="588c7-131">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="588c7-132">RFC 1454, IP 'nin sonraki sürümü için tekliflerin karşılaştırması.</span><span class="sxs-lookup"><span data-stu-id="588c7-132">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="588c7-133">RFC 2373, IP sürüm 6 Adresleme Mimarisi.</span><span class="sxs-lookup"><span data-stu-id="588c7-133">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="588c7-134">Bir IPv6 toplanabilir genel tek noktaya yayın adresi biçimi olan RFC 2374.</span><span class="sxs-lookup"><span data-stu-id="588c7-134">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="588c7-135">IPv6 ile ilgili bilgileri [IP sürüm 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29)üzerinde de bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="588c7-135">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="588c7-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="588c7-136">See also</span></span>

- [<span data-ttu-id="588c7-137">IPv6 yuvaları örneği</span><span class="sxs-lookup"><span data-stu-id="588c7-137">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="588c7-138">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="588c7-138">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="588c7-139">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="588c7-139">Sockets</span></span>](sockets.md)
