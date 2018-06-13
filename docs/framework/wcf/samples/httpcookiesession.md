---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 64a7cba7b1bbc55a4504e3af4784fcb2a84f0fa1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807234"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Bu örnek özel protokol kanalı oturum yönetimi için HTTP tanımlama bilgilerini kullanacak şekilde nasıl oluşturulacağını gösterir. Bu kanal veya WCF istemcileri ile ASMX Hizmetleri Windows Communication Foundation (WCF) hizmetlerini ve ASMX istemciler arasında iletişim sağlar.  
  
 Oturum tabanlı bir istemci Web yöntemi bir ASMX Web hizmetinde, çağırdığında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] altyapısı şunları gerçekleştirir:  
  
-   Benzersiz bir kimliği (oturum kimliği) oluşturur.  
  
-   Oturum nesnesi oluşturur ve benzersiz kimliği ile ilişkilendirir  
  
-   Set-Cookie HTTP yanıt üst bilgisi için benzersiz kimlik ekler ve istemciye gönderir.  
  
-   Oturum kimliği temel alarak sonraki çağrılar için gönderir istemcide tanımlar.  
  
 İstemci bu oturum kimliği, sonraki istekleri sunucuya içerir. Sunucu, geçerli HTTP bağlamı için uygun session nesnesi yüklemek için istemci oturum kimliği kullanır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>HttpCookieSession kanal ileti değişim deseni  
 Bu örnek oturumları ASMX gibi senaryolar için etkinleştirir. Bizim kanal yığın alt kısmındaki sahibiz desteklediği HTTP taşıma <xref:System.ServiceModel.Channels.IRequestChannel> ve <xref:System.ServiceModel.Channels.IReplyChannel>. Kanal yığını daha yüksek düzeyde oturumları sağlamak için kanalının işidir. Örnek iki kanalı uygular (<xref:System.ServiceModel.Channels.IRequestSessionChannel> ve <xref:System.ServiceModel.Channels.IReplySessionChannel>) oturumları destekler.  
  
## <a name="service-channel"></a>Hizmet kanal  
 Örnek bir hizmet kanalda sağlar `HttpCookieReplySessionChannelListener` sınıfı. Bu sınıf uygulayan <xref:System.ServiceModel.Channels.IChannelListener> arabirimi ve dönüştürür <xref:System.ServiceModel.Channels.IReplyChannel> için kanal yığındaki alt kanalından bir <xref:System.ServiceModel.Channels.IReplySessionChannel>. Bu işlem aşağıdaki bölümlere ayrılmıştır:  
  
