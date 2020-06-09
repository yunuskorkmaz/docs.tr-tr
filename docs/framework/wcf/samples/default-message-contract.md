---
title: Varsayılan İleti Sözleşmesi
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 404fd9ddc911327bbc09c65d74da22bd88d08e2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602576"
---
# <a name="default-message-contract"></a>Varsayılan İleti Sözleşmesi
Varsayılan Ileti sözleşmesi örneği, hizmet işlemlerine ve bu işlemlerden özel kullanıcı tanımlı bir iletinin geçirildiği bir hizmeti gösterir. Bu örnek, türü belirlenmiş bir hizmet olarak Hesaplayıcı arabirimi uygulayan [Başlarken](getting-started-sample.md) ' i temel alır. [Başlarken](getting-started-sample.md), çıkarma, çarpma ve bölme işlemlerinde kullanılan tek hizmet işlemleri yerine, bu örnek hem işlenen hem de işlecini içeren bir özel ileti geçirir ve aritmetik hesaplamanın sonucunu döndürür.  
  
 İstemci bir konsol programıdır (. exe) ve hizmet kitaplığı (. dll) Internet Information Services (IIS) tarafından barındırılır. İstemci etkinliği konsol penceresinde görünür.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmette, Özel iletileri kabul eden ve döndüren tek bir hizmet işlemi tanımlanmıştır `MyMessage` . Bu örnekte istek ve yanıt iletileri aynı türde olsa da, gerektiğinde farklı ileti sözleşmeleri olabilir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Özel ileti `MyMessage` <xref:System.ServiceModel.MessageContractAttribute> , ve öznitelikleri ile açıklanmış bir sınıfta tanımlanmıştır <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> . Bu örnekte yalnızca üçüncü Oluşturucu kullanılır. İleti sözleşmelerini kullanmak, SOAP iletisi üzerinde tam denetim yapmanıza olanak sağlar. Bu örnekte, <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği BIR SOAP üstbilgisine koymak için kullanılır `Operation` . İşlenenler `N1` `N2` ve `Result` ÖZNITELIĞI uygulanmış olduğundan SOAP gövdesi içinde görüntülenir <xref:System.ServiceModel.MessageBodyMemberAttribute> .  
  
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
  
 Uygulama sınıfı, `Calculate` hizmet işleminin kodunu içerir. `CalculateService`Sınıfı, istek iletisinden işlenen ve işleci edinir ve aşağıdaki örnek kodda gösterildiği gibi istenen hesaplamanın sonucunu içeren bir yanıt iletisi oluşturur.  
  
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
  
 İstemci için üretilen istemci kodu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) aracıyla oluşturulmuştur. Araç, gerekirse oluşturulan istemci kodunda ileti sözleşme türlerini otomatik olarak oluşturur. `/messageContract`İleti sözleşmelerinin oluşturulmasını zorlamak için komut seçeneği belirtilebilir.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Aşağıdaki örnek kod, iletisini kullanarak istemciyi gösterir `MyMessage` .  
  
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
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
