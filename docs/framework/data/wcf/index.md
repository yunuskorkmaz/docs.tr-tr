---
title: WCF Veri Hizmetleri 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 1ce152b84f17a35982a75f54b5418623ba39210f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975228"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="61b78-102">WCF Veri Hizmetleri 4.5</span><span class="sxs-lookup"><span data-stu-id="61b78-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="61b78-103">WCF Veri Hizmetleri (eskiden "ADO.NET Data Services" olarak bilinirdi), [temsili durum aktarımı (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)semantiğini kullanarak Web veya intranet üzerinden veri sunmak ve kullanmak Için açık veri Protokolü 'Nü (OData) kullanan hizmetler oluşturmanızı sağlayan bir .NET Framework bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="61b78-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="61b78-104">OData, verileri URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="61b78-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="61b78-105">Al, koy, POST ve DELETE için standart HTTP fiilleri kullanılarak verilere erişilir ve değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="61b78-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="61b78-106">OData, kaynakları ilişkilendirmeler ile ilgili varlık kümeleri olarak göstermek için [varlık veri modeli](../adonet/entity-data-model.md) varlık ilişkisi kurallarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="61b78-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="61b78-107">WCF Veri Hizmetleri, kaynakları adresleme ve güncelleştirme için OData protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="61b78-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="61b78-108">Bu şekilde, bu hizmetlere OData destekleyen herhangi bir istemciden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61b78-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="61b78-109">OData, iyi bilinen aktarım biçimlerini kullanarak kaynaklara istek yapmanızı ve veri yazmanızı sağlar: Atom, verileri XML olarak değiştirme ve güncelleştirme için bir standartlar kümesi ve JavaScript Nesne Gösterimi (JSON), AJAX 'ta yaygın olarak kullanılan metin tabanlı veri değişim biçimi uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="61b78-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="61b78-110">WCF Veri Hizmetleri, çeşitli kaynaklardan kaynaklanan verileri OData akışları olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="61b78-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="61b78-111">Visual Studio Araçları, bir ADO.NET Entity Framework veri modeli kullanarak OData tabanlı bir hizmet oluşturmanızı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="61b78-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="61b78-112">Ayrıca, ortak dil çalışma zamanı (CLR) sınıflarını ve hatta geç bağlı veya yazılmamış verileri temel alan OData akışları da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61b78-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="61b78-113">WCF Veri Hizmetleri ayrıca, biri genel .NET Framework istemci uygulamaları ve özel olarak Silverlight tabanlı uygulamalar için başka bir istemci kitaplıkları kümesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="61b78-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="61b78-114">Bu istemci kitaplıkları, .NET Framework ve Silverlight gibi ortamlardan bir OData akışına eriştiğinizde nesne tabanlı bir programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="61b78-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="61b78-115">Nereden başlamalıyım?</span><span class="sxs-lookup"><span data-stu-id="61b78-115">Where Should I Start?</span></span>

<span data-ttu-id="61b78-116">İlgi alanlarınıza bağlı olarak, aşağıdaki konulardan birinde WCF Veri Hizmetleri kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="61b78-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="61b78-117">Hemen hızlı bir şekilde geçmek istiyorum...</span><span class="sxs-lookup"><span data-stu-id="61b78-117">I want to jump right in...</span></span>

- [<span data-ttu-id="61b78-118">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="61b78-118">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="61b78-119">Başlarken</span><span class="sxs-lookup"><span data-stu-id="61b78-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

- [<span data-ttu-id="61b78-120">Silverlight hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="61b78-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="61b78-121">Windows Phone geliştirme için Silverlight hızlı başlangıcı</span><span class="sxs-lookup"><span data-stu-id="61b78-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="61b78-122">Yalnızca bana bir kod göster...</span><span class="sxs-lookup"><span data-stu-id="61b78-122">Just show me some code...</span></span>

- [<span data-ttu-id="61b78-123">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="61b78-123">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="61b78-124">Nasıl yapılır: Veri Hizmeti Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="61b78-124">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="61b78-125">Nasıl yapılır: Windows Presentation Foundation Öğelerine Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="61b78-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="61b78-126">OData hakkında daha fazla bilgi edinmek istiyorum...</span><span class="sxs-lookup"><span data-stu-id="61b78-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="61b78-127">Teknik İnceleme: OData 'e giriş</span><span class="sxs-lookup"><span data-stu-id="61b78-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="61b78-128">Veri Protokolü Web sitesini aç</span><span class="sxs-lookup"><span data-stu-id="61b78-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

- [<span data-ttu-id="61b78-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="61b78-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

- [<span data-ttu-id="61b78-130">OData: sık sorulan sorular</span><span class="sxs-lookup"><span data-stu-id="61b78-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="61b78-131">Bazı videoları izlemek istiyorum...</span><span class="sxs-lookup"><span data-stu-id="61b78-131">I want to watch some videos...</span></span>

- [<span data-ttu-id="61b78-132">WCF Veri Hizmetleri için başlangıç kılavuzu</span><span class="sxs-lookup"><span data-stu-id="61b78-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

- [<span data-ttu-id="61b78-133">Geliştirici videolarını WCF Veri Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="61b78-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

- [<span data-ttu-id="61b78-134">OData: Geliştirici Web sitesi</span><span class="sxs-lookup"><span data-stu-id="61b78-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="61b78-135">Uçtan uca örnekleri görmek istiyorum...</span><span class="sxs-lookup"><span data-stu-id="61b78-135">I want to see end-to-end samples...</span></span>

- [<span data-ttu-id="61b78-136">MSDN örnekleri galerisinde WCF Veri Hizmetleri belge örnekleri</span><span class="sxs-lookup"><span data-stu-id="61b78-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

- [<span data-ttu-id="61b78-137">MSDN örnekleri galerisinde diğer WCF Veri Hizmetleri örnekleri</span><span class="sxs-lookup"><span data-stu-id="61b78-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

- [<span data-ttu-id="61b78-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="61b78-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="61b78-139">Visual Studio ile nasıl tümleştirilir?</span><span class="sxs-lookup"><span data-stu-id="61b78-139">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="61b78-140">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="61b78-140">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="61b78-141">Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="61b78-141">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="61b78-142">Entity Framework Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="61b78-142">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="61b78-143">Bununla ne yapabilirim?</span><span class="sxs-lookup"><span data-stu-id="61b78-143">What can I do with it?</span></span>

- [<span data-ttu-id="61b78-144">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="61b78-144">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="61b78-145">Teknik İnceleme: OData 'e giriş</span><span class="sxs-lookup"><span data-stu-id="61b78-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="61b78-146">Uygulama Senaryoları</span><span class="sxs-lookup"><span data-stu-id="61b78-146">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="61b78-147">Silverlight kullanmak istiyorum...</span><span class="sxs-lookup"><span data-stu-id="61b78-147">I want to use Silverlight...</span></span>

- [<span data-ttu-id="61b78-148">Silverlight hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="61b78-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="61b78-149">WCF Veri Hizmetleri (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="61b78-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

- [<span data-ttu-id="61b78-150">Silverlight 'ı kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="61b78-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="61b78-151">LINQ kullanmak istiyorum...</span><span class="sxs-lookup"><span data-stu-id="61b78-151">I want to use LINQ...</span></span>

- [<span data-ttu-id="61b78-152">Veri Hizmetini Sorgulama</span><span class="sxs-lookup"><span data-stu-id="61b78-152">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="61b78-153">LINQ Konuları</span><span class="sxs-lookup"><span data-stu-id="61b78-153">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="61b78-154">Nasıl yapılır: Veri Hizmeti Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="61b78-154">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="61b78-155">Hala daha fazla bilgi gerekiyor...</span><span class="sxs-lookup"><span data-stu-id="61b78-155">I still need some more information...</span></span>

- [<span data-ttu-id="61b78-156">Ekip Blogu WCF Veri Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="61b78-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

- [<span data-ttu-id="61b78-157">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="61b78-157">Resources</span></span>](wcf-data-services-resources.md)

- [<span data-ttu-id="61b78-158">WCF Veri Hizmetleri Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="61b78-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

- [<span data-ttu-id="61b78-159">Veri Protokolü Web sitesini aç</span><span class="sxs-lookup"><span data-stu-id="61b78-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="61b78-160">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="61b78-160">In This Section</span></span>

[<span data-ttu-id="61b78-161">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="61b78-161">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="61b78-162">WCF Veri Hizmetleri ' de kullanılabilen özellikler ve işlevlere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="61b78-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="61b78-163">[WCF Veri Hizmetleri 5,0 ' deki yenilikler](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="61b78-163">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="61b78-164">WCF Veri Hizmetleri yeni işlevleri ve yeni OData özellikleri desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="61b78-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="61b78-165">Başlarken</span><span class="sxs-lookup"><span data-stu-id="61b78-165">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="61b78-166">WCF Veri Hizmetleri kullanarak OData akışlarını kullanıma sunma ve kullanma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61b78-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="61b78-167">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="61b78-167">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="61b78-168">OData akışlarını kullanıma sunan bir veri hizmetinin nasıl oluşturulduğunu ve yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="61b78-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="61b78-169">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="61b78-169">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="61b78-170">İstemci kitaplıklarının, bir .NET Framework istemci uygulamasından OData akışlarını kullanmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="61b78-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="61b78-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61b78-171">See also</span></span>

- [<span data-ttu-id="61b78-172">Temsili durum aktarımı (REST)</span><span class="sxs-lookup"><span data-stu-id="61b78-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
