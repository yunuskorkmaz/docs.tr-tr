---
title: Taşıma Güvenliği
description: Bu başvuruları, WFC 'deki aktarım güvenliği mekanizmalarını, nasıl uygulandığını ve bunların seçeneklerini anlamak için kullanın.
ms.date: 03/30/2017
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
ms.openlocfilehash: d39aa49906b79b9e12eecf04629080863719f986
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244757"
---
# <a name="transport-security"></a><span data-ttu-id="b0cbe-103">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b0cbe-103">Transport Security</span></span>
<span data-ttu-id="b0cbe-104">Windows Communication Foundation (WCF) içindeki taşıma güvenliği, seçilen bağlamaya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-104">Transport security in Windows Communication Foundation (WCF) depends on the binding selected.</span></span> <span data-ttu-id="b0cbe-105">Bağlamanın uyguladığı aktarım, gerçek güvenlik mekanizmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-105">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="b0cbe-106">Bu bölümdeki konularda, uygulanan mekanizmalar ve bunların seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-106">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0cbe-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b0cbe-107">In This Section</span></span>  
 [<span data-ttu-id="b0cbe-108">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b0cbe-108">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="b0cbe-109">WCF 'de aktarım güvenliği esaslarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-109">Explains the basics of transport security in WCF.</span></span>  
  
 [<span data-ttu-id="b0cbe-110">HTTP Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b0cbe-110">HTTP Transport Security</span></span>](http-transport-security.md)  
 <span data-ttu-id="b0cbe-111">WCF 'nin Güvenli Yuva Katmanı (SSL veya HTTPS) nasıl uyguladığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-111">Explains how WCF implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="b0cbe-112">HTTP Kimlik Doğrulamasını Anlama</span><span class="sxs-lookup"><span data-stu-id="b0cbe-112">Understanding HTTP Authentication</span></span>](understanding-http-authentication.md)  
 <span data-ttu-id="b0cbe-113">Temel, Özet, NT LAN Manager (NTLM) ve diğerleri gibi HTTP kimlik doğrulama düzenlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-113">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="b0cbe-114">Taşıma Güvenliği ile Kimliğe Bürünme Kullanma</span><span class="sxs-lookup"><span data-stu-id="b0cbe-114">Using Impersonation with Transport Security</span></span>](using-impersonation-with-transport-security.md)  
 <span data-ttu-id="b0cbe-115">Aktarım güvenliği moduyla mümkün olan beş kimliğe bürünme düzeyini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-115">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="b0cbe-116">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b0cbe-116">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="b0cbe-117">SSL için X. 509.440 sertifikası (aktarım) güvenliği olan bir makinede bağlantı noktası yapılandırma temellerini adım adım açıklar.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-117">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b0cbe-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b0cbe-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="b0cbe-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b0cbe-119">Related Sections</span></span>  
 [<span data-ttu-id="b0cbe-120">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b0cbe-120">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="b0cbe-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-121">See also</span></span>

- [<span data-ttu-id="b0cbe-122">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="b0cbe-122">Programming WCF Security</span></span>](programming-wcf-security.md)
