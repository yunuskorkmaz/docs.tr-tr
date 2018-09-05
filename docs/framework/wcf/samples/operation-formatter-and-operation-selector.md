---
title: İşlem Biçimlendirici ve İşlem Seçici
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: a814de7433f2d06491245dc1d6e6e637b514118a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542368"
---
# <a name="operation-formatter-and-operation-selector"></a>İşlem Biçimlendirici ve İşlem Seçici
Bu örnek ileti verilerini ne WCF bekliyor farklı bir biçimde izin vermek için Windows Communication Foundation (WCF) genişletilebilirlik noktaları'nın nasıl kullanılabileceğini gösterir. Varsayılan olarak, WCF biçimlendiricileri altında dahil edilecek yöntem parametreleri beklediğiniz `soap:body` öğesi. Örnek uygulama, bunun yerine bir HTTP GET sorgu dizesi parametresi verileri ayrıştırır ve bu verileri kullanarak yöntemleri çağıran bir özel işlem biçimlendirici gösterir.  
  
 Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi. Bunu nasıl gösterir ekleme, çıkarma, birden çok kez ve bölme iletileri, istemci-sunucu isteği için HTTP GET kullanmak için değiştirilebilir ve POX ile HTTP POST için sunucu istemciye yanıt iletileri.  
  
 Bunu yapmak için örnek aşağıdakileri sağlar:  
  
-   `QueryStringFormatter`, uygulayan <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> istemci ve sunucu için sırasıyla ve sorgu dizesi verileri işler.  
  
-   `UriOperationSelector`, uygulayan <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> GET isteği işlem adına göre işlem gönderme gerçekleştirmek için sunucu üzerinde.  
  
-   `EnableHttpGetRequestsBehavior` uç nokta davranışı (ve karşılık gelen yapılandırma), çalışma zamanı için gerekli işlem Seçici ekler.  
  
-   Yeni bir işlem biçimlendirici çalışma zamanına nasıl ekleneceğini gösterir.  
  
-   Bu örnekte, hem istemci hem de hizmet Konsolu (.exe) uygulamalardır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
## <a name="key-concepts"></a>Temel Kavramlar  
 `QueryStringFormatter` -İşlem biçimlendirici parametresi nesnelerinin bir dizisi ve bir iletiye parametresi nesneleri içeren bir dizi ileti oluşturmaktan sorumludur wcf'de bileşendir. Bu istemciyi kullanarak gerçekleştirilir <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirimi hem de sunucu ile <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimi. Bu arabirimler, istek ve yanıt iletilerin alınacağı açabileceğinizi `Serialize` ve `Deserialize` yöntemleri.  
  
 Bu örnekte `QueryStringFormatter` hem de bu arabirimleri uygulayan ve istemci ve sunucu üzerinde uygulanır.  
  
 İstek:  
  
-   Örnek kullanır <xref:System.ComponentModel.TypeConverter> dizeleri gelen ve giden istek iletisi parametre verileri dönüştürmek için sınıf. Varsa bir <xref:System.ComponentModel.TypeConverter> örnek biçimlendirici oluşturur bir özel durumu belirli bir tür için kullanılamaz.  
  
-   İçinde `IClientMessageFormatter.SerializeRequest` istemcisinde, biçimlendirici yöntemi adresi uygun bir URI oluşturur ve işlem adı soneki olarak ekler. Bu ad, sunucudaki uygun işlemini gönderileceği kullanılır. Ardından parametresi nesneleri dizisi alır ve parametre adları ve dönüştürülen değerler kullanarak URI sorgu dizesi parametresi verileri serileştirir <xref:System.ComponentModel.TypeConverter> sınıfı. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> Ve <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> özellikleri daha sonra bu URI'ye ayarlayın. <xref:System.ServiceModel.Channels.MessageProperties> üzerinden erişilen <xref:System.ServiceModel.Channels.Message.Properties%2A> özelliği.  
  
-   İçinde `IDispatchMessageFormatter.DeserializeRequest` yöntemi sunucuda biçimlendiriciyi alır `Via` gelen istek ileti özelliklerinde bir URI. Ad-değer çiftlerini URI sorgu dizesinde, parametre adları ve değerlerine ayrıştırır ve parametre adları ve değerleri, yönteme geçirilen parametreler dizisi doldurmak için kullanır. Bu yöntemde işlem adı soneki göz ardı edilir şekilde gönderme işlemi zaten oluştu unutmayın.  
  
 Yanıt:  
  
-   Bu örnekte, HTTP GET isteği yalnızca kullanılır. Biçimlendirici bir XML iletisi oluşturmak için kullanılanla özgün biçimlendirici yanıtı gönderen atar. Bu örnek hedeflerinden temsilci bir biçimlendirici nasıl uygulanabileceği göstermektir.  
  
