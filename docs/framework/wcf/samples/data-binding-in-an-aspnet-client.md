---
title: "Bir ASP.NET İstemcisinde Veri Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f7a3c4adb1a72a31029da7f73778a5ed407b2f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding-in-an-aspnet-client"></a><span data-ttu-id="c6929-102">Bir ASP.NET İstemcisinde Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="c6929-102">Data Binding in an ASP.NET Client</span></span>
<span data-ttu-id="c6929-103">Bu örnek, tipik bir tarafından döndürülen veri bağlamak gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web Forms uygulamasında hizmet.</span><span class="sxs-lookup"><span data-stu-id="c6929-103">This sample demonstrates how to bind data returned by a typical [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Web Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6929-104">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c6929-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c6929-105">Bu örnek, bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6929-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="c6929-106">İstemci Web Forms uygulama tarayıcıdan erişilebilir örnek oluşur ve bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Internet Information Services (IIS) tarafından barındırılan hizmeti.</span><span class="sxs-lookup"><span data-stu-id="c6929-106">The sample consists of a client Web Forms application accessible from a browser and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="c6929-107">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="c6929-107">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="c6929-108">Anlaşma tarafından tanımlanan `IWeatherService` adlı bir işlem kullanıma sunan arabirim `GetWeatherData`.</span><span class="sxs-lookup"><span data-stu-id="c6929-108">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="c6929-109">Bu işlem bir dizi Şehir kabul eder ve bir dizi döndürür `WeatherData` bir şehir için yüksek ve düşük tahmin edilen sıcaklık temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="c6929-109">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="c6929-110">Üzerinde [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] istemci .aspx sayfası, bir DataGrid denetimi tanımlanır, hizmet tarafından döndürülen veri grafik gösterimi içeren Web.</span><span class="sxs-lookup"><span data-stu-id="c6929-110">On the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] client .aspx page, a DataGrid Web control is defined, which contains the graphical representation of the data returned by the service.</span></span> <span data-ttu-id="c6929-111">.Aspx sayfa çağrıları kodu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hava durumu verileri için hizmet ve veriler için bir dizi döndürür `WeatherData` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c6929-111">Code on the .aspx page calls the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service for weather data and returns the data to an array of `WeatherData` objects.</span></span> <span data-ttu-id="c6929-112">DataGrid ayarlayarak kendi verisinden alınacağı konumu belirtir, `DataSource` bu diziye özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6929-112">The DataGrid specifies where to get its data from by setting its `DataSource` property to that array.</span></span> <span data-ttu-id="c6929-113">Veri bağlama DataGrid'in çağrısıyla oluşur `DataBind` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c6929-113">The data binding occurs with a call to the DataGrid's `DataBind` method.</span></span> <span data-ttu-id="c6929-114">Bu kod tümünün barındırılan içinde.`aspx`</span><span class="sxs-lookup"><span data-stu-id="c6929-114">All of this code is contained inside the .`aspx`</span></span> <span data-ttu-id="c6929-115">sayfanın `Page_Load` her zaman kullanıcı tarayıcı sayfasında, verileri yeniler. böylece yöntemi DataGrid denetiminde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c6929-115">page's `Page_Load` method, so every time the user refreshes the browser page, the data is updated in the DataGrid.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c6929-116">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c6929-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c6929-117">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6929-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c6929-118">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6929-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c6929-119">Bu örnek 's istemci Geliştirme Web sunucusu altında çalışan bir Web sitesidir.</span><span class="sxs-lookup"><span data-stu-id="c6929-119">This sample's client is a Web site that runs under a development Web server.</span></span> <span data-ttu-id="c6929-120">Geliştirme Web sunucusu başlatmak için komut istemine aşağıdaki komutu yazın: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span><span class="sxs-lookup"><span data-stu-id="c6929-120">To launch the development Web server, type the following at the command prompt: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span></span> <span data-ttu-id="c6929-121">Ardından 8000/istemciye göz atın.</span><span class="sxs-lookup"><span data-stu-id="c6929-121">Then browse to http://localhost:8000/client.</span></span> <span data-ttu-id="c6929-122">Bilgisayarlar arasında bu örneği çalıştırmak için tüm başvuruları değiştirin `localhost` istemcinin Web.config dosyasında sunucunun bilgisayar adı.</span><span class="sxs-lookup"><span data-stu-id="c6929-122">To run this sample across computers, replace all references to `localhost` in the client's Web.config file with the computer name of the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6929-123">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c6929-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6929-124">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c6929-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c6929-125">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c6929-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6929-126">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c6929-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a><span data-ttu-id="c6929-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6929-127">See Also</span></span>
