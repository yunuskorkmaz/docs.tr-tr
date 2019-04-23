---
title: Bilinen Türler
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: f2a5e6d5f5755d15bdc642ea3e64fb44af05cdab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768702"
---
# <a name="known-types"></a><span data-ttu-id="8325d-102">Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="8325d-102">Known Types</span></span>
<span data-ttu-id="8325d-103">Bu örnek, bir veri sözleşmesi türetilmiş türleri hakkında bilgi belirtmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="8325d-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="8325d-104">Veri sözleşmeleri, yapılandırılmış veriler için ve hizmetlerden geçmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="8325d-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="8325d-105">Nesne yönelimli programlama, başka bir türünden devralan bir tür, özgün türü yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8325d-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="8325d-106">Hizmet yönelimli programlama, türleri yerine şemaları iletildiği ve bu nedenle, türleri arasındaki ilişkiyi korunmaz.</span><span class="sxs-lookup"><span data-stu-id="8325d-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="8325d-107"><xref:System.Runtime.Serialization.KnownTypeAttribute> Özniteliği veri sözleşmesi içerisinde bulunan için türetilmiş türleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8325d-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="8325d-108">Bu mekanizma kullanılmıyorsa, türetilmiş bir tür gönderilen veya olamaz bir taban türü beklenirken aldı.</span><span class="sxs-lookup"><span data-stu-id="8325d-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8325d-109">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="8325d-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8325d-110">Aşağıdaki örnek kodda gösterildiği gibi hizmeti için hizmet sözleşmesi karmaşık sayılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="8325d-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
```csharp
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="8325d-111"><xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> uygulanan `ComplexNumber` sınıf hangi alanları istemci ile hizmet arasında geçirilen göstermek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="8325d-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="8325d-112">Türetilmiş `ComplexNumberWithMagnitude` sınıfı yerine kullanılabilir `ComplexNumber`.</span><span class="sxs-lookup"><span data-stu-id="8325d-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="8325d-113"><xref:System.Runtime.Serialization.KnownTypeAttribute> Özniteliği `ComplexNumber` türü bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8325d-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
[KnownType(typeof(ComplexNumberWithMagnitude))]  
public class ComplexNumber  
{  
    [DataMember]  
    public double Real = 0.0D;  
    [DataMember]  
    public double Imaginary = 0.0D;  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
 <span data-ttu-id="8325d-114">`ComplexNumberWithMagnitude` Tür türetilir `ComplexNumber` ancak bir ek veri üyesi ekler `Magnitude`.</span><span class="sxs-lookup"><span data-stu-id="8325d-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class ComplexNumberWithMagnitude : ComplexNumber  
{  
    public ComplexNumberWithMagnitude(double real, double imaginary) :  
        base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary*Imaginary  + Real*Real); }  
        set { throw new NotImplementedException(); }  
    }  
}  
```  
  
 <span data-ttu-id="8325d-115">Bilinen türler özelliği göstermek için hizmet gibi içinde uygulanan döndürdüğü şekilde bir `ComplexNumberWithMagnitude` yalnızca toplama ve çıkarma için.</span><span class="sxs-lookup"><span data-stu-id="8325d-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="8325d-116">(Sözleşme belirtmesine rağmen `ComplexNumber`, bu nedenle izin `KnownTypeAttribute` özniteliği).</span><span class="sxs-lookup"><span data-stu-id="8325d-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="8325d-117">Çarpma ve bölme hala temel dönüş `ComplexNumber` türü.</span><span class="sxs-lookup"><span data-stu-id="8325d-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
```csharp
public class DataContractCalculatorService : IDataContractCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real,  
                                      n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real,   
                                 n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        //Return the base type.  
        return new ComplexNumber(real1 + real2, imaginary1 +   
                                                  imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real,   
                                     -1*n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
        //Return the base type.  
        return new ComplexNumber(numerator.Real / denominator.Real,  
                                             numerator.Imaginary);  
    }  
}  
```  
  
 <span data-ttu-id="8325d-118">İstemcide, hem hizmet sözleşmesi hem de veri anlaşması tarafından üretilen kaynak dosyası generatedClient.cs tanımlanan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti meta veriler.</span><span class="sxs-lookup"><span data-stu-id="8325d-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="8325d-119">Çünkü <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği, hizmetin veri sözleşmede, istemci her ikisi de alabilir belirtilirse `ComplexNumber` ve `ComplexNumberWithMagnitude` hizmeti kullanırken sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8325d-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="8325d-120">İstemci var olup olmadığını algılayan bir `ComplexNumberWithMagnitude` ve uygun çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8325d-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
```csharp
// Create a client  
DataContractCalculatorClient client =   
    new DataContractCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber() { real = 1, imaginary = 2 };  
ComplexNumber value2 = new ComplexNumber() { real = 3, imaginary = 4 };  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.real, value1.imaginary, value2.real, value2.imaginary,  
    result.real, result.imaginary);  
if (result is ComplexNumberWithMagnitude)  
{  
    Console.WriteLine("Magnitude: {0}",   
        ((ComplexNumberWithMagnitude)result).Magnitude);  
}  
else  
{  
    Console.WriteLine("No magnitude was sent from the service");  
}  
```  
  
 <span data-ttu-id="8325d-121">Örneği çalıştırdığında istek ve yanıtların işlemin istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8325d-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="8325d-122">Bir boyuta, toplama ve çıkarma için yazdırılır ancak değil çarpma ve bölme biçimi nedeniyle için hizmet uygulanmıştır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8325d-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="8325d-123">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8325d-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
    Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8325d-124">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8325d-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8325d-125">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8325d-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8325d-126">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8325d-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8325d-127">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8325d-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8325d-128">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="8325d-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8325d-129">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8325d-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8325d-130">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8325d-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8325d-131">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8325d-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