### <a name="uripathsuffixoperationselector-class"></a>UriPathSuffixOperationSelector sınıfı  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Arabirimi kullanıcıların kendi mantığını hangi işlem için belirli bir ileti gönderilen sağlar.  
  
 Bu örnekte `UriPathSuffixOperationSelector` işlem adı bir eylem üst bilgi iletisi yerine HTTP almak URI'ye dahil olduğundan uygun işlemi seçmek için sunucuda uygulanmalıdır. Örnek yalnızca büyük küçük harf duyarsız işlem adları izin verecek şekilde ayarlanır.  
  
 `SelectOperation` Yöntemi gelen iletiyi alır ve şuna `Via` ileti özelliklerinde bir URI. İşlem adı soneki URI'SİNDEN ayıklar, ileti için dağıtılması işlem adını almak için iç tablo arar ve bu işlem adı döndürür.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>EnableHttpGetRequestsBehavior sınıfı  
 `UriPathSuffixOperationSelector` Bileşen ayarlanabilir programlı olarak veya bir uç nokta davranışı. Örnek uygulayan `EnableHttpGetRequestsBehavior` hizmetin uygulama yapılandırma dosyasında belirtilen davranışı.  
  
 Sunucuda:  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Ayarlanır <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulaması.  
  
 Varsayılan olarak, bir tam eşleşme adresi filtresi WCF kullanır. Gelen ileti URİ'SİNDE parametre verisi içeren bir sorgu dize tarafından izlenen bir işlem adı soneki içeriyor, uç nokta davranışı olmasını adresi filtresi de değişiklikler filtresi eşleşen bir önek. WCF kullanan<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> bu amaç için.  
  
### <a name="installing-operation-formatters"></a>Yükleme işlemi biçimlendiricileri  
 Biçimlendiricileri belirtin işlem davranışları benzersizdir. Böyle bir davranış, her zaman gerekli işlem biçimlendirici oluşturmak her işlem için varsayılan olarak uygulanır. Ancak, bu davranışlar gibi başka bir işlem davranışı arar; Bunlar herhangi bir öznitelik tarafından tanımlanabilir değildir. Değiştirme davranışı yüklemek için uygulama varsayılan ve ya da WCF türü yükleyicisi tarafından yüklenen belirli biçimlendirici davranışları değiştirmek arayın veya sonra varsayılan davranış çalıştırmak için uyumlu bir davranış ekleyin.  
  
 Bu işlem biçimlendiricileri davranışların çağırmadan önce programlama yoluyla ayarlanabilir <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> veya varsayılan bir sonra yürütülecek olan bir işlemi davranışı belirterek. Ancak, bunu kolayca bir uç nokta davranışı ayarlanamıyor (ve bu nedenle yapılandırmaya göre) davranış modeli davranışları değiştirin veya aksi halde açıklama ağaç değiştirmek bir davranış izin vermediğinden.  
  
 İstemcide:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Uygulama uygulanmalı, böylece istekler HTTP GET isteklerine dönüştüren ve yanıtlarının özgün biçimlendirici için temsilci. Bu çağrılarak gerçekleştirilir `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi.  
  
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
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Arabirimi uygulanmalı okuma HTTP GET istekleri ve yanıtları yazmak için temsilci seçme için özgün biçimlendirici. Bu aynı çağrılarak gerçekleştirilir `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi istemci olarak (Yukarıdaki örnek kod bakın).  
  
-   Bu, önce yapılmalıdır <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> çağrılır. Bu örnekte, biçimlendirici çağırmadan önce el ile nasıl değiştirilmiş olan göstereceğiz <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Öğesinden bir sınıf türetmek için aynı şeyi elde etmek için başka bir yolu olan <xref:System.ServiceModel.ServiceHost> çağrıları yapar `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` açmadan önce (belgeler ve örnekler için örnekleri barındırma Lütfen bakın).  
  
### <a name="user-experience"></a>Kullanıcı deneyimleri  
 Sunucuda:  
  
-   Sunucu `ICalculator` uygulama değiştirmeniz gerekmez.  
  
-   App.config hizmeti için özel ayarlar bir POX bağlama kullanmalısınız `messageVersion` özniteliği `textMessageEncoding` öğesine `None`.  
  
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
  
-   App.config hizmeti için özel de belirtmeniz gerekir `EnableHttpGetRequestsBehavior` davranış Uzantıları bölümüne ekleyerek ve onu kullanarak.  
  
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
  
 İstemcide:  
  
-   İstemci uygulaması değiştirmeniz gerekmez.  
  
-   İstemcisi için App.config ayarlar özel bir POX bağlama kullanmalısınız `messageVersion` özniteliği `textMessageEncoding` öğesine `None`. Bir hizmetten istemci adresine giden değiştirilebilir böylece, el ile adresleme etkinleştirmelisiniz farktır.  
  
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
  
-   App.config istemci için aynı özel belirtmelisiniz `EnableHttpGetRequestsBehavior` sunucusu.  
  
-   Ekleme işlemi biçimlendiricileri çağırmadan önce <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Tüm dört işlemleri (ekleme, çıkarma, çarpma ve bölme) başarılı olması gerekir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
