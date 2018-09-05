---
title: Dayanıklı Çift Yönlü
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 107c617fa4a8ee0279dcaa07e495587c617b866e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513359"
---
# <a name="durable-duplex"></a>Dayanıklı Çift Yönlü
Bu örnek, ayarlama ve mesajlaşma etkinlikleri Windows Workflow Foundation (WF) kullanan dayanıklı çift yönlü ileti alışverişi yapılandırma gösterilmektedir. Dayanıklı çift yönlü ileti exchange uzun bir süre gerçekleşen bir iki yönlü ileti değişimi ' dir. İleti alışverişi ömrünü iletişim kanalını ömrünü ve hizmet örnekleri bellek içi ömrünü uzun olabilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte, iki Windows Communication Foundation (WCF) Hizmetleri, Windows Workflow Foundation kullanılarak uygulanan bir dayanıklı çift yönlü ileti değişimi için yapılandırılır. Dayanıklı çift yönlü ileti alışverişi MSMQ gönderilen ve kullanarak bağıntılı iki yönlü gelen iletileri oluşur [.NET bağlam değişimi](https://go.microsoft.com/fwlink/?LinkID=166059). İletileri kullanılarak gönderilen <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> Mesajlaşma etkinlikleri. .NET bağlam değişimi gönderilen iletilerde geri çağırma adresini belirtmek için kullanın. Her iki hizmet de, Windows İşlem Etkinleştirme Hizmetleri (WAS) kullanılarak buluta barındırılır ve Hizmetleri örnekleri kalıcılığını sağlamak için yapılandırılır.  
  
 İlk hizmeti (Service1.xamlx) bazı iş yapmak için gönderme hizmete (Service2.xamlx) bir isteği gönderir. İş tamamlandıktan sonra Service2.xamlx iş tamamlanmış olduğunu belirtmek için geri için Service1.xamlx bir bildirim gönderir. Bir iş akışı konsol uygulaması hizmetlerin dinlediği sıralarını ayarlar ve Service1.xamlx etkinleştirmek için ilk başlatma iletisi gönderir. İstenen iş tamamlandığını Service2.xamlx bildirimden service1.xamlx aldıktan sonra Service1.xamlx sonucu bir XML dosyasına kaydeder. Geri çağırma ileti için beklenirken Service1.xamlx varsayılan kullanarak örnek durumu kalıcı <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>. Service2.xamlx Service1.xamlx tarafından istenen işinin tamamlanmasına bir parçası olarak, örnek durumu devam ettirir.  
  
 MSMQ üzerinde .NET bağlam değişimi Hizmetleri'ni yapılandırmak için her iki hizmet de oluşan özel bir bağlama kullanmak üzere yapılandırılmış <xref:System.ServiceModel.Channels.ContextBindingElement> ve <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>. Bir geri çağırma adresi belirtilmiş <xref:System.ServiceModel.Channels.ContextBindingElement> ve özel bir bağlama kullanılarak gönderilen tüm iletiler ile bir geri çağırma içerik üstbilgisinde dahil edilir. Aşağıdaki kod örneği, özel bir bağlama tanımlar.  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Bu örnek tarafından kullanılan bağlama güvenli değildir. Uygulamanızın dağıtım yaparken, bağlama, uygulamanızın güvenlik gereksinimlerine göre yapılandırmanız gerekir.  
  
> [!NOTE]
>  Bu örnekte kullanılan kuyrukları işlemsel değildir. İşlem kuyruklarını kullanan WCF ileti alışverişlerinde ayarlama işlemini gösteren bir örnek için bkz: [MSMQ etkinleştirme](../../../../docs/framework/wcf/samples/msmq-activation.md) örnek.  
  
 Özel bağlama Service2.xamlx ve adresi ile yapılandırılmış bir istemci uç noktası kullanarak, önceden tanımlanmış için Service2.xamlx service1.xamlx tarafından gönderilen ileti gönderilir. İstemci uç noktası Service1.xamlx tarafından gönderilen geri çağırma bağlamından alınan adresi ile açıkça yapılandırılmış adres kullanarak Service1.xamlx Service2.xamlx gelen geri gönderilir. Aşağıdaki kod örneği, istemci uç noktalarını tanımlar.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 Aşağıdaki kod örneği, bu özel bağlama kullanılacak net.msmq temel adresler için varsayılan protokol eşleşmelerinin değiştirerek bu özel bağlama kullanma uç noktalarını kullanıma sunar.  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 Aşağıdaki kod örneği ekleyerek her iki hizmet kalıcılığını etkinleştirir. <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> hem Hizmetleri, hem de Kalıcılık veritabanı için bağlantı dizesi belirterek davranışı.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a>Sistem Gereksinimleri  
 Bu örnek aşağıdaki bileşenleri gerektirir.  
  
