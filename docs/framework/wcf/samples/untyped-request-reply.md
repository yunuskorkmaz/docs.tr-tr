---
title: "Türsüz istek-yanıt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f11f142912bf08ce00dbcd3ff4aeba939a996a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="untyped-requestreply"></a>Yazılmamış İstek/Yanıt
Bu örnek ileti sınıfını kullanma işlemi sözleşmelerini tanımlamak gösterilmiştir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Hizmet sözleşmesi ileti türünde bir bağımsız değişken olarak alan ve bir ileti döndüren bir işlemi tanımlar. İşlemi, ileti gövdesi Topla hesaplamak için gerekli tüm verileri toplar ve ardından Dönüş iletisinin gövdesinde olarak toplamı gönderir.  
  
```  
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Hizmet işlemi giriş iletisinde geçirilen dizisi alır ve toplamı hesaplar. Bir yanıt iletisi göndermek için örnek uygun ileti sürümü ve eylem ile yeni bir ileti oluşturur ve onun gövdesi olarak hesaplanan toplam ekler. Aşağıdaki örnek kod bu gösterir.  
  
```  
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
  
 İstemci tarafından oluşturulan kodu kullanır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) uzak hizmet için bir proxy oluşturmak için. Bir istek iletisi göndermek için istemci temel alınan kanalında bağlıdır ileti sürüm olmalıdır. Bu nedenle, yeni bir oluşturur <xref:System.ServiceModel.OperationContextScope> oluşturur oluşturulduğu, proxy kanal kapsamlı bir <xref:System.ServiceModel.OperationContext> içinde doldurulmuş doğru ileti sürümü ile kendi `OutgoingMessageHeaders.MessageVersion` özelliği. İstemci istek iletisi gövdesi olarak Giriş dizisinin geçirir ve ardından çağırır `ComputeSum` proxy. İstemci ardından geçirilen erişerek girişleri toplamını alır `GetBody<T>` yanıt iletisi yöntemi. Aşağıdaki örnek kod bu gösterir.  
  
```  
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
  
 Bu örnek bir Web barındırılan bir örnektir ve bu nedenle yalnızca istemci yürütülebilir çalıştırmanız gerekir. İstemci üzerinde örnek çıktı verilmiştir.  
  
```  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Bu, bir örnek Web barındırılan ve bağlantıyı derlemeyi ve çalıştırmayı örnek nasıl görmek için 3. adım sağlanan kontrol örnektir.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>Ayrıca Bkz.
