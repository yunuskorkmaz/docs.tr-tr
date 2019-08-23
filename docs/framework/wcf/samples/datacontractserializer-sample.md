---
title: DataContractSerializer Örneği
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: e4a3779b8351ae30f7c316d37952f208a287d5e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961823"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="d517e-102">DataContractSerializer Örneği</span><span class="sxs-lookup"><span data-stu-id="d517e-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="d517e-103">DataContractSerializer örneği, veri sözleşmesi <xref:System.Runtime.Serialization.DataContractSerializer>sınıfları için genel serileştirme ve seri durumdan çıkarma hizmetlerini gerçekleştiren öğesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d517e-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="d517e-104">Örnek, bir `Record` nesnesi oluşturur, bunu bir bellek akışına serileştirir ve ' nin kullanımını <xref:System.Runtime.Serialization.DataContractSerializer>göstermek için bellek akışını başka bir `Record` nesneye geri çıkarır.</span><span class="sxs-lookup"><span data-stu-id="d517e-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="d517e-105">Örnek daha sonra, yazıcının Serileştirmeyi nasıl etkilediğini göstermek için bir ikili yazıcı kullanarak `Record` nesneyi serileştirir.</span><span class="sxs-lookup"><span data-stu-id="d517e-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d517e-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d517e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d517e-107">İçin `Record` veri sözleşmesi aşağıdaki örnek kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d517e-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```csharp  
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
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 <span data-ttu-id="d517e-108">Örnek kod, daha sonra `Record` nesnesini görüntüleyen `record1` adlı bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d517e-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="d517e-109">Örnek daha sonra bir bellek <xref:System.Runtime.Serialization.DataContractSerializer> akışına seri `record1` hale getirmek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d517e-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="d517e-110">Ardından örnek, bellek akışını yeni <xref:System.Runtime.Serialization.DataContractSerializer> `Record` bir nesneye geri çıkarmak için öğesini kullanır ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d517e-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="d517e-111">Varsayılan olarak, nesneleri `DataContractSerializer` XML 'nin metinsel gösterimini kullanarak bir akışa kodluyor.</span><span class="sxs-lookup"><span data-stu-id="d517e-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="d517e-112">Ancak, XML 'nin kodlamasını farklı bir yazıcıya geçirerek de etkileyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d517e-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="d517e-113">Örnek, çağırarak <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>bir ikili yazıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d517e-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="d517e-114">Daha sonra, aradığında <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>, yazıcı ve kayıt nesnesini serileştiriciye geçirir.</span><span class="sxs-lookup"><span data-stu-id="d517e-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="d517e-115">Son olarak, örnek, yazıcıyı ve akış uzunlularındaki raporları temizler.</span><span class="sxs-lookup"><span data-stu-id="d517e-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="d517e-116">Örneği çalıştırdığınızda, özgün kayıt ve seri durumdan çıkarılan kayıt görüntülenir ve ardından metin kodlamasının uzunluğu ile ikili kodlama arasındaki karşılaştırma gelir.</span><span class="sxs-lookup"><span data-stu-id="d517e-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="d517e-117">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d517e-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d517e-118">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d517e-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d517e-119">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d517e-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d517e-120">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d517e-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d517e-121">Örneği çalıştırmak için client\bin\client.exeyazarak istemciyi komut isteminden başlatın.</span><span class="sxs-lookup"><span data-stu-id="d517e-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d517e-122">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d517e-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d517e-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d517e-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d517e-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="d517e-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d517e-125">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d517e-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
