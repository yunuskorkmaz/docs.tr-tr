---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: f0c6cee2eb7ed9552452f95b71db7e942e84bcb0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044922"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Bu örnek, oturum yönetimi için HTTP tanımlama bilgilerini kullanmak üzere özel bir protokol kanalının nasıl oluşturulacağını gösterir. Bu kanal, Windows Communication Foundation (WCF) Hizmetleri ile ASMX istemcileri veya WCF istemcileri ile ASMX hizmetleri arasında iletişime izin verebilir.  
  
 İstemci, oturum tabanlı bir ASMX Web hizmetinde bir Web yöntemi çağırdığında, ASP.NET altyapısı şunları yapar:  
  
- Benzersiz bir KIMLIK (oturum KIMLIĞI) oluşturur.  
  
- Oturum nesnesini oluşturur ve benzersiz KIMLIK ile ilişkilendirir.  
  
- Benzersiz KIMLIĞI bir set-Cookie HTTP yanıt üstbilgisine ekler ve istemciye gönderir.  
  
- İstemciye gönderdiği oturum KIMLIĞINE göre sonraki çağrılarda istemciyi tanımlar.  
  
 İstemci, sonraki isteklerinde bu oturum KIMLIĞINI sunucusuna ekler. Sunucu, geçerli HTTP bağlamı için uygun oturum nesnesini yüklemek üzere istemcisinden oturum KIMLIĞINI kullanır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Httppişiriesession kanal Iletisi değişim stili  
 Bu örnek, ASMX benzeri senaryolar için oturumları mümkün bir şekilde sunar. Kanal yığınımızın en altında, ve <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IReplyChannel>' yi destekleyen http taşıdık. Kanal yığınının daha yüksek düzeylerine oturumlar sağlamak için kanal işdir. Örnek, oturumları destekleyen iki kanal (<xref:System.ServiceModel.Channels.IRequestSessionChannel> ve <xref:System.ServiceModel.Channels.IReplySessionChannel>) uygular.  
  
## <a name="service-channel"></a>Hizmet kanalı  
 Örnek, `HttpCookieReplySessionChannelListener` sınıfında bir hizmet kanalı sağlar. Bu sınıf, <xref:System.ServiceModel.Channels.IChannelListener> arabirimini uygular ve kanalı kanal <xref:System.ServiceModel.Channels.IReplyChannel> yığınında daha düşük bir <xref:System.ServiceModel.Channels.IReplySessionChannel>değerine dönüştürür. Bu işlem aşağıdaki bölümlere ayrılabilir:  
  
- Kanal dinleyicisi açıldığında, iç dinleyicisinden bir iç kanalı kabul eder. İç dinleyici bir veri birimi dinleyicisi olduğundan ve kabul edilen bir kanalın ömrü, dinleyicinin yaşam süresinden ayrıldığından, iç dinleyiciyi kapatabilir ve yalnızca iç kanala sahip olabilir  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- Açık işlem tamamlandığında, iç kanaldan ileti almak için bir ileti döngüsü ayarladık.  
  
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
  
