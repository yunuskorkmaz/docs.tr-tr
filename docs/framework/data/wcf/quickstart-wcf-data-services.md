---
title: Hızlı Başlangıç (WCF Veri Hizmetleri)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: d0002182c5ae519c36348acdd2587bca499fe72e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975135"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="840ea-102">Hızlı Başlangıç (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="840ea-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="840ea-103">Bu hızlı başlangıç, Başlarken ile ilgili konuları destekleyen bir dizi görev aracılığıyla WCF Veri Hizmetleri ve açık veri Protokolü (OData) hakkında bilgi sahibi olmanıza yardımcı [olur.](getting-started-with-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="840ea-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="840ea-104">Ne öğrenirsiniz</span><span class="sxs-lookup"><span data-stu-id="840ea-104">What you'll learn</span></span>

<span data-ttu-id="840ea-105">Bu hızlı başlangıçta bulunan ilk görevde, Northwind örnek veritabanından bir OData akışını açığa çıkarmak için bir veri hizmetinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="840ea-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="840ea-106">Sonraki konularda, OData akışına bir Web tarayıcısı kullanarak erişecek ve ayrıca istemci kitaplıklarını kullanarak OData akışını tüketen bir Windows Presentation Foundation (WPF) istemci uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="840ea-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="840ea-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="840ea-107">Prerequisites</span></span>

<span data-ttu-id="840ea-108">Bu hızlı başlangıcı tamamlayabilmeniz için aşağıdaki bileşenleri yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="840ea-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="840ea-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="840ea-109">Visual Studio</span></span>

- <span data-ttu-id="840ea-110">SQL Server örneği.</span><span class="sxs-lookup"><span data-stu-id="840ea-110">An instance of SQL Server.</span></span> <span data-ttu-id="840ea-111">Bu, varsayılan Visual Studio 2015 yüklemesinde veya Visual Studio 2017 ' de **veri depolama ve işleme** iş yükünün parçası olarak bulunan SQL Server Express içerir.</span><span class="sxs-lookup"><span data-stu-id="840ea-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="840ea-112">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="840ea-112">The Northwind sample database.</span></span> <span data-ttu-id="840ea-113">Bu örnek veritabanını indirmek için indirme sayfasına, [SQL Server Için örnek veritabanlarına](https://go.microsoft.com/fwlink/?linkid=24758)bakın.</span><span class="sxs-lookup"><span data-stu-id="840ea-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="840ea-114">WCF veri hizmetleri hızlı başlangıç görevleri</span><span class="sxs-lookup"><span data-stu-id="840ea-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="840ea-115">Veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="840ea-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="840ea-116">ASP.NET uygulamasını tanımlayın, veri modelini tanımlayın, veri hizmetini oluşturun ve kaynaklara erişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="840ea-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="840ea-117">Hizmete bir Web tarayıcısından erişin</span><span class="sxs-lookup"><span data-stu-id="840ea-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="840ea-118">Hizmeti Visual Studio 'dan başlatın ve sunulan akışa bir Web tarayıcısı aracılığıyla HTTP GET istekleri göndererek hizmete erişin.</span><span class="sxs-lookup"><span data-stu-id="840ea-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="840ea-119">.NET Framework Istemci uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="840ea-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="840ea-120">OData akışını kullanmak, verileri Windows denetimlerine bağlamak, bağlama denetimlerindeki verileri değiştirmek ve sonra değişiklikleri veri hizmetine geri göndermek için bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="840ea-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="840ea-121">Hızlı başlangıç sürümünün tamamlanmış sürümlerinden proje dosyaları [WCF veri Hizmetleri belge örnekleri](https://go.microsoft.com/fwlink/?LinkId=179994) sayfasından indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="840ea-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="840ea-122">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="840ea-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="840ea-123">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="840ea-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="840ea-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="840ea-124">See also</span></span>

- [<span data-ttu-id="840ea-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="840ea-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
