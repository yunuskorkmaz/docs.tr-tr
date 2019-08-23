---
title: Bilinen Türler
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: ebcf5e4a1e6d587a3047e3faffb03847715f7a85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952866"
---
# <a name="known-types"></a><span data-ttu-id="aa521-102">Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="aa521-102">Known Types</span></span>
<span data-ttu-id="aa521-103">Bu örnekte, bir veri sözleşmesindeki türetilmiş türler hakkında bilgilerin nasıl belirtileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aa521-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="aa521-104">Veri sözleşmeleri, yapılandırılmış verileri hizmetlere ve hizmetlerden geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa521-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="aa521-105">Nesne odaklı programlamada, başka bir türden devralan bir tür özgün türün yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa521-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="aa521-106">Hizmet odaklı programlamada türler yerine şemalar iletilir ve bu nedenle, türler arasındaki ilişki korunmaz.</span><span class="sxs-lookup"><span data-stu-id="aa521-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="aa521-107"><xref:System.Runtime.Serialization.KnownTypeAttribute> Özniteliği türetilmiş türler hakkındaki bilgilerin veri sözleşmesine dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa521-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="aa521-108">Bu mekanizma kullanılmazsa, bir temel türün beklenildiği bir türetilmiş tür gönderilemez veya alınamaz.</span><span class="sxs-lookup"><span data-stu-id="aa521-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa521-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="aa521-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="aa521-110">Hizmet sözleşmesi, aşağıdaki örnek kodda gösterildiği gibi karmaşık sayılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa521-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="aa521-111">`ComplexNumber` Ve <xref:System.Runtime.Serialization.DataContractAttribute> ,istemcivehizmetarasındasınıfınhangialanlarınıngeçirilebileceğinigöstermekiçinsınıfınauygulanır.<xref:System.Runtime.Serialization.DataMemberAttribute></span><span class="sxs-lookup"><span data-stu-id="aa521-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="aa521-112">Türetilmiş `ComplexNumberWithMagnitude` sınıf, yerine kullanılabilir `ComplexNumber`.</span><span class="sxs-lookup"><span data-stu-id="aa521-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="aa521-113">`ComplexNumber` Türündeki <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa521-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
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
  
 <span data-ttu-id="aa521-114">Tür öğesinden `ComplexNumber` türetilir ,`Magnitude`ancak ek bir veri üyesi ekler. `ComplexNumberWithMagnitude`</span><span class="sxs-lookup"><span data-stu-id="aa521-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
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
  
 <span data-ttu-id="aa521-115">Bilinen türler özelliğini göstermek için hizmet, `ComplexNumberWithMagnitude` yalnızca toplama ve çıkarma için döndüren bir şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aa521-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="aa521-116">(Sözleşme `ComplexNumber`, ' i belirtse de, `KnownTypeAttribute` özniteliği nedeniyle bu izin verilir).</span><span class="sxs-lookup"><span data-stu-id="aa521-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="aa521-117">Çarpma ve bölme hala temel `ComplexNumber` türü döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="aa521-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
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
  
 <span data-ttu-id="aa521-118">İstemcide, hizmet sözleşmesinin ve veri sözleşmesinin her ikisi de, hizmet meta verilerinden [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan generatedClient.cs kaynak dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aa521-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="aa521-119">Özniteliği hizmetin veri sözleşmesinde belirtildiğinden, istemci, hizmeti kullanırken `ComplexNumber` hem hem `ComplexNumberWithMagnitude` de sınıflarını alabilir. <xref:System.Runtime.Serialization.KnownTypeAttribute></span><span class="sxs-lookup"><span data-stu-id="aa521-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="aa521-120">İstemci, bir `ComplexNumberWithMagnitude` olup olmadığını algılar ve uygun çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="aa521-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
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
  
 <span data-ttu-id="aa521-121">Örneği çalıştırdığınızda, işlemin istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aa521-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="aa521-122">Bir büyüklük, hizmetin uygulanma biçimi nedeniyle toplama ve çıkarma için yazdırılmıştır ancak çarpma ve bölme için değildir.</span><span class="sxs-lookup"><span data-stu-id="aa521-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="aa521-123">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="aa521-123">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aa521-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="aa521-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="aa521-125">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="aa521-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="aa521-126">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="aa521-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="aa521-127">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="aa521-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aa521-128">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="aa521-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aa521-129">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="aa521-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aa521-130">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="aa521-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa521-131">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="aa521-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
