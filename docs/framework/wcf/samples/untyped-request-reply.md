---
title: Türsüz Istek-yanıt
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: 132ae05236b23ff5bb0cce67d66d26d308cce305
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038677"
---
# <a name="untyped-requestreply"></a>Yazılmamış İstek/Yanıt
Bu örnek, Ileti sınıfını kullanan işlem sözleşmelerinin nasıl tanımlanacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Hizmet sözleşmesi bir ileti türünde bağımsız değişken olarak alan ve bir ileti döndüren bir işlemi tanımlar. İşlem, ileti gövdesinden toplamı hesaplamak için gerekli tüm verileri toplar ve sonra toplamı dönüş iletisinde gövde olarak gönderir.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Hizmette, işlem giriş iletisinde geçirilen tamsayıların dizisini alır ve toplamı hesaplar. Yanıt iletisi göndermek için örnek, uygun ileti sürümü ve eylemiyle yeni bir ileti oluşturur ve hesaplanan toplamı gövde olarak ekler. Aşağıdaki örnek kod bunu gösterir.  
  
```csharp
public Message ComputeSum(Message request)  
{  
    //The body of the message contains a list of numbers which will be   
    //read as a int[] using GetBody<T>  
    int result = 0;  
  
    int[] inputs = request.GetBody<int[]>();  
    foreach (int i in inputs)  
    {  
        result += i;  
    }  
  
    Message response = Message.CreateMessage(request.Version,   
                                      ReplyAction, result);  
    return response;  
}  
```  
  
 İstemci, uzak hizmete bir ara sunucu oluşturmak için [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan kodu kullanır. İstek iletisi göndermek için, istemci, temeldeki kanala bağlı olan ileti sürümüne sahip olmalıdır. Bu nedenle, <xref:System.ServiceModel.OperationContextScope> `OutgoingMessageHeaders.MessageVersion` özelliği içinde doldurulmuş doğru ileti sürümü <xref:System.ServiceModel.OperationContext> ile oluşturulan, oluşturduğu proxy kanalında yeni bir kapsam oluşturur. İstemci, istek iletisine gövde olarak bir giriş dizisi geçirir ve sonra proxy `ComputeSum` üzerinde çağırır. İstemci daha sonra yanıt iletisindeki `GetBody<T>` yöntemine erişerek, geçirildiği girişlerin toplamını alır. Aşağıdaki örnek kod bunu gösterir.  
  
```csharp
using (new OperationContextScope(client.InnerChannel))  
{  
    // Call the Sum service operation.  
    int[] values = { 1, 2, 3, 4, 5 };  
    Message request = Message.CreateMessage(  
        OperationContext.Current.OutgoingMessageHeaders.MessageVersion,   
        RequestAction, values);  
    Message reply = client.ComputeSum(request);  
    int response = reply.GetBody<int>();  
  
    Console.WriteLine("Sum of numbers passed (1,2,3,4,5) = {0}",   
                                                       response);  
}  
```  
  
 Bu örnek, Web 'de barındırılan bir örnektir ve bu nedenle yalnızca istemci yürütülebilirinin çalıştırılması gerekir. Aşağıda, istemcideki örnek çıktı verilmiştir.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Bu örnek, Web 'de barındırılan bir örnektir ve bu nedenle örneği oluşturma ve çalıştırma hakkında bilgi için 3. adımda sunulan bağlantıyı kontrol edin.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
