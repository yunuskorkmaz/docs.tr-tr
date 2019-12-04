---
title: Hatalı Sözleşme
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: d8ea7010bef389b49f68c811565a641a580e230a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716954"
---
# <a name="fault-contract"></a><span data-ttu-id="1cdf0-102">Hatalı Sözleşme</span><span class="sxs-lookup"><span data-stu-id="1cdf0-102">Fault Contract</span></span>
<span data-ttu-id="1cdf0-103">Hata sözleşmesi örneği, bir hizmetten istemciye hata bilgilerini nasıl ileteceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="1cdf0-104">Örnek, bir iç özel durumu hataya dönüştürmek için hizmete eklenen bazı ek kodlar ile [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="1cdf0-105">İstemci, hizmette bir hata koşulunu zorlamak için bölme işlemini sıfıra gerçekleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cdf0-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1cdf0-107">Hesap makinesi sözleşmesi aşağıdaki örnek kodda gösterildiği gibi bir <xref:System.ServiceModel.FaultContractAttribute> içerecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="1cdf0-108"><xref:System.ServiceModel.FaultContractAttribute> özniteliği, `Divide` işleminin `MathFault`türünde bir hata döndürebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="1cdf0-109">Bir hata, serileştirilemeyebilir herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="1cdf0-110">Bu durumda `MathFault`, aşağıdaki gibi bir veri sözleşmeniz:</span><span class="sxs-lookup"><span data-stu-id="1cdf0-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
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
  
 <span data-ttu-id="1cdf0-111">Aşağıdaki örnek kodda gösterildiği gibi, sıfıra bölme özel durumu oluştuğunda `Divide` yöntemi bir <xref:System.ServiceModel.FaultException%601> özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="1cdf0-112">Bu özel durum istemciye bir hata gönderilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-112">This exception results in a fault being sent to the client.</span></span>  
  
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
  
 <span data-ttu-id="1cdf0-113">İstemci kodu, sıfıra bölme isteyerek bir hata vererek zorlar.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="1cdf0-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1cdf0-115">Bir hata olarak bildirilen sıfıra göre bölmeyi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="1cdf0-116">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="1cdf0-117">İstemci bunu uygun `FaultException<MathFault>` özel durumunu ayırarak yapar:</span><span class="sxs-lookup"><span data-stu-id="1cdf0-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="1cdf0-118">Varsayılan olarak, hizmet uygulamasının ayrıntılarının hizmetin güvenli sınırını aşmasını engellemek için beklenmeyen özel durumların ayrıntıları istemciye gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="1cdf0-119">`FaultContract`, bir sözleşmede hataları açıklamanıza ve istemciye iletilmek için uygun olan belirli özel durum türlerini işaretleyecek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="1cdf0-120">`FaultException<T>` tüketicilere hata göndermek için çalışma zamanı mekanizmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="1cdf0-121">Ancak, hata ayıklama sırasında bir hizmet hatasının iç ayrıntılarını görmek faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="1cdf0-122">Daha önce açıklanan Güvenli davranışı devre dışı bırakmak için, sunucuda işlenmeyen her özel durumun ayrıntılarının istemciye gönderilen hataya dahil edileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="1cdf0-123">Bu, <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> `true`ayarlanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="1cdf0-124">Aşağıdaki örnekte gösterildiği gibi kodda ya da yapılandırmada ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="1cdf0-125">Ayrıca, yapılandırma dosyasındaki hizmetin `behaviorConfiguration` özniteliği "Hesaplatorservicebehavior" olarak ayarlanarak, davranışın hizmetle ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="1cdf0-126">İstemcide bu tür hataları yakalamak için genel olmayan <xref:System.ServiceModel.FaultException> yakalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="1cdf0-127">Bu davranış yalnızca hata ayıklama amacıyla kullanılmalıdır ve üretimde hiçbir şekilde etkinleştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1cdf0-128">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1cdf0-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1cdf0-129">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1cdf0-130">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1cdf0-131">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1cdf0-132">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1cdf0-133">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-133">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1cdf0-134">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1cdf0-135">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1cdf0-135">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
