---
title: Taşıma Güvenliği
description: Bu başvuruları, WFC 'deki aktarım güvenliği mekanizmalarını, nasıl uygulandığını ve bunların seçeneklerini anlamak için kullanın.
ms.date: 03/30/2017
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
ms.openlocfilehash: cecb1ec263d993e9d669d73245fad1a49fe041fd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251717"
---
# <a name="transport-security"></a><span data-ttu-id="10da8-103">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="10da8-103">Transport Security</span></span>

<span data-ttu-id="10da8-104">Windows Communication Foundation (WCF) içindeki taşıma güvenliği, seçilen bağlamaya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="10da8-104">Transport security in Windows Communication Foundation (WCF) depends on the binding selected.</span></span> <span data-ttu-id="10da8-105">Bağlamanın uyguladığı aktarım, gerçek güvenlik mekanizmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="10da8-105">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="10da8-106">Bu bölümdeki konularda, uygulanan mekanizmalar ve bunların seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10da8-106">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10da8-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="10da8-107">In This Section</span></span>  

 [<span data-ttu-id="10da8-108">Taşıma Güvenliği Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="10da8-108">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="10da8-109">WCF 'de aktarım güvenliği esaslarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="10da8-109">Explains the basics of transport security in WCF.</span></span>  
  
 [<span data-ttu-id="10da8-110">HTTP Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="10da8-110">HTTP Transport Security</span></span>](http-transport-security.md)  
 <span data-ttu-id="10da8-111">WCF 'nin Güvenli Yuva Katmanı (SSL veya HTTPS) nasıl uyguladığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10da8-111">Explains how WCF implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="10da8-112">HTTP Kimlik Doğrulamasını Anlama</span><span class="sxs-lookup"><span data-stu-id="10da8-112">Understanding HTTP Authentication</span></span>](understanding-http-authentication.md)  
 <span data-ttu-id="10da8-113">Temel, Özet, NT LAN Manager (NTLM) ve diğerleri gibi HTTP kimlik doğrulama düzenlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="10da8-113">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="10da8-114">Taşıma Güvenliği ile Kimliğe Bürünme Kullanma</span><span class="sxs-lookup"><span data-stu-id="10da8-114">Using Impersonation with Transport Security</span></span>](using-impersonation-with-transport-security.md)  
 <span data-ttu-id="10da8-115">Aktarım güvenliği moduyla mümkün olan beş kimliğe bürünme düzeyini açıklar.</span><span class="sxs-lookup"><span data-stu-id="10da8-115">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="10da8-116">Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="10da8-116">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="10da8-117">SSL için X. 509.440 sertifikası (aktarım) güvenliği olan bir makinede bağlantı noktası yapılandırma temellerini adım adım açıklar.</span><span class="sxs-lookup"><span data-stu-id="10da8-117">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="10da8-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="10da8-118">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="10da8-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="10da8-119">Related Sections</span></span>  

 [<span data-ttu-id="10da8-120">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="10da8-120">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="10da8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10da8-121">See also</span></span>

- [<span data-ttu-id="10da8-122">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="10da8-122">Programming WCF Security</span></span>](programming-wcf-security.md)
