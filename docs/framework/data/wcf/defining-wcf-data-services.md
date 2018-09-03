---
title: WCF veri hizmetlerini tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: c0c9010a71877d2c9757a2c9cf2d5c1fec8aedf7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481276"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="30925-102">WCF veri hizmetlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="30925-102">Defining WCF Data Services</span></span>

<span data-ttu-id="30925-103">Bu bölümde verileri olarak kullanıma sunmak için WCF veri hizmetlerini oluşturup yapılandırın açıklar bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="30925-103">This section describes how to create and configure WCF Data Services to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="30925-104">Bir veri hizmeti oluşturmak için gerekli temel adımlar hakkında daha fazla bilgi için bkz. [verilerinizi hizmet olarak kullanıma sunma](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="30925-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="30925-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="30925-105">In This Section</span></span>

 [<span data-ttu-id="30925-106">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="30925-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="30925-107">WCF Veri Hizmetleri tarafından sağlanan veri hizmeti yapılandırma seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="30925-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="30925-108">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="30925-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

 <span data-ttu-id="30925-109">Verileri bir veri hizmeti olarak kullanıma sunmak için sağlayıcı modeli açıklar.</span><span class="sxs-lookup"><span data-stu-id="30925-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="30925-110">Hizmet İşlemleri</span><span class="sxs-lookup"><span data-stu-id="30925-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)

 <span data-ttu-id="30925-111">Sunucu üzerinde yöntemleri açığa hizmet işlemleri tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="30925-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="30925-112">Akış Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="30925-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)

 <span data-ttu-id="30925-113">Veri akışı öğeleri ve veri hizmeti sağlayıcısı tarafından tanımlanan veri modeli'ndeki varlıkları arasında bir eşleme oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="30925-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="30925-114">Durdurucular</span><span class="sxs-lookup"><span data-stu-id="30925-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)

 <span data-ttu-id="30925-115">Veri Hizmeti isteklerinde özel iş mantığını gerçekleştirmek için dinleyiciyi yöntemleri tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="30925-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="30925-116">WCF Veri Hizmetleri Geliştirme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="30925-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="30925-117">Geliştirin ve Visual Studio kullanarak bir veri hizmeti dağıtma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="30925-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="30925-118">WCF Veri Hizmetlerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="30925-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)

 <span data-ttu-id="30925-119">Kimlik doğrulama ve yetkilendirme için veri hizmeti ve diğer güvenlik konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30925-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="30925-120">Veri Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="30925-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="30925-121">Veri Hizmeti için bir konak seçin açıklar.</span><span class="sxs-lookup"><span data-stu-id="30925-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="30925-122">Veri Hizmeti Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="30925-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="30925-123">OData farklı sürümleriyle çalışmaya açıklar.</span><span class="sxs-lookup"><span data-stu-id="30925-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="30925-124">WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="30925-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="30925-125">WCF Veri Hizmetleri tarafından şu anda uygulanmaz ve isteğe bağlı işlevler OData protokolü açıklar.</span><span class="sxs-lookup"><span data-stu-id="30925-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="30925-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30925-126">See Also</span></span>

- [<span data-ttu-id="30925-127">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="30925-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [<span data-ttu-id="30925-128">Veri Hizmeti Kaynaklarına Erişme</span><span class="sxs-lookup"><span data-stu-id="30925-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="30925-129">Başlarken</span><span class="sxs-lookup"><span data-stu-id="30925-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
