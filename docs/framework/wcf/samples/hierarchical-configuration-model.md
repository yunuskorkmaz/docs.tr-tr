---
title: Hiyerarşik Yapılandırma Modeli
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 233a8d4ba36835ab26e0c4a8cd044cf60d497a0b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="e4073-102">Hiyerarşik Yapılandırma Modeli</span><span class="sxs-lookup"><span data-stu-id="e4073-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="e4073-103">Bu örnek, hizmetler için yapılandırma dosyalarını hiyerarşisini uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e4073-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="e4073-104">Aynı zamanda, nasıl bağlamaları, hizmet davranışları ve uç nokta davranışları hiyerarşide daha yüksek bir düzeyinden devralınan gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4073-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e4073-105">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e4073-105">Sample details</span></span>  
 <span data-ttu-id="e4073-106">Özellikler geliştirilen içinde WCF için [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] hiyerarşik yapılandırma modeli iyileştirme.</span><span class="sxs-lookup"><span data-stu-id="e4073-106">One of the features developed for WCF in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="e4073-107">Hiyerarşik yapılandırma modeli örneği olacaktır Machine.config tarafından tanımlanan bir Rootweb.config -> Web.config ->. İçinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], bu bağlamalar ve yapılandırma hiyerarşideki üst düzey tanımlanan davranışları hizmetlerinize hiçbir açık yapılandırmasıyla eklenir.</span><span class="sxs-lookup"><span data-stu-id="e4073-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="e4073-108">Bu örnek nasıl bilgisayar veya uygulama düzeyinde tanımlanan yapılandırma öğeleri güvenmek, hizmet yapılandırmasını basitleştirmek olası olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4073-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="e4073-109">Bu örnek dokuz Hizmetleri, üç düzeyde hiyerarşi içinde tanımlı oluşur.</span><span class="sxs-lookup"><span data-stu-id="e4073-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="e4073-110">`Service1` kök dizininde ' dir.</span><span class="sxs-lookup"><span data-stu-id="e4073-110">`Service1` is at the root.</span></span> <span data-ttu-id="e4073-111">`Service2` ve `Service3` varsayılan öğelerinden devralır `Service1`.</span><span class="sxs-lookup"><span data-stu-id="e4073-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="e4073-112">`Service4`, `Service5`, `Service6` ve `Service7` varsayılan öğeleri devralma hiyerarşisi, üçüncü bir düzeyde tanımlanan `Service3`.</span><span class="sxs-lookup"><span data-stu-id="e4073-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="e4073-113">Son olarak `Service10` ve `Service11` dördüncü hiyerarşisini düzeyi şunlardır.</span><span class="sxs-lookup"><span data-stu-id="e4073-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="e4073-114">Tüm hizmetler uygulamak `IDesc` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="e4073-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="e4073-115">Aşağıdaki tanımıdır `IDesc` arabirimi bu arabirimde kullanıma sunulan yöntemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4073-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="e4073-116">`IDesc` Arabirimi service1.cs dosyasını tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e4073-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```  
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
  
 <span data-ttu-id="e4073-117">Uygulama Hizmetleri tarafından bu yöntemlerin basittir.</span><span class="sxs-lookup"><span data-stu-id="e4073-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="e4073-118">`ListEndpoints` tüm hizmet uç noktaları yoluyla ilerler ve hizmetin tüm uç noktaları listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4073-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="e4073-119">`ListServiceBehaviors` hizmetine eklediğiniz tüm davranışları dolaşır ve hizmetle ilişkilendirilmiş tüm hizmet davranışları listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4073-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="e4073-120">`ListEndpointBehaviors` benzer şekilde davranır `ListServiceBehaviors`, ancak bunun yerine uç nokta davranışları listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4073-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="e4073-121">Bu uygulama, hizmet kaç tane uç noktaları bilmeniz istemci gösterme ve hangi hizmet davranışları ve uç nokta davranışları hizmete eklenmiştir sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4073-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="e4073-122">Örnek bir parçası olarak uygulanan istemci Çözümdeki tüm Hizmetleri hizmeti başvuru ekler ve hizmetlerinin her biri için bu öğeler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e4073-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="e4073-123">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e4073-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="e4073-124">İstemci çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e4073-124">To run the client</span></span>  
  
1.  <span data-ttu-id="e4073-125">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ConfigHierarchicalModel.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e4073-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="e4073-126">İstemci projesi zaten başlangıç projesi olarak kurulu değil, şu adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="e4073-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="e4073-127">İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e4073-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="e4073-128">İçinde **ortak özellikleri**seçin **başlangıç projesi**ve ardından **tek başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="e4073-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="e4073-129">Gelen **tek başlangıç projesi** açılan listesinde, select **istemci**.</span><span class="sxs-lookup"><span data-stu-id="e4073-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="e4073-130">Tıklatın **Tamam** iletişim kutusunu kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="e4073-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="e4073-131">Örneği oluşturmak için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e4073-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="e4073-132">İstemci çalıştırmak için Ctrl + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e4073-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4073-133">Bu adımlar işe yaramazsa, ortamınızın düzgün bir şekilde, aşağıdaki adımları kullanarak ayarlandığını emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4073-133">If these steps do not work, then make sure that your environment has been properly set up, using the following steps.</span></span>  
>   
>  1.  <span data-ttu-id="e4073-134">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4073-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="e4073-135">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4073-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="e4073-136">Tek bir veya birden çok bilgisayar yapılandırması örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4073-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e4073-137">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="e4073-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e4073-138">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e4073-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e4073-139">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e4073-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4073-140">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e4073-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="e4073-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4073-141">See Also</span></span>  
 [<span data-ttu-id="e4073-142">AppFabric Yönetimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="e4073-142">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)
