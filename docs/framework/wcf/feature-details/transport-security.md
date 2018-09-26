---
title: Taşıma Güvenliği
ms.date: 03/30/2017
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
author: BrucePerlerMS
ms.openlocfilehash: 7a52ac584abe766a7517436e697aff89333c9833
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171432"
---
# <a name="transport-security"></a><span data-ttu-id="c08f7-102">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c08f7-102">Transport Security</span></span>
<span data-ttu-id="c08f7-103">Seçili bağlamadaki aktarım güvenliği Windows Communication Foundation (WCF) bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c08f7-103">Transport security in Windows Communication Foundation (WCF) depends on the binding selected.</span></span> <span data-ttu-id="c08f7-104">Bağlama uygulayan aktarım gerçek güvenlik mekanizması belirler.</span><span class="sxs-lookup"><span data-stu-id="c08f7-104">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="c08f7-105">Bu bölümdeki konularda, uygulanan mekanizmaları ve seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c08f7-105">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c08f7-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c08f7-106">In This Section</span></span>  
 [<span data-ttu-id="c08f7-107">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c08f7-107">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="c08f7-108">Wcf'de aktarım güvenliği ile ilgili temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="c08f7-108">Explains the basics of transport security in WCF.</span></span>  
  
 [<span data-ttu-id="c08f7-109">HTTP Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c08f7-109">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)  
 <span data-ttu-id="c08f7-110">WCF Güvenli Yuva Katmanı (SSL veya HTTPS) nasıl uyguladığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c08f7-110">Explains how WCF implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="c08f7-111">HTTP Kimlik Doğrulamasını Anlama</span><span class="sxs-lookup"><span data-stu-id="c08f7-111">Understanding HTTP Authentication</span></span>](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)  
 <span data-ttu-id="c08f7-112">Temel, Özet, NT LAN Manager (NTLM) ve diğerleri gibi HTTP kimlik doğrulaması düzenlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c08f7-112">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="c08f7-113">Aktarım Güvenliği ile Kimliğe Bürünme Kullanma</span><span class="sxs-lookup"><span data-stu-id="c08f7-113">Using Impersonation with Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 <span data-ttu-id="c08f7-114">Kimliğe bürünme transport güvenlik modunu ile mümkün olan beş düzeyleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c08f7-114">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="c08f7-115">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c08f7-115">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="c08f7-116">Bir bağlantı noktası için SSL (taşıma) güvenlik X.509 sertifikası ile bir makinede yapılandırma temelleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c08f7-116">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c08f7-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c08f7-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="c08f7-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c08f7-118">Related Sections</span></span>  
 [<span data-ttu-id="c08f7-119">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c08f7-119">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="c08f7-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c08f7-120">See Also</span></span>  
 [<span data-ttu-id="c08f7-121">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="c08f7-121">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
