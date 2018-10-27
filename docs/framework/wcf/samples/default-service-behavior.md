---
title: Varsayılan Hizmet Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 2c49c28d99bb3d300fd4589a088b2f086bdfd45d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184484"
---
# <a name="default-service-behavior"></a><span data-ttu-id="5fa0e-102">Varsayılan Hizmet Davranışı</span><span class="sxs-lookup"><span data-stu-id="5fa0e-102">Default Service Behavior</span></span>
<span data-ttu-id="5fa0e-103">Bu örnek, hizmet davranışı ayarları nasıl yapılandırılabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="5fa0e-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="5fa0e-105">Bu örnek hizmet davranışları ve işlem davranışları kullanarak açıkça tanımlar <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="5fa0e-106">(Bu örnekte gösterildiği gibi), yapılandırma dosyalarında veya kesin kod davranışlarını yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="5fa0e-107">Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fa0e-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5fa0e-109">Hizmet sınıfını içeren davranışlar belirtir <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="5fa0e-110">Belirtilen tüm varsayılan değerler.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-110">All values specified are the defaults.</span></span>  
  
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
  
 <span data-ttu-id="5fa0e-111">Hizmet davranışları ile belirtilen <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="5fa0e-112">Aşağıdaki tabloda bu davranışların bazılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="5fa0e-113">Hizmet davranışı</span><span class="sxs-lookup"><span data-stu-id="5fa0e-113">Service behavior</span></span>|<span data-ttu-id="5fa0e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fa0e-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="5fa0e-115">Otomatik olarak istemci isteğinde bir oturumu kapatır.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="5fa0e-116">Her hizmet örneği için eşzamanlılık modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="5fa0e-117">Örnek içerik modu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="5fa0e-118">Biri ayarlanmışsa belirtilen eşitleme bağlamı kullanılıp kullanılmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="5fa0e-119">Kullanılıp kullanılmayacağını kontrol etmek istediğinizde bunu kullanmak bir `WindowsFormsSynchronizationContext` Windows Forms uygulamalarındaki.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="5fa0e-120">Genel işlenmemiş yürütme özel durumları dönüştürülecek olup olmadığını belirler bir `Fault<string>` ve bir hata iletisi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="5fa0e-121">İşlem yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="5fa0e-122">Beklenmeyen ileti üstbilgileri hata durumuna neden olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="5fa0e-123">İşlem davranışları kullanarak belirtilen <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="5fa0e-124">Aşağıdaki tabloda bu davranışların bazılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="5fa0e-125">İşlem davranışı</span><span class="sxs-lookup"><span data-stu-id="5fa0e-125">Operation Behavior</span></span>|<span data-ttu-id="5fa0e-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fa0e-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="5fa0e-127">Hizmet işlemi tamamlama geçerli işlem yürütmeleri olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="5fa0e-128">Hizmet işlemi istemci akışı yapılan işlemler bir işlemde kaydeder olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="5fa0e-129">Hizmet işlemi çağıranın kimliğini taklit olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="5fa0e-130">Hizmet örnekleri başlangıç veya bitiş hizmet işlemi çağrısının geri olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="5fa0e-131">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5fa0e-132">Çağrılar arasındaki gecikmeyi çağrıları sonucudur `System.Threading.Thread.Sleep()` hizmet işlemlerinde yapılan.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="5fa0e-133">Davranış örnekleri geri kalanını Bu davranışların daha ayrıntılı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="5fa0e-134">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5fa0e-135">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5fa0e-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5fa0e-136">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5fa0e-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5fa0e-137">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5fa0e-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5fa0e-138">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5fa0e-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fa0e-139">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5fa0e-140">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5fa0e-141">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5fa0e-142">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a><span data-ttu-id="5fa0e-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fa0e-143">See Also</span></span>
