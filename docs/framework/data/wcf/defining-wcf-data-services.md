---
title: WCF Veri Hizmetlerini Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: ac75f5fd91f68d9403dc7b42325bf8970f0c6794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765654"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="67e2d-102">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="67e2d-102">Defining WCF Data Services</span></span>

<span data-ttu-id="67e2d-103">Bu bölümde verileri olarak kullanıma sunmak için WCF veri hizmetlerini oluşturup yapılandırın açıklar bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="67e2d-103">This section describes how to create and configure WCF Data Services to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="67e2d-104">Bir veri hizmeti oluşturmak için gerekli temel adımlar hakkında daha fazla bilgi için bkz. [verilerinizi hizmet olarak kullanıma sunma](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="67e2d-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="67e2d-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="67e2d-105">In This Section</span></span>

 [<span data-ttu-id="67e2d-106">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="67e2d-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="67e2d-107">WCF Veri Hizmetleri tarafından sağlanan veri hizmeti yapılandırma seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="67e2d-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="67e2d-108">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="67e2d-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

 <span data-ttu-id="67e2d-109">Verileri bir veri hizmeti olarak kullanıma sunmak için sağlayıcı modeli açıklar.</span><span class="sxs-lookup"><span data-stu-id="67e2d-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="67e2d-110">Hizmet İşlemleri</span><span class="sxs-lookup"><span data-stu-id="67e2d-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)

 <span data-ttu-id="67e2d-111">Sunucu üzerinde yöntemleri açığa hizmet işlemleri tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="67e2d-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="67e2d-112">Akış Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="67e2d-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)

 <span data-ttu-id="67e2d-113">Veri akışı öğeleri ve veri hizmeti sağlayıcısı tarafından tanımlanan veri modeli'ndeki varlıkları arasında bir eşleme oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="67e2d-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="67e2d-114">Durdurucular</span><span class="sxs-lookup"><span data-stu-id="67e2d-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)

 <span data-ttu-id="67e2d-115">Veri Hizmeti isteklerinde özel iş mantığını gerçekleştirmek için dinleyiciyi yöntemleri tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="67e2d-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="67e2d-116">WCF Veri Hizmetleri Geliştirme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="67e2d-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="67e2d-117">Geliştirin ve Visual Studio kullanarak bir veri hizmeti dağıtma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="67e2d-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="67e2d-118">WCF Veri Hizmetlerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="67e2d-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)

 <span data-ttu-id="67e2d-119">Kimlik doğrulama ve yetkilendirme için veri hizmeti ve diğer güvenlik konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="67e2d-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="67e2d-120">Veri Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="67e2d-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="67e2d-121">Veri Hizmeti için bir konak seçin açıklar.</span><span class="sxs-lookup"><span data-stu-id="67e2d-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="67e2d-122">Veri Hizmeti Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="67e2d-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="67e2d-123">OData farklı sürümleriyle çalışmaya açıklar.</span><span class="sxs-lookup"><span data-stu-id="67e2d-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="67e2d-124">WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="67e2d-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="67e2d-125">WCF Veri Hizmetleri tarafından şu anda uygulanmaz ve isteğe bağlı işlevler OData protokolü açıklar.</span><span class="sxs-lookup"><span data-stu-id="67e2d-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="67e2d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e2d-126">See also</span></span>

- [<span data-ttu-id="67e2d-127">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="67e2d-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [<span data-ttu-id="67e2d-128">Veri Hizmeti Kaynaklarına Erişme</span><span class="sxs-lookup"><span data-stu-id="67e2d-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="67e2d-129">Başlarken</span><span class="sxs-lookup"><span data-stu-id="67e2d-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
