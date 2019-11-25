---
title: WCF Veri Hizmetlerini Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: 26cfee95f7cd3b956ff263d90b713e9d70b98202
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975326"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="c6994-102">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="c6994-102">Defining WCF Data Services</span></span>

<span data-ttu-id="c6994-103">Bu bölümde, verileri bir açık veri Protokolü (OData) akışı olarak göstermek için WCF Veri Hizmetleri oluşturma ve yapılandırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6994-103">This section describes how to create and configure WCF Data Services to expose data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="c6994-104">Veri hizmeti oluşturmak için gereken temel adımlar hakkında daha fazla bilgi için bkz. [verilerinizi hizmet olarak gösterme](exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c6994-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c6994-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c6994-105">In This Section</span></span>

 [<span data-ttu-id="c6994-106">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c6994-106">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="c6994-107">WCF Veri Hizmetleri tarafından sunulan veri hizmeti yapılandırma seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6994-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="c6994-108">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="c6994-108">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)

 <span data-ttu-id="c6994-109">Veri hizmeti olarak verileri açığa çıkarmak için sağlayıcı modellerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6994-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="c6994-110">Hizmet İşlemleri</span><span class="sxs-lookup"><span data-stu-id="c6994-110">Service Operations</span></span>](service-operations-wcf-data-services.md)

 <span data-ttu-id="c6994-111">Sunucuda Yöntemler sunan hizmet işlemlerinin nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6994-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="c6994-112">Akış Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c6994-112">Feed Customization</span></span>](feed-customization-wcf-data-services.md)

 <span data-ttu-id="c6994-113">Veri akışında veri hizmeti sağlayıcısı ve öğeleri tarafından tanımlanan veri modelindeki varlıklar arasında bir eşlemenin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6994-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="c6994-114">Durdurucular</span><span class="sxs-lookup"><span data-stu-id="c6994-114">Interceptors</span></span>](interceptors-wcf-data-services.md)

 <span data-ttu-id="c6994-115">Veri hizmetine yönelik isteklerde özel iş mantığı gerçekleştirmek için dinleyici oluşturma yöntemlerinin nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6994-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="c6994-116">WCF Veri Hizmetleri Geliştirme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="c6994-116">Developing and Deploying WCF Data Services</span></span>](developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="c6994-117">Visual Studio kullanarak bir veri hizmetinin nasıl geliştirileceği ve dağıtılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6994-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="c6994-118">WCF Veri Hizmetlerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="c6994-118">Securing WCF Data Services</span></span>](securing-wcf-data-services.md)

 <span data-ttu-id="c6994-119">Veri hizmeti için kimlik doğrulaması ve yetkilendirmeyi ve diğer güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6994-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="c6994-120">Veri Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="c6994-120">Hosting the Data Service</span></span>](hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="c6994-121">Veri hizmetiniz için bir konak seçme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6994-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="c6994-122">Veri Hizmeti Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6994-122">Data Service Versioning</span></span>](data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="c6994-123">OData 'in farklı sürümleriyle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6994-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="c6994-124">WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="c6994-124">WCF Data Services Protocol Implementation Details</span></span>](wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="c6994-125">WCF Veri Hizmetleri tarafından şu anda uygulanmayan OData protokolünün isteğe bağlı işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6994-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6994-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6994-126">See also</span></span>

- [<span data-ttu-id="c6994-127">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c6994-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="c6994-128">Veri Hizmeti Kaynaklarına Erişme</span><span class="sxs-lookup"><span data-stu-id="c6994-128">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="c6994-129">Başlarken</span><span class="sxs-lookup"><span data-stu-id="c6994-129">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
