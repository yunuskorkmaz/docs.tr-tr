---
title: Varsayılan Hizmet Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 798231cbfddf17dd63a61f3e2a07a6490289e56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183758"
---
# <a name="default-service-behavior"></a><span data-ttu-id="a86b8-102">Varsayılan Hizmet Davranışı</span><span class="sxs-lookup"><span data-stu-id="a86b8-102">Default Service Behavior</span></span>
<span data-ttu-id="a86b8-103">Bu örnek, hizmet davranış ayarlarının nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="a86b8-104">Örnek, hizmet sözleşmesini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) `ICalculator` dayanır.</span><span class="sxs-lookup"><span data-stu-id="a86b8-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="a86b8-105">Bu örnek, hizmet davranışlarını ve işleyiş <xref:System.ServiceModel.ServiceBehaviorAttribute> davranışlarını ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerini kullanarak açıkça tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a86b8-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="a86b8-106">Yapılandırma dosyalarındaki veya zorunlu olarak koddaki (bu örnekte gösterildiği gibi) davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a86b8-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="a86b8-107">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="a86b8-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a86b8-108">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a86b8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a86b8-109">Hizmet sınıfı, aşağıdaki kod örneğinde gösterildiği <xref:System.ServiceModel.ServiceBehaviorAttribute> gibi <xref:System.ServiceModel.OperationBehaviorAttribute> davranışları belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="a86b8-110">Belirtilen tüm değerler varsayılandeğerlerdir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-110">All values specified are the defaults.</span></span>  
  
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
  
 <span data-ttu-id="a86b8-111">Hizmet davranışları öznitelik <xref:System.ServiceModel.ServiceBehaviorAttribute> ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="a86b8-112">Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a86b8-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="a86b8-113">Hizmet davranışı</span><span class="sxs-lookup"><span data-stu-id="a86b8-113">Service behavior</span></span>|<span data-ttu-id="a86b8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a86b8-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="a86b8-115">Müşterinin isteği üzerine bir oturumu otomatik olarak kapatır.</span><span class="sxs-lookup"><span data-stu-id="a86b8-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="a86b8-116">Her hizmet örneği için eşzamanlılık modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="a86b8-117">Örnek bağlam modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="a86b8-118">Sağlanan eşitleme bağlamını kullanıp kullanmayacağını, ayarlanmış olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a86b8-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="a86b8-119">Windows Forms uygulamalarında bir uygulama `WindowsFormsSynchronizationContext` kullanıp kullanmayacağını denetlemek istediğinizde bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="a86b8-120">Genel işlenmemiş yürütme özel durumlarının a'ya `Fault<string>` dönüştürülüp hata iletisi olarak gönderilip gönderilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a86b8-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="a86b8-121">Hareketler için yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="a86b8-122">Beklenmeyen ileti üstbilgilerinin hata durumuna neden olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a86b8-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="a86b8-123">İşlem davranışları öznitelik kullanılarak <xref:System.ServiceModel.OperationBehaviorAttribute> belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="a86b8-124">Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a86b8-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="a86b8-125">Operasyon Davranışı</span><span class="sxs-lookup"><span data-stu-id="a86b8-125">Operation Behavior</span></span>|<span data-ttu-id="a86b8-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a86b8-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="a86b8-127">Hizmet işleminin tamamlanmasının geçerli hareketi gerçekleştirip işlemediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a86b8-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="a86b8-128">Hizmet işleminin istemci tarafından akan bir harekette kaydolup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a86b8-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="a86b8-129">Hizmet işleminin arayanın kimliğini taklit edip etmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a86b8-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="a86b8-130">Hizmet örneklerinin hizmet işlem çağrısının başında mı yoksa sonunda mı geri dönüştürülür olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="a86b8-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="a86b8-131">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a86b8-132">Aramalar arasındaki gecikme, hizmet işlemlerinde `System.Threading.Thread.Sleep()` yapılan aramaların sonucudur.</span><span class="sxs-lookup"><span data-stu-id="a86b8-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="a86b8-133">Davranış örneklerinin geri kalanı bu davranışları daha ayrıntılı olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="a86b8-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="a86b8-134">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a86b8-135">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a86b8-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a86b8-136">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="a86b8-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a86b8-137">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a86b8-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a86b8-138">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a86b8-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a86b8-139">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a86b8-140">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a86b8-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a86b8-141">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="a86b8-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a86b8-142">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="a86b8-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
