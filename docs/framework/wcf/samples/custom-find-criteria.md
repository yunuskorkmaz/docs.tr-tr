---
title: "Özel Bulma Ölçütleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b57a9535b34441a8f1c86beeffa94046cf8944f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-find-criteria"></a><span data-ttu-id="0b58b-102">Özel Bulma Ölçütleri</span><span class="sxs-lookup"><span data-stu-id="0b58b-102">Custom Find Criteria</span></span>
<span data-ttu-id="0b58b-103">Bu örnek mantığı kullanarak özel kapsam eşleşme oluşturma ve özel bulma hizmeti uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-103">This sample demonstrates how to create a custom scope match using logic and how to implement a custom discovery service.</span></span> <span data-ttu-id="0b58b-104">İstemciler işlevselliği eşleşen özel kapsam daraltın ve WCF bulma sistem tarafından sağlanan Bul işlevselliği üzerinde daha fazla yapı için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b58b-104">Clients use custom scope matching functionality to refine and further build on top of the system-provided find functionality of WCF Discovery.</span></span> <span data-ttu-id="0b58b-105">Bu örnek kapsayan senaryo aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0b58b-105">The scenario this sample covers is as follows:</span></span>  
  
1.  <span data-ttu-id="0b58b-106">Bir istemci için bir hesap makinesi hizmeti arıyor.</span><span class="sxs-lookup"><span data-stu-id="0b58b-106">A client is looking for a calculator service.</span></span>  
  
2.  <span data-ttu-id="0b58b-107">Kendi aramasını daraltmak için istemci kural eşleşen özel bir kapsam kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-107">To refine its search, the client must use a custom scope matching rule.</span></span>  
  
3.  <span data-ttu-id="0b58b-108">Bu kural göre bir hizmet, uç noktasında herhangi bir istemci tarafından belirtilen kapsamlar eşleşirse istemciye yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-108">According to this rule, a service responds back to the client if its endpoint matches any of the scopes specified by the client.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0b58b-109">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="0b58b-109">Demonstrates</span></span>  
  
-   <span data-ttu-id="0b58b-110">Özel bulma hizmeti oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0b58b-110">Creating a custom discovery service.</span></span>  
  
-   <span data-ttu-id="0b58b-111">Bir özel kapsam eşleştirme algoritması tarafından uygulama.</span><span class="sxs-lookup"><span data-stu-id="0b58b-111">Implementing a custom scope match by algorithm.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="0b58b-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="0b58b-112">Discussion</span></span>  
 <span data-ttu-id="0b58b-113">İstemci ölçütlerle eşleşen "Veya" türü için arıyor.</span><span class="sxs-lookup"><span data-stu-id="0b58b-113">The client is looking for "OR" type matching criteria.</span></span> <span data-ttu-id="0b58b-114">Bir hizmet, kendi uç noktalarda kapsamları herhangi bir istemci tarafından sağlanan kapsamları eşleşiyorsa geri yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-114">A service responds back if the scopes on its endpoints match any of the scopes provided by the client.</span></span> <span data-ttu-id="0b58b-115">Bu durumda, istemci, aşağıdaki listede kapsamları hiçbirini sahip bir hesap makinesi hizmeti için arıyor:</span><span class="sxs-lookup"><span data-stu-id="0b58b-115">In this case, the client is looking for a calculator service that has any of the scopes in the following list:</span></span>  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 <span data-ttu-id="0b58b-116">Bunu gerçekleştirmek için bir özel kapsam eşleşme URI tarafından geçirerek kural eşleşen özel bir kapsam kullanmak üzere hizmetlerin istemci yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-116">To accomplish this, the client directs services to use a custom scope matching rule by passing in a custom scope match by URI.</span></span> <span data-ttu-id="0b58b-117">Özel kapsam eşleşen kolaylaştırmak için hizmet özel kapsam eşleşen kural anlar ve ilişkili eşleştirme mantığını uygulayan bir özel bulma hizmeti kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-117">To facilitate the custom scope matching, the service must use a custom discovery service that understands the custom scope match rule and implements the associated matching logic.</span></span>  
  
 <span data-ttu-id="0b58b-118">İstemci projesinde Program.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0b58b-118">In the client project, open the Program.cs file.</span></span> <span data-ttu-id="0b58b-119">Unutmayın `ScopeMatchBy` alanını `FindCriteria` nesne için belirli bir URI ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0b58b-119">Note that the `ScopeMatchBy` field of the `FindCriteria` object is set to a specific URI.</span></span> <span data-ttu-id="0b58b-120">Bu tanımlayıcı hizmetine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-120">This identifier is sent to the service.</span></span> <span data-ttu-id="0b58b-121">Hizmet bu kural anlamıyorsa istemcinin bulma isteği yok sayar.</span><span class="sxs-lookup"><span data-stu-id="0b58b-121">If the service does not understand this rule, it ignores the client’s find request.</span></span>  
  
 <span data-ttu-id="0b58b-122">Hizmet projesini açın.</span><span class="sxs-lookup"><span data-stu-id="0b58b-122">Open the service project.</span></span> <span data-ttu-id="0b58b-123">Üç dosyaları özel bulma hizmeti uygulamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="0b58b-123">Three files are used to implement the Custom Discovery Service:</span></span>  
  
1.  <span data-ttu-id="0b58b-124">**AsyncResult.cs**: Bu uygulamasıdır `AsyncResult` bulma yöntemleri ile gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-124">**AsyncResult.cs**: This is the implementation of the `AsyncResult` that is required by Discovery methods.</span></span>  
  
