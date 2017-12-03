---
title: "Varsayılan İleti Sözleşmesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 407fa758c6564c3b7a5a8573acef1b6e181399d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="default-message-contract"></a>Varsayılan İleti Sözleşmesi
Varsayılan ileti sözleşmesi örnek özel bir kullanıcı tarafından tanımlanan ileti için ve hizmet işlemleri geçirildiği hizmet gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı arabirimi yazılan hizmet olarak uygular. Ayrıca, çıkarma, çarpma ve bölme kullanılan bireysel hizmet işlemlerinde yerine [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), bu örnek işlenenler ve işlecini içeriyor ve döndüren özel bir ileti geçirir aritmetik hesaplama sonucu.  
  
 İstemci bir konsol programı (.exe) ve hizmet kitaplığı (.dll) Internet Information Services (IIS) tarafından barındırılır. İstemci etkinliği konsol penceresinde görünür olur.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Hizmetinde kabul eder ve özel iletileri türü döndüren bir tek hizmet işlemi tanımlanan `MyMessage`. Bu örnekte istek ve yanıt iletileri aynı türde olsa da, bunlar farklı ileti sözleşmeleri Elbette gerekirse olabilir.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Özel ileti `MyMessage` ile Açıklama sınıfında tanımlanan <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri. Bu örnekte yalnızca üçüncü Oluşturucusu kullanılır. İleti sözleşmeleri kullanılıyor SOAP iletisi üzerinde tam denetim sağlar. Bu örnekte <xref:System.ServiceModel.MessageHeaderAttribute> yerleştirmek için kullanılan öznitelik `Operation` SOAP üstbilgisinde. İşlenen `N1`, `N2` ve `Result` sahip oldukları için SOAP gövdesi içinde görünür <xref:System.ServiceModel.MessageBodyMemberAttribute> özniteliği uygulanmıştır.  
  
```  
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
  
 Uygulama sınıfı için kod içeren `Calculate` hizmet işlemi. `CalculateService` Sınıfı işleci ve işlenen istek iletisinden alır ve aşağıdaki örnek kodda gösterildiği gibi istenen hesaplama sonucunu içeren bir yanıt iletisi oluşturur.  
  
```  
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
  
 İstemci için oluşturulan istemci kodu ile oluşturulduğundan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı. Araç, ileti sözleşme türleri gerekirse oluşturulan istemci kodu otomatik olarak oluşturur. `/messageContract` Komut seçeneği, ileti sözleşmeleri zorlamanızı belirtilebilir.  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Aşağıdaki örnek kod kullanarak istemciyi gösteren `MyMessage` ileti.  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage();  
request.N1 = 100D;  
request.N2 = 15.99D;  
request.Operation = "+";  
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 Örneği çalıştırdığınızda, hesaplamaları istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Bu noktada, kullanıcı tanımlı özel iletileri istemci ve hizmet işlemini arasında geçti. İleti sözleşmesi sonuçları ve işlenen ileti gövdesini olduğunu ve işleci bir ileti üstbilgisinde olduğunu tanımlanır. İleti günlüğe kaydetme, bu ileti yapısı izlemek için yapılandırılabilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
## <a name="see-also"></a>Ayrıca Bkz.