1.  Internet Information Services.  
  
2.  Internet Information Services IIS 6.0 Yönetim uyumluluğu -> IIS metatabanı ve IIS 6.0 yapılandırma uyumluluğu ->.  
  
3.  World Wide Web Hizmetleri, uygulama geliştirme -> Özellikler -> ASP.NET.  
  
4.  Microsoft ileti kuyrukları (MSMQ) sunucusu.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kalıcılık veritabanı ve sonuçlar dizini ayarlayın.  
  
    1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
    2.  Bu örnek klasörüne gidin ve ardından Setup.cmd'yi çalıştırın.  
  
2.  Sanal uygulama ayarlama.  
  
    1.  Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut isteminde, aşağıdaki komutu çalıştırarak ASP.NET'i kaydedin.  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklayarak yönetici izinleriyle [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] seçerek **yönetici olarak çalıştır**.  
  
    3.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DurableDuplex.sln dosyasını açın.  
  
3.  Hizmet sıraları ayarlayabilir.  
  
    1.  DurableDuplex istemciyi çalıştırmak için F5 tuşuna basın.  
  
    2.  Açık **Bilgisayar Yönetimi** çalıştırarak konsol `Compmgmt.msc` bir komut isteminden.  
  
    3.  Genişletin **hizmet ve uygulamaları**, **Message Queuing**. **Özel sıralar**.  
  
    4.  Kuyrukları durableduplex/service1.xamlx ve durableduplex/service2.xamlx sağ tıklayıp **özellikleri**.  
  
    5.  Seçin **güvenlik** sekmesini ve izin **herkesin İleti Al**, **iletiye** ve **iletisi gönder** hem kuyruklar için izinleri.  
  
    6.  İnternet Bilgi Hizmetleri (IIS) Yöneticisini açın.  
  
    7.  Gözat **sunucu**, **siteleri**, **varsayılan Web sitesi**, **özel**, **dayanıklı çift yönlü** seçin **Gelişmiş Seçenekler**.  
  
    8.  Değişiklik **etkin protokoller** için **http,net.msmq**.  
  
4.  Örneği çalıştırın.  
  
    1.  Gözat http://localhost/private/durableduplex/service1.xamlx ve http://localhost/private/durableduplex/service2.xamlx hem hizmetlerin çalışır durumda olduğundan emin olmak için.  
  
    2.  DurableDuplexClient çalıştırmak için F5 tuşuna basın.  
  
         Dayanıklı çift yönlü ileti alışverişi tamamlandığında result.xml dosya C:\Inbox klasörüne kaydedilir ve ileti alışverişi sonucunu içerir.  
  
#### <a name="to-cleanup-optional"></a>(İsteğe bağlı) temizlemek için  
  
1.  CleanUp.cmd çalıştırın.  
  
    1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
    2.  Bu örnek klasörüne gidin ve Cleanup.cmd çalıştırın.  
  
2.  Sanal uygulama hizmetleri için kaldırın.  
  
    1.  Internet Information Services (IIS) Yöneticisi'ni çalıştırarak açmak `Inetmgr.exe` bir komut isteminden.  
  
    2.  Varsayılan Web sitesine gidin ve Kaldır **özel** sanal dizin.  
  
3.  Bu örnek için ayarlanan kuyrukları kaldırın.  
  
    1.  Çalıştırarak Bilgisayar Yönetimi konsolunu açın `Compmgmt.msc` bir komut isteminden.  
  
    2.  Genişletin **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.  
  
    3.  Kuyrukları durableduplex/service1.xamlx ve durableduplex/service2.xamlx silin.  
  
4.  C:\Inbox dizini kaldırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`