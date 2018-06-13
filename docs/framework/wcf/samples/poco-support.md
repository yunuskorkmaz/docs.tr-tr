---
title: POCO Desteği
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: ab95469afa53bd0b27efc451875d4912db74a45a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501992"
---
# <a name="poco-support"></a><span data-ttu-id="cf46a-102">POCO Desteği</span><span class="sxs-lookup"><span data-stu-id="cf46a-102">POCO Support</span></span>
<span data-ttu-id="cf46a-103">Bu örnek işaretsiz türleri için seri hale getirme destek gösterir; diğer bir deyişle, kendisine serileştirme özniteliklerini uygulanmamış, türleri bazen başvurduğu düz eski CLR nesnesi (POCO) türleri olarak.</span><span class="sxs-lookup"><span data-stu-id="cf46a-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="cf46a-104"><xref:System.Runtime.Serialization.DataContractSerializer> Veri sözleşmesi varsayılan bir oluşturucuya sahip tüm ortak işaretsiz türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf46a-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a default constructor.</span></span> <span data-ttu-id="cf46a-105">Veri sözleşmeleri için ve Hizmetleri'nden yapılandırılmış veri iletmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf46a-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="cf46a-106">İşaretsiz türleri hakkında daha fazla bilgi için bkz: [seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="cf46a-106">For more information about unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="cf46a-107">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), ancak yerine basit sayısal türler karmaşık numaralar kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf46a-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="cf46a-108">Ayrıca benzer [temel veri sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md) , durumlar dışında örnek <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="cf46a-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="cf46a-109">Internet Information Services (IIS) tarafından barındırılan hizmetindeki ve istemcinin bir konsol uygulaması (.exe).</span><span class="sxs-lookup"><span data-stu-id="cf46a-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf46a-110">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="cf46a-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cf46a-111">`ComplexNumber` Sınıfı kullanılıyor `ServiceContract`.</span><span class="sxs-lookup"><span data-stu-id="cf46a-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="cf46a-112">`ComplexNumber` Türü yok <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> , aşağıdaki örnek kodda gösterildiği gibi öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="cf46a-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="cf46a-113">Varsayılan olarak, tüm genel özellikleri ve alanları serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="cf46a-113">By default, all public properties and fields are serialized.</span></span>  
  
```  
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cf46a-114">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="cf46a-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cf46a-115">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf46a-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cf46a-116">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf46a-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="cf46a-117">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf46a-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cf46a-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf46a-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf46a-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cf46a-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cf46a-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cf46a-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf46a-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cf46a-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="cf46a-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf46a-122">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [<span data-ttu-id="cf46a-123">Seri Hale Getirilebilir Türler</span><span class="sxs-lookup"><span data-stu-id="cf46a-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
