---
title: İşlem Biçimlendirici ve İşlem Seçici
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 64f2d807946d5365c01cd1a46488c868ebc603ac
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714635"
---
# <a name="operation-formatter-and-operation-selector"></a>İşlem Biçimlendirici ve İşlem Seçici
Bu örnek, WCF 'nin beklediği farklı biçimdeki ileti verilerine izin vermek için Windows Communication Foundation (WCF) genişletilebilirlik noktalarının nasıl kullanılabileceğini gösterir. Varsayılan olarak, WCF biçimleri `soap:body` öğesi altına eklenecek yöntem parametrelerini bekler. Örnek, bunun yerine bir HTTP GET sorgu dizesinden parametre verilerini çözümleyen ve bu verileri kullanarak yöntemleri çağıran özel bir işlem biçimlendiricinin nasıl uygulanacağını gösterir.  
  
 Örnek, `ICalculator` hizmet sözleşmesini uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Ekleme, çıkarma, çarpma ve bölme iletilerinin, sunucudan istemciye yanıtlara yönelik POX iletileri ile istemci-sunucu istekleri ve HTTP POST için HTTP GET kullanmak üzere nasıl değiştirileceğini gösterir.  
  
 Bunu yapmak için örnek şunları sağlar:  
  
- istemci ve sunucu için sırasıyla <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> uygulayan `QueryStringFormatter`ve sorgu dizesindeki verileri işler.  
  
- `UriOperationSelector`, GET isteğindeki işlem adına göre işlem gönderimi gerçekleştirmek üzere sunucuda <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulayan.  
  
- gerekli işlem seçiciyi çalışma zamanına ekleyen uç nokta davranışı (ve karşılık gelen yapılandırma) `EnableHttpGetRequestsBehavior`.  
  
- Çalışma zamanına nasıl yeni bir işlem biçimlendirici ekleneceğini gösterir.  
  
- Bu örnekte, hem istemci hem de hizmet konsol uygulamalardır (. exe).  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="key-concepts"></a>Temel Kavramlar  
 `QueryStringFormatter` işlem biçimlendirici, bir iletiyi bir parametre nesneleri dizisine ve bir dizi parametre nesnesine dönüştürmekten sorumlu WCF 'deki bileşendir. Bu işlem istemcisinde <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirimi kullanılarak ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimiyle sunucu üzerinde yapılır. Bu arabirimler, kullanıcıların `Serialize` ve `Deserialize` metotlarından gelen istek ve yanıt iletilerini almasını sağlar.  
  
 Bu örnekte, `QueryStringFormatter` bu arabirimlerin her ikisini de uygular ve istemci ve sunucu üzerinde uygulanır.  
  
 İsteyen  
  
- Örnek, istek iletisindeki parametre verilerini dizeden ve dizeden dönüştürmek için <xref:System.ComponentModel.TypeConverter> sınıfını kullanır. <xref:System.ComponentModel.TypeConverter> belirli bir tür için kullanılabilir değilse, örnek biçimlendirici bir özel durum oluşturur.  
  
- İstemci üzerindeki `IClientMessageFormatter.SerializeRequest` yönteminde, biçimlendirici uygun bir URI oluşturur ve işlem adını bir sonek olarak ekler. Bu ad, sunucuda uygun işleme göndermek için kullanılır. Daha sonra parametre nesnelerinin dizisini alır ve parametre adlarını ve <xref:System.ComponentModel.TypeConverter> sınıfı tarafından dönüştürülen değerleri kullanarak parametre verilerini URI sorgu dizesine serileştirir. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> ve <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> özellikleri bu URI 'ye ayarlanır. <xref:System.ServiceModel.Channels.MessageProperties> <xref:System.ServiceModel.Channels.Message.Properties%2A> özelliği aracılığıyla erişilir.  
  
- Sunucu üzerindeki `IDispatchMessageFormatter.DeserializeRequest` yönteminde, biçimlendirici gelen istek iletisi özelliklerindeki `Via` URI 'sini alır. URI sorgu dizesindeki ad-değer çiftlerini parametre adları ve değerleri olarak ayrıştırır ve yönteme geçirilen parametrelerin dizisini doldurmak için parametre adlarını ve değerlerini kullanır. İşlem dağıtımının zaten gerçekleştiğini, bu nedenle işlem adı son ekinin bu yöntemde yoksayıldığını unutmayın.  
  
 Yanıtıyla  
  
- Bu örnekte, HTTP GET yalnızca istek için kullanılır. Biçimlendirici, yanıtın bir XML iletisi oluşturmak için kullanılan özgün biçimlendirici öğesine gönderilmesini destekler. Bu örneğin hedeflerinden biri, bu tür bir temsilci seçme biçimlendiricisi nasıl uygulankullanabileceğinizi gösterir.  
  
