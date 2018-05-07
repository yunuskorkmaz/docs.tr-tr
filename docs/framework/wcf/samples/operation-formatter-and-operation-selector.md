---
title: İşlem Biçimlendirici ve İşlem Seçici
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 469b7f2c99652cb6fceb2e8f12f1c74f0140b5ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="operation-formatter-and-operation-selector"></a>İşlem Biçimlendirici ve İşlem Seçici
Bu örnek ileti verilerin ne öğesinden farklı bir biçimde izin vermek için Windows Communication Foundation (WCF) genişletilebilirlik noktaları'nın nasıl kullanılabileceğini gösteren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bekliyor. Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] biçimlendiricileri beklediğiniz altında dahil edilecek yöntem parametreleri `soap:body` öğesi. Örnek, bunun yerine bir HTTP GET sorgu dizesi parametre verilerini ayrıştırır ve bu verileri kullanarak yöntemlerini çağıran bir özel işlem biçimlendirici uygulamak gösterilmiştir.  
  
 Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hangi uygulayan `ICalculator` hizmet sözleşme. Bunu gösterir nasıl eklenir, çıkarma, Çarp, bölme iletileri, HTTP GET istemci-sunucu istekleri için kullanılacak değiştirilebilir ve POX ile HTTP POST için sunucudan istemciye yanıt iletileri.  
  
 Bunu yapmak için örnek aşağıdakileri sağlar:  
  
-   `QueryStringFormatter`, hangi uygulayan <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> istemci ve sunucu için sırasıyla ve sorgu dizesi verileri işler.  
  
-   `UriOperationSelector`, hangi uygulayan <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> GET isteği işlemi adına dayalı gönderme işlemi gerçekleştirmek için sunucu üzerinde.  
  
-   `EnableHttpGetRequestsBehavior` uç noktası davranışı (ve karşılık gelen yapılandırma), çalışma zamanı için gerekli işlem Seçici ekler.  
  
-   Nasıl yeni bir işlem biçimlendirici çalışma zamanına ekleneceğini gösterir.  
  
-   Bu örnekte, hem istemci hem de hizmet konsol (.exe) uygulamalardır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
## <a name="key-concepts"></a>Temel Kavramlar  
 `QueryStringFormatter` -İşlemini biçimlendiricisi bileşenidir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] parametresi nesnelerinin bir dizisi ve bir iletisine parametre nesnelerinin bir dizisi için bir ileti dönüştürme sorumlu. Bu istemciyi kullanarak yapılır <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirimi ve ile sunucuya <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimi. Gelen istek ve yanıt iletileri almak kullanıcıların bu arabirimleri sağlamak `Serialize` ve `Deserialize` yöntemleri.  
  
 Bu örnekte `QueryStringFormatter` hem de bu arabirimlerini uygular ve istemci ve sunucu üzerinde uygulanır.  
  
 İsteği:  
  
-   Örnek kullanır <xref:System.ComponentModel.TypeConverter> dizeleri gelen ve giden istek iletisindeki parametre veri dönüştürmek için sınıf. Varsa bir <xref:System.ComponentModel.TypeConverter> özel bir örnek biçimlendirici atar belirli bir türü için kullanılamaz.  
  
-   İçinde `IClientMessageFormatter.SerializeRequest` yöntemi istemcisinde, biçimlendirici uygun adresine sahip bir URI oluşturur ve işlem adı soneki olarak ekler. Bu ad, sunucudaki uygun işlemini gönderilmesi için kullanılır. Ardından parametre nesneler dizisi alır ve parametre adları ve dönüştürülen değerleri kullanarak URI sorgu dizesi parametresi verileri serileştirir <xref:System.ComponentModel.TypeConverter> sınıfı. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> Ve <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> özellikleri daha sonra bu URI ayarlayın. <xref:System.ServiceModel.Channels.MessageProperties> üzerinden erişilen <xref:System.ServiceModel.Channels.Message.Properties%2A> özelliği.  
  
-   İçinde `IDispatchMessageFormatter.DeserializeRequest` yöntemi sunucuda biçimlendirici alır `Via` gelen istek ileti özelliklerinde URI. Ad-değer çiftleri URI sorgu dizesinde parametre adları ve değerlerine ayrıştırır ve yönteme geçirilen parametre dizisi doldurmak için parametre adları ve değerleri kullanır. Bu nedenle bu yöntemi, işlem adı soneki yoksayıldı işlemi gönderme zaten oluştu unutmayın.  
  
 Yanıtı:  
  
-   Bu örnekte, HTTP GET isteği yalnızca için kullanılır. Biçimlendirici bir XML iletisi oluşturmak için kullanılanla özgün biçimlendirici yanıtı gönderilirken atar. Bu örnek hedeflerinden temsilci bir biçimlendirici nasıl uygulanabilir göstermektir.  
  
