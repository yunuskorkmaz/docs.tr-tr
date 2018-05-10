---
title: Dayanıklı Çift Yönlü
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 3df5ba962ef33594df1eaebc20789fa9e2d35244
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="durable-duplex"></a>Dayanıklı Çift Yönlü
Bu örnek, ayarlama ve mesajlaşma etkinlikleri Windows Workflow Foundation (WF) kullanan dayanıklı çift yönlü ileti alışverişi yapılandırma gösterilmektedir. Dayanıklı çift yönlü ileti değişimi gerçekleşir uzun bir süre boyunca bir iki yönlü ileti değişimi ' dir. İleti değişimi ömrü iletişim kanalını ömrü ve hizmet örnekleri bellek içi ömrü uzun olabilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte, iki Windows Communication Foundation (WCF) hizmetlerini Windows Workflow Foundation kullanılarak uygulanan bir dayanıklı çift yönlü ileti alışverişi olacak şekilde yapılandırılmış. Dayanıklı çift yönlü ileti değişimi MSMQ gönderilir ve kullanılarak bağıntılı iki tek yönlü gelen iletileri oluşan [.NET bağlam değişimi](http://go.microsoft.com/fwlink/?LinkID=166059). İletileri kullanılarak gönderilen <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> Mesajlaşma etkinlikleri. .NET bağlam değişimi gönderilen iletileri geri çağırma adresini belirtmek için kullanın. Her iki hizmet Windows İşlem Etkinleştirme Hizmetleri (WAS) kullanılarak barındırılır ve Hizmetleri örneklerinin Kalıcılık etkinleştirmek için yapılandırılır.  
  
 İlk hizmet (Service1.xamlx) biraz çalışmanız gönderme hizmete (Service2.xamlx) bir isteği gönderir. İş tamamlandığında, Service2.xamlx iş tamamlanıp tamamlanmadığını göstermek için geri için Service1.xamlx bir bildirim gönderir. Bir iş akışı konsol uygulaması hizmetlerin dinlediği sıralarını ayarlar ve Service1.xamlx etkinleştirmek için ilk başlatma iletisi gönderir. İstenen iş tamamlandı Service2.xamlx bildirimden service1.xamlx aldıktan sonra Service1.xamlx sonucu bir XML dosyasına kaydeder. Geri çağırma ileti için beklenirken Service1.xamlx varsayılan kullanılarak örneği durumu devam <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>. Service2.xamlx örneği durumuna Service1.xamlx tarafından istenen çalışmayı tamamladıktan bir parçası olarak devam ettirir.  
  
 .NET bağlam değişimi üzerinde MSMQ kullanmak üzere hizmetlerin yapılandırmak için her iki hizmet oluşan özel bağlama kullanmak üzere yapılandırılmış <xref:System.ServiceModel.Channels.ContextBindingElement> ve <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>. Bir geri çağırma adresi ile belirtilen <xref:System.ServiceModel.Channels.ContextBindingElement> ve bir geri çağırma içerik üstbilgisinde özel bağlama kullanılarak gönderilen tüm iletiler eklenir. Aşağıdaki kod örneğinde özel bağlama tanımlar.  
  
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
>  Bu örnek tarafından kullanılan bağlama güvenli değildir. Uygulamanızı dağıtırken, uygulamanızın güvenlik gereksinimlerine bağlı olarak, bağlama yapılandırmanız gerekir.  
  
> [!NOTE]
>  Bu örnekte kullanılan sıraları işlem değildir. İşlem sıraları kullanarak WCF ileti alışverişleri ayarlamak üzere nasıl oluşturulduğunu gösteren bir örnek için bkz: [MSMQ etkinleştirme](../../../../docs/framework/wcf/samples/msmq-activation.md) örnek.  
  
 İçin Service2.xamlx service1.xamlx tarafından gönderilen ileti Service2.xamlx ve özel bağlama adresiyle yapılandırılmış bir istemci uç noktası kullanarak, önceden tanımlanmış gönderilir. Geri Service2.xamlx aramasından Service1.xamlx için adresi Service1.xamlx tarafından gönderilen geri çağırma içeriğinden alınır için açıkça yapılandırılmış hiçbir adresiyle bir istemci uç noktası kullanılarak gönderilir. Aşağıdaki kod örneği, istemci uç noktaları tanımlar.  
  
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
  
 Aşağıdaki kod örneği, bu özel bağlama kullanmak için net.msmq temel adres için varsayılan protokolü eşleme değiştirerek bu özel bağlama kullanma uç noktaları kullanıma sunar.  
  
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
  
 Aşağıdaki kod örneğinde ekleyerek her iki hizmet kalıcılığını etkinleştirir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranışı hem Hizmetleri, hem de Kalıcılık veritabanı için bağlantı dizesini belirleme.  
  
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
 Bu örnek, aşağıdaki bileşenleri gerektirir.  
  
