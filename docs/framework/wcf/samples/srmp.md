---
title: SRMP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b33ecabb6796ee123e27213a92b6b0d7aefaf9a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="srmp"></a>SRMP
Bu örnek, HTTP üzerinden Message Queuing (MSMQ) kullanarak hizmetteki kuyruğa alınan iletişim gerçekleştirmek gösterilmiştir.  
  
 Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar. Daha hassas bir şekilde istemci kuyruğa ileti gönderir. Hizmet kuyruktan iletileri alır. Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 MSMQ HTTP (HTTPS kullanımı dahil) kullanımını kuyruğa ileti göndermek için etkinleştirir. Bu örnekte, biz kullanarak göstermek [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] iletişim ve HTTP üzerinden ileti göndermek nasıl sıraya alındı. MSMQ SRMP, HTTP üzerinden iletişim için SOAP tabanlı bir protokol olan adlı bir protokolünü kullanır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Örneği çalıştırmadan önce **Windows Bileşenlerini Ekle/Kaldır**, MSMQ yüklü olduğundan emin olun HTTP desteği. HTTP desteği otomatik olarak yükleme Internet Information Services (IIS) yükler ve protokol desteği için MSMQ IIS'de ekler.  
  
5.  HTTP iletişimi için kullanılan emin olmak istiyorsanız, sağlamlaştırılmış modda çalıştırmak MSMQ etkinleştirebilirsiniz. Bu makinede barındırılan herhangi bir sıra hiçbir iletileri herhangi bir HTTP olmayan aktarım kullanarak gelmesini sağlar.  
  
6.  Sağlamlaştırılmış modda çalıştırmak için MSMQ seçtikten sonra makinenin yeniden önyükleme gerektiriyorsa [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
7.  Hizmet çalıştırın.  
  
8.  İstemciyi çalıştırın. Makine adı işaret edecek şekilde uç noktası adresi veya IP adresi localhost yerine değiştirdiğinizden emin olun. İstemci bir ileti gönderir ve çıkar.  
  
## <a name="requirements"></a>Gereksinimler  
 Bu örneği çalıştırmak için IIS hem hizmet hem de istemci makinelere MSMQ yanı sıra yüklenmesi gerekir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Örnek gönderme gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ HTTP üzerinden kullanarak sıradaki iletiler. Bu, SRMP Mesajlaşma olarak da adlandırılır. Ne zaman bir Sıraya alınan iletinin gönderildiği, MSMQ alıcı sıra yöneticisine TCP veya HTTP taşıması üzerinden gönderme makine aktarımları iletileri üzerinde. SRMP seçerek kullanıcı HTTP seçimi sıra aktarımı için bir taşıma olarak gösterir. SRMP güvenli HTTPS kullanımını etkinleştirir.  
  
## <a name="example"></a>Örnek  
 Örnek kod hizmetteki örnek üzerinde temel alır. Nasıl kuyruğa ileti gönderme ve SRMP kullanarak kuyruktan ileti alma yerel protokolünü kullanarak ileti gönderme ve alma ile aynı olur.  
  
 Sıra Aktarım Protokolü seçimi belirtmek için istemci yapılandırmasını değiştirdi. Sıra Aktarım Protokolü yerel, SRMP ya da SrmpSecure biri olabilir. Varsayılan olarak, yerel aktarım protokolüdür. Bu örnekte SRMP kullanmak üzere yapılandırma istemci ve hizmet belirtin.  
  
 Taşıma güvenliği ile ilgili olarak SRMP sınırlamalar vardır. Varsayılan MSMQ taşıma güvenliği gönderme sırası Yöneticisi ve alıcı sırası aynı Windows etki alanında bulunan gerektirir Active Directory gerektirir. Bu iletileri HTTP sınırından gönderirken mümkün değildir. Bu nedenle, varsayılan taşıma güvenliği çalışmaz. Taşıma güvenliği isterseniz taşıma güvenliği için sertifika ayarlamanız gerekir. İleti güvenliği, ileti güvenliğini sağlamak için de kullanılabilir. Bu örnekte, taşıma ve ileti güvenliği SRMP Mesajlaşma göstermeye kapalıdır.  
  
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
          <security mode="None"></security>  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Örnek çalıştıran şu çıkışı üretir.  
  
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
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a>Ayrıca Bkz.
