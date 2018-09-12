---
title: DataContractSerializer Örneği
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: ef1b01ff59fc32546dca8ed9c95f3a981ed408e3
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44698829"
---
# <a name="datacontractserializer-sample"></a>DataContractSerializer Örneği
DataContractSerializer örneği gösterir <xref:System.Runtime.Serialization.DataContractSerializer>gerçekleştirir genel serileştirme ve seri durumundan çıkarma için veri anlaşması sınıfları Hizmetleri. Örnek, oluşturur bir `Record` nesnesi, bir bellek akışa serileştirir ve bellek akışa geri başka bir'seri durumdan çıkarır `Record` kullanımını göstermek için nesne <xref:System.Runtime.Serialization.DataContractSerializer>. Ardından örnek serileştiren `Record` yazıcı serileştirme nasıl etkilediğini göstermek için bir ikili yazıcı kullanarak nesne.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Veri anlaşması için `Record` aşağıdaki örnek kodda gösterilmiştir.  
  
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
  
 Örnek kod oluşturur bir `Record` adlı nesne `record1` sonra nesneyi görüntüler.  
  
```  
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Ardından örnek kullanır <xref:System.Runtime.Serialization.DataContractSerializer> serileştirmek için `record1` içine bir bellek akış.  
  
```  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Ardından, örnek kullanır <xref:System.Runtime.Serialization.DataContractSerializer> bellek akışı geri yeni dosyaya seri durumdan çıkarılacak `Record` nesne ve görüntüler.  
  
```  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Varsayılan olarak, `DataContractSerializer` XML metinsel bir gösterimini kullanarak bir akış nesneleri kodlar. Ancak, farklı bir yazıcı geçirerek XML kodlaması etkileyebilir. Örnek bir ikili yazıcı çağırarak oluşturur <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Çağırdığında ardından yazıcı ve kayıt nesnesi için seri hale getirici arabimini <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Son olarak, örnek yazıcı temizler ve akışları uzunluğuna bildirir.  
  
```  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Örneği çalıştırdığınızda, orijinal kayıt ve seri durumdan çıkarılmış kayıt uzunluğu metin kodlama ile ikili kodlama arasında karşılaştırma tarafından izlenen görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Örneği çalıştırmak için Komut İstemi'nden istemci client\bin\client.exe yazarak başlatın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
  
## <a name="see-also"></a>Ayrıca Bkz.
