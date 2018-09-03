---
title: Hızlı Başlangıç (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f20ffcf356aa0493b1e2356746d9ad7b27d9a1aa
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480519"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="72b50-102">Hızlı Başlangıç (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="72b50-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="72b50-103">Bu Hızlı Başlangıç ile WCF veri hizmetlerini öğrenmenize yardımcı olur ve [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] konularında destek görevleri bir dizi [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="72b50-103">This quickstart helps you become familiar with WCF Data Services and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="72b50-104">Öğrenecekleriniz</span><span class="sxs-lookup"><span data-stu-id="72b50-104">What you'll learn</span></span>

<span data-ttu-id="72b50-105">Bu hızlı başlangıçta ilk görev bir OData akışına Northwind örnek veritabanından kullanıma sunmak için veri hizmeti oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="72b50-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="72b50-106">Sonraki konu başlıklarında, OData erişecek bir Web tarayıcısı kullanarak akış ve OData kullandığı istemci uygulaması akışı istemci kitaplıklarını kullanarak Windows Presentation Foundation (WPF) oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="72b50-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72b50-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="72b50-107">Prerequisites</span></span>

<span data-ttu-id="72b50-108">Bu hızlı başlangıcı tamamlamak için aşağıdaki bileşenleri yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="72b50-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="72b50-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="72b50-109">Visual Studio</span></span>

- <span data-ttu-id="72b50-110">SQL Server örneği.</span><span class="sxs-lookup"><span data-stu-id="72b50-110">An instance of SQL Server.</span></span> <span data-ttu-id="72b50-111">Bu, Visual Studio 2015 veya parçası olarak varsayılan yüklemede bulunan SQL Server Express içerir **veri depolama ve işleme** Visual Studio 2017'de iş yükü.</span><span class="sxs-lookup"><span data-stu-id="72b50-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="72b50-112">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="72b50-112">The Northwind sample database.</span></span> <span data-ttu-id="72b50-113">Bu örnek veritabanı karşıdan yüklemek için indirme sayfasında bakın [örnek veritabanları için SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="72b50-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="72b50-114">WCF Veri Hizmetleri hızlı başlangıç görevleri</span><span class="sxs-lookup"><span data-stu-id="72b50-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="72b50-115">Veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="72b50-115">Create the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

 <span data-ttu-id="72b50-116">Tanımlama [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama, veri modelini tanımlama, veri hizmeti oluşturma ve kaynaklarına erişimi etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="72b50-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="72b50-117">Bir Web tarayıcısından hizmete erişme</span><span class="sxs-lookup"><span data-stu-id="72b50-117">Access the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="72b50-118">Visual Studio'dan hizmeti başlatın ve HTTP GET isteklerini ifşa edilen akış için bir Web tarayıcısı üzerinden göndererek hizmet erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72b50-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="72b50-119">.NET Framework istemci uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="72b50-119">Create the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="72b50-120">OData akışı kullanma, Windows denetimlere veri bağlama, veri bağlama denetimleri değiştirmek için bir WPF uygulaması oluşturma ve sonra veri hizmetine değişiklikleri geri gönderin.</span><span class="sxs-lookup"><span data-stu-id="72b50-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="72b50-121">Hızlı Başlangıç tamamlanmış bir sürümünü proje dosyalarından gelen indirilebilir [WCF Veri Hizmetleri belgeleri örnekleri](https://go.microsoft.com/fwlink/?LinkId=179994) sayfası.</span><span class="sxs-lookup"><span data-stu-id="72b50-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="72b50-122">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="72b50-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="72b50-123">Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="72b50-123">Start the quickstart</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="72b50-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72b50-124">See also</span></span>

- [<span data-ttu-id="72b50-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="72b50-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
