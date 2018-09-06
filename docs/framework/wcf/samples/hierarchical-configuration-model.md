---
title: Hiyerarşik Yapılandırma Modeli
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 8ca9b01eb022e2e2ab940866a6230e8227ceb2dc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736399"
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="16739-102">Hiyerarşik Yapılandırma Modeli</span><span class="sxs-lookup"><span data-stu-id="16739-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="16739-103">Bu örnek, uygulama hizmetleri için yapılandırma dosyalarını hiyerarşisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16739-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="16739-104">Ayrıca, uç nokta davranışları bağlamaları ve hizmet davranışlarını hiyerarşideki üst düzey nasıl devralınır gösterir.</span><span class="sxs-lookup"><span data-stu-id="16739-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="16739-105">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="16739-105">Sample details</span></span>  
 <span data-ttu-id="16739-106">WCF'de için geliştirilen özelliklerinden [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] hiyerarşik yapılandırma modeli iyileştirmedir.</span><span class="sxs-lookup"><span data-stu-id="16739-106">One of the features developed for WCF in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="16739-107">Hiyerarşik yapılandırma modeli örnek verilebilir Machine.config tarafından tanımlanan bir Rootweb.config -> Web.config ->. İçinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], hizmetlerinizi açık bir yapılandırma gerekmeden bu bağlamaları ve yapılandırma hiyerarşideki üst düzey tanımlanan davranışları eklenir.</span><span class="sxs-lookup"><span data-stu-id="16739-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="16739-108">Bu örnek nasıl bilgisayar veya uygulama düzeyinde tanımlanan yapılandırma öğeleri bağlı hizmet yapılandırmanızı basitleştirmek mümkün olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="16739-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="16739-109">Bu örnek dokuz Hizmetleri, üç hiyerarşi düzeylerinde tanımlı oluşur.</span><span class="sxs-lookup"><span data-stu-id="16739-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="16739-110">`Service1` kök dizininde ' dir.</span><span class="sxs-lookup"><span data-stu-id="16739-110">`Service1` is at the root.</span></span> <span data-ttu-id="16739-111">`Service2` ve `Service3` varsayılan öğelerden devralınan `Service1`.</span><span class="sxs-lookup"><span data-stu-id="16739-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="16739-112">`Service4`, `Service5`, `Service6` ve `Service7` varsayılan öğeleri devralma hiyerarşisinin üçüncü bir düzeyde tanımlanan `Service3`.</span><span class="sxs-lookup"><span data-stu-id="16739-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="16739-113">Son olarak `Service10` ve `Service11` dördüncü hiyerarşisini düzeyi olan.</span><span class="sxs-lookup"><span data-stu-id="16739-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="16739-114">Tüm hizmetleri uygulayan `IDesc` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="16739-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="16739-115">Aşağıdaki tanımıdır `IDesc` bu arabirimde kullanıma sunulan yöntemleri gösteren arabirimi.</span><span class="sxs-lookup"><span data-stu-id="16739-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="16739-116">`IDesc` Arabirimi Service1.cs içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="16739-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```csharp  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 <span data-ttu-id="16739-117">Uygulama Hizmetleri tarafından bu yöntemlerin oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="16739-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="16739-118">`ListEndpoints` tüm hizmet uç noktaları yinelenir ve hizmetin tüm uç noktalar listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="16739-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="16739-119">`ListServiceBehaviors` Bu hizmete eklenen tüm davranışları gezinir ve hizmetle ilişkili hizmet davranışları listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="16739-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="16739-120">`ListEndpointBehaviors` benzer şekilde davranır `ListServiceBehaviors`, ancak bunun yerine uç nokta davranışları listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="16739-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="16739-121">Bu uygulama, hizmet kaç uç noktaları öğrenmek için istemci gösterme ve hangi hizmet davranışları ve uç nokta davranışları hizmetine eklenmiştir sağlar.</span><span class="sxs-lookup"><span data-stu-id="16739-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="16739-122">Örnek bir parçası olarak uygulanan istemci, Çözümdeki tüm hizmetler için bir hizmet başvurusu ekler ve bu hizmetlerin her biri, öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="16739-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="16739-123">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="16739-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="16739-124">İstemciyi çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="16739-124">To run the client</span></span>  
  
1.  <span data-ttu-id="16739-125">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ConfigHierarchicalModel.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="16739-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="16739-126">İstemci projeyi başlangıç projesi olarak ayarlamış değil, aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="16739-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="16739-127">İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="16739-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="16739-128">İçinde **ortak özellikler**seçin **başlangıç projesi**ve ardından **tek başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="16739-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="16739-129">Gelen **tek başlangıç projesi** açılan listesinde, select **istemci**.</span><span class="sxs-lookup"><span data-stu-id="16739-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="16739-130">Tıklayın **Tamam** iletişim kutusunu kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="16739-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="16739-131">Örneği oluşturmak için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="16739-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="16739-132">İstemciyi çalıştırmak için Ctrl + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="16739-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16739-133">Bu adımlar da işe yaramazsa, ortamınızı düzgün bir şekilde, aşağıdaki adımları kullanarak ayarlandığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="16739-133">If these steps do not work, make sure that your environment has been properly set up, using the following steps:</span></span>  
>   
> 1.  <span data-ttu-id="16739-134">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16739-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="16739-135">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16739-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="16739-136">Tek bir veya birden çok bilgisayar yapılandırmalarını örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16739-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16739-137">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="16739-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="16739-138">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="16739-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="16739-139">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="16739-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="16739-140">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="16739-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="16739-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16739-141">See Also</span></span>  
 [<span data-ttu-id="16739-142">AppFabric Yönetimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="16739-142">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
