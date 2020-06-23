---
title: DataContractSerializer Örneği
description: Bu örnekte, veri sözleşmesi sınıfları için genel serileştirme ve seri durumdan çıkarma hizmetleri gerçekleştiren WCF 'de DataContractSerializer gösterilmektedir.
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: c2f62c8926f09e2d4cdea1941909e7d8f59c43a0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244419"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="a9830-103">DataContractSerializer Örneği</span><span class="sxs-lookup"><span data-stu-id="a9830-103">DataContractSerializer Sample</span></span>
<span data-ttu-id="a9830-104">DataContractSerializer örneği, <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesi sınıfları için genel serileştirme ve seri durumdan çıkarma hizmetlerini gerçekleştiren öğesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9830-104">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="a9830-105">Örnek, bir `Record` nesnesi oluşturur, bunu bir bellek akışına serileştirir ve ' `Record` nin kullanımını göstermek için bellek akışını başka bir nesneye geri çıkarır <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="a9830-105">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="a9830-106">Örnek daha sonra, `Record` yazıcının Serileştirmeyi nasıl etkilediğini göstermek için bir ikili yazıcı kullanarak nesneyi serileştirir.</span><span class="sxs-lookup"><span data-stu-id="a9830-106">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9830-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a9830-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a9830-108">İçin veri sözleşmesi `Record` Aşağıdaki örnek kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a9830-108">The data contract for `Record` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="a9830-109">Örnek kod, `Record` `record1` daha sonra nesnesini görüntüleyen adlı bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a9830-109">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="a9830-110">Örnek daha sonra <xref:System.Runtime.Serialization.DataContractSerializer> bir bellek akışına seri hale getirmek için öğesini kullanır `record1` .</span><span class="sxs-lookup"><span data-stu-id="a9830-110">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="a9830-111">Ardından örnek, <xref:System.Runtime.Serialization.DataContractSerializer> bellek akışını yeni bir nesneye geri çıkarmak için öğesini kullanır `Record` ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a9830-111">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="a9830-112">Varsayılan olarak, `DataContractSerializer` NESNELERI XML 'nin metinsel gösterimini kullanarak bir akışa kodluyor.</span><span class="sxs-lookup"><span data-stu-id="a9830-112">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="a9830-113">Ancak, XML 'nin kodlamasını farklı bir yazıcıya geçirerek de etkileyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9830-113">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="a9830-114">Örnek, çağırarak bir ikili yazıcı oluşturur <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A> .</span><span class="sxs-lookup"><span data-stu-id="a9830-114">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="a9830-115">Daha sonra, aradığında, yazıcı ve kayıt nesnesini serileştiriciye geçirir <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A> .</span><span class="sxs-lookup"><span data-stu-id="a9830-115">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="a9830-116">Son olarak, örnek, yazıcıyı ve akış uzunlularındaki raporları temizler.</span><span class="sxs-lookup"><span data-stu-id="a9830-116">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="a9830-117">Örneği çalıştırdığınızda, özgün kayıt ve seri durumdan çıkarılan kayıt görüntülenir ve ardından metin kodlamasının uzunluğu ile ikili kodlama arasındaki karşılaştırma gelir.</span><span class="sxs-lookup"><span data-stu-id="a9830-117">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="a9830-118">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a9830-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a9830-119">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a9830-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a9830-120">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a9830-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a9830-121">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a9830-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a9830-122">Örneği çalıştırmak için client\bin\client.exe yazarak istemciyi komut isteminden başlatın.</span><span class="sxs-lookup"><span data-stu-id="a9830-122">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a9830-123">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9830-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a9830-124">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a9830-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a9830-125">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a9830-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9830-126">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a9830-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
