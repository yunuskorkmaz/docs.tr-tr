---
title: Yazılmamış istek-yanıt
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: 2eb6a46d339c9277c1622c0cc16d057b186f1d79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612755"
---
# <a name="untyped-requestreply"></a>Yazılmamış İstek/Yanıt
Bu örnek ileti sınıfını kullanma işlemi sözleşmelerini tanımlamak nasıl gösterir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Hizmet sözleşmesi bir ileti türü bağımsız değişken olarak alır ve bir ileti döndüren bir işlemi tanımlar. İşlemi, iletinin gövdesinden toplamı hesaplamak için gerekli tüm verileri toplar ve toplamı dönüş ileti gövdesinde olarak gönderir.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Hizmet işlemi giriş iletisinde geçirilen dizisi alır ve toplamı hesaplar. Bir yanıt iletisi göndermek için örnek uygun ileti sürümü ve eylem ile yeni bir ileti oluşturur ve kendi gövdesi olarak hesaplanan toplam ekler. Aşağıdaki örnek kod bu gösterir.  
  
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
  
 İstemci tarafından oluşturulan kodda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) uzak hizmet için bir ara sunucu oluşturmak için. Bir istek iletisi göndermek için istemci bağlıdır altındaki bir kanalda ileti sürümü olması gerekir. Bu nedenle, yeni bir oluşturur <xref:System.ServiceModel.OperationContextScope> oluşturur, oluşturulan proxy kanalı kapsamlı bir <xref:System.ServiceModel.OperationContext> içinde doldurulmuş doğru ileti sürümü ile kendi `OutgoingMessageHeaders.MessageVersion` özelliği. İstemci Giriş dizisinin için istek iletisi gövdesi olarak geçirir ve sonra çağırır `ComputeSum` proxy. İstemci ardından geçirilen erişerek girişleri toplamını alır `GetBody<T>` yöntemi yanıt iletisi. Aşağıdaki örnek kod bu gösterir.  
  
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
  
 Bu örnek bir Web barındırılan bir örnektir ve bu nedenle yalnızca istemci yürütülebilir dosyayı çalıştırmanız gerekir. İstemci örnek çıktı verilmiştir.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Bu, bir örnek Web barındırılan ve derleme ve çalıştırma örneği yapılacağını görmek için 3. adım, bağlantıyı sağlanan kontrol edin örnektir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>Ayrıca bkz.
