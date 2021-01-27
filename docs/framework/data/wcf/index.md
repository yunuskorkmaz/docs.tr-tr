---
title: WCF Veri Hizmetleri 4.5
description: REST semantiğini kullanarak verileri kullanıma sunmak ve kullanmak için hizmetleri destekleyen bir .NET Framework bileşeni olan WCF Veri Hizmetleri hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 2d3da2ca9cd958fc70d3b91362dde71d68dc9d8a
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898768"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="657c5-103">WCF Veri Hizmetleri 4.5</span><span class="sxs-lookup"><span data-stu-id="657c5-103">WCF Data Services 4.5</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

## <a name="overview"></a><span data-ttu-id="657c5-104">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="657c5-104">Overview</span></span>

<span data-ttu-id="657c5-105">WCF Veri Hizmetleri (eskiden "ADO.NET Data Services" olarak bilinirdi), [temsili durum aktarımı (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)semantiğini kullanarak Web veya intranet üzerinden veri sunmak ve kullanmak Için açık veri Protokolü 'Nü (OData) kullanan hizmetler oluşturmanızı sağlayan bir .NET Framework bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="657c5-105">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="657c5-106">OData, verileri URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="657c5-106">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="657c5-107">Al, koy, POST ve DELETE için standart HTTP fiilleri kullanılarak verilere erişilir ve değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="657c5-107">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="657c5-108">OData, kaynakları ilişkilendirmeler ile ilgili varlık kümeleri olarak göstermek için [varlık veri modeli](../adonet/entity-data-model.md) varlık ilişkisi kurallarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="657c5-108">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="657c5-109">WCF Veri Hizmetleri, kaynakları adresleme ve güncelleştirme için OData protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="657c5-109">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="657c5-110">Bu şekilde, bu hizmetlere OData destekleyen herhangi bir istemciden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="657c5-110">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="657c5-111">OData, iyi bilinen aktarım biçimlerini kullanarak kaynaklara istek yapmanızı ve veri yazmanızı sağlar: Atom, verileri XML olarak değiştirme ve güncelleştirme için bir standartlar kümesi ve AJAX uygulamalarında yaygın olarak kullanılan metin tabanlı veri değişim biçimi JavaScript Nesne Gösterimi (JSON).</span><span class="sxs-lookup"><span data-stu-id="657c5-111">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="657c5-112">WCF Veri Hizmetleri, çeşitli kaynaklardan kaynaklanan verileri OData akışları olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="657c5-112">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="657c5-113">Visual Studio Araçları, bir ADO.NET Entity Framework veri modeli kullanarak OData tabanlı bir hizmet oluşturmanızı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="657c5-113">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="657c5-114">Ayrıca, ortak dil çalışma zamanı (CLR) sınıflarını ve hatta geç bağlı veya yazılmamış verileri temel alan OData akışları da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="657c5-114">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="657c5-115">WCF Veri Hizmetleri ayrıca, biri genel .NET Framework istemci uygulamaları ve özel olarak Silverlight tabanlı uygulamalar için başka bir istemci kitaplıkları kümesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="657c5-115">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="657c5-116">Bu istemci kitaplıkları, .NET Framework ve Silverlight gibi ortamlardan bir OData akışına eriştiğinizde nesne tabanlı bir programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="657c5-116">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="657c5-117">Nereden başlamalıyım?</span><span class="sxs-lookup"><span data-stu-id="657c5-117">Where Should I Start?</span></span>

<span data-ttu-id="657c5-118">İlgi alanlarınıza bağlı olarak, aşağıdaki konulardan birinde WCF Veri Hizmetleri kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="657c5-118">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="657c5-119">Hemen hızlı bir şekilde geçmek istiyorum...</span><span class="sxs-lookup"><span data-stu-id="657c5-119">I want to jump right in...</span></span>

- [<span data-ttu-id="657c5-120">Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="657c5-120">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="657c5-121">Başlarken</span><span class="sxs-lookup"><span data-stu-id="657c5-121">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="657c5-122">Yalnızca bana bir kod göster...</span><span class="sxs-lookup"><span data-stu-id="657c5-122">Just show me some code...</span></span>

- [<span data-ttu-id="657c5-123">Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="657c5-123">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="657c5-124">Nasıl yapılır: Veri Hizmeti Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="657c5-124">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="657c5-125">Nasıl yapılır: Windows Presentation Foundation Öğelerine Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="657c5-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="657c5-126">OData hakkında daha fazla bilgi edinmek istiyorum...</span><span class="sxs-lookup"><span data-stu-id="657c5-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="657c5-127">Teknik İnceleme: OData 'e giriş</span><span class="sxs-lookup"><span data-stu-id="657c5-127">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="657c5-128">Veri Protokolü Web sitesini aç</span><span class="sxs-lookup"><span data-stu-id="657c5-128">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="657c5-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="657c5-129">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="657c5-130">Uçtan uca örnekleri görmek istiyorum...</span><span class="sxs-lookup"><span data-stu-id="657c5-130">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="657c5-131">[Hızlı başlangıç WCF Veri Hizmetleri](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="657c5-131">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="657c5-132">OData SDK-örnek kod</span><span class="sxs-lookup"><span data-stu-id="657c5-132">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="657c5-133">Visual Studio ile nasıl tümleştirilir?</span><span class="sxs-lookup"><span data-stu-id="657c5-133">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="657c5-134">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="657c5-134">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="657c5-135">Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="657c5-135">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="657c5-136">Entity Framework Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="657c5-136">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="657c5-137">Bununla ne yapabilirim?</span><span class="sxs-lookup"><span data-stu-id="657c5-137">What can I do with it?</span></span>

- [<span data-ttu-id="657c5-138">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="657c5-138">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="657c5-139">Uygulama senaryoları</span><span class="sxs-lookup"><span data-stu-id="657c5-139">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="657c5-140">LINQ kullanmak istiyorum...</span><span class="sxs-lookup"><span data-stu-id="657c5-140">I want to use LINQ...</span></span>

- [<span data-ttu-id="657c5-141">Veri Hizmetini Sorgulama</span><span class="sxs-lookup"><span data-stu-id="657c5-141">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="657c5-142">LINQ Konuları</span><span class="sxs-lookup"><span data-stu-id="657c5-142">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="657c5-143">Nasıl yapılır: Veri Hizmeti Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="657c5-143">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="657c5-144">Hala daha fazla bilgi gerekiyor...</span><span class="sxs-lookup"><span data-stu-id="657c5-144">I still need some more information...</span></span>

- [<span data-ttu-id="657c5-145">Ekip Blogu WCF Veri Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="657c5-145">WCF Data Services Team Blog</span></span>](/archive/blogs/astoriateam/)

- [<span data-ttu-id="657c5-146">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="657c5-146">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="657c5-147">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="657c5-147">In This Section</span></span>

[<span data-ttu-id="657c5-148">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="657c5-148">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="657c5-149">WCF Veri Hizmetleri ' de kullanılabilen özellikler ve işlevlere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="657c5-149">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="657c5-150">[WCF Veri Hizmetleri 5,0 ' deki yenilikler](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="657c5-150">[What's New in WCF Data Services 5.0](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="657c5-151">WCF Veri Hizmetleri yeni işlevleri ve yeni OData özellikleri desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="657c5-151">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="657c5-152">Başlarken</span><span class="sxs-lookup"><span data-stu-id="657c5-152">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="657c5-153">WCF Veri Hizmetleri kullanarak OData akışlarını kullanıma sunma ve kullanma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="657c5-153">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="657c5-154">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="657c5-154">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="657c5-155">OData akışlarını kullanıma sunan bir veri hizmetinin nasıl oluşturulduğunu ve yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="657c5-155">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="657c5-156">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="657c5-156">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="657c5-157">İstemci kitaplıklarının, bir .NET Framework istemci uygulamasından OData akışlarını kullanmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="657c5-157">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="657c5-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="657c5-158">See also</span></span>

- [<span data-ttu-id="657c5-159">Temsili durum aktarımı (REST)</span><span class="sxs-lookup"><span data-stu-id="657c5-159">Representational State Transfer (REST)</span></span>](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
