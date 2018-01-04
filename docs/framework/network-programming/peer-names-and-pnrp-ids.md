---
title: "Eş adlarını ve PNRP kimlikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 02f3f7585babd54c9d807afb308bccb7d67e2f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="peer-names-and-pnrp-ids"></a><span data-ttu-id="2d5ee-102">Eş adlarını ve PNRP kimlikleri</span><span class="sxs-lookup"><span data-stu-id="2d5ee-102">Peer Names and PNRP IDs</span></span>
<span data-ttu-id="2d5ee-103">Eş adı bir bilgisayar, bir kullanıcı, bir grup, bir hizmet veya bir IPv6 adresine çözülebilir bir eş ile ilişkili herhangi bir şey olabilir, iletişimi için bir uç noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-103">A Peer Name represents an endpoint for communication, which can be a computer, a user, a group, a service, or anything associated with a Peer that can be resolved to an IPv6 address.</span></span> <span data-ttu-id="2d5ee-104">Eş Adı Çözümleme Protokolü (PNRP) bir PNRP bulut üyelerini tanımlamak için kullanılan kimliği oluşturulması için istatistiksel olarak benzersiz eş adını alır.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-104">The Peer Name Resolution Protocol (PNRP) takes the statistically unique Peer Name for the creation of a PNRP ID, which is used to identify cloud members.</span></span>  
  
## <a name="peer-names"></a><span data-ttu-id="2d5ee-105">Eş adları</span><span class="sxs-lookup"><span data-stu-id="2d5ee-105">Peer Names</span></span>  
 <span data-ttu-id="2d5ee-106">Eş adları olarak kaydedilebilir güvenli veya güvenli.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-106">Peer names can be registered as unsecured or secured.</span></span> <span data-ttu-id="2d5ee-107">Herhangi bir yinelenen güvenli olmayan ad kaydedebilecekleri güvenli yalnızca yanıltma tabi olan metin dizelerini adlardır.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-107">Unsecured names are just text strings that are subject to spoofing, as anyone can register a duplicate unsecured name.</span></span> <span data-ttu-id="2d5ee-108">Güvenli olmayan adlar en iyi özel veya aksi korumalı ağlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-108">Unsecured names are best used in private or otherwise protected networks.</span></span> <span data-ttu-id="2d5ee-109">Güvenli adları bir sertifika ve dijital imza ile korunur.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-109">Secured names are protected with a certificate and a digital signature.</span></span> <span data-ttu-id="2d5ee-110">Yalnızca özgün yayımcısı güvenli bir ad sahipliğini kanıtlamak mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-110">Only the original publisher will be able to prove ownership of a secured name.</span></span>  
  
 <span data-ttu-id="2d5ee-111">Bulut ve kapsamın birleşimi PNRP etkinliğinde katılmak eşleri için makul biçimde güvenli bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-111">The combination of cloud and scope provides a reasonably secure environment for peers that participate in PNRP activity.</span></span> <span data-ttu-id="2d5ee-112">Ancak, bir güvenli Eş adı kullanarak Ağ uygulamasının genel güvenlik olunmasını sağlamamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-112">However, using a secured peer name does not ensure the overall security of the networking application.</span></span> <span data-ttu-id="2d5ee-113">Güvenlik uygulamasının uygulama bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-113">Security of the application is implementation-dependent.</span></span>  
  
 <span data-ttu-id="2d5ee-114">Güvenli eş adları, yalnızca kendi sahibi tarafından kaydedilir ve ortak anahtar şifrelemesi ile korunan.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-114">Secured peer names are only registered by their owner and are protected with public key cryptography.</span></span> <span data-ttu-id="2d5ee-115">Güvenli eş adını ilgili özel anahtara sahip eş varlık tarafından ait kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-115">A secured peer name is considered owned by the peer entity having the corresponding private key.</span></span> <span data-ttu-id="2d5ee-116">Sahipliği özel anahtarı ile imzalanmış sertifikalı eş adresi (CPA) oluyor uygulamasına yol açıyordu.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-116">Ownership can be proved via the certified peer address (CPA), which is signed using the private key.</span></span> <span data-ttu-id="2d5ee-117">Kötü niyetli bir kullanıcının bir eş adı karşılık gelen özel anahtar olmadan sahipliğini taklit edilemez.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-117">A malicious user cannot forge ownership of a peer name without the corresponding private key.</span></span>  
  
## <a name="pnrp-ids"></a><span data-ttu-id="2d5ee-118">PNRP kimlikleri</span><span class="sxs-lookup"><span data-stu-id="2d5ee-118">PNRP IDs</span></span>  
 <span data-ttu-id="2d5ee-119">![PNRP kimliği](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span><span class="sxs-lookup"><span data-stu-id="2d5ee-119">![PNRP ID](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span></span>  
  
 <span data-ttu-id="2d5ee-120">PNRP kimlikleri aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="2d5ee-120">PNRP IDs are composed of the following:</span></span>  
  
-   <span data-ttu-id="2d5ee-121">Yüksek düzey 128 bit eşler arası (P2P) kimliği olarak da bilinen eş adı uç noktasına atanmış karmasını değerleridir.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-121">The high-order 128 bits, known as the peer-to-peer (P2P) ID, are a hash of a peer name assigned to the endpoint.</span></span> <span data-ttu-id="2d5ee-122">Eş adı şu biçimdedir: *Authority.Classifier*.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-122">The peer name has the following format: *Authority.Classifier*.</span></span> <span data-ttu-id="2d5ee-123">Güvenli adları için *yetkilisi* onaltılı karakter Eş adı ortak anahtarını Güvenli Karma Algoritması 1 (SHA1) karmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-123">For secured names, *Authority* is the Secure Hash Algorithm 1 (SHA1) hash of the public key of the peer name in hexadecimal characters.</span></span> <span data-ttu-id="2d5ee-124">Güvenli olmayan adları için *yetkilisi* "0" joker karakterleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-124">For unsecured names, the *Authority* is the single character "0".</span></span> <span data-ttu-id="2d5ee-125">*Sınıflandırıcı* uygulama tanımlayan bir dize değil.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-125">*Classifier* is a string that identifies the application.</span></span> <span data-ttu-id="2d5ee-126">Hiçbir eş adı sınıflandırıcı 149 karakterden uzun dahil olmak üzere büyük `null` Sonlandırıcı.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-126">No peer name classifier can be greater than 149 characters long, including the `null` terminator.</span></span>  
  
-   <span data-ttu-id="2d5ee-127">Düşük düzey 128 bit aynı P2P kimliği aynı buluttaki farklı örneklerini tanımlayan oluşturulan bir sayıdır hizmet konumu için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-127">The low-order 128 bits are used for the Service Location, which is a generated number that identifies different instances of the same P2P ID in the same cloud.</span></span>  
  
 <span data-ttu-id="2d5ee-128">Bu birleşim P2P Kimliğinin ve hizmet konumu tek bir bilgisayardan kaydedilmesi birden çok PNRP kimlikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-128">This combination of P2P ID and Service Location allows multiple PNRP IDs to be registered from a single computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d5ee-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d5ee-129">See Also</span></span>  
 <xref:System.Net.PeerToPeer.PeerName>  
 <xref:System.Net.PeerToPeer>
