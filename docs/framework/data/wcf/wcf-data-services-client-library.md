---
title: WCF Veri Hizmetleri İstemci Kitaplığı
description: WCF Veri Hizmetleri istemci kitaplıklarını kullanarak .NET Framework istemci uygulamasına erişme ve verileri değiştirme hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 3d8a0f869454ce24d847127c2097239886f3395b
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805668"
---
# <a name="wcf-data-services-client-library"></a><span data-ttu-id="04b2a-103">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="04b2a-103">WCF Data Services Client Library</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="04b2a-104">Bir HTTP isteği gönderebileceği ve bir veri hizmetinin döndürdüğü OData akışını işlebiliyorsanız, herhangi bir uygulama açık veri Protokolü (OData) tabanlı bir veri hizmeti ile etkileşime geçebilir.</span><span class="sxs-lookup"><span data-stu-id="04b2a-104">Any application can interact with an Open Data Protocol (OData)-based data service if it can send an HTTP request and process the OData feed that a data service returns.</span></span> <span data-ttu-id="04b2a-105">Bu birlikte çalışabilirlik, çok çeşitli web özellikli uygulamalardan OData tabanlı hizmetlere erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-105">This interoperability enables you to access OData-based services from a broad range of Web-enabled applications.</span></span> <span data-ttu-id="04b2a-106">WCF Veri Hizmetleri, .NET Framework veya Silverlight tabanlı uygulamalardan OData akışlarını kullanırken daha zengin bir programlama deneyimi sağlayan istemci kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="04b2a-106">WCF Data Services includes client libraries that provide a richer programming experience when you consume OData feeds from .NET Framework or Silverlight-based applications.</span></span>  
  
 <span data-ttu-id="04b2a-107">İstemci kitaplığının iki ana sınıfı <xref:System.Data.Services.Client.DataServiceContext> sınıfı ve <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="04b2a-107">The two main classes of the client library are the <xref:System.Data.Services.Client.DataServiceContext> class and the <xref:System.Data.Services.Client.DataServiceQuery%601> class.</span></span> <span data-ttu-id="04b2a-108"><xref:System.Data.Services.Client.DataServiceContext>Sınıfı, belirtilen bir veri hizmetine göre desteklenen işlemleri kapsüller.</span><span class="sxs-lookup"><span data-stu-id="04b2a-108">The <xref:System.Data.Services.Client.DataServiceContext> class encapsulates operations that are supported against a specified data service.</span></span> <span data-ttu-id="04b2a-109">OData Hizmetleri durum bilgisiz olmasına karşın bağlam değildir.</span><span class="sxs-lookup"><span data-stu-id="04b2a-109">Although OData services are stateless, the context is not.</span></span> <span data-ttu-id="04b2a-110">Bu nedenle, <xref:System.Data.Services.Client.DataServiceContext> değişiklik yönetimi gibi özellikleri desteklemek için veri hizmeti ile etkileşimler arasında istemcideki durumu korumak için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04b2a-110">Therefore, you can use the <xref:System.Data.Services.Client.DataServiceContext> class to maintain state on the client between interactions with the data service in order to support features such as change management.</span></span> <span data-ttu-id="04b2a-111">Bu sınıf Ayrıca kimlikleri yönetir ve değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="04b2a-111">This class also manages identities and tracks changes.</span></span> <span data-ttu-id="04b2a-112"><xref:System.Data.Services.Client.DataServiceQuery%601>Sınıfı, belirli bir varlık kümesine karşı bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="04b2a-112">The <xref:System.Data.Services.Client.DataServiceQuery%601> class represents a query against a specific entity set.</span></span>  
  
 <span data-ttu-id="04b2a-113">Bu bölümde, istemci kitaplıklarının bir .NET Framework istemci uygulamasına erişmek ve verileri değiştirmek için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="04b2a-113">This section describes how to use client libraries to access and change data from a .NET Framework client application.</span></span> <span data-ttu-id="04b2a-114">WCF Veri Hizmetleri istemci kitaplığını Silverlight tabanlı bir uygulamayla kullanma hakkında daha fazla bilgi için, bkz. [WCF veri Hizmetleri (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).</span><span class="sxs-lookup"><span data-stu-id="04b2a-114">For more information about how to use the WCF Data Services client library with a Silverlight-based application, see [WCF Data Services (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).</span></span> <span data-ttu-id="04b2a-115">Diğer istemci kitaplıkları, bir OData akışını diğer türlerde uygulamalarda kullanmanıza olanak sağlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04b2a-115">Other client libraries are available that enable you to consume an OData feed in other kinds of applications.</span></span> <span data-ttu-id="04b2a-116">OData SDK hakkında daha fazla bilgi için bkz. [OData SDK-örnek kodu](https://www.odata.org/ecosystem/#sdk).</span><span class="sxs-lookup"><span data-stu-id="04b2a-116">For more information on OData SDK, see [OData SDK - Sample Code](https://www.odata.org/ecosystem/#sdk).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="04b2a-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="04b2a-117">In This Section</span></span>  

 [<span data-ttu-id="04b2a-118">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="04b2a-118">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)  
 <span data-ttu-id="04b2a-119">OData akışlarını temel alan istemci kitaplığı ve istemci veri hizmeti sınıflarının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-119">Describes how to generate a client library and client data service classes that are based on OData feeds.</span></span>  
  
 [<span data-ttu-id="04b2a-120">Veri Hizmetini Sorgulama</span><span class="sxs-lookup"><span data-stu-id="04b2a-120">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="04b2a-121">İstemci kitaplıklarını kullanarak bir veri hizmetinin .NET Framework tabanlı bir uygulamadan nasıl sorgulanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-121">Describes how to query a data service from a .NET Framework-based application by using client libraries.</span></span>  
  
 [<span data-ttu-id="04b2a-122">Ertelenmiş İçerik Yükleme</span><span class="sxs-lookup"><span data-stu-id="04b2a-122">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)  
 <span data-ttu-id="04b2a-123">İlk sorgu yanıtında bulunmayan ek içeriğin nasıl yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-123">Describes how to load additional content not included in the initial query response.</span></span>  
  
 [<span data-ttu-id="04b2a-124">Veri Hizmetini Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="04b2a-124">Updating the Data Service</span></span>](updating-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="04b2a-125">İstemci kitaplıklarını kullanarak varlıkları ve ilişkileri oluşturma, değiştirme ve silme işlemlerinin nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-125">Describes how to create, modify, and delete entities and relationships by using the client libraries.</span></span>  
  
 [<span data-ttu-id="04b2a-126">Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="04b2a-126">Asynchronous Operations</span></span>](asynchronous-operations-wcf-data-services.md)  
 <span data-ttu-id="04b2a-127">Zaman uyumsuz bir şekilde veri hizmetiyle çalışmak için istemci kitaplıkları tarafından sunulan tesislerin açıklar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-127">Describes the facilities provided by the client libraries for working with a data service in an asynchronous manner.</span></span>  
  
 [<span data-ttu-id="04b2a-128">Toplu İşlemler</span><span class="sxs-lookup"><span data-stu-id="04b2a-128">Batching Operations</span></span>](batching-operations-wcf-data-services.md)  
 <span data-ttu-id="04b2a-129">İstemci kitaplıklarını kullanarak tek bir toplu işte veri hizmetine birden çok isteğin nasıl gönderileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-129">Describes how to send multiple requests to the data service in a single batch by using the client libraries.</span></span>  
  
 [<span data-ttu-id="04b2a-130">Veriyi Denetimlere Bağlama</span><span class="sxs-lookup"><span data-stu-id="04b2a-130">Binding Data to Controls</span></span>](binding-data-to-controls-wcf-data-services.md)  
 <span data-ttu-id="04b2a-131">Denetimlerin bir veri hizmeti tarafından döndürülen bir OData akışına nasıl bağlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-131">Describes how to bind controls to a OData feed returned by a data service.</span></span>  
  
 [<span data-ttu-id="04b2a-132">Hizmet İşlemleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="04b2a-132">Calling Service Operations</span></span>](calling-service-operations-wcf-data-services.md)  
 <span data-ttu-id="04b2a-133">Hizmet işlemlerini çağırmak için istemci kitaplığının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-133">Describes how to use the client library to call service operations.</span></span>  
  
 [<span data-ttu-id="04b2a-134">Veri Hizmeti Bağlamını Yönetme</span><span class="sxs-lookup"><span data-stu-id="04b2a-134">Managing the Data Service Context</span></span>](managing-the-data-service-context-wcf-data-services.md)  
 <span data-ttu-id="04b2a-135">İstemci kitaplığı davranışlarını yönetme seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="04b2a-135">Describes options for managing the behavior of the client library.</span></span>  
  
 [<span data-ttu-id="04b2a-136">İkili Verilerle Çalışma</span><span class="sxs-lookup"><span data-stu-id="04b2a-136">Working with Binary Data</span></span>](working-with-binary-data-wcf-data-services.md)  
 <span data-ttu-id="04b2a-137">Veri hizmeti tarafından veri akışı olarak döndürülen ikili verilerin nasıl erişebileceğini ve değiştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="04b2a-137">Describes how to access and change binary data returned by the data service as a data stream.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b2a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04b2a-138">See also</span></span>

- [<span data-ttu-id="04b2a-139">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="04b2a-139">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="04b2a-140">Başlarken</span><span class="sxs-lookup"><span data-stu-id="04b2a-140">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
