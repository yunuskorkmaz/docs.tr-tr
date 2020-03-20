---
title: Yazılmamış İstek-Yanıt
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: a526837b9bccf7a6287972e482a189a53ecadaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183283"
---
# <a name="untyped-requestreply"></a>Yazılmamış İstek/Yanıt
Bu örnek, İleti sınıfını kullanan işlem sözleşmelerinin nasıl tanımlandığını gösterir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır. Hizmet sözleşmesi, ileti türünü bağımsız değişken olarak alan ve bir iletiyi döndüren bir işlemi tanımlar. İşlem, ileti gövdesinden toplamı hesaplamak için gerekli tüm verileri toplar ve sonra toplamı iade iletisinde gövde olarak gönderir.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Hizmette, işlem giriş iletisinde geçirilen bir dizi veya toplamı alır ve toplamı hesaplar. Yanıt iletisi göndermek için örnek, uygun ileti sürümü ve Eylem içeren yeni bir ileti oluşturur ve hesaplanan toplamı gövdesi olarak ekler. Aşağıdaki örnek kod bunu göstermektedir.  
  
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
  
 İstemci, uzak hizmete proxy oluşturmak için [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan kodu kullanır. İstek iletisi göndermek için istemcinin, temel kanala bağlı olan ileti sürümüne sahip olması gerekir. Böylece, oluşturduğu proxy <xref:System.ServiceModel.OperationContextScope> kanalına yönelik yeni bir kapsam oluşturur <xref:System.ServiceModel.OperationContext> ve bu da `OutgoingMessageHeaders.MessageVersion` özelliğinde doldurulan doğru ileti sürümüyle birlikte bir ileti sürümü oluşturur. İstemci, istek iletisine gövde olarak bir giriş dizisi `ComputeSum` geçirir ve proxy'yi çağırır. İstemci daha sonra yanıt iletisindeki `GetBody<T>` yönteme erişerek geçtiği girişlerin toplamını alır. Aşağıdaki örnek kod bunu göstermektedir.  
  
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
  
 Bu örnek, Web tarafından barındırılan bir örnektir ve bu nedenle yalnızca yürütülebilir istemci çalıştırılmalıdır. Aşağıdaki istemci üzerinde örnek çıktı.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Bu örnek, Web tarafından barındırılan bir örnektir ve bu nedenle, örneğin nasıl oluşturup çalıştırılabildiğini görmek için adım 3'te sağlanan bağlantıyı kontrol edin.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
