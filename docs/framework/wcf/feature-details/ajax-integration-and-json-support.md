---
title: "AJAX Tümleştirme ve JSON Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd5c84250349f4adaaac68a302d771280328a4e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="df18b-102">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="df18b-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="df18b-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) ve JavaScript nesne gösterimi (JSON) veri biçimi izin vermek için destek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX istemcilere işlemlerinin açığa Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="df18b-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span> <span data-ttu-id="df18b-104">AJAX istemcileridir Web JavaScript kodunu çalıştıran ve bunlara erişme sayfaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP isteklerini kullanarak hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="df18b-104">AJAX clients are Web pages running JavaScript code and accessing these [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using HTTP requests.</span></span> <span data-ttu-id="df18b-105">Bu bölümdeki konular, bunu gerçekleştirme ve bu destek hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="df18b-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="df18b-106">Bkz: ASP.NET AJAX ve ASP.NET 2.0 ile kendi tümleştirme [ASP.NET AJAX genel bakış](http://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="df18b-106"> ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df18b-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="df18b-107">In This Section</span></span>  
 [<span data-ttu-id="df18b-108">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="df18b-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="df18b-109">Açıklar nasıl bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet ortaya AJAX istemcilere hizmet ana bilgisayar üreteci kullanarak veya yapılandırma aracılığıyla özelleştirilmiş AJAX uç noktası otomatik olarak yapılandırır hizmet ana bilgisayarını oluşturmak için uygun AJAX uç noktası ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="df18b-109">Describes how an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="df18b-110">ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="df18b-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="df18b-111">Nasıl oluşturulacağını açıklar bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET kullanmadan hizmet.</span><span class="sxs-lookup"><span data-stu-id="df18b-111">Describes how to create an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="df18b-112">JSON ve Diğer Veri Aktarma Biçimleri için Destek</span><span class="sxs-lookup"><span data-stu-id="df18b-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="df18b-113">ASP.NET AJAX Hizmetleri ile ileti için genellikle kullanılan (XML yerine) JSON biçimine desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="df18b-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="df18b-114">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="df18b-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="df18b-115">Bir AJAX etkinleştirilmiş ASP.NET Web Service'e geçirme açıklanmaktadır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web hizmeti.</span><span class="sxs-lookup"><span data-stu-id="df18b-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df18b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df18b-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="df18b-117">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="df18b-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