2.  <span data-ttu-id="0b58b-125">**CustomDiscoveryService.cs**: özel bulma hizmeti bu dosyayı uygular.</span><span class="sxs-lookup"><span data-stu-id="0b58b-125">**CustomDiscoveryService.cs**: This file implements the custom discovery service.</span></span> <span data-ttu-id="0b58b-126">Uygulama genişletir <xref:System.ServiceModel.Discovery.DiscoveryService> sınıfı ve gerekli yöntemlerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0b58b-126">The implementation extends the <xref:System.ServiceModel.Discovery.DiscoveryService> class and overrides the necessary methods.</span></span> <span data-ttu-id="0b58b-127">Uygulaması Not <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b58b-127">Note the implementation of the <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> method.</span></span> <span data-ttu-id="0b58b-128">Yöntemi, istemci tarafından özel kapsam eşleşme kuralı tarafından belirtilen olup olmadığını görmek için denetler.</span><span class="sxs-lookup"><span data-stu-id="0b58b-128">The method checks to see whether the custom scope match by rule was specified by the client.</span></span> <span data-ttu-id="0b58b-129">İstemci daha önce belirtilen aynı özel URI budur.</span><span class="sxs-lookup"><span data-stu-id="0b58b-129">This is the same custom URI that the client specified previously.</span></span> <span data-ttu-id="0b58b-130">Özel kural belirtilirse, "Veya" eşleştirme mantığını uygulayan kod yolu izlenir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-130">If the custom rule is specified, the code path that implements the "OR" match logic is followed.</span></span>  
  
     <span data-ttu-id="0b58b-131">Bu özel mantık tüm kapsamlar her hizmet uç noktaları gider.</span><span class="sxs-lookup"><span data-stu-id="0b58b-131">This custom logic goes through all of the scopes on each of the endpoints that the service has.</span></span> <span data-ttu-id="0b58b-132">Herhangi bir uç noktanın kapsamları herhangi bir istemci tarafından sağlanan kapsamları eşleşiyorsa, bulma hizmeti bu uç istemciye gönderilen yanıta ekler.</span><span class="sxs-lookup"><span data-stu-id="0b58b-132">If any of the endpoint's scopes match any of the scopes provided by the client, the discovery service adds that endpoint to the response that is sent back to the client.</span></span>  
  
3.  <span data-ttu-id="0b58b-133">**CustomDiscoveryExtension.cs**: bulma hizmeti uygulama son adımı özel bu uygulama bağlamaktır hizmet ana bilgisayar hizmetine keşfedin.</span><span class="sxs-lookup"><span data-stu-id="0b58b-133">**CustomDiscoveryExtension.cs**: The last step in implementing the discovery service is to connect this implementation of the custom discover service to the service host.</span></span> <span data-ttu-id="0b58b-134">Burada kullanılan Yardımcısı sınıfı, `CustomDiscoveryExtension` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0b58b-134">The helper class used here is the `CustomDiscoveryExtension` class.</span></span> <span data-ttu-id="0b58b-135">Bu sınıfını genişleten <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0b58b-135">This class extends the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> class.</span></span> <span data-ttu-id="0b58b-136">Kullanıcı geçersiz kılmanız gerekir <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b58b-136">The user must override the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> method.</span></span> <span data-ttu-id="0b58b-137">Bu durumda, yöntem önce oluşturulan özel bulma Hizmeti'nin bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b58b-137">In this case, the method returns an instance of the custom discovery service that was created before.</span></span> <span data-ttu-id="0b58b-138">`PublishedEndpoints`olan bir <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> eklenir uygulama bitiş noktalarının tümü içeren <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="0b58b-138">`PublishedEndpoints` is a <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> that contains all of the application endpoints that are added to the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="0b58b-139">Özel bulma hizmeti bu kendi iç listeyi doldurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b58b-139">The custom discovery service uses this to populate its internal list.</span></span> <span data-ttu-id="0b58b-140">Bir kullanıcı de diğer uç nokta meta verileri eklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b58b-140">A user can to add other endpoint metadata as well.</span></span>  
  
 <span data-ttu-id="0b58b-141">Son olarak, Program.cs açın.</span><span class="sxs-lookup"><span data-stu-id="0b58b-141">Lastly, open Program.cs.</span></span> <span data-ttu-id="0b58b-142">Unutmayın hem <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve `CustomDiscoveryExtension` ana bilgisayara eklenir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-142">Note that both the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and `CustomDiscoveryExtension` are added to the host.</span></span> <span data-ttu-id="0b58b-143">Bu yapılır ve ana bilgisayar üzerinden bulma iletileri almak bir uç nokta sonra uygulama için özel bulma hizmetini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b58b-143">Once this is done and the host has an endpoint over which to receive discovery messages, the application can use the custom discovery service.</span></span>  
  
 <span data-ttu-id="0b58b-144">İstemci hizmet adresini bilmeden bulamıyor olup olmadığına bakın.</span><span class="sxs-lookup"><span data-stu-id="0b58b-144">Observe that the client is able to find the service without knowing its address.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b58b-145">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="0b58b-145">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0b58b-146">Projeyi içeren çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="0b58b-146">Open the solution that contains the project.</span></span>  
  
2.  <span data-ttu-id="0b58b-147">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b58b-147">Build the project.</span></span>  
  
3.  <span data-ttu-id="0b58b-148">Hizmet uygulaması çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b58b-148">Run the service application.</span></span>  
  
4.  <span data-ttu-id="0b58b-149">İstemci uygulaması çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b58b-149">Run the client application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b58b-150">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b58b-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b58b-151">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0b58b-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0b58b-152">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0b58b-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b58b-153">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0b58b-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
