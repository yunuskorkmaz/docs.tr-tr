---
title: WCF Veri Hizmetleri 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 9ece2fe051855d0fd39556f56a4343ead2c437bc
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46482137"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="80be9-102">WCF Veri Hizmetleri 4.5</span><span class="sxs-lookup"><span data-stu-id="80be9-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="80be9-103">WCF Veri Hizmetleri (eski adıyla "ADO.NET Data Services" da bilinir) kullanan hizmetler oluşturmanıza olanak tanıyan .NET Framework'ün bir bileşenidir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] semantiği kullanarak Web veya intranet üzerinden verileri kullanır ve [ temsili durum aktarımı (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="80be9-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="80be9-104">OData veri tarafından bir URI'leri adreslenebilir kaynakları olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="80be9-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="80be9-105">Veri erişim ve GET, PUT, POST ve DELETE, standart HTTP fiillerini kullanarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="80be9-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="80be9-106">OData varlık ilişkisi kuralları kullanan [varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md) kaynakları ilişkilendirmeleri ilgili varlık kümeleri olarak kullanıma sunmak için.</span><span class="sxs-lookup"><span data-stu-id="80be9-106">OData uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="80be9-107">Adresleme ve kaynaklar güncelleştiriliyor, WCF Veri Hizmetleri OData protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="80be9-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="80be9-108">Bu şekilde, OData destekleyen herhangi bir istemciden Bu hizmetlere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80be9-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="80be9-109">OData istek ve iyi bilinen aktarma biçimleri kullanarak veri kaynaklarına yazma olanak tanır: Atom, bir dizi değişimi ve veri XML ve JavaScript nesne gösterimi (JSON) güncelleştirmek için standartları AJAX içinde yaygın olarak kullanılan bir metin tabanlı veri exchange biçimi uygulama.</span><span class="sxs-lookup"><span data-stu-id="80be9-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>

<span data-ttu-id="80be9-110">WCF Veri Hizmetleri OData akışları olarak, çeşitli kaynaklardan veri kaynağı verilerini açığa çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="80be9-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="80be9-111">Visual Studio Araçları bir ADO.NET varlık çerçevesi veri modelini kullanarak bir OData tabanlı bir hizmet oluşturmak için kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="80be9-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="80be9-112">Ortak dil çalışma zamanı (CLR) sınıflar ve hatta geç bağlanan veya türsüz veriler temel alınarak OData akışları da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80be9-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="80be9-113">WCF Veri Hizmetleri, bir dizi istemci kitaplıkları, genel .NET Framework istemci uygulamaları için diğeri Silverlight tabanlı uygulamalar için özellikle de içerir.</span><span class="sxs-lookup"><span data-stu-id="80be9-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="80be9-114">Bir OData akışına gibi .NET Framework ve Silverlight ortamlarından eriştiğinizde bu istemci kitaplıklarının nesne tabanlı programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="80be9-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="80be9-115">Nereden başlamalıyım?</span><span class="sxs-lookup"><span data-stu-id="80be9-115">Where Should I Start?</span></span>

<span data-ttu-id="80be9-116">Alanlarınızı bağlı olarak aşağıdaki konulardan birindeki WCF Data Services ile çalışmaya başlama göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="80be9-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="80be9-117">Hemen istediğiniz...</span><span class="sxs-lookup"><span data-stu-id="80be9-117">I want to jump right in...</span></span>

