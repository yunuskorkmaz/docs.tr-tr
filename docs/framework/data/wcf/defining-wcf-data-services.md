---
description: 'Hakkında daha fazla bilgi edinin: WCF Veri Hizmetleri tanımlama'
title: WCF Veri Hizmetlerini Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: 43a4887226b03e80c4a966a118f210fe8a28000d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766094"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="6a665-103">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="6a665-103">Defining WCF Data Services</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="6a665-104">Bu bölümde, verileri bir açık veri Protokolü (OData) akışı olarak göstermek için WCF Veri Hizmetleri oluşturma ve yapılandırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a665-104">This section describes how to create and configure WCF Data Services to expose data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="6a665-105">Veri hizmeti oluşturmak için gereken temel adımlar hakkında daha fazla bilgi için bkz. [verilerinizi hizmet olarak gösterme](exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a665-105">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6a665-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6a665-106">In This Section</span></span>

 [<span data-ttu-id="6a665-107">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6a665-107">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="6a665-108">WCF Veri Hizmetleri tarafından sunulan veri hizmeti yapılandırma seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6a665-108">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="6a665-109">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="6a665-109">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)

 <span data-ttu-id="6a665-110">Veri hizmeti olarak verileri açığa çıkarmak için sağlayıcı modellerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6a665-110">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="6a665-111">Hizmet İşlemleri</span><span class="sxs-lookup"><span data-stu-id="6a665-111">Service Operations</span></span>](service-operations-wcf-data-services.md)

 <span data-ttu-id="6a665-112">Sunucuda Yöntemler sunan hizmet işlemlerinin nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6a665-112">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="6a665-113">Akış Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6a665-113">Feed Customization</span></span>](feed-customization-wcf-data-services.md)

 <span data-ttu-id="6a665-114">Veri akışında veri hizmeti sağlayıcısı ve öğeleri tarafından tanımlanan veri modelindeki varlıklar arasında bir eşlemenin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="6a665-114">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="6a665-115">Durdurucular</span><span class="sxs-lookup"><span data-stu-id="6a665-115">Interceptors</span></span>](interceptors-wcf-data-services.md)

 <span data-ttu-id="6a665-116">Veri hizmetine yönelik isteklerde özel iş mantığı gerçekleştirmek için dinleyici oluşturma yöntemlerinin nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6a665-116">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="6a665-117">WCF Veri Hizmetleri Geliştirme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="6a665-117">Developing and Deploying WCF Data Services</span></span>](developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="6a665-118">Visual Studio kullanarak bir veri hizmetinin nasıl geliştirileceği ve dağıtılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a665-118">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="6a665-119">WCF Veri Hizmetlerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="6a665-119">Securing WCF Data Services</span></span>](securing-wcf-data-services.md)

 <span data-ttu-id="6a665-120">Veri hizmeti için kimlik doğrulaması ve yetkilendirmeyi ve diğer güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6a665-120">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="6a665-121">Veri Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="6a665-121">Hosting the Data Service</span></span>](hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="6a665-122">Veri hizmetiniz için bir konak seçme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6a665-122">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="6a665-123">Veri Hizmeti Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6a665-123">Data Service Versioning</span></span>](data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="6a665-124">OData 'in farklı sürümleriyle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="6a665-124">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="6a665-125">WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="6a665-125">WCF Data Services Protocol Implementation Details</span></span>](wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="6a665-126">WCF Veri Hizmetleri tarafından şu anda uygulanmayan OData protokolünün isteğe bağlı işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6a665-126">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a665-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a665-127">See also</span></span>

- [<span data-ttu-id="6a665-128">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6a665-128">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="6a665-129">Veri Hizmeti Kaynaklarına Erişme</span><span class="sxs-lookup"><span data-stu-id="6a665-129">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="6a665-130">Başlarken</span><span class="sxs-lookup"><span data-stu-id="6a665-130">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
