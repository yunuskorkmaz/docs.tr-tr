---
title: AJAX Tümleştirme ve JSON Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: bcf1cab9386d9d9503af6258c1bb39f8744c073b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638905"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="4925d-102">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="4925d-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="4925d-103">ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) için Windows Communication Foundation (WCF) desteği ve JavaScript nesne gösterimi (JSON) veri biçimi operations AJAX istemcilerine kullanıma sunmak WCF hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4925d-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="4925d-104">AJAX Web JavaScript kodu çalıştıran ve HTTP isteklerini kullanarak bu WCF hizmetlerine erişme sayfaları istemcileridir.</span><span class="sxs-lookup"><span data-stu-id="4925d-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="4925d-105">Bu bölümdeki konular, nasıl ve bu destek hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4925d-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="4925d-106">ASP.NET 2.0 ile tümleştirmesi ve ASP.NET AJAX hakkında daha fazla bilgi [ASP.NET AJAX genel bakış](https://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="4925d-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4925d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4925d-107">In This Section</span></span>  
 [<span data-ttu-id="4925d-108">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4925d-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="4925d-109">Nasıl bir WCF Hizmeti AJAX istemcilerine uygun AJAX uç noktası ya da yapılandırma yoluyla ekleyerek veya AJAX uç noktası otomatik olarak yapılandırır bir hizmet konağı oluşturmak için özelleştirilmiş bir hizmet barındırma ortamı fabrikası kullanarak kullanıma sunulabilecek açıklar.</span><span class="sxs-lookup"><span data-stu-id="4925d-109">Describes how an WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="4925d-110">ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4925d-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="4925d-111">Bir WCF hizmetini ASP.NET kullanmadan oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="4925d-111">Describes how to create an WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="4925d-112">JSON ve Diğer Veri Aktarma Biçimleri için Destek</span><span class="sxs-lookup"><span data-stu-id="4925d-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="4925d-113">ASP.NET AJAX hizmetleriyle Mesajlaşma için genellikle kullanılan (XML yerine) JSON biçimine desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4925d-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="4925d-114">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="4925d-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="4925d-115">Bir WCF Web hizmeti için bir AJAX etkinleştirilmiş ASP.NET Web hizmeti geçişi işlemi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4925d-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4925d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4925d-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="4925d-117">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="4925d-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