### <a name="uripathsuffixoperationselector-class"></a>UriPathSuffixOperationSelector sınıfı  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Arabirimi hangi işlemi için belirli bir ileti gönderilen kendi mantığını uygulamak kullanıcıların sağlar.  
  
 Bu örnekte `UriPathSuffixOperationSelector` işlem adı bir eylem üstbilgisi iletisi yerine HTTP GET URI bulunduğundan uygun işlemi seçmek için sunucuda uygulanmalıdır. Örnek adları yalnızca küçük harf işlemi izin verecek şekilde ayarlanır.  
  
 `SelectOperation` Yöntemi gelen iletiyi alır ve arayan `Via` ileti özelliklerinde URI. URI'den işlemi ad soneki ayıklar, ileti gönderilen işlemi adını almak için bir iç tablosu arar ve bu işlemi adını döndürür.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>EnableHttpGetRequestsBehavior sınıfı  
 `UriPathSuffixOperationSelector` Bileşen ayarlanabilir programlı olarak veya bir uç noktası davranışı. Örnek uygulayan `EnableHttpGetRequestsBehavior` hizmetin uygulama yapılandırma dosyasında belirtilen davranışı.  
  
 Sunucuda:  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Ayarlanır <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulaması.  
  
 Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir tam eşleşme adresi filtresi kullanır. Uç noktası davranışı olmasını adresi Filtresi ayrıca değişiklikler filtre eşleşen bir önek, URI gelen ileti üzerinde parametre veri içeren bir sorgu dizesi tarafından izlenen bir işlemi ad soneki içerir. Kullandığı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> bu amaç için.  
  
### <a name="installing-operation-formatters"></a>Yükleme işlemi biçimlendiricileri  
 Biçimlendiricileri belirtin işlemi davranışları benzersizdir. Bu tür bir davranış her zaman gerekli işlemini biçimlendiricisi oluşturmak her işlem için varsayılan olarak uygulanır. Ancak, bu davranışların gibi başka bir işlem davranışı arar; Bunlar herhangi bir öznitelik tarafından tanımlanabilen değildir. Değiştirme davranışı yüklemek için uygulama tarafından yüklenen belirli biçimlendirici davranışları aramanız gerekir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] varsayılan türü Yükleyicisi ve değiştirmek veya varsayılan davranışı sonra çalıştırmak için uyumlu bir davranış ekleyin.  
  
 Bu işlemi biçimlendiricileri davranışları önce arama program aracılığıyla ayarlanabilir <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> veya varsayılan sonra yürütülen bir işlem davranışı belirterek. Ancak, bunu kolayca bir uç noktası davranışı tarafından ayarlanamaz (ve bu nedenle yapılandırmaya göre) davranış modeli davranışları değiştirin veya aksi halde açıklama ağaç değiştirmek bir davranış izin vermediğinden.  
  
 İstemci üzerinde:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Uygulaması gerekir uygulanan isteklerini HTTP GET isteklerine dönüştürmek ve yanıtlarının özgün biçimlendirici için temsilci. Bu çağırarak yapılır `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi.  
  
 Bu çağırmadan önce yapılmalıdır `CreateChannel`.  
  
```  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 Sunucuda:  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Arabirimi gerekir uygulanan böylece okuma HTTP GET istekleri ve yanıtlar yazmak için temsilci seçme için özgün biçimlendirici. Bu aynı çağırarak yapılır `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi istemci olarak (Yukarıdaki örnek kod bakın).  
  
-   Bu, önce yapılmalıdır <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> olarak adlandırılır. Bu örnekte, biçimlendirici çağırmadan önce el ile nasıl değiştirilmiş olan gösteriyoruz <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Aynı şey elde etmek için başka bir öğesinden bir sınıf türetin yoldur <xref:System.ServiceModel.ServiceHost> çağrı yapar `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` açmadan önce (belgeler ve örnekler için örnekler barındırma Lütfen bakın).  
  
### <a name="user-experience"></a>Kullanıcı deneyimleri  
 Sunucuda:  
  
-   Sunucunun `ICalculator` uygulama değiştirmeniz gerekmez.  
  
-   Hizmeti için App.config ayarlar özel bir POX bağlama kullanmalısınız `messageVersion` özniteliği `textMessageEncoding` öğesine `None`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   Hizmeti için App.config özel de belirtmeniz gerekir `EnableHttpGetRequestsBehavior` davranışı Uzantıları bölümüne ekleyerek ve bunu kullanarak.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add   
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
-   Ekleme işlemi biçimlendiricileri çağırmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
 İstemci üzerinde:  
  
-   İstemci uygulaması değiştirmeniz gerekmez.  
  
-   İstemci için App.config ayarlar özel bir POX bağlama kullanmalısınız `messageVersion` özniteliği `textMessageEncoding` öğesine `None`. Bir hizmet istemci adresine giden değiştirilebilir böylece el ile adresleme etkinleştirmelisiniz farktır.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   App.config istemci için aynı özel belirtmelisiniz `EnableHttpGetRequestsBehavior` sunucusu olarak.  
  
-   Ekleme işlemi biçimlendiricileri çağırmadan önce <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Tüm dört işlemleri (eklemek, çıkarma, çarpma ve bölme) başarılı olması gerekir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
