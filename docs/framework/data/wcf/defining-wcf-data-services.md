---
title: "WCF veri hizmetleri tanımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 888f0af14e31c432cd4ad737232a22ed6f079a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="fbf60-102">WCF veri hizmetleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="fbf60-102">Defining WCF Data Services</span></span>
<span data-ttu-id="fbf60-103">Bu bölümde oluşturmak ve yapılandırmak açıklar [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] verileri olarak kullanıma sunmak için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="fbf60-103">This section describes how to create and configure [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fbf60-104">bir veri hizmeti oluşturmak için gereken temel adımlarda bkz [verilerinizi gösterme hizmet olarak](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="fbf60-104"> the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fbf60-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fbf60-105">In This Section</span></span>  
 [<span data-ttu-id="fbf60-106">Veri Hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fbf60-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="fbf60-107">Tarafından sağlanan veri hizmeti yapılandırma seçenekleri açıklanmaktadır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbf60-107">Describes the data service configuration options provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="fbf60-108">Veri Hizmetleri sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="fbf60-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 <span data-ttu-id="fbf60-109">Veri Hizmeti olarak verilerin açığa için sağlayıcı modellerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fbf60-109">Describes the provider models for exposing data as a data service.</span></span>  
  
 [<span data-ttu-id="fbf60-110">Hizmet işlemleri</span><span class="sxs-lookup"><span data-stu-id="fbf60-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)  
 <span data-ttu-id="fbf60-111">Sunucu üzerindeki yöntemleri kullanıma hizmet işlemleri tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="fbf60-111">Describes how to define service operations that expose methods on the server.</span></span>  
  
 [<span data-ttu-id="fbf60-112">Akış özelleştirme</span><span class="sxs-lookup"><span data-stu-id="fbf60-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)  
 <span data-ttu-id="fbf60-113">Veri akışı öğelerinde ve veri hizmeti sağlayıcısı tarafından tanımlanan veri modelindeki varlıklar arasında bir eşleme oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="fbf60-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>  
  
 [<span data-ttu-id="fbf60-114">Dinleyiciler</span><span class="sxs-lookup"><span data-stu-id="fbf60-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)  
 <span data-ttu-id="fbf60-115">Veri Hizmeti isteklerinde özel iş mantığı gerçekleştirmek için dinleyiciyi yöntemleri tanımlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="fbf60-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>  
  
 [<span data-ttu-id="fbf60-116">Geliştirme ve WCF Veri Hizmetleri dağıtma</span><span class="sxs-lookup"><span data-stu-id="fbf60-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 <span data-ttu-id="fbf60-117">Geliştirmek ve Visual Studio kullanarak bir veri hizmeti dağıtmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="fbf60-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>  
  
 [<span data-ttu-id="fbf60-118">WCF Veri Hizmetleri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="fbf60-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 <span data-ttu-id="fbf60-119">Kimlik doğrulama ve yetkilendirme için veri hizmeti ve diğer güvenlik konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fbf60-119">Describes authentication and authorization for the data service and other security considerations.</span></span>  
  
 [<span data-ttu-id="fbf60-120">Veri Hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="fbf60-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="fbf60-121">Veri Hizmeti için bir konak seçin açıklar.</span><span class="sxs-lookup"><span data-stu-id="fbf60-121">Describes how to select a host for your data service.</span></span>  
  
 [<span data-ttu-id="fbf60-122">Veri Hizmeti sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="fbf60-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)  
 <span data-ttu-id="fbf60-123">Farklı sürümleri ile çalışmak açıklar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbf60-123">Describes how to work with different versions of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span>  
  
 [<span data-ttu-id="fbf60-124">Protokol uygulama ayrıntılarını WCF Veri Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="fbf60-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)  
 <span data-ttu-id="fbf60-125">İsteğe bağlı işlevlerini açıklar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] WCF Veri Hizmetleri tarafından şu anda uygulanmadı protokolü.</span><span class="sxs-lookup"><span data-stu-id="fbf60-125">Describes optional functionalities of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol that are not currently implemented by WCF Data Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf60-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbf60-126">See Also</span></span>  
 [<span data-ttu-id="fbf60-127">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="fbf60-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="fbf60-128">Veri Hizmeti kaynaklara erişmeyi</span><span class="sxs-lookup"><span data-stu-id="fbf60-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [<span data-ttu-id="fbf60-129">Başlarken</span><span class="sxs-lookup"><span data-stu-id="fbf60-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
