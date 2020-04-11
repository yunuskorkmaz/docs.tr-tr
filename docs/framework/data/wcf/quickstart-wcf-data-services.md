---
title: Quickstart (WCF Veri Hizmetleri)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121220"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="301d4-102">Quickstart (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="301d4-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="301d4-103">Bu hızlı başlangıç, [Başlarken'deki](getting-started-with-wcf-data-services.md)konuları destekleyen bir dizi görev aracılığıyla WCF Veri Hizmetleri ve Açık Veri Protokolü'nü (OData) tanımanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="301d4-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="301d4-104">Öğrenecekleriniz</span><span class="sxs-lookup"><span data-stu-id="301d4-104">What you'll learn</span></span>

<span data-ttu-id="301d4-105">Bu hızlı başlatmadaki ilk görev, Northwind örnek veritabanından bir OData akışını ortaya çıkarmak için nasıl bir veri hizmeti oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="301d4-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="301d4-106">Daha sonraki konularda, bir Web tarayıcısı kullanarak OData akışına erişecek ve istemci kitaplıklarını kullanarak OData akışını tüketen bir Windows Presentation Foundation (WPF) istemci uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="301d4-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="301d4-107">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="301d4-107">Prerequisites</span></span>

<span data-ttu-id="301d4-108">Bu hızlı başlatmayı tamamlamak için aşağıdaki bileşenleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="301d4-108">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="301d4-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="301d4-109">Visual Studio</span></span>

- <span data-ttu-id="301d4-110">SQL Server örneği.</span><span class="sxs-lookup"><span data-stu-id="301d4-110">An instance of SQL Server.</span></span> <span data-ttu-id="301d4-111">Buna Visual Studio 2015'in varsayılan yüklemesinde veya Visual Studio 2017 veya sonraki yıllarda **veri depolama ve işleme** iş yükünün bir parçası olarak dahil edilen SQL Server Express dahildir.</span><span class="sxs-lookup"><span data-stu-id="301d4-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="301d4-112">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="301d4-112">The Northwind sample database.</span></span> <span data-ttu-id="301d4-113">Veritabanını yüklemek [için, Northwind'den](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)Transact-SQL komut dosyasını çalıştırın ve Microsoft SQL Server için pub örnek veritabanlarını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="301d4-113">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="301d4-114">WCF veri hizmetleri hızlı başlangıç görevleri</span><span class="sxs-lookup"><span data-stu-id="301d4-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="301d4-115">Veri Hizmetini Oluşturma</span><span class="sxs-lookup"><span data-stu-id="301d4-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="301d4-116">uygulamaASP.NET tanımlayın, veri modelini tanımlayın, veri hizmeti oluşturun ve kaynaklara erişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="301d4-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="301d4-117">Hizmete Bir Web Tarayıcısından Erişin</span><span class="sxs-lookup"><span data-stu-id="301d4-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="301d4-118">Hizmeti Visual Studio'dan başlatın ve http GET isteklerini bir Web tarayıcısı aracılığıyla açıkta kalan özet akışına göndererek hizmete erişin.</span><span class="sxs-lookup"><span data-stu-id="301d4-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="301d4-119">.NET Framework İstemci Uygulamasını Oluştur</span><span class="sxs-lookup"><span data-stu-id="301d4-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="301d4-120">OData akışını tüketmek, verileri Windows denetimlerine bağlamak, bağlı denetimlerde verileri değiştirmek ve değişiklikleri veri hizmetine geri göndermek için bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="301d4-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="301d4-121">Quickstart tamamlanmış bir sürümünden Proje dosyaları [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="301d4-121">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="301d4-122">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="301d4-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="301d4-123">Hızlı başlatmayı başlatın</span><span class="sxs-lookup"><span data-stu-id="301d4-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="301d4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="301d4-124">See also</span></span>

- [<span data-ttu-id="301d4-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="301d4-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
