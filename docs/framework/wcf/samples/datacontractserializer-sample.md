---
title: DataContractSerializer Örneği
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 59bbeb4091c101efeac4e0562f0e3cbd5a8b5f79
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716360"
---
# <a name="datacontractserializer-sample"></a>DataContractSerializer Örneği
DataContractSerializer örneği, veri sözleşmesi sınıfları için genel serileştirme ve seri durumdan çıkarma hizmetlerini gerçekleştiren <xref:System.Runtime.Serialization.DataContractSerializer>gösterir. Örnek, bir `Record` nesnesi oluşturur, bunu bir bellek akışına serileştirir ve <xref:System.Runtime.Serialization.DataContractSerializer>kullanımını göstermek için bellek akışını başka bir `Record` nesnesine yeniden serileştirir. Örnek daha sonra, yazıcının Serileştirmeyi nasıl etkilediğini göstermek için bir ikili yazıcı kullanarak `Record` nesnesini serileştirir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 `Record` için veri sözleşmesi aşağıdaki örnek kodda gösterilmiştir.  
  
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
  
 Örnek kod, `record1` adlı bir `Record` nesnesi oluşturur ve sonra nesneyi görüntüler.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Örnek daha sonra `record1` bir bellek akışına seri hale getirmek için <xref:System.Runtime.Serialization.DataContractSerializer> kullanır.  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Ardından örnek, bellek akışının serisini yeni bir `Record` nesnesine geri yüklemek için <xref:System.Runtime.Serialization.DataContractSerializer> kullanır ve onu görüntüler.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Varsayılan olarak `DataContractSerializer`, XML 'nin metinsel gösterimini kullanarak nesneleri bir akışa kodluyor. Ancak, XML 'nin kodlamasını farklı bir yazıcıya geçirerek de etkileyebilirsiniz. Örnek, <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>çağırarak bir ikili yazıcı oluşturur. Daha sonra, <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>çağırdığında yazıcı ve kayıt nesnesini serileştiriciye geçirir. Son olarak, örnek, yazıcıyı ve akış uzunlularındaki raporları temizler.  
  
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
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği çalıştırmak için client\bin\client.exeyazarak istemciyi komut isteminden başlatın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
