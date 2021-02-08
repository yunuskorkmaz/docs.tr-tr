---
description: 'Daha fazla bilgi edinin: hızlı başlangıç (WCF Veri Hizmetleri)'
title: Hızlı Başlangıç (WCF Veri Hizmetleri)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: 92a1b8882f6a7db2ed33f032ad434efd06400421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794955"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="56d28-103">Hızlı Başlangıç (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="56d28-103">Quickstart (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="56d28-104">Bu hızlı başlangıç, Başlarken ile ilgili konuları destekleyen bir dizi görev aracılığıyla WCF Veri Hizmetleri ve açık veri Protokolü (OData) hakkında bilgi sahibi olmanıza yardımcı [olur.](getting-started-with-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="56d28-104">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="56d28-105">Öğrenecekleriniz</span><span class="sxs-lookup"><span data-stu-id="56d28-105">What you'll learn</span></span>

<span data-ttu-id="56d28-106">Bu hızlı başlangıçta bulunan ilk görevde, Northwind örnek veritabanından bir OData akışını açığa çıkarmak için bir veri hizmetinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="56d28-106">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="56d28-107">Sonraki konularda, OData akışına bir Web tarayıcısı kullanarak erişecek ve ayrıca istemci kitaplıklarını kullanarak OData akışını tüketen bir Windows Presentation Foundation (WPF) istemci uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="56d28-107">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56d28-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="56d28-108">Prerequisites</span></span>

<span data-ttu-id="56d28-109">Bu hızlı başlangıcı gerçekleştirmek için aşağıdaki bileşenleri yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="56d28-109">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="56d28-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="56d28-110">Visual Studio</span></span>

- <span data-ttu-id="56d28-111">SQL Server örneği.</span><span class="sxs-lookup"><span data-stu-id="56d28-111">An instance of SQL Server.</span></span> <span data-ttu-id="56d28-112">Bu, varsayılan Visual Studio 2015 yüklemesinde veya Visual Studio 2017 veya sonraki bir sürümünde **veri depolama ve işleme** iş yükünün parçası olarak bulunan SQL Server Express içerir.</span><span class="sxs-lookup"><span data-stu-id="56d28-112">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="56d28-113">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="56d28-113">The Northwind sample database.</span></span> <span data-ttu-id="56d28-114">Veritabanını yüklemek için [Northwind ve pubs örnek veritabanlarından](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)Transact-SQL betiğini çalıştırın Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="56d28-114">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="56d28-115">WCF veri hizmetleri hızlı başlangıç görevleri</span><span class="sxs-lookup"><span data-stu-id="56d28-115">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="56d28-116">Veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="56d28-116">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="56d28-117">ASP.NET uygulamasını tanımlayın, veri modelini tanımlayın, veri hizmetini oluşturun ve kaynaklara erişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="56d28-117">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="56d28-118">Hizmete bir Web tarayıcısından erişin</span><span class="sxs-lookup"><span data-stu-id="56d28-118">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="56d28-119">Hizmeti Visual Studio 'dan başlatın ve sunulan akışa bir Web tarayıcısı aracılığıyla HTTP GET istekleri göndererek hizmete erişin.</span><span class="sxs-lookup"><span data-stu-id="56d28-119">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="56d28-120">.NET Framework Istemci uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="56d28-120">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="56d28-121">OData akışını kullanmak, verileri Windows denetimlerine bağlamak, bağlama denetimlerindeki verileri değiştirmek ve sonra değişiklikleri veri hizmetine geri göndermek için bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="56d28-121">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="56d28-122">Hızlı başlangıç sürümünün tamamlanmış sürümlerinden proje dosyaları [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))'dan indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="56d28-122">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="56d28-123">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="56d28-123">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56d28-124">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="56d28-124">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="56d28-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56d28-125">See also</span></span>

- [<span data-ttu-id="56d28-126">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="56d28-126">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
