---
title: "Taşıma Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 364326e2ded11f7174adc891a5fd9bcdd3c98334
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security"></a><span data-ttu-id="a985c-102">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a985c-102">Transport Security</span></span>
<span data-ttu-id="a985c-103">Taşıma güvenliği [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] seçili bağlama bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a985c-103">Transport security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] depends on the binding selected.</span></span> <span data-ttu-id="a985c-104">Bağlama uygulayan taşıma gerçek güvenlik mekanizması belirler.</span><span class="sxs-lookup"><span data-stu-id="a985c-104">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="a985c-105">Bu bölümdeki konular, uygulanan mekanizmaları ve bunların seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a985c-105">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a985c-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a985c-106">In This Section</span></span>  
 [<span data-ttu-id="a985c-107">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a985c-107">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="a985c-108">Taşıma güvenliği temelleri açıklanır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a985c-108">Explains the basics of transport security in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="a985c-109">HTTP Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a985c-109">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)  
 <span data-ttu-id="a985c-110">Açıklar nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Güvenli Yuva Katmanı (SSL veya HTTPS) uygular.</span><span class="sxs-lookup"><span data-stu-id="a985c-110">Explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="a985c-111">HTTP Kimlik Doğrulamasını Anlama</span><span class="sxs-lookup"><span data-stu-id="a985c-111">Understanding HTTP Authentication</span></span>](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)  
 <span data-ttu-id="a985c-112">Temel, Özet, NT LAN Yöneticisi (NTLM) ve diğerleri gibi HTTP kimlik doğrulama şemasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a985c-112">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="a985c-113">Aktarım Güvenliği ile Kimliğe Bürünme Kullanma</span><span class="sxs-lookup"><span data-stu-id="a985c-113">Using Impersonation with Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 <span data-ttu-id="a985c-114">Aktarım güvenlik modu ile olası beş kimliğe bürünme düzeyini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a985c-114">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="a985c-115">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a985c-115">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="a985c-116">SSL (aktarım) güvenliği için bir X.509 sertifikası ile bir makinede bir bağlantı noktası yapılandırma temellerini anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a985c-116">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a985c-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a985c-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="a985c-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a985c-118">Related Sections</span></span>  
 [<span data-ttu-id="a985c-119">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a985c-119">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="a985c-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a985c-120">See Also</span></span>  
 [<span data-ttu-id="a985c-121">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="a985c-121">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
