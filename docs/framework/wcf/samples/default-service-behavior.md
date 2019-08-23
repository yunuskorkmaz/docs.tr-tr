---
title: Varsayılan Hizmet Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 31c6e0b8bf2b058fbefa76f48ade39ba8e7def69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961763"
---
# <a name="default-service-behavior"></a><span data-ttu-id="5fef0-102">Varsayılan Hizmet Davranışı</span><span class="sxs-lookup"><span data-stu-id="5fef0-102">Default Service Behavior</span></span>
<span data-ttu-id="5fef0-103">Bu örnek, hizmet davranışı ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="5fef0-104">Örnek, `ICalculator` hizmet sözleşmesini uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlarken ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="5fef0-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="5fef0-105">Bu örnek, <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerini kullanarak hizmet davranışlarını ve işlem davranışlarını açıkça tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5fef0-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="5fef0-106">Yapılandırma dosyalarındaki veya koddaki imperatively (Bu örnekte gösterildiği gibi) davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fef0-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="5fef0-107">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="5fef0-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fef0-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="5fef0-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5fef0-109">Hizmet sınıfı, aşağıdaki kod örneğinde gösterildiği <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> gibi, ve içeren davranışları belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="5fef0-110">Belirtilen tüm değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-110">All values specified are the defaults.</span></span>  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="5fef0-111">Hizmet davranışları <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="5fef0-112">Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fef0-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="5fef0-113">Hizmet davranışı</span><span class="sxs-lookup"><span data-stu-id="5fef0-113">Service behavior</span></span>|<span data-ttu-id="5fef0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fef0-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="5fef0-115">İstemci isteğindeki bir oturumu otomatik olarak kapatır.</span><span class="sxs-lookup"><span data-stu-id="5fef0-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="5fef0-116">Her hizmet örneği için eşzamanlılık modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="5fef0-117">Örnek bağlam modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="5fef0-118">Bir ayarlanmışsa, belirtilen eşitleme bağlamının kullanılıp kullanılmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="5fef0-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="5fef0-119">Windows Forms uygulamalarında kullanmak `WindowsFormsSynchronizationContext` isteyip istemediğinizi denetlemek istediğinizde bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5fef0-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="5fef0-120">Genel işlenmemiş yürütme özel durumlarının bir `Fault<string>` hata iletisi olarak dönüştürülüp dönüştürülmeyeceğini ve gönderilip gönderilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="5fef0-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="5fef0-121">İşlemler için yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="5fef0-122">Beklenmeyen ileti üstbilgilerinin hata koşuluna neden olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5fef0-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="5fef0-123">İşlem davranışları <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="5fef0-124">Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fef0-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="5fef0-125">İşlem davranışı</span><span class="sxs-lookup"><span data-stu-id="5fef0-125">Operation Behavior</span></span>|<span data-ttu-id="5fef0-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fef0-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="5fef0-127">Hizmet işleminin tamamlanmasının geçerli işlemi yürütmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="5fef0-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="5fef0-128">Hizmet işleminin istemci tarafından akışlı bir işlemde görüntülenip görüntülenmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="5fef0-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="5fef0-129">Hizmet işleminin arayanın kimliğini taklit etmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="5fef0-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="5fef0-130">Hizmet örneklerinin, hizmet işlemi çağrısının başlangıcında veya sonunda geri dönüştürülüp dönüştürülmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="5fef0-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="5fef0-131">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5fef0-132">Çağrılar arasındaki gecikme, hizmet işlemlerinde `System.Threading.Thread.Sleep()` yapılan çağrıların sonucudur.</span><span class="sxs-lookup"><span data-stu-id="5fef0-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="5fef0-133">Davranış örneklerinin geri kalanı bu davranışları daha ayrıntılı bir şekilde açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fef0-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="5fef0-134">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5fef0-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5fef0-135">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5fef0-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5fef0-136">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5fef0-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5fef0-137">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5fef0-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5fef0-138">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5fef0-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fef0-139">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5fef0-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5fef0-140">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5fef0-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5fef0-141">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="5fef0-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5fef0-142">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5fef0-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
