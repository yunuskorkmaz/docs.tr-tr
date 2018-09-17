---
title: DataContractSerializer Örneği
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: ef1b01ff59fc32546dca8ed9c95f3a981ed408e3
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743884"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="54f45-102">DataContractSerializer Örneği</span><span class="sxs-lookup"><span data-stu-id="54f45-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="54f45-103">DataContractSerializer örneği gösterir <xref:System.Runtime.Serialization.DataContractSerializer>gerçekleştirir genel serileştirme ve seri durumundan çıkarma için veri anlaşması sınıfları Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="54f45-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="54f45-104">Örnek, oluşturur bir `Record` nesnesi, bir bellek akışa serileştirir ve bellek akışa geri başka bir'seri durumdan çıkarır `Record` kullanımını göstermek için nesne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="54f45-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="54f45-105">Ardından örnek serileştiren `Record` yazıcı serileştirme nasıl etkilediğini göstermek için bir ikili yazıcı kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="54f45-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54f45-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="54f45-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="54f45-107">Veri anlaşması için `Record` aşağıdaki örnek kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="54f45-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return string.Format("Record: {0} {1} {2} = {3}", n1,  
            operation, n2, result);  
    }  
}  
```  
  
 <span data-ttu-id="54f45-108">Örnek kod oluşturur bir `Record` adlı nesne `record1` sonra nesneyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54f45-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```  
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="54f45-109">Ardından örnek kullanır <xref:System.Runtime.Serialization.DataContractSerializer> serileştirmek için `record1` içine bir bellek akış.</span><span class="sxs-lookup"><span data-stu-id="54f45-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="54f45-110">Ardından, örnek kullanır <xref:System.Runtime.Serialization.DataContractSerializer> bellek akışı geri yeni dosyaya seri durumdan çıkarılacak `Record` nesne ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54f45-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="54f45-111">Varsayılan olarak, `DataContractSerializer` XML metinsel bir gösterimini kullanarak bir akış nesneleri kodlar.</span><span class="sxs-lookup"><span data-stu-id="54f45-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="54f45-112">Ancak, farklı bir yazıcı geçirerek XML kodlaması etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="54f45-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="54f45-113">Örnek bir ikili yazıcı çağırarak oluşturur <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span><span class="sxs-lookup"><span data-stu-id="54f45-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="54f45-114">Çağırdığında ardından yazıcı ve kayıt nesnesi için seri hale getirici arabimini <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="54f45-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="54f45-115">Son olarak, örnek yazıcı temizler ve akışları uzunluğuna bildirir.</span><span class="sxs-lookup"><span data-stu-id="54f45-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="54f45-116">Örneği çalıştırdığınızda, orijinal kayıt ve seri durumdan çıkarılmış kayıt uzunluğu metin kodlama ile ikili kodlama arasında karşılaştırma tarafından izlenen görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="54f45-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="54f45-117">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="54f45-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="54f45-118">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="54f45-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="54f45-119">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54f45-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="54f45-120">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54f45-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="54f45-121">Örneği çalıştırmak için Komut İstemi'nden istemci client\bin\client.exe yazarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="54f45-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="54f45-122">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="54f45-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="54f45-123">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="54f45-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="54f45-124">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="54f45-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="54f45-125">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="54f45-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
  
## <a name="see-also"></a><span data-ttu-id="54f45-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54f45-126">See Also</span></span>