-   Kanal dinleyicisi açıldığında, kendi iç dinleyici iç bir kanaldan kabul eder. Bir veri birimi dinleyicisi iç dinleyici olduğundan ve kabul edilen bir kanal ömrü dinleyicisi ömrü ayrılmış olduğundan, biz iç dinleyici kapatın ve yalnızca iç kanala tutun  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   Açma işlemi tamamlandıktan sonra bir ileti döngüsü iç kanaldan iletiler alan için ayarlarız.  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   Bir ileti geldiğinde hizmet kanalı oturum tanımlayıcısı inceler ve uygun oturum kanalı çoğullamasını. Kanal dinleyicisi oturum tanımlayıcıları oturum kanalı örneklerine eşleyen bir sözlüğü bulundurur.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` Uygulayan sınıf <xref:System.ServiceModel.Channels.IReplySessionChannel>. Kanal yüksek düzeyde çağrı yığınını <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> bu oturum için okunan isteklere yöntemi. Her oturum kanalı hizmet kanal tarafından doldurulan bir özel ileti sırası vardır.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 Birisi çağırdığında durumda <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> yöntemi ve ileti sıraya iletiler yoktur, kendisini kapatmadan önce belirtilen bir süre için kanal bekler. Bu, WCF olmayan istemciler için oluşturulan oturum kanalları temizler.  
  
 Kullanırız `channelMapping` izlemek için `ReplySessionChannels`, ve bizim temel kapatmayın `innerChannel` kabul edilen tüm kanalları kapatılana kadar. Bu şekilde `HttpCookieReplySessionChannel` ömrü bulunabilir `HttpCookieReplySessionChannelListener`. Biz de kabul edilen kanallar kendi dinleyicisi başvuru korudukları için bize altında toplanacak alma dinleyicisi hakkında endişelenmeniz gerekmez `OnClosed` geri çağırma.  
  
## <a name="client-channel"></a>İstemci kanal  
 Karşılık gelen istemci kanal bulunduğu `HttpCookieSessionChannelFactory` sınıfı. Kanal oluşturma sırasında kanal fabrikası iç isteği kanalıyla saran bir `HttpCookieRequestSessionChannel`. `HttpCookieRequestSessionChannel` Sınıfı, temel alınan istek kanalı çağrıları iletir. İstemci proxy kapandığında `HttpCookieRequestSessionChannel` kanal kapatıldığını gösterir hizmeti için bir ileti gönderir. Bu nedenle, hizmet kanal yığını kapatılabilir düzgün biçimde kullanımda oturum kanalı.  
  
## <a name="binding-and-binding-element"></a>Bağlama ve bağlama öğesi  
 Hizmet ve istemci kanalları oluşturduktan sonra WCF çalışma zamanına tümleştirmek için sonraki adım olacaktır. Kanallar için WCF bağlamalar ve bağlama öğeleri sunulur. Bir bağlama bir veya daha çok bağlama öğelerden oluşur. WCF birkaç sistem tanımlı bağlamalar sunar. Örneğin, BasicHttpBinding veya WSHttpBinding. `HttpCookieSessionBindingElement` Sınıfı bağlama öğesi uygulamasını içerir. Kanal fabrikası oluşturma yöntemleri ve kanal dinleyicisi gerekli kanal dinleyicisi veya kanal fabrikası örneklemesi yapmak için geçersiz kılar.  
  
 Örnek ilke onaylamalarını hizmet açıklaması kullanır. Bu hizmet tüketebileceği diğer istemcilere kanal gereklilikleri yayımlamak örnek sağlar. Örneğin, bu bağlama öğesi oturumları desteklendiğini bilmesini potansiyel istemcilerin ilke onaylamalarını yayımlar. Örnek sağladığından `ExchangeTerminateMessage` bağlama öğesi yapılandırma özelliği, hizmet oturumu konuşma sonlandırmak için ek ileti exchange eylem desteklediğini göstermek için gerekli onaylar ekler. İstemciler daha sonra bu eylemi kullanabilirsiniz. Aşağıdaki WSDL'ye oluşturulduğu ilke onaylamalarını gösterir `HttpCookieSessionBindingElement`.  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 `HttpCookieSessionBinding` Daha önce açıklanan bağlama öğesi kullanan sistem tarafından sağlanan bir bağlamayı bir sınıftır.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Yapılandırma sistemi kanal ekleme  
 Örnek örnek kanal yapılandırma aracılığıyla kullanıma iki sınıflar sağlar. İlki bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> için `HttpCookieSessionBindingElement`. Uygulama toplu temsilci için `HttpCookieSessionBindingConfigurationElement`, den türetilen <xref:System.ServiceModel.Configuration.StandardBindingElement>. `HttpCookieSessionBindingConfigurationElement` Özellikler üzerinde karşılık gelen özelliklere sahip `HttpCookieSessionBindingElement`.  
  
### <a name="binding-element-extension-section"></a>Bağlama öğesi uzantısı bölümü  
 Bölüm `HttpCookieSessionBindingElementSection` olan bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> kullanıma sunan `HttpCookieSessionBindingElement` yapılandırma sistemi. Birkaç geçersiz kılmalar, yapılandırma bölümü adı, bağlama öğesi türü ve bağlama öğesi oluşturmak nasıl tanımlanır. Biz sonra uzantısı bölümüne bir yapılandırma dosyasında şu şekilde kaydedebilirsiniz:  
  
```xml  
<configuration>        
    <system.serviceModel>        
      <extensions>          
        <bindingElementExtensions>            
          <add name="httpCookieSession"   
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,   
                    HttpCookieSessionExtension, Version=1.0.0.0,   
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>        
    </system.serviceModel>    
</configuration>  
```  
  
## <a name="test-code"></a>Kodu test  
 Bu örnek aktarım kullanmak için test kodu, istemci ve hizmet dizinler kullanılabilir. İki sınamaları oluşur — bir test kullanır sahip bir bağlama `allowCookies` kümesine `true` istemci üzerinde. İkinci test (Sonlandır iletisi exchange kullanarak) açık kapatma bağlamada sağlar.  
  
 Örneği çalıştırdığınızda, aşağıdaki çıktı görmeniz gerekir:  
  
```  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