1.  Internet Information Services.  
  
2.  Internet Information Services IIS 6.0 Yönetim uyumluluğu -> IIS metatabanı ve IIS 6.0 yapılandırma uyumluluğu ->.  
  
3.  World Wide Web Hizmetleri -> uygulama geliştirme özellikleri -> ASP.NET.  
  
4.  Microsoft Message sıraları (MSMQ) sunucusu.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kalıcılık veritabanı ve sonuçlar dizini ayarlayın.  
  
    1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
    2.  Bu örnek için klasörüne gidin ve Setup.cmd çalıştırın.  
  
2.  Sanal uygulama ayarlama.  
  
    1.  Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut isteminde, aşağıdaki komutu çalıştırarak ASP.NET kaydolun.  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yönetici izinlerine sahip [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve seçerek **yönetici olarak çalıştır**.  
  
    3.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DurableDuplex.sln dosyasını açın.  
  
3.  Hizmet sıralarını ayarlayın.  
  
    1.  DurableDuplex istemci çalıştırmak için F5 tuşuna basın.  
  
    2.  Açık **Bilgisayar Yönetimi** çalıştırarak konsol `Compmgmt.msc` bir komut isteminden.  
  
    3.  Genişletme **hizmet ve uygulamaları**, **Message Queuing**. **Özel sıralar**.  
  
    4.  Durableduplex/service1.xamlx ve durableduplex/service2.xamlx sıralar sağ tıklatıp **özellikleri**.  
  
    5.  Seçin **güvenlik** sekmesinde ve izin **herkes ileti Al**, **iletiye** ve **iletisi gönder** izinleri hem sıralar.  
  
    6.  İnternet Bilgi Hizmetleri (IIS) Yöneticisini açın.  
  
    7.  Gözat **Server**, **siteleri**, **varsayılan Web sitesi**, **özel**, **dayanıklı çift yönlü** ve seçin **Gelişmiş Seçenekler**.  
  
    8.  Değişiklik **etkin protokoller** için **http,net.msmq**.  
  
4.  Örnek çalıştırın.  
  
    1.  Gözat http://localhost/private/durableduplex/service1.xamlx ve http://localhost/private/durableduplex/service2.xamlx hem hizmetlerinin çalıştığından emin olmak için.  
  
    2.  DurableDuplexClient çalıştırmak için F5 tuşuna basın.  
  
         Dayanıklı çift yönlü ileti değişimi tamamlandığında result.xml dosya C:\Inbox klasörüne kaydedilir ve ileti değişimi sonucunu içerir.  
  
#### <a name="to-cleanup-optional"></a>Temizleme (isteğe bağlı)  
  
1.  CleanUp.cmd çalıştırın.  
  
    1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
    2.  Bu örnek için klasörüne gidin ve Cleanup.cmd çalıştırın.  
  
2.  Sanal uygulama hizmetleri için kaldırın.  
  
    1.  Internet Information Services (IIS) Yöneticisi'ni çalıştırarak açmak `Inetmgr.exe` bir komut isteminden.  
  
    2.  Varsayılan Web sitesine gidin ve Kaldır **özel** sanal dizin.  
  
3.  Bu örnek için ayarlanan sıraları kaldırın.  
  
    1.  Bilgisayar Yönetimi konsolunu açın `Compmgmt.msc` bir komut isteminden.  
  
    2.  Genişletme **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.  
  
    3.  Durableduplex/service1.xamlx ve durableduplex/service2.xamlx sıralar silin.  
  
4.  C:\Inbox dizini kaldırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`