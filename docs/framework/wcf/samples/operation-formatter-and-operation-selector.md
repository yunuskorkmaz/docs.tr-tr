---
title: İşlem Biçimlendirici ve İşlem Seçici
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 344d3122d03e89a7f20e391db49005d0e085dfa6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575179"
---
# <a name="operation-formatter-and-operation-selector"></a>İşlem Biçimlendirici ve İşlem Seçici
Bu örnek, WCF 'nin beklediği farklı biçimdeki ileti verilerine izin vermek için Windows Communication Foundation (WCF) genişletilebilirlik noktalarının nasıl kullanılabileceğini gösterir. Varsayılan olarak, WCF biçimleri öğesi altına eklenecek yöntem parametrelerini bekler `soap:body` . Örnek, bunun yerine bir HTTP GET sorgu dizesinden parametre verilerini çözümleyen ve bu verileri kullanarak yöntemleri çağıran özel bir işlem biçimlendiricinin nasıl uygulanacağını gösterir.  
  
 Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` . Ekleme, çıkarma, çarpma ve bölme iletilerinin, sunucudan istemciye yanıtlara yönelik POX iletileri ile istemci-sunucu istekleri ve HTTP POST için HTTP GET kullanmak üzere nasıl değiştirileceğini gösterir.  
  
 Bunu yapmak için örnek şunları sağlar:  
  
- `QueryStringFormatter`, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> sırasıyla istemci ve sunucu uygulayan ve sorgu dizesindeki verileri işleyen.  
  
- `UriOperationSelector`Bu, <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Get isteğindeki işlem adına göre işlem gönderimi gerçekleştirmek için sunucusunu kullanır.  
  
- `EnableHttpGetRequestsBehavior`gerekli işlem seçiciyi çalışma zamanına ekleyen uç nokta davranışı (ve karşılık gelen yapılandırma).  
  
- Çalışma zamanına nasıl yeni bir işlem biçimlendirici ekleneceğini gösterir.  
  
- Bu örnekte, hem istemci hem de hizmet konsol uygulamalardır (. exe).  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="key-concepts"></a>Önemli Kavramlar  
 `QueryStringFormatter`-İşlem biçimlendirici, bir iletiyi bir parametre nesneleri dizisine ve bir dizi parametre nesnesine dönüştürmekten sorumlu olan WCF 'deki bileşendir. Bu, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirimi kullanılarak ve arabirimi ile sunucusunda yapılır <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> . Bu arabirimler, kullanıcıların ve yöntemlerinden istek ve yanıt iletilerini almasını sağlar `Serialize` `Deserialize` .  
  
 Bu örnekte, `QueryStringFormatter` Bu arabirimlerin her ikisini de uygular ve istemci ve sunucu üzerinde uygulanır.  
  
 İstek:  
  
- Örnek, <xref:System.ComponentModel.TypeConverter> istek iletisindeki parametre verilerini dizeden ve dizeden dönüştürmek için sınıfını kullanır. Belirli bir <xref:System.ComponentModel.TypeConverter> tür için kullanılabilir değilse, örnek biçimlendirici bir özel durum oluşturur.  
  
- `IClientMessageFormatter.SerializeRequest`İstemci üzerindeki yönteminde, biçimlendirici uygun BIR URI oluşturur ve işlem adını bir sonek olarak ekler. Bu ad, sunucuda uygun işleme göndermek için kullanılır. Daha sonra parametre nesnelerinin dizisini alır ve parametre adlarını ve sınıf tarafından dönüştürülen değerleri kullanarak parametre verilerini URI sorgu dizesine dizleştirir <xref:System.ComponentModel.TypeConverter> . <xref:System.ServiceModel.Channels.MessageHeaders.To%2A>Ve <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> ÖZELLIKLERI bu URI 'ye ayarlanır. <xref:System.ServiceModel.Channels.MessageProperties>özelliği aracılığıyla erişilir <xref:System.ServiceModel.Channels.Message.Properties%2A> .  
  
- `IDispatchMessageFormatter.DeserializeRequest`Sunucusundaki yönteminde, biçimlendirici `Via` gelen istek iletisi özelliklerindeki URI 'yi alır. URI sorgu dizesindeki ad-değer çiftlerini parametre adları ve değerleri olarak ayrıştırır ve yönteme geçirilen parametrelerin dizisini doldurmak için parametre adlarını ve değerlerini kullanır. İşlem dağıtımının zaten gerçekleştiğini, bu nedenle işlem adı son ekinin bu yöntemde yoksayıldığını unutmayın.  
  
 Yanıt:  
  
- Bu örnekte, HTTP GET yalnızca istek için kullanılır. Biçimlendirici, yanıtın bir XML iletisi oluşturmak için kullanılan özgün biçimlendirici öğesine gönderilmesini destekler. Bu örneğin hedeflerinden biri, bu tür bir temsilci seçme biçimlendiricisi nasıl uygulankullanabileceğinizi gösterir.  
  
### <a name="uripathsuffixoperationselector-class"></a>Urıthsonson Fixoperationselector sınıfı  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>Arabirim, kullanıcıların belirli bir ileti dağıtılması için kendi mantığını uygulamasına olanak sağlar.  
  
 Bu örnekte, `UriPathSuffixOperationSelector` işlem adı iletideki bir eylem üst bilgisi yerıne http get URI 'sine dahil edildiğinden, uygun işlemi seçmek için sunucuda uygulanması gerekir. Örnek yalnızca büyük/küçük harf duyarsız işlem adlarına izin verecek şekilde ayarlanır.  
  
 `SelectOperation`Yöntemi gelen iletiyi alır ve `Via` kendi ileti özelliklerinde URI 'yi arar. URI 'den işlem adı sonekini ayıklar, iletinin dağıtılması gereken işlem adını almak için bir iç tablo arar ve bu işlem adını döndürür.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>EnableHttpGetRequestsBehavior sınıfı  
 `UriPathSuffixOperationSelector`Bileşen program aracılığıyla veya bir uç nokta davranışı aracılığıyla ayarlanabilir. Örnek, `EnableHttpGetRequestsBehavior` hizmetin uygulama yapılandırma dosyasında belirtilen davranışı uygular.  
  
 Sunucusunda:  
  
 , <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Uygulama olarak ayarlanır <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> .  
  
 Varsayılan olarak, WCF tam eşleşme adresi filtresi kullanır. Gelen iletideki URI, bir işlem adı soneki ve ardından parametre verilerini içeren bir sorgu dizesi içerir, bu nedenle uç nokta davranışı da adres filtresini önek eşleşme filtresi olacak şekilde değiştirir. <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>Bu amaçla WCF 'yi kullanır.  
  
### <a name="installing-operation-formatters"></a>İşlem formatlayıcıları yükleniyor  
 Formatlayıcıları belirten işlem davranışları benzersizdir. Bu tür bir davranış, her zaman gerekli işlem biçimlendirici oluşturmak için her işlem için varsayılan olarak uygulanır. Ancak, bu davranışlar yalnızca başka bir işlem davranışı gibi görünür; Bunlar başka bir öznitelik tarafından tanımlanabilir değildir. Değiştirme davranışı yüklemek için, uygulamanın varsayılan olarak WCF türü yükleyici tarafından yüklenen belirli biçimlendirici davranışlarını araması ve bunu değiştirmesi ya da varsayılan davranışından sonra çalışacak uyumlu bir davranış eklemesi gerekir.  
  
 Bu işlem biçimlendiricileri davranışları, çağrılmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> veya varsayılan bir işlemden sonra yürütülen bir işlem davranışı belirtilerek program aracılığıyla ayarlanabilir. Ancak, davranış modeli bir davranışın diğer davranışları değiştirmesine izin vermediğinden veya açıklama ağacını değiştiremediğinden, bir uç nokta davranışı (ve dolayısıyla yapılandırmaya göre) kolayca ayarlanamaz.  
  
 İstemcide:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>Uygulamanın ISTEKLERI http get isteklerine dönüştürebilmesi ve yanıtlar için özgün biçimlendirici için temsilci olarak uygulanması gerekir. Bu, yardımcı yöntemi çağırarak yapılır `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` .  
  
 Çağrılmadan önce bunun yapılması gerekir `CreateChannel` .  
  
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
  
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>ARABIRIMIN http get isteklerini okuyabilmesi ve yanıtları yazmak için özgün biçimlendirici için temsilci olarak uygulanması gerekir. Bu, `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` istemcisiyle aynı yardımcı yöntemi çağırarak yapılır (önceki kod örneğine bakın).  
  
- Çağrılmadan önce bunun yapılması gerekir <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> . Bu örnekte, bir biçimlendirici çağrılmadan önce el ile nasıl değiştirildiğini gösteririz <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> . Aynı şeyi elde etmenin bir diğer yolu da, <xref:System.ServiceModel.ServiceHost> açmadan önce çağrıları yapan öğesinden bir sınıf türetmektir `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` (lütfen bkz. barındırma belgeleri ve örnekler için örnekler).  
  
### <a name="user-experience"></a>Kullanıcı deneyimi  
 Sunucusunda:  
  
- Sunucu `ICalculator` uygulamasının değiştirilmesi gerekmez.  
  
- Hizmetin App. config `messageVersion` öğesinin özniteliğini olarak ayarlayan özel bır POX bağlaması kullanması gerekir `textMessageEncoding` `None` .  
  
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
  
- Hizmetin App. config dosyası, `EnableHttpGetRequestsBehavior` davranış uzantıları bölümüne ekleyerek ve onu kullanarak özel olarak belirtilmelidir.  
  
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
  
- Çağrılmadan önce işlem formatlayıcıları ekleyin <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> .  
  
 İstemcide:  
  
- İstemci uygulamasının değiştirilmesi gerekmez.  
  
- İstemci için App. config `messageVersion` öğesinin özniteliğini olarak ayarlayan özel bır POX bağlaması kullanması gerekir `textMessageEncoding` `None` . Hizmetin bir farkı, istemcinin el ile adreslemeyi etkinleştirmek zorunda olduğundan, giden adresinin değiştirilmesini sağlar.  
  
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
  
- İstemci için App. config, sunucu ile aynı özel öğesini belirtmelidir `EnableHttpGetRequestsBehavior` .  
  
- Çağrılmadan önce işlem formatlayıcıları ekleyin <xref:System.ServiceModel.ChannelFactory%601.CreateChannel> .  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Dört işlemin tümü (Ekle, çıkart, çarp ve Böl) başarılı olmalıdır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
