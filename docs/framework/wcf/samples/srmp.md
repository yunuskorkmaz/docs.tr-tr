---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183334"
---
# <a name="srmp"></a>SRMP
Bu örnek, http üzerinden Ileti Sırası (MSMQ) kullanarak işlemyapılan sıralı iletişimin nasıl gerçekleştiriltilebildiğini gösterir.  
  
 Sıralı iletişimde, istemci bir sıra kullanarak hizmete iletişim kurar. Daha doğrusu, istemci sıraya ileti gönderir. Hizmet, kuyruktan iletiler alır. Bu nedenle, hizmet ve istemci, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 MSMQ, kuyruğa ileti göndermek için HTTP (HTTPS kullanımı dahil) kullanımını sağlar. Bu örnekte, Windows Communication Foundation (WCF) sıralı iletişimi ve HTTP üzerinden nasıl ileti gönderebileceğimizi gösteriyoruz. MSMQ, HTTP üzerinden iletişim için SOAP tabanlı bir protokol olan SRMP adlı bir protokol kullanır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
4. **Windows Bileşenleri ekle/kaldır'da**örneği çalıştırmadan önce, MSMQ'nun HTTP desteğiyle yüklendiğinden emin olun. HTTP desteğinin yüklenmesi Internet Information Services 'ı (IIS) otomatik olarak yükler ve MSMQ için IIS'ye protokol desteği ekler.  
  
5. HTTP'nin iletişim için kullanıldığından emin olmak istiyorsanız, MSMQ'nun sertleştirilmiş modda çalışmasını etkinleştirebilirsiniz. Bu, makinede barındırılan herhangi bir kuyruğa gönderilen hiçbir iletinin HTTP dışı aktarımları kullanarak ulaşmasını sağlar.  
  
6. Sertleştirilmiş modda çalışmak üzere MSMQ'yu seçtikten sonra, makine windows server 2003'te yeniden önyükleme gerektirir.  
  
7. Servisi çalıştırın.  
  
8. İstemciyi çalıştırın. Uç nokta adresini yerel ana bilgisayar yerine makine adını veya IP adresini işaret edecek şekilde değiştirdiğinden emin olun. İstemci bir ileti gönderir ve çıkar.  
  
## <a name="requirements"></a>Gereksinimler  
 Bu örneği çalıştırmak için IIS'nin MSMQ'ya ek olarak hem hizmete hem de istemci makinelere yüklenmesi gerekir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Örnek, HTTP üzerinden MSMQ kullanarak WCF sıralı iletiler göndermeyi göstermektedir. Buna SRMP iletisi de denir. Sıraya alınan bir ileti gönderildiğinde, gönderen makinedeki MSMQ iletileri TCP veya HTTP aktarımı üzerinden alan sıra yöneticisine aktarıyor. SRMP'yi seçerek, kullanıcı sıra transferi için bir aktarım olarak HTTP seçimini gösterir. SRMP Secure HTTPS kullanımını sağlar.  
  
## <a name="example"></a>Örnek  
 Örnek kodu, işlem yapılan örneğe dayanır. SRMP kullanarak kuyruğa ileti gönderme ve kuyruktan ileti alma şekliniz, Yerel protokol kullanarak ileti gönderip almakla aynıdır.  
  
 İstemcinin yapılandırması, sıra aktarım protokolünün seçimini gösterecek şekilde değiştirilir. Sıra aktarım protokolü Yerel, SRMP veya SrmpSecure'dan biri olabilir. Varsayılan olarak, aktarım protokolü Yerel'dir. İstemci ve hizmet yapılandırmada bu örnekte SRMP'yi kullanacağını belirtin.  
  
 Aktarım güvenliğiyle ilgili olarak SRMP'de sınırlamalar vardır. Varsayılan MSMQ aktarım güvenliği, gönderen sıra yöneticisi ve alan sıra yöneticisinin aynı Windows etki alanında ikamet ettiğini gerektiren Etkin Dizin gerektirir. Bu, HTTP sınırı üzerinden ileti gönderirken mümkün değildir. Bu nedenle, varsayılan aktarım güvenliği çalışmıyor. Taşıma güvenliği isteniyorsa, taşıma güvenliği Sertifika olarak ayarlanmalıdır. İleti güvenliği, iletiyi güvenli hale getirmek için de kullanılabilir. Bu örnekte, SRMP iletisini göstermek için hem aktarım hem de ileti güvenliği kapatılır.  
  
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
  
 Numunenin çalıştırılsa, aşağıdaki çıktıyı verir.  
  
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
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
