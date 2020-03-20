---
title: Hatalı Sözleşme
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: c8e93f73d150132c9d6750b81ba2ade944808d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183661"
---
# <a name="fault-contract"></a><span data-ttu-id="ee9fc-102">Hatalı Sözleşme</span><span class="sxs-lookup"><span data-stu-id="ee9fc-102">Fault Contract</span></span>
<span data-ttu-id="ee9fc-103">Hata Sözleşmesi örneği, bir hizmetten istemciye hata bilgilerinin nasıl iletilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="ee9fc-104">Örnek, bir iç özel durumu hataya dönüştürmek için hizmete eklenen bazı ek kodlarla [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanır.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="ee9fc-105">İstemci, hizmette hata koşulunu zorlamak için bölmeyi sıfıra kadar gerçekleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee9fc-106">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ee9fc-107">Hesap makinesi sözleşmesi, aşağıdaki <xref:System.ServiceModel.FaultContractAttribute> örnek kodda gösterildiği gibi bir sözleşme içerecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="ee9fc-108">Öznitelik, <xref:System.ServiceModel.FaultContractAttribute> `Divide` işlemin bir tür `MathFault`hatası döndürebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="ee9fc-109">Bir hata seri hale getirilebilen herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="ee9fc-110">Bu durumda, `MathFault` aşağıdaki gibi bir veri sözleşmesi:</span><span class="sxs-lookup"><span data-stu-id="ee9fc-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 <span data-ttu-id="ee9fc-111">Yöntem, `Divide` aşağıdaki <xref:System.ServiceModel.FaultException%601> örnek kodda gösterildiği gibi sıfır özel durum bölme sayılsa özel bir durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="ee9fc-112">Bu özel durum, istemciye bir hata gönderilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-112">This exception results in a fault being sent to the client.</span></span>  
  
```csharp
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 <span data-ttu-id="ee9fc-113">İstemci kodu sıfır a bölme isteyerek bir hata zorlar.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="ee9fc-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ee9fc-115">Bölünmenin sıfır adedinin bir hata olarak rapor edildiğini görüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="ee9fc-116">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="ee9fc-117">İstemci bunu uygun `FaultException<MathFault>` özel durumu yakalayarak yapar:</span><span class="sxs-lookup"><span data-stu-id="ee9fc-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="ee9fc-118">Varsayılan olarak, hizmet uygulamasının ayrıntılarının hizmetin güvenli sınırından kaçmasını önlemek için beklenmeyen özel durumların ayrıntıları istemciye gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="ee9fc-119">`FaultContract`bir sözleşmedeki hataları açıklamak ve istemciye iletim için uygun olarak belirli türde özel durumları işaretlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="ee9fc-120">`FaultException<T>`tüketicilere hata göndermek için çalışma süresi mekanizmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="ee9fc-121">Ancak, hata ayıklama yaparken bir hizmet hatasıiç ayrıntılarını görmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="ee9fc-122">Daha önce açıklanan güvenli davranışı kapatmak için, sunucudaki işlenmemiş her özel durum ayrıntılarının istemciye gönderilen hataya dahil edilmesi gerektiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="ee9fc-123">Bu ayarlayarak <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> `true`gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="ee9fc-124">Aşağıdaki örnekte gösterildiği gibi kodolarak veya yapılandırmada ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="ee9fc-125">Ayrıca, yapılandırma dosyasındaki hizmetin özniteliğini "CalculatorServiceBehavior" olarak ayarlayarak `behaviorConfiguration` hizmetle ilişkili olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="ee9fc-126">İstemci üzerinde bu tür hataları yakalamak <xref:System.ServiceModel.FaultException> için, olmayan genel yakalanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="ee9fc-127">Bu davranış yalnızca hata ayıklama amacıyla kullanılmalı ve üretimde asla etkinleştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee9fc-128">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ee9fc-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ee9fc-129">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ee9fc-130">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ee9fc-131">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ee9fc-132">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee9fc-133">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-133">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ee9fc-134">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee9fc-135">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee9fc-135">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
