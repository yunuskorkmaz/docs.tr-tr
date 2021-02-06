---
description: 'Daha fazla bilgi edinin: varsayılan hizmet davranışı'
title: Varsayılan Hizmet Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: a0b83180c9ab758cb7a8db7f92a8bf0c081e4489
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631989"
---
# <a name="default-service-behavior"></a><span data-ttu-id="bb71b-103">Varsayılan Hizmet Davranışı</span><span class="sxs-lookup"><span data-stu-id="bb71b-103">Default Service Behavior</span></span>

<span data-ttu-id="bb71b-104">Bu örnek, hizmet davranışı ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb71b-104">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="bb71b-105">Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="bb71b-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="bb71b-106">Bu örnek, ve özniteliklerini kullanarak hizmet davranışlarını ve işlem davranışlarını açıkça tanımlar <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="bb71b-106">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="bb71b-107">Yapılandırma dosyalarındaki veya koddaki imperatively (Bu örnekte gösterildiği gibi) davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb71b-107">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="bb71b-108">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="bb71b-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb71b-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="bb71b-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bb71b-110">Hizmet sınıfı, <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> Aşağıdaki kod örneğinde gösterildiği gibi, ve içeren davranışları belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb71b-110">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="bb71b-111">Belirtilen tüm değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="bb71b-111">All values specified are the defaults.</span></span>  
  
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
  
 <span data-ttu-id="bb71b-112">Hizmet davranışları <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bb71b-112">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="bb71b-113">Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb71b-113">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="bb71b-114">Hizmet davranışı</span><span class="sxs-lookup"><span data-stu-id="bb71b-114">Service behavior</span></span>|<span data-ttu-id="bb71b-115">Description</span><span class="sxs-lookup"><span data-stu-id="bb71b-115">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="bb71b-116">İstemci isteğindeki bir oturumu otomatik olarak kapatır.</span><span class="sxs-lookup"><span data-stu-id="bb71b-116">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="bb71b-117">Her hizmet örneği için eşzamanlılık modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb71b-117">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="bb71b-118">Örnek bağlam modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb71b-118">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="bb71b-119">Bir ayarlanmışsa, belirtilen eşitleme bağlamının kullanılıp kullanılmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="bb71b-119">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="bb71b-120">Windows Forms uygulamalarında kullanmak isteyip istemediğinizi denetlemek istediğinizde bunu kullanın `WindowsFormsSynchronizationContext` .</span><span class="sxs-lookup"><span data-stu-id="bb71b-120">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="bb71b-121">Genel işlenmemiş yürütme özel durumlarının bir hata iletisi olarak dönüştürülüp dönüştürülmeyeceğini `Fault<string>` ve gönderilip gönderilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bb71b-121">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="bb71b-122">İşlemler için yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb71b-122">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="bb71b-123">Beklenmeyen ileti üstbilgilerinin hata koşuluna neden olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="bb71b-123">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="bb71b-124">İşlem davranışları özniteliği kullanılarak belirtilir <xref:System.ServiceModel.OperationBehaviorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="bb71b-124">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="bb71b-125">Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb71b-125">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="bb71b-126">İşlem davranışı</span><span class="sxs-lookup"><span data-stu-id="bb71b-126">Operation Behavior</span></span>|<span data-ttu-id="bb71b-127">Description</span><span class="sxs-lookup"><span data-stu-id="bb71b-127">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="bb71b-128">Hizmet işleminin tamamlanmasının geçerli işlemi yürütmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bb71b-128">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="bb71b-129">Hizmet işleminin istemci tarafından akışlı bir işlemde görüntülenip görüntülenmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bb71b-129">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="bb71b-130">Hizmet işleminin arayanın kimliğini taklit etmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bb71b-130">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="bb71b-131">Hizmet örneklerinin, hizmet işlemi çağrısının başlangıcında veya sonunda geri dönüştürülüp dönüştürülmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bb71b-131">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="bb71b-132">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bb71b-132">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bb71b-133">Çağrılar arasındaki gecikme, `System.Threading.Thread.Sleep()` hizmet işlemlerinde yapılan çağrıların sonucudur.</span><span class="sxs-lookup"><span data-stu-id="bb71b-133">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="bb71b-134">Davranış örneklerinin geri kalanı bu davranışları daha ayrıntılı bir şekilde açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb71b-134">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="bb71b-135">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bb71b-135">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bb71b-136">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bb71b-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bb71b-137">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="bb71b-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bb71b-138">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="bb71b-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="bb71b-139">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="bb71b-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bb71b-140">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb71b-140">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bb71b-141">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bb71b-141">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bb71b-142">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bb71b-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bb71b-143">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="bb71b-143">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
