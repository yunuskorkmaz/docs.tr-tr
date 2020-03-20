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
ms.openlocfilehash: 367db4fa4e585d6066009dbd1afacb154829319a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047871"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="43db0-102">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="43db0-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="43db0-103">Internet Protokolü sürüm 6 (IPv6), Internet'in ağ katmanı için yeni bir standart protokol paketidir.</span><span class="sxs-lookup"><span data-stu-id="43db0-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="43db0-104">IPv6, adres tükenmesi, güvenlik, otomatik yapılandırma, genişletilebilirlik vb. ile ilgili olarak Internet Protocol paketinin (IPv4 olarak da bilinir) geçerli sürümünün birçok sorununu çözmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="43db0-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="43db0-105">IPv6, eşler arası ve mobil uygulamalar da dahil olmak üzere yeni uygulama türlerini etkinleştirmek için Internet'in yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="43db0-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="43db0-106">Geçerli IPv4 protokolünün ana konuları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="43db0-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="43db0-107">Adres alanının hızla tükenmesi.</span><span class="sxs-lookup"><span data-stu-id="43db0-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="43db0-108">Bu, birden çok özel adresi tek bir genel IP adresiyle eşleyen Ağ Adresi Çevirmenlerinin (NAT' ler) kullanılmasına yol açmıştır.</span><span class="sxs-lookup"><span data-stu-id="43db0-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="43db0-109">Bu mekanizma tarafından oluşturulan temel sorunlar, genel olarak işlenmek ve uçtan uca bağlantı eksikliğidir.</span><span class="sxs-lookup"><span data-stu-id="43db0-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="43db0-110">Hiyerarşi desteği eksikliği.</span><span class="sxs-lookup"><span data-stu-id="43db0-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="43db0-111">Doğası nda var olan önceden tanımlanmış sınıf organizasyonu nedeniyle, IPv4 gerçek hiyerarşik destekyoksundur.</span><span class="sxs-lookup"><span data-stu-id="43db0-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="43db0-112">IP adreslerini ağ topolojisini gerçekten eşleyen bir şekilde yapılandırmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="43db0-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="43db0-113">Bu önemli tasarım hatası, IPv4 paketlerini Internet'teki herhangi bir konuma teslim etmek için büyük yönlendirme tablolarına ihtiyaç yaratır.</span><span class="sxs-lookup"><span data-stu-id="43db0-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="43db0-114">Karmaşık ağ yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="43db0-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="43db0-115">IPv4 ile adreslere statik olarak veya DHCP gibi bir yapılandırma protokolü kullanılarak atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43db0-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="43db0-116">İdeal bir durumda, ev sahipleri bir DHCP altyapısının yönetimine güvenmek zorunda kalmaz.</span><span class="sxs-lookup"><span data-stu-id="43db0-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="43db0-117">Bunun yerine, bulundukları ağ kesimine göre kendilerini yapılandırabilirler.</span><span class="sxs-lookup"><span data-stu-id="43db0-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="43db0-118">Yerleşik kimlik doğrulama ve gizlilik eksikliği.</span><span class="sxs-lookup"><span data-stu-id="43db0-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="43db0-119">IPv4, değiştirilen verilerin kimlik doğrulamasını veya şifrelemesini sağlayan herhangi bir mekanizma için destek gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="43db0-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="43db0-120">Bu IPv6 ile değişir.</span><span class="sxs-lookup"><span data-stu-id="43db0-120">This changes with IPv6.</span></span> <span data-ttu-id="43db0-121">Internet Protocol security (IPSec) bir IPv6 destek gereksinimidir.</span><span class="sxs-lookup"><span data-stu-id="43db0-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="43db0-122">Yeni bir protokol paketi aşağıdaki temel gereksinimleri karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="43db0-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="43db0-123">Büyük ölçekli yönlendirme ve düşük yükü ile adresleme.</span><span class="sxs-lookup"><span data-stu-id="43db0-123">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="43db0-124">Çeşitli bağlantı durumları için otomatik yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="43db0-124">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="43db0-125">Dahili kimlik doğrulama ve gizlilik.</span><span class="sxs-lookup"><span data-stu-id="43db0-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="43db0-126">Daha fazla bilgi için, [IPv6 Adresleme](ipv6-addressing.md), [IPv6 Yönlendirme](ipv6-routing.md), [IPv6 Otomatik Yapılandırma](ipv6-auto-configuration.md), [Etkinleştirme ve Devre Dışı Bırakma IPv6](enabling-and-disabling-ipv6.md), ve [Nasıl bakınız: IPv6 Desteği etkinleştirmek için Bilgisayar Yapılandırma Dosyasını değiştirin](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="43db0-126">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="43db0-127">Başvurular</span><span class="sxs-lookup"><span data-stu-id="43db0-127">References</span></span>  
 <span data-ttu-id="43db0-128">[İnternet Mühendisliği Görev Gücü (IETF)](https://www.ietf.org/) web sitesinde bulabileceğiniz seçilmiş RFC belgeleri aşağıda veda edilebilmelidir:</span><span class="sxs-lookup"><span data-stu-id="43db0-128">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="43db0-129">RFC 1287, Geleceğe Doğru İnternet Mimarisi.</span><span class="sxs-lookup"><span data-stu-id="43db0-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="43db0-130">RFC 1454, IP Sonraki Sürümü için Tekliflerin Karşılaştırılması.</span><span class="sxs-lookup"><span data-stu-id="43db0-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="43db0-131">RFC 2373, IP Sürüm 6 Adresleme Mimarisi.</span><span class="sxs-lookup"><span data-stu-id="43db0-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="43db0-132">RFC 2374, Bir IPv6 Toplayıcı Küresel Unicast Adres Biçimi.</span><span class="sxs-lookup"><span data-stu-id="43db0-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="43db0-133">[Ayrıca IP Sürüm 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29)iPv6 ile ilgili bilgileri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43db0-133">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43db0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43db0-134">See also</span></span>

- [<span data-ttu-id="43db0-135">IPv6 Soketleri Örneği</span><span class="sxs-lookup"><span data-stu-id="43db0-135">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="43db0-136">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="43db0-136">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="43db0-137">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="43db0-137">Sockets</span></span>](sockets.md)
