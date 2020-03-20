---
title: İşlem Biçimlendirici ve İşlem Seçici
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 9d1bc0afa54f89e064eab3f3e45da60c8d10de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144285"
---
# <a name="operation-formatter-and-operation-selector"></a>İşlem Biçimlendirici ve İşlem Seçici
Bu örnek, Windows Communication Foundation (WCF) genişletilebilirlik noktalarının, ileti verilerine WCF'nin beklediğinden farklı bir biçimde izin vermek için nasıl kullanılabileceğini göstermektedir. Varsayılan olarak, WCF formatters yöntem parametrelerinin `soap:body` öğenin altına dahil olmasını bekler. Örnek, parametre verilerini bir HTTP GET sorgu dizesinden ayrıştıran ve bu verileri kullanarak yöntemler çağıran özel bir işlem formatter'ın nasıl uygulanacağını gösterir.  
  
 Örnek, hizmet sözleşmesini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) `ICalculator` dayanır. İletileri Ekle, Çıkar, Çarpve Böl'ün istemciden sunucuya istekler için HTTP GET'i ve sunucudan istemciye yanıtlar için POX iletileriyle HTTP POST'u kullanmak üzere nasıl değiştirilebileceğini gösterir.  
  
 Bunu yapmak için, örnek aşağıdakileri sağlar:  
  
- `QueryStringFormatter`, sırasıyla <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> istemci ve sunucu için uygular ve sorgu dizesindeki verileri işler.  
  
- `UriOperationSelector`, GET <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> isteğindeki işlem adına göre işlem gönderme gerçekleştirmek için sunucuda uygular.  
  
- `EnableHttpGetRequestsBehavior`çalışma süresine gerekli işlem seçicisini ekleyen uç nokta davranışı (ve buna karşılık gelen yapılandırma).  
  
- Çalışma süresine yeni bir işlem için nasıl ekilir gösterir.  
  
- Bu örnekte, hem istemci hem de hizmet konsol uygulamaları (.exe) vardır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
## <a name="key-concepts"></a>Önemli Kavramlar  
 `QueryStringFormatter`- Formatter işlemi, WCF'de bir iletiyi parametre nesnelerine ve bir dizi parametre nesnesine bir iletiye dönüştürmekten sorumlu olan bileşendir. Bu <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirim kullanılarak istemci ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirim ile sunucuda yapılır. Bu arabirimler, kullanıcıların istek ve yanıt `Serialize` iletilerini `Deserialize` yöntem ve yöntemlerden almalarını sağlar.  
  
 Bu örnekte, `QueryStringFormatter` bu arabirimlerin her ikisini de uygular ve istemci ve sunucu üzerinde uygulanır.  
  
 İstek:  
  
- Örnek, istek <xref:System.ComponentModel.TypeConverter> iletisindeki parametre verilerini dizeleri dizeleri ve dizeleri dönüştürmek için sınıfı kullanır. Belirli <xref:System.ComponentModel.TypeConverter> bir tür için a kullanılamıyorsa, örnek madde bir özel durum oluşturur.  
  
- İstemci `IClientMessageFormatter.SerializeRequest` üzerindeki yöntemde, formatter uygun Adres ile bir URI oluşturur ve bir sonek olarak işlem adı ekler. Bu ad, sunucudaki uygun işlemi göndermek için kullanılır. Daha sonra parametre nesneleri dizialır ve parametre adları ve <xref:System.ComponentModel.TypeConverter> sınıf tarafından dönüştürülen değerleri kullanarak URI sorgu dizepara verileri serileştirir. Ve <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> özellikleri daha sonra bu URI ayarlanır. <xref:System.ServiceModel.Channels.MessageProperties><xref:System.ServiceModel.Channels.Message.Properties%2A> tesis üzerinden erişilir.  
  
- Sunucudaki `IDispatchMessageFormatter.DeserializeRequest` yöntemde, formatter gelen istek `Via` iletisi özelliklerinde URI'yi alır. URI sorgu dizesindeki ad-değer çiftlerini parametre adları ve değerleri olarak parlar ve yönteme geçirilen parametre dizisini doldurmak için parametre adlarını ve değerlerini kullanır. Bu yöntemde işlem adı sonek lerinin yoksayıldığını unutmayın.  
  
 Yanıt:  
  
- Bu örnekte, HTTP GET yalnızca istek için kullanılır. Formatter, xml iletisi oluşturmak için kullanılan orijinal maddeye yanıt gönderilmesini delege eder. Bu örneğin amaçlarından biri, böyle bir yasal maddenin nasıl uygulanabileceğini göstermektir.  
  
