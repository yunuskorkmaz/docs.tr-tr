---
description: 'Daha fazla bilgi edinin: AJAX Tümleştirme ve JSON desteği'
title: AJAX Tümleştirme ve JSON Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 13e52a3013e9c04f57d6303caf18fd23a41ebf25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643897"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="a040f-103">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="a040f-103">AJAX Integration and JSON Support</span></span>

<span data-ttu-id="a040f-104">ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) ve JavaScript Nesne Gösterimi (JSON) veri biçimi için Windows Communication Foundation (WCF) desteği, WCF hizmetlerinin işlemleri AJAX istemcilerine kullanıma sunmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a040f-104">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="a040f-105">AJAX istemcileri, JavaScript kodu çalıştıran ve HTTP isteklerini kullanarak bu WCF hizmetlerine erişen web sayfalarıdır.</span><span class="sxs-lookup"><span data-stu-id="a040f-105">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="a040f-106">Bu bölümdeki konularda, bu destek ve nasıl uygulanacağı hakkında bilgi sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a040f-106">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="a040f-107">ASP.NET AJAX ve ASP.NET 2,0 ile tümleştirmesi hakkında daha fazla bilgi için bkz. [ASP.NET AJAX 'e genel bakış](/previous-versions/aspnet/bb398874(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a040f-107">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](/previous-versions/aspnet/bb398874(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a040f-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a040f-108">In This Section</span></span>  

 [<span data-ttu-id="a040f-109">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a040f-109">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="a040f-110">Yapılandırma aracılığıyla uygun AJAX uç noktasını ekleyerek veya AJAX uç noktasını otomatik olarak yapılandıran bir hizmet konağı oluşturmak üzere özelleştirilmiş bir hizmet ana bilgisayarı fabrikası kullanarak, bir WCF hizmetinin AJAX istemcilerine nasıl sunulanamayacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a040f-110">Describes how a WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="a040f-111">ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a040f-111">Creating WCF AJAX Services without ASP.NET</span></span>](creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="a040f-112">ASP.NET kullanmadan bir WCF hizmeti oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a040f-112">Describes how to create a WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="a040f-113">JSON ve Diğer Veri Aktarma Biçimleri için Destek</span><span class="sxs-lookup"><span data-stu-id="a040f-113">Support for JSON and Other Data Transfer Formats</span></span>](support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="a040f-114">ASP.NET AJAX hizmetleriyle mesajlaşma için genellikle kullanılan JSON biçiminin (XML yerine) desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a040f-114">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="a040f-115">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="a040f-115">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="a040f-116">AJAX özellikli bir ASP.NET Web hizmetinin bir WCF Web hizmetine nasıl geçirileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a040f-116">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a040f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a040f-117">See also</span></span>

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="a040f-118">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="a040f-118">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
