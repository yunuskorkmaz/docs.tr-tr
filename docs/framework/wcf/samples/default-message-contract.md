---
title: Varsayılan İleti Sözleşmesi
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 0a9b6ddb67f914c2c1c228f3042152ef9582f7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961796"
---
# <a name="default-message-contract"></a>Varsayılan İleti Sözleşmesi
Varsayılan Ileti sözleşmesi örneği, hizmet işlemlerine ve bu işlemlerden özel kullanıcı tanımlı bir iletinin geçirildiği bir hizmeti gösterir. Bu örnek, türü belirlenmiş bir hizmet olarak Hesaplayıcı arabirimi uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ' i temel alır. [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), çıkarma, çarpma ve bölme işlemlerinde kullanılan tek tek hizmet işlemleri yerine, bu örnek hem işlenen hem de işlecini içeren özel bir ileti geçirir ve bu işlemin sonucunu döndürür. aritmetik hesaplama.  
  
 İstemci bir konsol programıdır (. exe) ve hizmet kitaplığı (. dll) Internet Information Services (IIS) tarafından barındırılır. İstemci etkinliği konsol penceresinde görünür.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmette, Özel iletileri `MyMessage`kabul eden ve döndüren tek bir hizmet işlemi tanımlanmıştır. Bu örnekte istek ve yanıt iletileri aynı türde olsa da, gerektiğinde farklı ileti sözleşmeleri olabilir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Özel ileti `MyMessage` , ve<xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageContractAttribute> öznitelikleri<xref:System.ServiceModel.MessageBodyMemberAttribute> ile açıklanmış bir sınıfta tanımlanmıştır. Bu örnekte yalnızca üçüncü Oluşturucu kullanılır. İleti sözleşmelerini kullanmak, SOAP iletisi üzerinde tam denetim yapmanıza olanak sağlar. Bu örnekte, <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği bir soap üstbilgisine koymak `Operation` için kullanılır. İşlenenler `N1` <xref:System.ServiceModel.MessageBodyMemberAttribute> ve özniteliği uygulanmış olduğundan SOAP gövdesi içinde görüntülenir.`Result` `N2`  
  
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
  
 Uygulama sınıfı, `Calculate` hizmet işleminin kodunu içerir. `CalculateService` Sınıfı, istek iletisinden işlenen ve işleci edinir ve aşağıdaki örnek kodda gösterildiği gibi istenen hesaplamanın sonucunu içeren bir yanıt iletisi oluşturur.  
  
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
  
 İstemci için üretilen istemci kodu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracıyla oluşturulmuştur. Araç, gerekirse oluşturulan istemci kodunda ileti sözleşme türlerini otomatik olarak oluşturur. İleti sözleşmelerinin oluşturulmasını zorlamak için komutseçeneğibelirtilebilir.`/messageContract`  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Aşağıdaki örnek kod, `MyMessage` iletisini kullanarak istemciyi gösterir.  
  
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
  
 Örneği çalıştırdığınızda, hesaplamalar istemci konsolu penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Bu noktada, istemci ve hizmet işlemi arasında özel kullanıcı tanımlı iletiler geçirilir. İleti anlaşması, işlenen ve sonuçların ileti gövdesinde olduğunu ve işlecin bir ileti üstbilgisinde olduğunu tanımlandı. İleti günlüğe kaydetme, bu ileti yapısını gözlemleyecek şekilde yapılandırılabilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
