---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 9e15aefd4a66eac98b679e60c628f90149fe908a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520860"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Bu örnek, bir özel Protokolü kanalı HTTP tanımlama bilgileri oturum yönetimi için kullanılacak yapı gösterilmiştir. Bu kanal, Windows Communication Foundation (WCF) Hizmetleri ile ASMX istemciler veya WCF istemcileri ve ASMX hizmetleri arasında iletişimi sağlar.  
  
 Oturum tabanlı bir istemci bir Web yöntemine bir ASMX Web hizmetinde, çağırdığında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] altyapısı şunları yapar:  
  
-   Benzersiz bir kimliği (oturum kimliği) oluşturur.  
  
-   Oturum nesnesi oluşturur ve onu benzersiz kimliği ile ilişkilendirir  
  
-   Set-Cookie HTTP yanıt üst bilgisi için benzersiz kimliği ekler ve istemciye gönderir.  
  
-   Bu kümeye gönderen oturum kimliği temel alarak sonraki çağrılar istemcide tanımlar.  
  
 İstemci bu oturum kimliği, sonraki istekleri sunucuya içerir. Sunucu, geçerli HTTP bağlamı için uygun bir oturum nesnesi yüklemek için istemci oturum kimliği kullanır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>HttpCookieSession kanal ileti değişim deseni  
 Bu örnek, ASMX gibi senaryolar için oturum sağlar. Bizim kanal yığının en altında desteklediği HTTP aktarımı sahibiz <xref:System.ServiceModel.Channels.IRequestChannel> ve <xref:System.ServiceModel.Channels.IReplyChannel>. Kanal yığın daha yüksek düzeyde oturumları sağlamak için kanal işidir. Örnek iki kanal uygular (<xref:System.ServiceModel.Channels.IRequestSessionChannel> ve <xref:System.ServiceModel.Channels.IReplySessionChannel>) oturumları destekler.  
  
## <a name="service-channel"></a>Hizmet kanalı  
 Örnek, bir hizmet kanalı sağlar `HttpCookieReplySessionChannelListener` sınıfı. Bu sınıfın uyguladığı <xref:System.ServiceModel.Channels.IChannelListener> dönüştürür ve arabirimi <xref:System.ServiceModel.Channels.IReplyChannel> kanaldan için kanal yığınında daha düşük bir <xref:System.ServiceModel.Channels.IReplySessionChannel>. Bu işlem, aşağıdaki bölümlere ayrılabilir:  
  
-   Kanal dinleyicisi açıldığında, kendi iç dinleyici iç bir kanaldan kabul eder. Bir veri birimi dinleyici iç dinleyici olduğunu ve kabul edilen bir kanal ömrünü, dinleyici ömrünü ayrılmış olduğundan, biz iç dinleyici kapatın ve yalnızca iç kanala tutun  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   Açma işlemi tamamlandıktan sonra bir ileti döngüsü iç kanaldan iletileri alacak şekilde ayarladık.  
  
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
  
