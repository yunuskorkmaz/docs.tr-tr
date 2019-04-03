---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 736633733ab9c882c1d1520a5acf20c49324eeb3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828036"
---
# <a name="srmp"></a>SRMP
Bu örnek HTTP üzerinden Message Queuing (MSMQ) kullanarak hizmetteki kuyruğa alınan iletişim gerçekleştirme gösterir.  
  
 Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar. Daha kesin bir istemci bir kuyruğa iletiler gönderir. Hizmet iletileri kuyruktan alır. Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.  
  
 MSMQ bir kuyruğa ileti göndermek için HTTP (HTTPS kullanımı dahil) kullanılmasına olanak tanır. Bu örnekte, Windows Communication Foundation (WCF) kullanarak sıraya iletişim ve HTTP üzerinden ileti göndermek nasıl ekleyebileceğiniz gösterilmektedir. MSMQ HTTP üzerinden iletişim için SOAP tabanlı bir protokol olan SRMP, adlı bir protokolü kullanır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Örneği çalıştırmadan önce **Windows Bileşenlerini Ekle/Kaldır**, MSMQ yüklü olduğundan emin olun HTTP desteği. HTTP desteği otomatik olarak yükleme, Internet Information Services (IIS) yükler ve protokol desteği için MSMQ IIS'de ekler.  
  
5.  HTTP iletişimi için kullanılan emin olmak istiyorsanız, sağlamlaştırılmış modda çalıştırmak MSMQ etkinleştirebilirsiniz. Bu makinede barındırılan herhangi bir kuyruğa ileti herhangi bir HTTP olmayan aktarım kullanarak ulaşmasını sağlar.  
  
6.  Sağlamlaştırılmış modda çalıştırmak için MSMQ seçtikten sonra makine yeniden önyükleme gerektiği [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
7.  Hizmet çalıştırın.  
  
8.  İstemciyi çalıştırın. Makine adı için işaret edecek şekilde uç nokta adresini veya IP adresi localhost yerine değiştirdiğinizden emin olun. İstemci bir ileti gönderir ve çıkar.  
  
## <a name="requirements"></a>Gereksinimler  
 Bu örneği çalıştırmak için IIS hem hizmet hem de istemci makinelerin MSMQ yanı sıra yüklenmesi gerekir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Örneği, WCF gönderme gösterir. MSMQ kullanarak HTTP üzerinden ileti kuyruğa alındı. Bu, SRMP Mesajlaşma olarak da adlandırılır. Ne zaman bir kuyruğa alınmış ileti gönderilir, MSMQ alıcı Kuyruk Yöneticisi üzerinden TCP veya HTTP aktarım için gönderme makine aktarımlarında iletileri üzerinde. SRMP seçerek kullanıcı seçimi HTTP kuyruk aktarımı için aktarım olarak gösterir. SRMP güvenli HTTPS kullanımını etkinleştirir.  
  
## <a name="example"></a>Örnek  
 Örnek kod, hizmetteki örnek üzerinde temel alır. Kuyruğa bir ileti göndermek ve SRMP kullanarak kuyruktan bir ileti alırsınız nasıl yerel protokolünü kullanarak ileti gönderme ve alma ile aynı olur.  
  
 İstemci yapılandırması seçeneği sırası Aktarımı Protokolü belirtmek için değiştirilir. Kuyruk Aktarım Protokolü, yerel, SRMP ya da SrmpSecure biri olabilir. Varsayılan olarak, yerel aktarımı protokolüdür. Hizmet ve istemci bu örnekte SRMP kullanmak için yapılandırmayı belirtin.  
  
 SRMP aktarım güvenliği ile ilgili sınırlamalar vardır. Gönderme sırası Yöneticisi ve alıcı sırası aynı Windows etki alanında bulunan gerektiren Active Directory varsayılan MSMQ taşıma güvenliği gerektirir. Bu HTTP sınır ileti gönderirken mümkün değildir. Bu nedenle, varsayılan aktarım güvenliği çalışmaz. Aktarım güvenliği isterseniz aktarım güvenliği için sertifika ayarlamanız gerekir. İleti güvenliği, ileti güvenliğini sağlamak için de kullanılabilir. Bu örnekte, hem aktarım hem de ileti güvenlik SRMP Mesajlaşma göstermek için kapalıdır.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"   
           bindingConfiguration="srmpBinding"   
           binding="netMsmqBinding"   
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Çalışan örnek aşağıdaki çıktıyı üretir.  
  
```  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
