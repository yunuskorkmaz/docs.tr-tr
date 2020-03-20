---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 6b7a72fdd814aa9d2e0f125cf4dbdaf63ba753e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183625"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Bu örnek, oturum yönetimi için HTTP tanımlama bilgilerini kullanmak üzere özel bir iletişim kanalının nasıl oluşturulabildiğini gösterir. Bu kanal, Windows Communication Foundation (WCF) hizmetleri ile ASMX istemcileri arasında veya WCF istemcileri ile ASMX hizmetleri arasında iletişim ilerler.  
  
 Bir istemci oturum tabanlı bir ASMX Web hizmetinde bir Web yöntemi ni aradığında, ASP.NET altyapısı aşağıdakileri yapar:  
  
- Benzersiz bir kimlik (oturum kimliği) oluşturur.  
  
- Oturum nesnesini oluşturur ve benzersiz kimlikle ilişkilendirer.  
  
- Set-Cookie HTTP yanıt üstbilgisine benzersiz kimliği ekler ve istemciye gönderir.  
  
- İstemciyi, kendisine gönderdiği oturum kimliğine göre sonraki aramalarda tanımlar.  
  
 İstemci, sunucuya sonraki isteklerinde bu oturum kimliğini içerir. Sunucu, geçerli HTTP bağlamı için uygun oturum nesnesini yüklemek için istemciden gelen oturum kimliğini kullanır.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>httpcookiesession kanal ileti alışverişi deseni  
 Bu örnek, ASMX benzeri senaryolar için oturumlar sağlar. Kanal yığınımızın alt kısmında, http ulaşımı <xref:System.ServiceModel.Channels.IRequestChannel> destekler <xref:System.ServiceModel.Channels.IReplyChannel>ve . Kanal yığınının daha yüksek seviyelerine oturumlar sağlamak kanalın işidir. Örnek,<xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel>oturumları destekleyen iki kanal uygular.  
  
## <a name="service-channel"></a>Servis Kanalı  
 `HttpCookieReplySessionChannelListener` Örnek, sınıfta bir servis kanalı sağlar. Bu sınıf <xref:System.ServiceModel.Channels.IChannelListener> arabirimi uygular ve <xref:System.ServiceModel.Channels.IReplyChannel> kanalı kanal yığınının alt <xref:System.ServiceModel.Channels.IReplySessionChannel>tan bir ' e dönüştürür. Bu işlem aşağıdaki bölümlere ayrılabilir:  
  
- Kanal dinleyicisi açıldığında, iç dinleyicisinden bir iç kanalı kabul eder. İç dinleyici bir datagram dinleyici sayıldığından ve kabul edilen bir kanalın ömrü dinleyicinin ömründen ayrıştırıldığı için, iç dinleyiciyi kapatabilir ve yalnızca iç kanala tutunabiliriz.  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- Açık işlem tamamlandığında, iç kanaldan ileti almak için bir ileti döngüsü oluştururuz.  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- Bir ileti geldiğinde, servis kanalı oturum tanımlayıcısını inceler ve uygun oturum kanalına çok katlı ları inceler. Kanal dinleyicisi, oturum tanımlayıcılarını oturum kanalı örnekleriyle eşleyen bir sözlük tutar.  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 Sınıf `HttpCookieReplySessionChannel` uygular. <xref:System.ServiceModel.Channels.IReplySessionChannel> Kanal yığınının daha yüksek <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> düzeyleri, bu oturum için isteklerini okumak için yöntemi çağırır. Her oturum kanalının, hizmet kanalı tarafından doldurulan özel bir ileti sırası vardır.  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 Birisi <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> yöntemi aradığında ve ileti kuyruğunda ileti yoksa, kanal kendisini kapatmadan önce belirli bir süre bekler. Bu, WCF olmayan istemciler için oluşturulan oturum kanallarını temizler.  
  
 Biz izlemek `channelMapping` için `ReplySessionChannels`kullanın , ve tüm `innerChannel` kabul edilen kanallar kapatılmış kadar bizim temel kapatmaz. Bu `HttpCookieReplySessionChannel` yol ömrü boyunca `HttpCookieReplySessionChannelListener`var olabilir. Ayrıca, kabul edilen kanallar `OnClosed` geri arama yoluyla dinleyicilerine bir referans tuttuğu ndan, dinleyicinin altımızda çöp toplanması konusunda endişelenmemize de gerek yok.  
  
