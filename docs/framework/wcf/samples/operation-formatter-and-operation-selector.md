---
title: İşlem Biçimlendirici ve İşlem Seçici
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 977a759b2c3f6d803879fc640439cd0b3465ffbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965584"
---
# <a name="operation-formatter-and-operation-selector"></a>İşlem Biçimlendirici ve İşlem Seçici
Bu örnek, WCF 'nin beklediği farklı biçimdeki ileti verilerine izin vermek için Windows Communication Foundation (WCF) genişletilebilirlik noktalarının nasıl kullanılabileceğini gösterir. Varsayılan olarak, WCF biçimleri `soap:body` öğesi altına eklenecek yöntem parametrelerini bekler. Örnek, bunun yerine bir HTTP GET sorgu dizesinden parametre verilerini çözümleyen ve bu verileri kullanarak yöntemleri çağıran özel bir işlem biçimlendiricinin nasıl uygulanacağını gösterir.  
  
 Örnek, `ICalculator` hizmet sözleşmesini uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlarken ' i temel alır. Ekleme, çıkarma, çarpma ve bölme iletilerinin, sunucudan istemciye yanıtlara yönelik POX iletileri ile istemci-sunucu istekleri ve HTTP POST için HTTP GET kullanmak üzere nasıl değiştirileceğini gösterir.  
  
 Bunu yapmak için örnek şunları sağlar:  
  
- `QueryStringFormatter`, sırasıyla istemci <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> sunucu uygulayan ve sorgu dizesindeki verileri işleyen.  
  
- `UriOperationSelector`Bu, Get <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> isteğindeki işlem adına göre işlem gönderimi gerçekleştirmek için sunucusunu kullanır.  
  
- `EnableHttpGetRequestsBehavior`gerekli işlem seçiciyi çalışma zamanına ekleyen uç nokta davranışı (ve karşılık gelen yapılandırma).  
  
- Çalışma zamanına nasıl yeni bir işlem biçimlendirici ekleneceğini gösterir.  
  
- Bu örnekte, hem istemci hem de hizmet konsol uygulamalardır (. exe).  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="key-concepts"></a>Temel Kavramlar  
 `QueryStringFormatter`-İşlem biçimlendirici, bir iletiyi bir parametre nesneleri dizisine ve bir dizi parametre nesnesine dönüştürmekten sorumlu olan WCF 'deki bileşendir. Bu, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirimi kullanılarak ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimi ile sunucusunda yapılır. Bu arabirimler, `Serialize` kullanıcıların ve `Deserialize` yöntemlerinden istek ve yanıt iletilerini almasını sağlar.  
  
 Bu örnekte, `QueryStringFormatter` bu arabirimlerin her ikisini de uygular ve istemci ve sunucu üzerinde uygulanır.  
  
 İsteyen  
  
- Örnek, istek iletisindeki <xref:System.ComponentModel.TypeConverter> parametre verilerini dizeden ve dizeden dönüştürmek için sınıfını kullanır. Belirli bir <xref:System.ComponentModel.TypeConverter> tür için kullanılabilir değilse, örnek biçimlendirici bir özel durum oluşturur.  
  
- İstemci üzerindeki `IClientMessageFormatter.SerializeRequest` yönteminde, biçimlendirici uygun bir URI oluşturur ve işlem adını bir sonek olarak ekler. Bu ad, sunucuda uygun işleme göndermek için kullanılır. Daha sonra parametre nesnelerinin dizisini alır ve parametre adlarını ve <xref:System.ComponentModel.TypeConverter> sınıf tarafından dönüştürülen değerleri kullanarak parametre verilerini URI sorgu dizesine dizleştirir. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> Ve<xref:System.ServiceModel.Channels.MessageProperties.Via%2A> özellikleri bu URI 'ye ayarlanır. <xref:System.ServiceModel.Channels.MessageProperties><xref:System.ServiceModel.Channels.Message.Properties%2A> özelliği aracılığıyla erişilir.  
  
- Sunucusundaki yönteminde, biçimlendirici gelen istek iletisi özelliklerindeki `Via` URI 'yi alır. `IDispatchMessageFormatter.DeserializeRequest` URI sorgu dizesindeki ad-değer çiftlerini parametre adları ve değerleri olarak ayrıştırır ve yönteme geçirilen parametrelerin dizisini doldurmak için parametre adlarını ve değerlerini kullanır. İşlem dağıtımının zaten gerçekleştiğini, bu nedenle işlem adı son ekinin bu yöntemde yoksayıldığını unutmayın.  
  
 Yanıtıyla  
  
- Bu örnekte, HTTP GET yalnızca istek için kullanılır. Biçimlendirici, yanıtın bir XML iletisi oluşturmak için kullanılan özgün biçimlendirici öğesine gönderilmesini destekler. Bu örneğin hedeflerinden biri, bu tür bir temsilci seçme biçimlendiricisi nasıl uygulankullanabileceğinizi gösterir.  
  
