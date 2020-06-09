---
title: DataContractSerializer Örneği
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 07c6d3b10f2a0478f8fb3835f0b040668c5013ce
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600016"
---
# <a name="datacontractserializer-sample"></a>DataContractSerializer Örneği
DataContractSerializer örneği, <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesi sınıfları için genel serileştirme ve seri durumdan çıkarma hizmetlerini gerçekleştiren öğesini gösterir. Örnek, bir `Record` nesnesi oluşturur, bunu bir bellek akışına serileştirir ve ' `Record` nin kullanımını göstermek için bellek akışını başka bir nesneye geri çıkarır <xref:System.Runtime.Serialization.DataContractSerializer> . Örnek daha sonra, `Record` yazıcının Serileştirmeyi nasıl etkilediğini göstermek için bir ikili yazıcı kullanarak nesneyi serileştirir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 İçin veri sözleşmesi `Record` Aşağıdaki örnek kodda gösterilmiştir.  
  
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
  
 Örnek kod, `Record` `record1` daha sonra nesnesini görüntüleyen adlı bir nesne oluşturur.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Örnek daha sonra <xref:System.Runtime.Serialization.DataContractSerializer> bir bellek akışına seri hale getirmek için öğesini kullanır `record1` .  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Ardından örnek, <xref:System.Runtime.Serialization.DataContractSerializer> bellek akışını yeni bir nesneye geri çıkarmak için öğesini kullanır `Record` ve görüntüler.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Varsayılan olarak, `DataContractSerializer` NESNELERI XML 'nin metinsel gösterimini kullanarak bir akışa kodluyor. Ancak, XML 'nin kodlamasını farklı bir yazıcıya geçirerek de etkileyebilirsiniz. Örnek, çağırarak bir ikili yazıcı oluşturur <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A> . Daha sonra, aradığında, yazıcı ve kayıt nesnesini serileştiriciye geçirir <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A> . Son olarak, örnek, yazıcıyı ve akış uzunlularındaki raporları temizler.  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Örneği çalıştırdığınızda, özgün kayıt ve seri durumdan çıkarılan kayıt görüntülenir ve ardından metin kodlamasının uzunluğu ile ikili kodlama arasındaki karşılaştırma gelir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği çalıştırmak için client\bin\client.exeyazarak istemciyi komut isteminden başlatın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
