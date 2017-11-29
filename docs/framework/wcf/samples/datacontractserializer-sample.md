---
title: "DataContractSerializer Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
caps.latest.revision: "37"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2cb8ae40cb62c65bf6dbd394055fffadd7202f16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="datacontractserializer-sample"></a>DataContractSerializer Örneği
DataContractSerializer örneği gösterilmektedir <xref:System.Runtime.Serialization.DataContractSerializer>, genel serileştirme gerçekleştirir ve seri durumdan çıkarma Hizmetleri için veri sözleşmesi sınıfları. Bir örnek oluşturur bir `Record` nesne, bir bellek akışa serileştirir ve bellek akışa geri başka çıkarır `Record` kullanımını göstermek için nesne <xref:System.Runtime.Serialization.DataContractSerializer>. Örnek sonra serileştiren `Record` yazan serileştirme nasıl etkilediğini göstermek için bir ikili yazıcıyı kullanarak nesne.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Veri sözleşmesi için `Record` aşağıdaki örnek kodda gösterilir.  
  
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
  
 Örnek kod oluşturur bir `Record` adlı nesne `record1` nesne görüntüler.  
  
```  
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Örnek sonra kullanır <xref:System.Runtime.Serialization.DataContractSerializer> serileştirilecek `record1` bellek akışa.  
  
```  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Ardından, örnek kullanır <xref:System.Runtime.Serialization.DataContractSerializer> bellek akışı geri yeni seri durumdan çıkarılacak `Record` nesne ve görüntüler.  
  
```  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Varsayılan olarak, `DataContractSerializer` nesneleri XML metinsel gösterimini kullanarak bir akışa kodlar. Ancak, farklı bir yazıcı geçirerek XML kodlaması etkileyebilir. Çağırarak ikili yazan bir örnek oluşturur <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Çağırdığında bunu ardından yazıcı ve kayıt nesnesi için seri hale getirici geçirir <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Son olarak, örnek yazan temizler ve akışlar uzunluğu raporlar.  
  
```  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Örneği çalıştırdığınızda, özgün kaydı ve seri durumdan çıkarılmış kaydı, metin kodlama uzunluğu ve ikili kodlama arasında karşılaştırma tarafından izlenen görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Örneği çalıştırmak için istemci, komut isteminden client\bin\client.exe yazarak başlatın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
  
## <a name="see-also"></a>Ayrıca Bkz.