### <a name="uripathsuffixoperationselector-class"></a>Urıthsonson Fixoperationselector sınıfı  
 Arabirim <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> , kullanıcıların belirli bir ileti dağıtılması için kendi mantığını uygulamasına olanak sağlar.  
  
 Bu örnekte, işlem `UriPathSuffixOperationSelector` adı iletideki bir eylem üst bilgisi yerine http get URI 'sine dahil edildiğinden, uygun işlemi seçmek için sunucuda uygulanması gerekir. Örnek yalnızca büyük/küçük harf duyarsız işlem adlarına izin verecek şekilde ayarlanır.  
  
 Yöntemi gelen iletiyi alır ve kendi ileti özelliklerinde `Via` URI 'yi arar. `SelectOperation` URI 'den işlem adı sonekini ayıklar, iletinin dağıtılması gereken işlem adını almak için bir iç tablo arar ve bu işlem adını döndürür.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>EnableHttpGetRequestsBehavior sınıfı  
 `UriPathSuffixOperationSelector` Bileşen program aracılığıyla veya bir uç nokta davranışı aracılığıyla ayarlanabilir. Örnek, hizmetin uygulama `EnableHttpGetRequestsBehavior` yapılandırma dosyasında belirtilen davranışı uygular.  
  
 Sunucusunda:  
  
 , <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Uygulama<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> olarak ayarlanır.  
  
 Varsayılan olarak, WCF tam eşleşme adresi filtresi kullanır. Gelen iletideki URI, bir işlem adı soneki ve ardından parametre verilerini içeren bir sorgu dizesi içerir, bu nedenle uç nokta davranışı da adres filtresini önek eşleşme filtresi olacak şekilde değiştirir. Bu amaçla WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> 'yi kullanır.  
  
### <a name="installing-operation-formatters"></a>İşlem formatlayıcıları yükleniyor  
 Formatlayıcıları belirten işlem davranışları benzersizdir. Bu tür bir davranış, her zaman gerekli işlem biçimlendirici oluşturmak için her işlem için varsayılan olarak uygulanır. Ancak, bu davranışlar yalnızca başka bir işlem davranışı gibi görünür; Bunlar başka bir öznitelik tarafından tanımlanabilir değildir. Değiştirme davranışı yüklemek için, uygulamanın varsayılan olarak WCF türü yükleyici tarafından yüklenen belirli biçimlendirici davranışlarını araması ve bunu değiştirmesi ya da varsayılan davranışından sonra çalışacak uyumlu bir davranış eklemesi gerekir.  
  
 Bu işlem biçimlendiricileri davranışları, çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> önce veya varsayılan bir işlemden sonra yürütülen bir işlem davranışı belirtilerek program aracılığıyla ayarlanabilir. Ancak, davranış modeli bir davranışın diğer davranışları değiştirmesine izin vermediğinden veya açıklama ağacını değiştiremediğinden, bir uç nokta davranışı (ve dolayısıyla yapılandırmaya göre) kolayca ayarlanamaz.  
  
 İstemcide:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Uygulamanın istekleri HTTP GET isteklerine dönüştürebilmesi ve yanıtlar için özgün biçimlendirici için temsilci olarak uygulanması gerekir. Bu, `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi çağırarak yapılır.  
  
 Çağrılmadan `CreateChannel`önce bunun yapılması gerekir.  
  
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
  
 Sunucusunda:  
  
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Arabirimin http get isteklerini okuyabilmesi ve yanıtları yazmak için özgün biçimlendirici için temsilci olarak uygulanması gerekir. Bu, istemcisiyle aynı `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi çağırarak yapılır (önceki kod örneğine bakın).  
  
- Çağrılmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> bunun yapılması gerekir. Bu örnekte, bir biçimlendirici çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce el ile nasıl değiştirildiğini gösteririz. Aynı şeyi elde etmenin bir diğer yolu da, açmadan <xref:System.ServiceModel.ServiceHost> `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` önce çağrıları yapan öğesinden bir sınıf türetmektir (lütfen bkz. barındırma belgeleri ve örnekler için örnekler).  
  
### <a name="user-experience"></a>Kullanıcı deneyimleri  
 Sunucusunda:  
  
- Sunucu `ICalculator` uygulamasının değiştirilmesi gerekmez.  
  
- Hizmetin App. config `messageVersion` `textMessageEncoding` öğesinin özniteliğini olarak `None`ayarlayan özel bir POX bağlaması kullanması gerekir.  
  
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
  
- Hizmetin App. config dosyası, davranış uzantıları bölümüne ekleyerek ve onu `EnableHttpGetRequestsBehavior` kullanarak özel olarak belirtilmelidir.  
  
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
  
- Çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce işlem formatlayıcıları ekleyin.  
  
 İstemcide:  
  
- İstemci uygulamasının değiştirilmesi gerekmez.  
  
- İstemci için App. config `messageVersion` `textMessageEncoding` öğesinin özniteliğini olarak `None`ayarlayan özel bir POX bağlaması kullanması gerekir. Hizmetin bir farkı, istemcinin el ile adreslemeyi etkinleştirmek zorunda olduğundan, giden adresinin değiştirilmesini sağlar.  
  
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
  
- İstemci için App. config, sunucu ile aynı özel `EnableHttpGetRequestsBehavior` öğesini belirtmelidir.  
  
- Çağrılmadan <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>önce işlem formatlayıcıları ekleyin.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Dört işlemin tümü (Ekle, çıkart, çarp ve Böl) başarılı olmalıdır.  
  
> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