-   İleti geldiğinde, hizmet kanalı oturum tanımlayıcısı inceler ve devre dışı bırakmak için uygun bir oturum kanalı bağlantıları çoğaltır. Kanal dinleyicisi oturumu oturum kanalı örneklerine eşleştirir bir sözlük tutar.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` Sınıfının Implements <xref:System.ServiceModel.Channels.IReplySessionChannel>. Kanal daha yüksek düzeyde çağrı yığın <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> bu oturum için istek okumak için yöntem. Her oturum kanalı hizmet kanalı tarafından doldurulan özel bir ileti kuyruğu vardır.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 Birisi çağırdığında, bu durumda <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> yöntemi ve ileti kuyruğa iletiler yoktur, kanalın kendisi kapatmadan önce belirtilen bir süre bekler. Bu, WCF olmayan istemciler için oluşturulan oturum kanalları temizler.  
  
 Kullandığımız `channelMapping` izlemek için `ReplySessionChannels`, ve bizim temel kapatmayın `innerChannel` kabul edilen tüm kanalları kapatılana kadar. Bu şekilde `HttpCookieReplySessionChannel` ömrünü bulunabilir `HttpCookieReplySessionChannelListener`. Biz de kabul edilen kanallar kendi dinleyici başvuru sürekli değiştiğinden bize altında toplanan çöp alma dinleyici hakkında endişelenmenize gerek kalmaz `OnClosed` geri çağırma.  
  
## <a name="client-channel"></a>İstemci kanal  
 Karşılık gelen istemci kanal bulunduğu `HttpCookieSessionChannelFactory` sınıfı. Kanal oluşturma sırasında kanal fabrikası ile iç istek kanalı sarmalar bir `HttpCookieRequestSessionChannel`. `HttpCookieRequestSessionChannel` Sınıfı, temel alınan istek kanalı çağrıları iletir. İstemci proxy kapandığında `HttpCookieRequestSessionChannel` kanal kapalı olduğunu gösteren hizmete ileti gönderir. Bu nedenle, hizmet kanalı yığın kapatılabilir düzgün bir şekilde kullanılan oturum kanalı.  
  
## <a name="binding-and-binding-element"></a>Bağlama ve bağlama öğesi  
 Hizmet ve istemci kanalları oluşturduktan sonra bunları WCF çalışma zamanına tümleştirmek için sonraki adım olacaktır. Kanalları WCF'ye bağlamalar ve bağlama öğeleri sunulur. Bağlama, bir veya birden çok bağlama öğelerden oluşur. WCF birçok sistem tanımlı bağlamalar sunar. Örneğin, BasicHttpBinding veya WSHttpBinding. `HttpCookieSessionBindingElement` Sınıfı bağlama öğesi uygulamasını içerir. Kanal fabrikası oluşturma yöntemleri ve kanal dinleyicisi gerekli kanal dinleyicisi veya kanal fabrikası örneklemeleri yapmak için geçersiz kılar.  
  
 Örnek ilke onaylamalarını hizmet açıklamasını kullanır. Bu hizmet tüketebileceği diğer istemcilere, kanal gereksinimleri yayımlamak bir örnek sağlar. Örneğin, bu bağlama öğesi oturumları desteklendiğini olası istemcileri sağlamak için ilke onaylamalarını yayımlar. Örnek sağladığından `ExchangeTerminateMessage` bağlama öğesi yapılandırması özelliğinde hizmet konuşma oturumu sonlandırmak için ek ileti exchange eylem desteklediğini göstermek için gerekli bir onayları ekler. İstemciler daha sonra bu eylemi kullanabilirsiniz. Aşağıdaki WSDL kod oluşturulan ilke onaylamalarını gösterir `HttpCookieSessionBindingElement`.  
  
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
  
 `HttpCookieSessionBinding` Daha önce açıklanan bağlama öğesi kullanan sistem tarafından sağlanan bir bağlamayı sınıftır.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Kanal yapılandırmasını sisteme ekleme  
 Örnek yapılandırma örnek kanalımızdan kullanıma iki sınıflar sağlar. İlki bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> için `HttpCookieSessionBindingElement`. Toplu uygulama için temsilci `HttpCookieSessionBindingConfigurationElement`, öğesinden türetildiğini <xref:System.ServiceModel.Configuration.StandardBindingElement>. `HttpCookieSessionBindingConfigurationElement` Üzerinde özelliklerine karşılık gelen özelliklerle sahip `HttpCookieSessionBindingElement`.  
  
### <a name="binding-element-extension-section"></a>Bağlama öğesi uzantısı bölümü  
 Bölüm `HttpCookieSessionBindingElementSection` olduğu bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> kullanıma sunan `HttpCookieSessionBindingElement` yapılandırma sistemi için. İle bazı geçersiz kılmaları yapılandırma bölümü adı, bağlama öğesi türü ve bağlama öğesi oluşturmak nasıl tanımlanır. Biz ardından uzantısı bölümüne bir yapılandırma dosyasında şu şekilde kaydedebilirsiniz:  
  
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
  
## <a name="test-code"></a>Test kodu  
 Bu örnek aktarım kullanmak için test kodu, istemci ve hizmet dizinler kullanılabilir. İki testleri oluşur; bir test kullanan bir bağlamayla `allowCookies` ayarlayın `true` istemci üzerinde. İkinci test bağlamadaki açık kapatma (Sonlandır iletisi exchange kullanarak) sağlar.  
  
 Örneği çalıştırdığınızda, aşağıdaki çıktıyı görmeniz gerekir:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
