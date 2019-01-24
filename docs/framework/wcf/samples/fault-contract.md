---
title: Hatalı Sözleşme
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 39bb9b0ebd9feb6066c1c5e83128eb3a594d6d99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653937"
---
# <a name="fault-contract"></a><span data-ttu-id="87d62-102">Hatalı Sözleşme</span><span class="sxs-lookup"><span data-stu-id="87d62-102">Fault Contract</span></span>
<span data-ttu-id="87d62-103">Hatalı sözleşme örnek, bir istemci bir hizmet sağlayıcısından hata bilgiler iletmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="87d62-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="87d62-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), bazı ek kod bir hata için iç özel durum dönüştürmek için hizmet eklenir.</span><span class="sxs-lookup"><span data-stu-id="87d62-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="87d62-105">İstemci bir hata koşulu hizmette zorlamak için sıfır ile bölme gerçekleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="87d62-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87d62-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="87d62-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="87d62-107">Hesaplayıcı sözleşme içerecek şekilde değiştirilmiş bir <xref:System.ServiceModel.FaultContractAttribute> aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="87d62-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="87d62-108"><xref:System.ServiceModel.FaultContractAttribute> Özniteliği gösterir `Divide` işlemi türü bir hata döndürebilir `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="87d62-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="87d62-109">Seri hale getirilebilir herhangi bir türde bir hata olabilir.</span><span class="sxs-lookup"><span data-stu-id="87d62-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="87d62-110">Bu durumda, `MathFault` bir veri anlaşması aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="87d62-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
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
  
 <span data-ttu-id="87d62-111">`Divide` Yöntem bir <xref:System.ServiceModel.FaultException%601> aşağıdaki örnek kodda gösterildiği gibi özel bir bölme olduğunda sıfır özel durumun meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="87d62-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="87d62-112">Bu durum istemciye gönderilen bir hata ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="87d62-112">This exception results in a fault being sent to the client.</span></span>  
  
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
  
 <span data-ttu-id="87d62-113">İstemci kodu, bir hata sıfıra bölme isteyerek zorlar.</span><span class="sxs-lookup"><span data-stu-id="87d62-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="87d62-114">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="87d62-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="87d62-115">Bir hata bildirilen sıfıra bölme görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="87d62-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="87d62-116">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="87d62-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="87d62-117">İstemci uygun yakalama yapar `FaultException<MathFault>` özel durum:</span><span class="sxs-lookup"><span data-stu-id="87d62-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="87d62-118">Varsayılan olarak, beklenmeyen bir özel durumların ayrıntılarını istemciye hizmetinin güvenlik sınırının kaçış gelen hizmet uygulamasının Ayrıntılar önlemek için gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="87d62-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="87d62-119">`FaultContract` bir sözleşme hataları tanımlamak ve belirli türdeki özel durumlar iletilmesi istemci için uygun olarak işaretlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="87d62-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="87d62-120">`FaultException<T>` tüketicilere hataları göndermek için çalışma zamanı mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="87d62-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="87d62-121">Ancak, hata ayıklama sırasında iç hizmet hatası ayrıntılarını görmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="87d62-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="87d62-122">Daha önce açıklanan güvenli davranışı kapatmak için sunucu üzerindeki her bir işlenmeyen özel durum ayrıntılarını istemciye gönderilen hata eklenmelidir belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87d62-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="87d62-123">Bu ayarı gerçekleştirilir <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="87d62-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="87d62-124">Bunu aşağıdaki örnekte gösterildiği gibi yapılandırma veya kod ya da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87d62-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="87d62-125">Daha fazla davranış ayarlayarak hizmeti ile ilişkilendirilmelidir `behaviorConfiguration` hizmet yapılandırma dosyasında "CalculatorServiceBehavior" özniteliği.</span><span class="sxs-lookup"><span data-stu-id="87d62-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="87d62-126">İstemcide, genel olmayan bu tür hataları yakalamak için <xref:System.ServiceModel.FaultException> yakalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87d62-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="87d62-127">Bu davranış yalnızca hata ayıklama amacıyla kullanılmalıdır ve hiçbir zaman üretimde etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="87d62-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="87d62-128">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="87d62-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="87d62-129">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="87d62-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="87d62-130">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="87d62-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="87d62-131">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="87d62-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="87d62-132">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="87d62-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="87d62-133">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="87d62-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="87d62-134">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="87d62-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87d62-135">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="87d62-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="87d62-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87d62-136">See also</span></span>
