---
title: WCF veri hizmetleri tanımlama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 569f2e16cca7ec6dbfbe83cce5a597be37bce8e0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="eb91c-102">WCF veri hizmetleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="eb91c-102">Defining WCF Data Services</span></span>
<span data-ttu-id="eb91c-103">Bu bölümde oluşturmak ve yapılandırmak açıklar [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] verileri olarak kullanıma sunmak için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="eb91c-103">This section describes how to create and configure [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="eb91c-104">Veri Hizmeti oluşturmak için gereken temel adımlar hakkında daha fazla bilgi için bkz: [verilerinizi gösterme hizmet olarak](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="eb91c-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb91c-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="eb91c-105">In This Section</span></span>  
 [<span data-ttu-id="eb91c-106">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eb91c-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="eb91c-107">Tarafından sağlanan veri hizmeti yapılandırma seçenekleri açıklanmaktadır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb91c-107">Describes the data service configuration options provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="eb91c-108">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="eb91c-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 <span data-ttu-id="eb91c-109">Veri Hizmeti olarak verilerin açığa için sağlayıcı modellerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb91c-109">Describes the provider models for exposing data as a data service.</span></span>  
  
 [<span data-ttu-id="eb91c-110">Hizmet İşlemleri</span><span class="sxs-lookup"><span data-stu-id="eb91c-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)  
 <span data-ttu-id="eb91c-111">Sunucu üzerindeki yöntemleri kullanıma hizmet işlemleri tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb91c-111">Describes how to define service operations that expose methods on the server.</span></span>  
  
 [<span data-ttu-id="eb91c-112">Akış Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="eb91c-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)  
 <span data-ttu-id="eb91c-113">Veri akışı öğelerinde ve veri hizmeti sağlayıcısı tarafından tanımlanan veri modelindeki varlıklar arasında bir eşleme oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb91c-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>  
  
 [<span data-ttu-id="eb91c-114">Durdurucular</span><span class="sxs-lookup"><span data-stu-id="eb91c-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)  
 <span data-ttu-id="eb91c-115">Veri Hizmeti isteklerinde özel iş mantığı gerçekleştirmek için dinleyiciyi yöntemleri tanımlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb91c-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>  
  
 [<span data-ttu-id="eb91c-116">WCF Veri Hizmetleri Geliştirme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="eb91c-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 <span data-ttu-id="eb91c-117">Geliştirmek ve Visual Studio kullanarak bir veri hizmeti dağıtmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb91c-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>  
  
 [<span data-ttu-id="eb91c-118">WCF Veri Hizmetlerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="eb91c-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 <span data-ttu-id="eb91c-119">Kimlik doğrulama ve yetkilendirme için veri hizmeti ve diğer güvenlik konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb91c-119">Describes authentication and authorization for the data service and other security considerations.</span></span>  
  
 [<span data-ttu-id="eb91c-120">Veri Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="eb91c-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="eb91c-121">Veri Hizmeti için bir konak seçin açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb91c-121">Describes how to select a host for your data service.</span></span>  
  
 [<span data-ttu-id="eb91c-122">Veri Hizmeti Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb91c-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)  
 <span data-ttu-id="eb91c-123">Farklı sürümleri ile çalışmak açıklar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb91c-123">Describes how to work with different versions of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span>  
  
 [<span data-ttu-id="eb91c-124">WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="eb91c-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)  
 <span data-ttu-id="eb91c-125">İsteğe bağlı işlevlerini açıklar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] WCF Veri Hizmetleri tarafından şu anda uygulanmadı protokolü.</span><span class="sxs-lookup"><span data-stu-id="eb91c-125">Describes optional functionalities of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol that are not currently implemented by WCF Data Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb91c-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb91c-126">See Also</span></span>  
 [<span data-ttu-id="eb91c-127">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="eb91c-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="eb91c-128">Veri Hizmeti Kaynaklarına Erişme</span><span class="sxs-lookup"><span data-stu-id="eb91c-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [<span data-ttu-id="eb91c-129">Başlarken</span><span class="sxs-lookup"><span data-stu-id="eb91c-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