### <a name="uripathsuffixoperationselector-class"></a>UriPathSuffixOperationSeçici Sınıf  
 Arabirim, <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> kullanıcıların belirli bir iletinin gönderilmesi için kendi mantıklarını uygulamalarını sağlar.  
  
 Bu örnekte, işlem adı iletide bir eylem üstbilgisi yerine HTTP GET URI'ye dahil olduğundan, `UriPathSuffixOperationSelector` uygun işlemi seçmek için sunucuda uygulanması gerekir. Örnek, yalnızca büyük/küçük harf duyarlı işlem adlarına izin verecek şekilde ayarlanmıştır.  
  
 Yöntem `SelectOperation` gelen iletiyi alır ve `Via` ileti özelliklerinde URI'yi arar. URI'den işlem adı soneki ayıklar, iletinin gönderilmesi gereken işlem adını almak için dahili bir tabloya bakar ve bu işlem adını döndürür.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>EnablehttpGetRequestsBehavior Sınıfı  
 Bileşen `UriPathSuffixOperationSelector` programlı olarak veya bir bitiş noktası davranışı ile ayarlanabilir. Örnek, hizmetin `EnableHttpGetRequestsBehavior` uygulama yapılandırma dosyasında belirtilen davranışı uygular.  
  
 Sunucuda:  
  
 Uygulama <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> için <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> ayarlanır.  
  
 Varsayılan olarak, WCF tam eşleme adresi filtresi kullanır. Gelen iletideki URI, parametre verileri içeren bir sorgu dizesi tarafından izlenen bir işlem adı eki içerir, bu nedenle bitiş noktası davranışı adres filtresini önek eşleme filtresi olarak da değiştirir. Bu amaç için<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> WCF kullanır.  
  
### <a name="installing-operation-formatters"></a>Formatters operasyonun yüklenmesi  
 Formatters belirten işlem davranışları benzersizdir. Bu tür davranışlardan biri, her işlem için varsayılan olarak, gerekli işlemi oluşturmak için her zaman uygulanır. Ancak, bu davranışlar sadece başka bir işlem davranışı gibi görünür; başka bir öznitelik tarafından tanımlanabilir değildir. Bir yedek davranış yüklemek için, uygulama varsayılan olarak WCF türü yükleyici tarafından yüklenen belirli madde davranışları aramak gerekir ve ya değiştirmek ya da varsayılan davranış tan sonra çalıştırmak için uyumlu bir davranış eklemek.  
  
 Bu işlem formatters davranışları çağırmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> önce veya varsayılan bir sonra yürütülen bir işlem davranışı belirterek programlı olarak ayarlanabilir. Ancak, davranış modeli bir davranışın diğer davranışları değiştirmesine veya açıklama ağacını başka bir şekilde değiştirmesine izin vermedığından, bir bitiş noktası davranışı (ve bu nedenle yapılandırma) tarafından kolayca ayarlanamaz.  
  
 İstemci üzerinde:  
  
 Uygulama, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> istekleri HTTP GET isteklerine dönüştürebilmek ve yanıtlar için orijinal maddeye temsilci olarak uygulayabilmesi için uygulanmalıdır. Bu `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi çağırarak yapılır.  
  
 Bu aramadan `CreateChannel`önce yapılmalıdır.  
  
```csharp  
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
  
- Arayüz, <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> HTTP GET isteklerini okuyabilmesi ve yanıt ları yazmak için orijinal formatter'a temsilci olarak uygulanmalıdır. Bu, istemciyle aynı `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi ni arayarak yapılır (önceki kod örneğine bakın).  
  
- Bu çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> önce yapılmalıdır. Bu örnekte, formatter'ı aramadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce el ile nasıl değiştirildiğini gösteririz. Aynı şeyi elde etmenin başka bir yolu <xref:System.ServiceModel.ServiceHost> da, açmadan `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` önce aramaları yapan bir sınıf elde etmektir (lütfen örnekler için barındırma belgelerine ve örneklerine bakın).  
  
### <a name="user-experience"></a>Kullanıcı deneyimleri  
 Sunucuda:  
  
- Sunucu `ICalculator` uygulamasının değişmesi gerekmez.  
  
- Hizmet için App.config `messageVersion` `textMessageEncoding` öğenin özniteliğini ayarlayan özel bir POX bağlama kullanmanız `None`gerekir.  
  
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
  
- Hizmet için App.config de davranış `EnableHttpGetRequestsBehavior` uzantıları bölümüne ekleyerek ve kullanarak özel belirtmelidir.  
  
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
  
- Aramadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce işlem formatters ekleyin.  
  
 İstemci üzerinde:  
  
- İstemci uygulamasının değişmesi gerekmez.  
  
- İstemci için `messageVersion` `textMessageEncoding` App.config, öğenin özniteliğini ayarlayan özel `None`bir POX bağlama sı kullanmalıdır. Hizmetten bir fark, giden To adresinin değiştirilebilmesini sağlamak için istemcinin el ile ele alınmasını sağlaması dır.  
  
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
  
- İstemci için App.config sunucu `EnableHttpGetRequestsBehavior` ile aynı özel belirtmelidir.  
  
- Aramadan <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>önce işlem formatters ekleyin.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Dört işlem (Ekle, Çıkar, Çarp ve Böl) başarılı olmalıdır.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