### <a name="uripathsuffixoperationselector-class"></a>Urıthsonson Fixoperationselector sınıfı  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> arabirimi, kullanıcıların belirli bir iletinin dağıtılması için kendi mantığını uygulamasına olanak sağlar.  
  
 Bu örnekte, işlem adı iletideki bir eylem üst bilgisi yerine HTTP GET URI 'sine dahil edildiğinden, uygun işlemi seçmek için `UriPathSuffixOperationSelector` sunucuda uygulanmalıdır. Örnek yalnızca büyük/küçük harf duyarsız işlem adlarına izin verecek şekilde ayarlanır.  
  
 `SelectOperation` yöntemi gelen iletiyi alır ve ileti özelliklerinde `Via` URI 'sini arar. URI 'den işlem adı sonekini ayıklar, iletinin dağıtılması gereken işlem adını almak için bir iç tablo arar ve bu işlem adını döndürür.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>EnableHttpGetRequestsBehavior sınıfı  
 `UriPathSuffixOperationSelector` bileşeni program aracılığıyla veya bir uç nokta davranışı aracılığıyla ayarlanabilir. Örnek, hizmetin uygulama yapılandırma dosyasında belirtilen `EnableHttpGetRequestsBehavior` davranışını uygular.  
  
 Sunucusunda:  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulamasına ayarlanır.  
  
 Varsayılan olarak, WCF tam eşleşme adresi filtresi kullanır. Gelen iletideki URI, bir işlem adı soneki ve ardından parametre verilerini içeren bir sorgu dizesi içerir, bu nedenle uç nokta davranışı da adres filtresini önek eşleşme filtresi olacak şekilde değiştirir. Bu amaçla WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> kullanır.  
  
### <a name="installing-operation-formatters"></a>İşlem formatlayıcıları yükleniyor  
 Formatlayıcıları belirten işlem davranışları benzersizdir. Bu tür bir davranış, her zaman gerekli işlem biçimlendirici oluşturmak için her işlem için varsayılan olarak uygulanır. Ancak, bu davranışlar yalnızca başka bir işlem davranışı gibi görünür; Bunlar başka bir öznitelik tarafından tanımlanabilir değildir. Değiştirme davranışı yüklemek için, uygulamanın varsayılan olarak WCF türü yükleyici tarafından yüklenen belirli biçimlendirici davranışlarını araması ve bunu değiştirmesi ya da varsayılan davranışından sonra çalışacak uyumlu bir davranış eklemesi gerekir.  
  
 Bu işlem biçimlendiricileri davranışları, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> çağrılmadan önce veya varsayılan bir işlemden sonra yürütülen bir işlem davranışı belirtilerek program aracılığıyla ayarlanabilir. Ancak, davranış modeli bir davranışın diğer davranışları değiştirmesine izin vermediğinden veya açıklama ağacını değiştiremediğinden, bir uç nokta davranışı (ve dolayısıyla yapılandırmaya göre) kolayca ayarlanamaz.  
  
 İstemcide:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> uygulamasının, istekleri HTTP GET isteklerine dönüştürebilmesi ve yanıtlar için özgün biçimlendirici için temsilci olarak uygulanması gerekir. Bu, `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi çağırarak yapılır.  
  
 `CreateChannel`çağrılmadan önce bunun yapılması gerekir.  
  
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
  
 Sunucusunda:  
  
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimi, HTTP GET isteklerini okuyabilmesi ve yanıt yazmak için özgün biçimlendirici için temsilci olarak uygulanmalıdır. Bu, istemcisiyle aynı `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi çağırarak yapılır (önceki kod örneğine bakın).  
  
- <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> çağrılmadan önce bunun yapılması gerekir. Bu örnekte, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>çağrılmadan önce biçimlendirici 'nin el ile nasıl değiştirildiğini gösteririz. Aynı şeyi elde etmenin bir diğer yolu da, açmadan önce `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` çağrıları yapan <xref:System.ServiceModel.ServiceHost> bir sınıf türetmektir (lütfen bkz. barındırma belgeleri ve örnekler için örnekler).  
  
### <a name="user-experience"></a>Kullanıcı deneyimleri  
 Sunucusunda:  
  
- Sunucu `ICalculator` uygulamasının değiştirilmesi gerekmez.  
  
- Hizmet için App. config, `textMessageEncoding` öğesinin `messageVersion` özniteliğini `None`olarak ayarlayan özel bir POX bağlaması kullanmalıdır.  
  
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
  
- Hizmet için App. config Ayrıca, davranış uzantıları bölümüne ekleyerek ve kullanarak özel `EnableHttpGetRequestsBehavior` belirtmelidir.  
  
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
  
- <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>çağrılmadan önce işlem formatlayıcıları ekleyin.  
  
 İstemcide:  
  
- İstemci uygulamasının değiştirilmesi gerekmez.  
  
- İstemci için App. config, `textMessageEncoding` öğesinin `messageVersion` özniteliğini `None`olarak ayarlayan özel bir POX bağlaması kullanmalıdır. Hizmetin bir farkı, istemcinin el ile adreslemeyi etkinleştirmek zorunda olduğundan, giden adresinin değiştirilmesini sağlar.  
  
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
  
- İstemci için App. config sunucusuyla aynı özel `EnableHttpGetRequestsBehavior` belirtmelidir.  
  
- <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>çağrılmadan önce işlem formatlayıcıları ekleyin.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Dört işlemin tümü (Ekle, çıkart, çarp ve Böl) başarılı olmalıdır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
