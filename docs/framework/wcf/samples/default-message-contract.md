---
title: Varsayılan İleti Sözleşmesi
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 46b69697616ad7983daed16f8a180a4da7f61a16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183764"
---
# <a name="default-message-contract"></a>Varsayılan İleti Sözleşmesi
Varsayılan İleti Sözleşmesi örneği, özel kullanıcı tanımlı iletinin hizmet işlemlerine ve hizmet işlemlerine aktarıldığı bir hizmeti gösterir. Bu örnek, bir hesap makinesi arabirimini yazılı hizmet olarak uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır. [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlatılan'da kullanılan toplama, çıkarma, çarpma ve bölme için tek tek hizmet işlemleri yerine, bu örnek hem operandları hem de işleci içeren özel bir ileti geçirir ve aritmetik hesaplama nın sonucunu döndürür.  
  
 İstemci bir konsol programıdır (.exe) ve hizmet kitaplığı (.dll) Internet Information Services (IIS) tarafından barındırılır. İstemci etkinliği konsol penceresinde görünür.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hizmette, özel tür `MyMessage`iletilerini kabul eden ve döndüren tek bir hizmet işlemi tanımlanır. Bu örnekte istek ve yanıt iletileri aynı türde olsa da, gerekirse elbette farklı ileti sözleşmeleri olabilir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Özel `MyMessage` ileti, açıklamalı <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> özniteliklere sahip bir sınıfta tanımlanır. Bu örnekte yalnızca üçüncü yapıcı kullanılır. İleti sözleşmelerini kullanmak, SOAP iletisi üzerinde tam kontrol eve sahip olabilirsiniz. Bu örnekte, <xref:System.ServiceModel.MessageHeaderAttribute> öznitelik bir `Operation` SOAP üstbilgi koymak için kullanılır. Operands `N1`, `N2` ve `Result` onlar uygulanan <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelik var çünkü SOAP vücut içinde görünür.  
  
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
  
 Uygulama sınıfı `Calculate` hizmet çalışması için kod içerir. Sınıf, `CalculateService` istek iletisinden operands ve işleci alır ve aşağıdaki örnek kodda gösterildiği gibi istenen hesaplamanın sonucunu içeren bir yanıt iletisi oluşturur.  
  
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
  
 İstemci için oluşturulan istemci kodu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı ile oluşturuldu. Araç, gerekirse oluşturulan istemci kodunda otomatik olarak ileti sözleşmesi türleri oluşturur. Komut `/messageContract` seçeneği, ileti sözleşmelerinin oluşumunu zorlamak için belirtilebilir.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Aşağıdaki örnek kod, `MyMessage` istemcinin iletiyi kullandığını gösterir.  
  
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
  
 Örneği çalıştırdığınızda, hesaplamalar istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Bu noktada, istemci ve hizmet işlemi arasında özel kullanıcı tanımlı iletiler geçti. İleti sözleşmesi, operands ve sonuçları ileti gövdesinde olduğunu ve işleç bir ileti üstbilgisinde olduğunu tanımladı. İleti günlüğe kaydetme, bu ileti yapısını gözlemlemek için yapılandırılabilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
