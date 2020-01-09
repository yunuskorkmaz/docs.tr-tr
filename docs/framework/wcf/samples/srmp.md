---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 1e0290a4df688d39f84086dc4c1b41712f81076a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345141"
---
# <a name="srmp"></a>SRMP
Bu örnek, HTTP üzerinden Message Queuing (MSMQ) kullanılarak işlenen sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir.  
  
 Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar. Daha kesin olarak, istemci iletileri bir kuyruğa gönderir. Hizmet kuyruktaki iletileri alır. Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 MSMQ, bir kuyruğa ileti göndermek için HTTP kullanımını (HTTPS kullanımı dahil) sağlar. Bu örnekte, Windows Communication Foundation (WCF) kuyruğa alınan iletişimin kullanımını ve HTTP üzerinden ileti gönderilmesini gösteririz. MSMQ, HTTP üzerinden iletişim için SOAP tabanlı bir protokol olan SRMP adlı bir protokol kullanır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
4. **Windows Bileşenlerini Ekle/Kaldır**' da örneği çalıştırmadan önce, MSMQ 'nun http desteğiyle yüklü olduğundan emin olun. HTTP desteğinin yüklenmesi Internet Information Services (IIS) otomatik olarak yüklenir ve MSMQ için IIS 'de protokol desteğini ekler.  
  
5. İletişim için HTTP 'nin kullanıldığından emin olmak istiyorsanız, MSMQ 'YU güçlendirilmiş modda çalışacak şekilde etkinleştirebilirsiniz. Bu, makinede barındırılan herhangi bir sıraya hiçbir iletinin HTTP olmayan herhangi bir aktarımı kullanarak gelebilmesini sağlar.  
  
6. Sağlamlaştırılmış modda çalıştırmak için MSMQ ' yı seçtikten sonra, makine Windows Server 2003 ' de yeniden önyükleme gerektirir.  
  
7. Hizmeti çalıştırın.  
  
8. İstemcisini çalıştırın. Uç nokta adresini, localhost yerine makine adına veya IP adresine işaret etmek üzere değiştirdiğinizden emin olun. İstemci bir ileti gönderir ve çıkar.  
  
## <a name="requirements"></a>Gereksinimler  
 Bu örneği çalıştırmak için, MSMQ 'ya ek olarak hem hizmette hem de istemci makinelerde IIS yüklü olmalıdır.  
  
## <a name="demonstrates"></a>Gösterir  
 Örnek, HTTP üzerinden MSMQ kullanarak WCF sıraya alınan iletileri göndermeyi gösterir. Bu, SRMP mesajlaşma olarak da adlandırılır. Sıraya alınan bir ileti gönderildiğinde, Gönderen makinedeki MSMQ iletileri TCP veya HTTP taşıması üzerinden alma kuyruğu Yöneticisi 'ne aktarır. SRMP ' i seçerek Kullanıcı, kuyruk aktarımı için bir taşıma olarak HTTP seçeneğini belirtir. SRMP Secure, HTTPS kullanımını sunar.  
  
## <a name="example"></a>Örnek  
 Örnek kod, işlem temelli örneğe dayalıdır. Sıradan bir ileti gönderdiğinizde ve SRMP kullanarak kuyruktan ileti aldığınızda, yerel bir protokol kullanarak ileti gönderme ve alma ile aynı olur.  
  
 İstemci yapılandırması, sıra Aktarım protokolünün seçimini belirtecek şekilde değiştirilir. Sıra Aktarım Protokolü yerel, SRMP veya SrmpSecure değerinden biri olabilir. Varsayılan olarak, Aktarım Protokolü yereldir. İstemci ve hizmet, bu örnekte SRMP 'yi kullanmak için yapılandırmayı belirtir.  
  
 Aktarım güvenliği ile ilgili olarak SRMP için sınırlamalar vardır. Varsayılan MSMQ taşıma güvenliği, gönderme kuyruğu yöneticisinin ve alma kuyruğu yöneticisinin aynı Windows etki alanında bulunmasını gerektiren Active Directory gerektirir. HTTP sınırı üzerinden ileti gönderilirken bu mümkün değildir. Bu nedenle, varsayılan aktarım güvenliği çalışmaz. Aktarım güvenliği isteniyorsa aktarım güvenliği sertifika olarak ayarlanmalıdır. İleti güvenliği, iletinin güvenliğini sağlamak için de kullanılabilir. Bu örnekte, hem aktarım hem de ileti güvenliği, SRMP iletilerini göstermek için kapalıdır.  
  
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
  
 Örnek çalıştırmak aşağıdaki çıktıyı verir.  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