-   [<span data-ttu-id="80be9-118">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="80be9-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="80be9-119">Başlarken</span><span class="sxs-lookup"><span data-stu-id="80be9-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

-   [<span data-ttu-id="80be9-120">Silverlight hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="80be9-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="80be9-121">Windows Phone geliştirme için Silverlight hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="80be9-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="80be9-122">Yalnızca bazı kod göster...</span><span class="sxs-lookup"><span data-stu-id="80be9-122">Just show me some code...</span></span>

-   [<span data-ttu-id="80be9-123">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="80be9-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="80be9-124">Nasıl yapılır: Veri Hizmeti Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="80be9-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

-   [<span data-ttu-id="80be9-125">Nasıl yapılır: Windows Presentation Foundation Öğelerine Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="80be9-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="80be9-126">OData hakkında daha fazla bilgi edinmek istiyorsanız...</span><span class="sxs-lookup"><span data-stu-id="80be9-126">I want to know more about OData...</span></span>

 -   [<span data-ttu-id="80be9-127">Teknik İnceleme: OData ile tanışın</span><span class="sxs-lookup"><span data-stu-id="80be9-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="80be9-128">Açık Veri Protokolü Web sitesi</span><span class="sxs-lookup"><span data-stu-id="80be9-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

-   [<span data-ttu-id="80be9-129">OData: SDK'sı</span><span class="sxs-lookup"><span data-stu-id="80be9-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

-   [<span data-ttu-id="80be9-130">OData: Sık sorulan sorular</span><span class="sxs-lookup"><span data-stu-id="80be9-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="80be9-131">Bazı videoları izlemek istediğiniz...</span><span class="sxs-lookup"><span data-stu-id="80be9-131">I want to watch some videos...</span></span>

-   [<span data-ttu-id="80be9-132">WCF Veri Hizmetleri için Başlangıç Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="80be9-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

-   [<span data-ttu-id="80be9-133">Geliştirici videoları WCF Veri Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="80be9-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

-   [<span data-ttu-id="80be9-134">OData: Geliştiriciler Web sitesi</span><span class="sxs-lookup"><span data-stu-id="80be9-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="80be9-135">Uçtan uca örnekler görmek istiyorsanız...</span><span class="sxs-lookup"><span data-stu-id="80be9-135">I want to see end-to-end samples...</span></span>

-   [<span data-ttu-id="80be9-136">WCF Veri Hizmetleri belgeleri örnekleri MSDN Örnekler Galerisi</span><span class="sxs-lookup"><span data-stu-id="80be9-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

-   [<span data-ttu-id="80be9-137">MSDN Örnekler Galerisi örnekleri diğer WCF Veri Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="80be9-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

-   [<span data-ttu-id="80be9-138">OData: SDK'sı</span><span class="sxs-lookup"><span data-stu-id="80be9-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="80be9-139">Bu Visual Studio ile nasıl tümleştirilir?</span><span class="sxs-lookup"><span data-stu-id="80be9-139">How does it integrate with Visual Studio?</span></span>

-   [<span data-ttu-id="80be9-140">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="80be9-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

-   [<span data-ttu-id="80be9-141">Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="80be9-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

-   [<span data-ttu-id="80be9-142">Entity Framework Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="80be9-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="80be9-143">İle neler yapabilirim?</span><span class="sxs-lookup"><span data-stu-id="80be9-143">What can I do with it?</span></span>

-   [<span data-ttu-id="80be9-144">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="80be9-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

-   [<span data-ttu-id="80be9-145">Teknik İnceleme: OData ile tanışın</span><span class="sxs-lookup"><span data-stu-id="80be9-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="80be9-146">Uygulama Senaryoları</span><span class="sxs-lookup"><span data-stu-id="80be9-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

<span data-ttu-id="80be9-147">Silverlight kullanmak istediğiniz...</span><span class="sxs-lookup"><span data-stu-id="80be9-147">I want to use Silverlight...</span></span>

-   [<span data-ttu-id="80be9-148">Silverlight hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="80be9-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="80be9-149">WCF Veri Hizmetleri (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="80be9-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

-   [<span data-ttu-id="80be9-150">Silverlight ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="80be9-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="80be9-151">LINQ kullanmak istediğiniz...</span><span class="sxs-lookup"><span data-stu-id="80be9-151">I want to use LINQ...</span></span>

-   [<span data-ttu-id="80be9-152">Veri Hizmetini Sorgulama</span><span class="sxs-lookup"><span data-stu-id="80be9-152">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

-   [<span data-ttu-id="80be9-153">LINQ Konuları</span><span class="sxs-lookup"><span data-stu-id="80be9-153">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

-   [<span data-ttu-id="80be9-154">Nasıl yapılır: Veri Hizmeti Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="80be9-154">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="80be9-155">Yine de bazı ek bilgiler ihtiyacım...</span><span class="sxs-lookup"><span data-stu-id="80be9-155">I still need some more information...</span></span>

-   [<span data-ttu-id="80be9-156">WCF Veri Hizmetleri ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="80be9-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

-   [<span data-ttu-id="80be9-157">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="80be9-157">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

-   [<span data-ttu-id="80be9-158">WCF Veri Hizmetleri Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="80be9-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

-   [<span data-ttu-id="80be9-159">Açık Veri Protokolü Web sitesi</span><span class="sxs-lookup"><span data-stu-id="80be9-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="80be9-160">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="80be9-160">In This Section</span></span>

 [<span data-ttu-id="80be9-161">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="80be9-161">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

 <span data-ttu-id="80be9-162">WCF veri hizmetlerinde kullanılabilen işlevler ve özellikler hakkında genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="80be9-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

 [<span data-ttu-id="80be9-163">WCF veri hizmetlerinde yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="80be9-163">What's New in WCF Data Services</span></span>](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)

 <span data-ttu-id="80be9-164">WCF Veri Hizmetleri ve yeni OData özellikleri için destek yeni işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80be9-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

 [<span data-ttu-id="80be9-165">Başlarken</span><span class="sxs-lookup"><span data-stu-id="80be9-165">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

 <span data-ttu-id="80be9-166">Kullanıma sunma ve WCF veri hizmetlerini kullanarak OData akışları kullanma açıklar.</span><span class="sxs-lookup"><span data-stu-id="80be9-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

 [<span data-ttu-id="80be9-167">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="80be9-167">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

 <span data-ttu-id="80be9-168">Oluşturma ve OData akışları kullanıma sunan bir veri hizmeti yapılandırma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="80be9-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

 [<span data-ttu-id="80be9-169">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="80be9-169">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

 <span data-ttu-id="80be9-170">Bir .NET Framework istemci uygulamasından OData akışları kullanmak için istemci kitaplıkları kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="80be9-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="80be9-171">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80be9-171">See Also</span></span>

- [<span data-ttu-id="80be9-172">Temsili durum aktarımı (REST)</span><span class="sxs-lookup"><span data-stu-id="80be9-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