- Bir ileti geldiğinde hizmet kanalı, oturum tanımlayıcısını inceler ve uygun oturum kanalında aynı şekilde yeniden çoğuller. Kanal dinleyicisi, oturum tanımlayıcılarını oturum kanalı örnekleriyle eşleyen bir sözlük tutar.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` Sınıfı uygular<xref:System.ServiceModel.Channels.IReplySessionChannel>. Kanal yığınının daha yüksek düzeyleri, <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> bu oturum için istekleri okumak üzere yöntemini çağırır. Her oturum kanalının, hizmet kanalı tarafından doldurulan bir özel ileti kuyruğu vardır.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 Birisi <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> yöntemi çağırdığında ve ileti kuyruğunda hiç ileti olmadığında kanal, kendisini kapatmadan önce belirtilen miktarda süre bekler. Bu, WCF olmayan istemciler için oluşturulan oturum kanallarını temizler.  
  
 Öğesini izlemek için`channelMapping` kullanıyoruz, kabul edilen tüm kanallar kapanana kadar temeldeki `innerChannel` sistemimizi kapatmıyoruz. `ReplySessionChannels` Bu şekilde `HttpCookieReplySessionChannel` ömür süresinin ötesinde yer `HttpCookieReplySessionChannelListener`alabilir. Ayrıca, kabul edilen kanallar `OnClosed` geri çağırma aracılığıyla dinleyiciye bir başvuru tutacağından, atık toplama işlemi konusunda endişelenmenize gerek kalmaz.  
  
## <a name="client-channel"></a>İstemci kanalı  
 Karşılık gelen istemci kanalı `HttpCookieSessionChannelFactory` sınıfındır. Kanal oluşturma sırasında kanal fabrikası, iç istek kanalını bir `HttpCookieRequestSessionChannel`ile sarmalanmış. `HttpCookieRequestSessionChannel` Sınıfı, çağrıları temel alınan istek kanalına iletir. İstemci proxy 'yi kapattığında, `HttpCookieRequestSessionChannel` kanalın kapatıldığını belirten bir ileti gönderir. Bu nedenle, hizmet kanalı yığını kullanımda olan oturum kanalını düzgün şekilde kapatır.  
  
## <a name="binding-and-binding-element"></a>Bağlama ve bağlama öğesi  
 Hizmet ve istemci kanallarını oluşturduktan sonra, bir sonraki adım bunları WCF çalışma zamanına tümleştirmelidir. Kanallar, bağlamalar ve bağlama öğeleri aracılığıyla WCF 'ye sunulur. Bağlama bir veya daha fazla bağlama öğelerinden oluşur. WCF, sistem tarafından tanımlanan birkaç bağlama sunar; Örneğin, BasicHttpBinding veya WSHttpBinding. `HttpCookieSessionBindingElement` Sınıfı, bağlama öğesinin uygulamasını içerir. Gerekli kanal dinleyicisini veya kanal fabrikası örneklemesini yapmak için kanal dinleyicisini ve kanal fabrikası oluşturma yöntemlerini geçersiz kılar.  
  
 Örnek, hizmet açıklaması için ilke onayları kullanır. Bu, örneğin kanal gereksinimlerini hizmeti kullanabilen diğer istemcilere yayımlamasına olanak sağlar. Örneğin, bu bağlama öğesi, olası istemcilerin oturumları desteklediğini bilmesini sağlamak için ilke onayları yayımlar. Örnek, bağlama öğesi yapılandırmasındaki `ExchangeTerminateMessage` özelliği sağladığından, hizmetin oturum iletişimini sonlandırmak için ek bir ileti değişimi işlemini desteklediğini göstermek için gerekli onayları ekler. İstemciler daha sonra bu eylemi kullanabilir. Aşağıdaki WSDL kodunda, `HttpCookieSessionBindingElement`öğesinden oluşturulan ilke onayları gösterilmektedir.  
  
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
  
 `HttpCookieSessionBinding` Sınıfı, daha önce açıklanan bağlama öğesini kullanan sistem tarafından sağlanmış bir bağlamadır.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Kanal yapılandırma sistemine ekleniyor  
 Örnek, yapılandırma aracılığıyla örnek kanalı kullanıma sunan iki sınıf sağlar. Birincisi, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> `HttpCookieSessionBindingElement`için bir. Uygulamanın toplu işlemi, `HttpCookieSessionBindingConfigurationElement`' den <xref:System.ServiceModel.Configuration.StandardBindingElement>türetilen öğesine Temsilcili. , `HttpCookieSessionBindingConfigurationElement` Üzerindeki`HttpCookieSessionBindingElement`özelliklerine karşılık gelen özelliklere sahiptir.  
  
### <a name="binding-element-extension-section"></a>Bağlama öğesi uzantı bölümü  
 Bu `HttpCookieSessionBindingElementSection` bölüm,<xref:System.ServiceModel.Configuration.BindingElementExtensionElement> yapılandırma sistemine yönelikbir'dır.`HttpCookieSessionBindingElement` Yapılandırma bölümünün adı birkaç geçersiz kılındığında, bağlama öğesinin türü ve bağlama öğesinin nasıl oluşturulacağı tanımlanır. Daha sonra uzantı bölümünü bir yapılandırma dosyasına şu şekilde kaydedebiliriz:  
  
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
 Bu örnek taşımanın kullanılması için test kodu Istemci ve hizmet dizinlerinde kullanılabilir. İki testten oluşur; bir test, istemci üzerinde olarak `allowCookies` `true` ayarlanmış bir bağlama kullanır. İkinci test, bağlama üzerinde açık kapanmaya (sonlandırma iletisi değişimi kullanılarak) izin vermez.  
  
 Örneği çalıştırdığınızda aşağıdaki çıktıyı görmeniz gerekir:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
3. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
