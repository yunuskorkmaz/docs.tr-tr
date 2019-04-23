---
title: Varsayılan İleti Sözleşmesi
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 267cdffdc532aaa2b31de835c31d23e93aca8c54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975942"
---
# <a name="default-message-contract"></a>Varsayılan İleti Sözleşmesi
Varsayılan ileti anlaşması örnek, kullanıcı tarafından tanımlanan özel bir ileti için ve hizmet işlemlerine geçirildiği hizmet gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) belirlenmiş bir hizmet olarak bir hesap makinesi arabirimi uygulayan. Toplama, çıkarma, çarpma ve bölme kullanılan bireysel hizmet işlemlerinde yerine [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), bu örnek, hem işlenen hem de işleç içeren ve döndüren özel bir ileti geçirir. aritmetik hesaplama sonucu.  
  
 İstemci bir konsol programı (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmet kitaplığı (.dll). İstemci etkinliği konsol penceresinde görünür.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hizmetinde kabul eder ve özel ileti türü döndüren bir tek hizmet işlemi tanımlanan `MyMessage`. Bu örnekte, istek ve yanıt iletilerinin aynı türde olsa da, bunlar farklı ileti sözleşmeleri Elbette gerekirse olabilir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Özel ileti `MyMessage` ile ek açıklamalı bir sınıfta tanımlanan <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri. Yalnızca üçüncü Oluşturucu, bu örnekte kullanılır. İleti sözleşmeleri kullanılıyor, SOAP iletisi üzerinde tam denetimle alıştırma sağlar. Bu örnekte <xref:System.ServiceModel.MessageHeaderAttribute> yerleştirmek için kullanılan öznitelik `Operation` bir SOAP üst bilgisindeki. İşlenenler `N1`, `N2` ve `Result` SOAP gövdesi içinde sahip oldukları görünür <xref:System.ServiceModel.MessageBodyMemberAttribute> özniteliği uygulandı.  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,   
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 Uygulama sınıfı kodunu içeren `Calculate` hizmet işlemi. `CalculateService` Sınıfı, işleci ve işlenenleri istek iletisi alır ve aşağıdaki örnek kodda gösterildiği gibi istenen hesaplama sonucunu içeren bir yanıt iletisi oluşturur.  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 İstemcisi için oluşturulan istemci kodu oluşturulurken [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı. Araç, otomatik olarak oluşturulan istemci kodu gerekiyorsa, ileti anlaşması türleri oluşturur. `/messageContract` İleti sözleşmeleri zorlamanızı komut seçeneği belirtilebilir.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Aşağıdaki örnek kodu kullanarak istemciyi gösterir `MyMessage` ileti.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage() 
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 Örneği çalıştırdığında hesaplamalar istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Bu noktada, kullanıcı tanımlı özel iletiler, istemci ve hizmet işlemi arasında geçti. İşlenenler ve sonuçları ileti gövdesinde olduğunu ve işleci bir ileti üstbilgisinde olduğunu tanımlanan ileti sözleşmesi. İleti günlüğe kaydetme, bu ileti yapı gözlemlemek için yapılandırılabilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