## <a name="client-channel"></a>İstemci kanalı  
 Karşılık gelen istemci kanalı `HttpCookieSessionChannelFactory` sınıfta. Kanal oluşturma sırasında, kanal fabrikası iç istek `HttpCookieRequestSessionChannel`kanalını bir . Sınıf `HttpCookieRequestSessionChannel` çağrıları temel istek kanalına ileter. İstemci proxy'yi `HttpCookieRequestSessionChannel` kapattığında, hizmete kanalın kapatıldığını belirten bir ileti gönderir. Böylece, servis kanalı yığını kullanılmakta olan oturum kanalını düzgün bir şekilde kapatabilir.  
  
## <a name="binding-and-binding-element"></a>Bağlama ve Bağlama Elemanı  
 Hizmet ve istemci kanalları oluşturulduktan sonra, bir sonraki adım bunları WCF çalışma süresine entegre etmektir. Kanallar bağlamalar ve bağlama öğeleri aracılığıyla WCF'ye maruz kalır. Bağlama bir veya birkaç bağlama öğesinden oluşur. WCF çeşitli sistem tanımlı bağlamalar sunar; örneğin, Temel HttpBinding veya WSHttpBinding. Sınıf `HttpCookieSessionBindingElement` bağlama öğesi için uygulama içerir. Gerekli kanal dinleyicisi veya kanal fabrika anlık yapmak için kanal dinleyicive kanal fabrika oluşturma yöntemleri geçersiz kılar.  
  
 Örnek, hizmet açıklaması için ilke iddialarını kullanır. Bu, örnek kanalı gereksinimlerini hizmeti tüketebilecek diğer istemcilere yayımlamaolanağı sağlar. Örneğin, bu bağlayıcı öğe, olası istemcilere oturumları desteklediğini bildirmek için ilke iddiaları yayımlar. Örnek bağlama öğesi `ExchangeTerminateMessage` yapılandırmasında özelliği etkinleştirdiği için, hizmetoturum konuşma sona erdirmek için ek bir ileti alışverişi eylemi desteklediğini göstermek için gerekli iddiaları ekler. İstemciler daha sonra bu eylemi kullanabilirsiniz. Aşağıdaki WSDL kodu, `HttpCookieSessionBindingElement`.'dan oluşturulan ilke iddialarını gösterir.  
  
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
  
 Sınıf, `HttpCookieSessionBinding` daha önce açıklanan bağlama öğesini kullanan bir sistem sağlanan bağlamadır.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Yapılandırma Sistemine Kanal Ekleme  
 Örnek, yapılandırma yoluyla örnek kanalı ortaya çıkaran iki sınıf sağlar. İlki için <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> `HttpCookieSessionBindingElement`bir. Uygulamanın büyük bir kısmı `HttpCookieSessionBindingConfigurationElement`, ' den <xref:System.ServiceModel.Configuration.StandardBindingElement>türetilen . Üzerinde `HttpCookieSessionBindingConfigurationElement` özellikleri karşılık gelen özelliklere `HttpCookieSessionBindingElement`sahiptir.  
  
### <a name="binding-element-extension-section"></a>Bağlama Elemanı Uzatma Bölümü  
 Bölüm, `HttpCookieSessionBindingElementSection` yapılandırma <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sistemine `HttpCookieSessionBindingElement` maruz kalan bir bölümdür. Yapılandırma bölüm adını birkaç geçersiz kılar, bağlama öğesinin türü ve bağlama öğesi oluşturmak için nasıl tanımlanır. Daha sonra uzantı bölümünü bir yapılandırma dosyasına aşağıdaki gibi kaydedebiliriz:  
  
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
  
## <a name="test-code"></a>Test Kodu  
 Bu örnek aktarımı kullanmak için test kodu İstemci ve Hizmet dizinlerinde mevcuttur. İki testten oluşur- bir test `allowCookies` istemciye `true` ayarlanmış bir bağlama kullanır. İkinci sınama, bağlamada açık kapatmayı (sonlandırma iletisi değişimini kullanarak) sağlar.  
  
 Örneği çalıştırdığınızda, aşağıdaki çıktıyı görmeniz gerekir:  
  
```console  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
3. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
