---
title: DataContractSerializer Örneği
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 5e1a471cc4cc43b2aa36143eeecc18f7ec17b81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183786"
---
# <a name="datacontractserializer-sample"></a>DataContractSerializer Örneği
DataContractSerializer <xref:System.Runtime.Serialization.DataContractSerializer>örneği, veri sözleşmesi sınıfları için genel serileştirme ve deserialization hizmetlerini gerçekleştiren işeyliyi gösterir. Örnek bir `Record` nesne oluşturur, bir bellek akışına serileştirir ve bellek akışını başka `Record` bir nesneye geri <xref:System.Runtime.Serialization.DataContractSerializer>deserialize s. kullanımını göstermek için . Örnek daha sonra, `Record` yazarın serileştirmeyi nasıl etkilediğini göstermek için ikili bir yazar kullanarak nesneyi serihale eder.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Veri sözleşmesi `Record` aşağıdaki örnek kodda gösterilir.  
  
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
  
 Örnek kod, adı `Record` geçen `record1` bir nesne oluşturur ve nesneyi görüntüler.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Örnek daha sonra <xref:System.Runtime.Serialization.DataContractSerializer> bir `record1` bellek akışına serileştirmek için kullanır.  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Daha sonra, örnek <xref:System.Runtime.Serialization.DataContractSerializer> bellek akışını yeni `Record` bir nesneye yeniden deserialize etmek için kullanır ve görüntüler.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Varsayılan olarak, `DataContractSerializer` XML'in metinsel bir temsilini kullanarak nesneleri bir akışa kodlar. Ancak, farklı bir yazar geçirerek XML kodlama etkileyebilir. Örnek arayarak <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>bir ikili yazar oluşturur. Daha sonra yazar ve kayıt nesnesi serializer <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>için ne zaman çağırır geçer. Son olarak, örnek yazar ve akışların uzunluğu raporları floş.  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Örneği çalıştırdığınızda, özgün kayıt ve deserialized kayıt görüntülenir ve ardından metin kodlama uzunluğu ile ikili kodlama arasındaki karşılaştırma yapılır. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği çalıştırmak için istemci\bin\client.exe yazarak istemci komut isteminden başlatın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
