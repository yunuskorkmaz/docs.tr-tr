---
title: "Windows Forms İstemcisinde Veri Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b78cfbd63687fc7288c945ebcbec790150efed61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a><span data-ttu-id="42f7a-102">Windows Forms İstemcisinde Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="42f7a-102">Data Binding in a Windows Forms Client</span></span>
<span data-ttu-id="42f7a-103">Bu örnek tarafından döndürülen veri bağlamak nasıl gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir Windows Forms uygulamasında hizmet.</span><span class="sxs-lookup"><span data-stu-id="42f7a-103">This sample demonstrates how to bind to data returned by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Windows Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42f7a-104">Bu örnek için Kurulum yordamı ve yapı yönergeleri bu makalenin sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="42f7a-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>  
  
 <span data-ttu-id="42f7a-105">Bu örnek, bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="42f7a-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="42f7a-106">Örnek bir Windows Forms uygulaması (.exe) istemcisi oluşur ve bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Internet Information Services (IIS) tarafından barındırılan hizmeti.</span><span class="sxs-lookup"><span data-stu-id="42f7a-106">The sample consists of a client Windows Forms application (.exe) and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="42f7a-107">Anlaşma tarafından tanımlanan `IWeatherService` adlı bir işlem kullanıma sunan arabirim `GetWeatherData`.</span><span class="sxs-lookup"><span data-stu-id="42f7a-107">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="42f7a-108">Bu işlem bir dizi Şehir kabul eder ve bir dizi döndürür `WeatherData` bir şehir için yüksek ve düşük tahmin edilen sıcaklık temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="42f7a-108">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="42f7a-109">Windows Forms uygulamasında istemcisinde veri bağlama oluşur.</span><span class="sxs-lookup"><span data-stu-id="42f7a-109">The data binding occurs on the client in the Windows Forms application.</span></span> <span data-ttu-id="42f7a-110">A `DataGridView` verileri grafik gösterimi olan Windows Forms Tasarımcısı'nda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="42f7a-110">A `DataGridView` is defined in the Windows Forms designer, which is a graphical representation of the data.</span></span> <span data-ttu-id="42f7a-111">Adlı bir aracı `BindingSource` da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42f7a-111">An intermediary named `BindingSource` is also created.</span></span> <span data-ttu-id="42f7a-112">Veri kaynağı `BindingSource` hizmet tarafından döndürülen veri dizisi ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="42f7a-112">The data source of `BindingSource` is set to the data array returned by the service.</span></span> <span data-ttu-id="42f7a-113">Amacı `BindingSource` yöneltme verileri ve veri görünümü arasında bir katmanı sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="42f7a-113">The purpose of the `BindingSource` is to provide a layer of indirection between the data and the data view.</span></span> <span data-ttu-id="42f7a-114">Gezinme, sıralama, filtreleme ve güncelleştirilmesi gibi verilere tüm etkileşim çağrıları ile gerçekleştirilir `BindingSource` bileşeni.</span><span class="sxs-lookup"><span data-stu-id="42f7a-114">All interaction with the data, such as navigating, sorting, filtering, and updating, is accomplished with calls to the `BindingSource` component.</span></span> <span data-ttu-id="42f7a-115">Veri bağlama gerçekleştirmek için `DataGridView`, `datasource` , `DataGridView` sonra ayarlanır `BindingSource` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="42f7a-115">To accomplish data binding to the `DataGridView`, the `datasource` of the `DataGridView` is then set to the `BindingSource` object.</span></span> <span data-ttu-id="42f7a-116">Döndürülen verilerin tümünü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet sonra görüntülenen grafik kullanıcıya.</span><span class="sxs-lookup"><span data-stu-id="42f7a-116">All of the data returned from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is then displayed graphically to the user.</span></span>  <span data-ttu-id="42f7a-117">Kullanıcı düğmesine tıklar her zaman, döndürülen veriler içinde veri bağlama otomatik olarak güncelleştirilir `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="42f7a-117">Every time the user clicks the button, the returned data is automatically updated in the data-bound `DataGridView`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="42f7a-118">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="42f7a-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="42f7a-119">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42f7a-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="42f7a-120">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42f7a-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="42f7a-121">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42f7a-121">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="42f7a-122">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="42f7a-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="42f7a-123">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="42f7a-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="42f7a-124">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="42f7a-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="42f7a-125">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="42f7a-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a><span data-ttu-id="42f7a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42f7a-126">See Also</span></span>
