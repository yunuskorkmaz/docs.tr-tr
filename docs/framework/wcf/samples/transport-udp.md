---
title: 'Taşıma: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 3fd16ccd634b6875eae1e87547c35c6cba79c857
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143778"
---
# <a name="transport-udp"></a>Taşıma: UDP
UDP Transport örneği, udp unicast ve multicast'in özel bir Windows Communication Foundation (WCF) taşıması olarak nasıl uygulanacağını gösterir. Örnek, kanal çerçevesini kullanarak ve WCF en iyi uygulamalarını izleyerek WCF'de özel bir aktarım oluşturmak için önerilen yordamı açıklar. Özel bir aktarım oluşturma adımları aşağıdaki gibidir:  
  
1. Kanal [İleti Değişim Desenleri](#MessageExchangePatterns) 'nden hangisini (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel veya IReplyChannel) KanalFactory ve ChannelListener'ın destekleyeceğine karar verin. Ardından, bu arabirimlerin oturumlu varyasyonlarını destekleyip desteklemeyeceğinize karar verin.  
  
2. İleti Alışverişi Modelinizi destekleyen bir kanal fabrikası ve dinleyici oluşturun.  
  
3. Ağa özgü özel özel durumların uygun türemiş sınıfa normalleştirildiğinden emin <xref:System.ServiceModel.CommunicationException>olun.  
  
4. Kanal yığınına özel aktarım ekleyen [ \<bağlayıcı](../../configure-apps/file-schema/wcf/bindings.md) bir>öğesi ekleyin. Daha fazla bilgi için [bkz.](#AddingABindingElement)  
  
5. Yapılandırma sistemine yeni bağlama öğesi ortaya çıkarmak için bağlayıcı öğe uzantısı bölümü ekleyin.  
  
6. Yetenekleri diğer uç noktalara iletmek için meta veri uzantıları ekleyin.  
  
7. Iyi tanımlanmış bir profile göre bağlama öğeleri yığınını önceden yapılandıran bir bağlama ekleyin. Daha fazla bilgi için [bkz.](#AddingAStandardBinding)  
  
8. Yapılandırma sistemine bağlamayı ortaya çıkarmak için bağlama bölümü ve bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için [bkz.](#AddingConfigurationSupport)  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a>İleti Değişim Desenleri  
 Özel bir aktarım yazmanın ilk adımı, aktarım için hangi İleti Değişim Desenleri'nin (MEP) gerekli olduğuna karar vermektir. Aralarından seçim yapabileceğiniz üç MEP vardır:  
  
- Datagram (IInputChannel/IOutputChannel)  
  
     Bir datagram MEP kullanırken, bir istemci bir "yangın ve unut" değişimi kullanarak bir ileti gönderir. Bir yangın ve unutmak değişimi başarılı teslimat bant dışı onay gerektiren biridir. İleti geçiş sırasında kaybolabilir ve hizmete asla ulaşmaz. Gönderme işlemi istemci sonunda başarıyla tamamlanırsa, uzak bitiş noktasının iletiyi aldığını garanti etmez. Veri gramı, güvenilir protokoller ve güvenli protokoller de dahil olmak üzere kendi protokollerinizi oluşturabileceğiniz için mesajlaşma için temel bir yapı taşıdır. İstemci datagram <xref:System.ServiceModel.Channels.IOutputChannel> kanalları <xref:System.ServiceModel.Channels.IInputChannel> arabirimi uygular ve hizmet datagram kanalları arabirimi uygular.  
  
- İstek-Yanıt (IRequestChannel/IReplyChannel)  
  
     Bu MEP'de bir ileti gönderilir ve bir yanıt alınır. Desen istek-yanıt çiftlerinden oluşur. İstek yanıt çağrılarına örnek olarak uzaktan yordam çağrıları (RPC) ve tarayıcı GET'leri verilebilir. Bu desen, Yarı Çift Yönlü olarak da bilinir. Bu MEP'de istemci <xref:System.ServiceModel.Channels.IRequestChannel> kanalları uygular ve <xref:System.ServiceModel.Channels.IReplyChannel>hizmet kanalları uygular.  
  
- Çift yönlü (IDuplexChannel)  
  
     Çift yönlü MEP, bir istemci tarafından rasgele sayıda iletinin gönderilmesine ve herhangi bir sırada alınmasına izin verir. Dubleks MEP, konuşulan her kelimenin bir mesaj olduğu bir telefon konuşması gibidir. Her iki taraf da bu MEP'de gönderip alabileceğinden, istemci <xref:System.ServiceModel.Channels.IDuplexChannel>ve servis kanalları tarafından uygulanan arabirim.  
  
 Bu MEP'lerin her biri oturumları da destekleyebilir. Oturum alabilen bir kanal tarafından sağlanan ek işlevsellik, bir kanalda gönderilen ve alınan tüm iletileri ilişkilendirmektir. İstek ve yanıt ilişkilendirilmeden İstek-Yanıt deseni tek başına bir iki ileti oturumudur. Buna karşılık, oturumları destekleyen İstek-Yanıt deseni, o kanaldaki tüm istek/yanıt çiftlerinin birbiriyle ilişkili olduğunu gösterir. Bu size toplam altı MEPs-Datagram, İstek-Yanıt, Çift Yönlü, Oturumlu Datagram, oturumlarla İstek-Yanıt ve oturumlarla Çift Yönlü-seçim yapmanızı sağlar.  
  
> [!NOTE]
> UDP taşıma için desteklenen tek MEP Datagram'dır, çünkü UDP doğal olarak bir "ateş ve unut" protokolüdür.  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>ICommunicationObject ve WCF nesne yaşam döngüsü  
 WCF gibi <xref:System.ServiceModel.Channels.IChannel>nesnelerin yaşam döngüsü yönetmek için kullanılan ortak bir <xref:System.ServiceModel.Channels.IChannelFactory>durum <xref:System.ServiceModel.Channels.IChannelListener> makinesi vardır , , , ve iletişim için kullanılır. Bu iletişim nesnelerinin var olabileceği beş durum vardır. Bu durumlar numaralandırma <xref:System.ServiceModel.CommunicationState> ile temsil edilir ve aşağıdaki gibidir:  
  
- Oluşturuldu: Bu, ilk <xref:System.ServiceModel.ICommunicationObject> anlık olarak bir durumdur. Bu durumda giriş/çıktı (I/O) oluşmaz.  
  
- Açılış: Nesneler çağrıldığında <xref:System.ServiceModel.ICommunicationObject.Open%2A> bu duruma geçiş. Bu noktada özellikleri değişmez hale getirilir ve giriş/çıkış başlayabilir. Bu geçiş yalnızca Oluşturulan durumdan geçerlidir.  
  
- Açıldı: Açık işlem tamamlandığında nesneler bu duruma geçiş. Bu geçiş yalnızca Açılış durumundan geçerlidir. Bu noktada, nesne aktarım için tamamen kullanılabilir.  
  
- Kapanış: Zarif bir kapatma <xref:System.ServiceModel.ICommunicationObject.Close%2A> çağrıldığında nesneler bu duruma geçiş. Bu geçiş yalnızca Açılan durumdan geçerlidir.  
  
- Kapalı: Kapalı durumda nesneler artık kullanılabilir. Genel olarak, yapılandırmanın çoğu denetim için hala erişilebilir, ancak hiçbir iletişim oluşabilir. Bu durum elden çıkarılmaya eşdeğerdir.  
  
- Hatalı: Hatalı durumda, nesneler denetim için erişilebilir, ancak artık kullanılabilir. Kurtarılamayan bir hata oluştuğunda, nesne bu duruma geçiş eder. Bu durumdan tek geçerli geçiş `Closed` devlete.  
  
 Her eyalet geçişi için ateş eden olaylar vardır. Yöntem <xref:System.ServiceModel.ICommunicationObject.Abort%2A> herhangi bir zamanda çağrılabilir ve nesnenin geçerli durumundan Kapalı duruma hemen geçişine neden olur. Arama, <xref:System.ServiceModel.ICommunicationObject.Abort%2A> bitmemiş işleri sona erdirir.  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a>Kanal Fabrikası ve Kanal Dinleyicisi  
 Özel bir aktarım yazmanın bir sonraki <xref:System.ServiceModel.Channels.IChannelFactory> adımı, istemci kanalları <xref:System.ServiceModel.Channels.IChannelListener> ve servis kanalları için bir uygulama oluşturmaktır. Kanal katmanı, kanal oluşturmak için bir fabrika deseni kullanır. WCF bu işlem için taban sınıf yardımcıları sağlar.  
  
- Sınıf, <xref:System.ServiceModel.Channels.CommunicationObject> daha <xref:System.ServiceModel.ICommunicationObject> önce Adım 2'de açıklanan durum makinesini uygular ve zorlar.

- Sınıf <xref:System.ServiceModel.Channels.ChannelManagerBase> uygular <xref:System.ServiceModel.Channels.CommunicationObject> ve birleşik bir taban <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelListenerBase>sınıfı sağlar ve. Sınıf, <xref:System.ServiceModel.Channels.ChannelManagerBase> uygulayan bir <xref:System.ServiceModel.Channels.ChannelBase>taban sınıf olan ile <xref:System.ServiceModel.Channels.IChannel>birlikte çalışır.  
  
- Sınıf, <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelManagerBase> <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` aşırı yüklemeleri tek bir `OnCreateChannel` soyut yöntemde uygular ve birleştirir.  
  
- Sınıf <xref:System.ServiceModel.Channels.ChannelListenerBase> uygular. <xref:System.ServiceModel.Channels.IChannelListener> Temel devlet yönetimini hallediyor.  
  
 Bu örnekte fabrika uygulaması UdpChannelFactory.cs ve dinleyici uygulaması UdpChannelListener.cs yer almaktadır. <xref:System.ServiceModel.Channels.IChannel> Uygulamalar UdpOutputChannel.cs ve UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>UDP Kanal Fabrikası  
 <xref:System.ServiceModel.Channels.ChannelFactoryBase>Türetilmiştir. `UdpChannelFactory` Örnek, ileti <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> kodlayıcısının ileti sürümüne erişim sağlamak için geçersiz kılar. Örnek aynı zamanda, devlet makinesinin <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> <xref:System.ServiceModel.Channels.BufferManager> geçiş yaptığı örneğimizi yıkabilmemiz için de geçersiz kılıyor.  
  
#### <a name="the-udp-output-channel"></a>UDP Çıkış Kanalı  
 Uygular `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>. Oluşturucu bağımsız değişkenleri doğrular ve <xref:System.Net.EndPoint> geçirilene <xref:System.ServiceModel.EndpointAddress> göre bir hedef nesnesi inşa eder.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanal zarif veya zarif bir şekilde kapatılabilir. Kanal incelikle kapatılırsa soket kapatılır ve taban sınıf `OnClose` yöntemine çağrı yapılır. Bu bir özel durum oluşturursa, altyapı kanalının temizlenmesini sağlamak için çağırır. `Abort`  
  
```csharp
this.socket.Close(0);  
```  
  
 Daha sonra `Send()` `BeginSend()` / `EndSend()`uygulamak ve . Bu iki ana bölüme ayrılır. Önce iletiyi bir bayt dizisine serihale getireceğiz.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Sonra ortaya çıkan verileri kabloya göndeririz.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>The UdpChannelListener  
 `UdpChannelListener` Örneğin uyguladığı uygulama sınıftan <xref:System.ServiceModel.Channels.ChannelListenerBase> türetilmiştir. Veri gramlarını almak için tek bir UDP soketi kullanır. Yöntem, `OnOpen` udp soketi kullanarak asynchronous döngü içinde veri alır. Veriler daha sonra İleti Kodlama Çerçevesi kullanılarak iletilere dönüştürülür.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Aynı datagram kanalı bir dizi kaynaktan gelen iletileri `UdpChannelListener` temsil ettiği için, tek tonlu bir dinleyicidir. Bir anda bu dinleyiciile ilişkili en fazla bir etkin vardır. <xref:System.ServiceModel.Channels.IChannel> Örnek, yalnızca `AcceptChannel` yöntem tarafından döndürülen bir kanal sonradan imha edilirse başka bir kanal oluşturur. Bir ileti alındığı zaman, bu singleton kanala sıralanır.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 Sınıf `UdpInputChannel` uygular. `IInputChannel` Bu `UdpChannelListener`'soketi tarafından doldurulur gelen iletileri bir kuyruk oluşur. Bu iletiler `IInputChannel.Receive` yöntem tarafından dequeued vardır.  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a>Bağlama Öğesi Ekleme  
 Artık fabrikalar ve kanallar inşa edildiklerine göre, onları bir bağlama yoluyla ServiceModel çalışma süresine maruz bırakmalıyız. Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğeleri topluluğudur. Yığındaki her öğe bağlayıcı bir [ \<>](../../configure-apps/file-schema/wcf/bindings.md) öğesi ile temsil edilir.  
  
 Örnekte, bağlama öğesi `UdpTransportBindingElement`, hangi türetilmiştir <xref:System.ServiceModel.Channels.TransportBindingElement>. Bizim bağlama ile ilişkili fabrikalar oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Ayrıca klonlama `BindingElement` ve bizim düzeni (soap.udp) dönen üyeleri içerir.  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Aktarım Bağlama Öğesi için Meta Veri Desteği Ekleme  
 Taşımamızı meta veri sistemine entegre etmek için, hem ithalatı hem de dışa aktarmayı desteklemeliyiz. Bu bize [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)aracılığıyla bizim bağlama istemcileri oluşturmak için izin verir.  
  
### <a name="adding-wsdl-support"></a>WSDL Desteği Ekleme  
 Bağlayıcıdaki aktarım bağlama öğesi, meta verilerdeki adresleme bilgilerinin dışa aktarılmasından ve aktarılmasından sorumludur. SOAP bağlama kullanırken, taşıma bağlama elemanı da meta verilerde doğru bir aktarım URI dışa aktarmalıdır.  
  
#### <a name="wsdl-export"></a>WSDL İhracat  
 Adresbilgilerini dışa `UdpTransportBindingElement` aktarmak için `IWsdlExportExtension` arabirimi uygular. Yöntem, `ExportEndpoint` WSDL bağlantı noktasına doğru adresbilgilerini ekler.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 Yöntemin `UdpTransportBindingElement` `ExportEndpoint` uygulanması, son nokta bir SOAP bağlama kullandığında bir taşıma URI'si de dışa aktarMaktadır.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL İthalat  
 WSDL alma sistemini adresleri alma işlemlerini işlemek için genişletmek için, Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için yapılandırma dosyasına aşağıdaki yapılandırmayı eklememiz gerekir.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Svcutil.exe çalıştırırken, WSDL alma uzantıları yüklemek için Svcutil.exe almak için iki seçenek vardır:  
  
1. Svcutil.exe'yi /SvcutilConfig kullanarak yapılandırma\<dosyamıza yönlendirin: dosya>.  
  
2. Yapılandırma bölümünü Svcutil.exe ile aynı dizinde Svcutil.exe.config'e ekleyin.  
  
 Tür `UdpBindingElementImporter` `IWsdlImportExtension` arabirimi uygular. Yöntem `ImportEndpoint` adresi WSDL bağlantı noktasından içeri aktolur.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>İlke Desteği Ekleme  
 Özel bağlama öğesi, bu bağlama öğesinin yeteneklerini ifade etmek için bir hizmet bitiş noktası için WSDL bağlayıcıilki iddialarını dışa aktarabilir.  
  
#### <a name="policy-export"></a>İlke İhracatı  
 Tür, `UdpTransportBindingElement` dışa aktarma ilkesi için destek eklemek için uygular. `IPolicyExportExtension` Sonuç olarak, `System.ServiceModel.MetadataExporter` `UdpTransportBindingElement` bunu içeren herhangi bir bağlama için ilke oluşturma içerir.  
  
 Içinde, `IPolicyExportExtension.ExportPolicy`biz çok noktaya yayın modunda ise UDP ve başka bir iddia için bir iddia ekleyin. Bunun nedeni, çok noktaya yayın modunun iletişim yığınının nasıl oluşturulduğuna etki etmesi ve bu nedenle her iki taraf arasında koordine edilmesi dir.  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix,
        UdpPolicyStrings.MulticastAssertion,
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Özel aktarım bağlama öğeleri adresleme işlemekten sorumlu olduğundan, `IPolicyExportExtension` ws-addressing sürümünü niçin kullanıldığını göstermek için uygun WS Adresleme ilkesi iddialarını dışa aktarma yı da ele almalıdır. `UdpTransportBindingElement`  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>İlke İthalatı  
 İlke Alma sistemini genişletmek için, Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için yapılandırma dosyasına aşağıdaki yapılandırmayı eklememiz gerekir.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Sonra bizim `IPolicyImporterExtension` kayıtlı sınıftan`UdpBindingElementImporter`uygulamak ( ). 'de, `ImportPolicy()`ad alanımızdaki iddialara bakarız ve taşımayı oluşturmak için olanları işleyip çok noktaya yayın olup olmadığını kontrol ediyoruz. Ayrıca, ele aldığımız iddiaları bağlayıcı iddialar listesinden de kaldırmalıyız. Yine, Svcutil.exe çalıştırırken, tümleştirme için iki seçenek vardır:  
  
1. Svcutil.exe'yi /SvcutilConfig kullanarak yapılandırma\<dosyamıza yönlendirin: dosya>.  
  
2. Yapılandırma bölümünü Svcutil.exe ile aynı dizinde Svcutil.exe.config'e ekleyin.  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a>Standart Bağlama Ekleme  
 Bağlama öğemiz aşağıdaki iki şekilde kullanılabilir:  
  
- Özel bir bağlama yoluyla: Özel bir bağlama, kullanıcının rasgele bir bağlama öğesi kümesini temel alan kendi bağlamasını oluşturmasına olanak tanır.  
  
- Bağlama öğemizi içeren sistem tarafından sağlanan bir bağlama kullanarak. WCF, bu sistem tanımlı bağlamaların bir `BasicHttpBinding` `NetTcpBinding`dizi `WsHttpBinding`sini sağlar; Bu bağlamaların her biri iyi tanımlanmış bir profille ilişkilidir.  
  
 `SampleProfileUdpBinding`Örnek, <xref:System.ServiceModel.Channels.Binding>'den türeyen profil bağlama' uygular. İçinde `SampleProfileUdpBinding` en fazla dört bağlama `UdpTransportBindingElement`öğesi `TextMessageEncodingBindingElement CompositeDuplexBindingElement`içerir: , , ve `ReliableSessionBindingElement`.  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Özel Standart Bağlama İthalatçısı Ekleme  
 Svcutil.exe ve `WsdlImporter` türü, varsayılan olarak, tanır ve sistem tanımlı bağlamaları alır. Aksi takdirde, bağlama bir `CustomBinding` örnek olarak içe aktarılır. Svcutil.exe ve almak `WsdlImporter` `SampleProfileUdpBinding` için `UdpBindingElementImporter` de özel bir standart bağlayıcı ithalatçı olarak hareket etmesini sağlamak için.  
  
 Özel bir standart bağlayıcı içe `ImportEndpoint` aktarıcı, meta `CustomBinding` verilerden alınan örneği incelemek ve belirli bir standart bağlama tarafından oluşturulup oluşturulmadığını görmek için `IWsdlImportExtension` arabirimde yöntem uygular.  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 Genel olarak, özel bir standart bağlama içe aktarma işlemi, yalnızca standart bağlama tarafından ayarlanmış olabilecek özelliklerin değiştiğini ve diğer tüm özelliklerin varsayılanları olduğunu doğrulamak için içe aktarılan bağlama öğelerinin özelliklerini denetlemeyi içerir. Standart bağlayıcı lık uygulamak için temel bir strateji, standart bağlamanın bir örneğini oluşturmak, özellikleri bağlama öğelerinden standart bağlamanın desteklediği standart bağlama örneğine yaymak ve bağlamayı karşılaştırmaktır. alınan bağlama elemanları ile standart bağlama öğeleri.  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a>Yapılandırma Desteği Ekleme  
 Yapılandırma yoluyla taşımamızı ortaya çıkarmak için iki yapılandırma bölümü uygulamamız gerekir. İlki bir `BindingElementExtensionElement` `UdpTransportBindingElement`. Bu, `CustomBinding` uygulamaların bağlayıcı öğemize başvurması içindir. İkincisi bizim `Configuration` için `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Bağlama Öğesi Uzantısı Öğesi  
 Bölüm, `UdpTransportElement` yapılandırma `BindingElementExtensionElement` sistemine `UdpTransportBindingElement` maruz kalan bir bölümdür. Birkaç temel geçersiz kılmayla yapılandırma bölüm adımızı, bağlama öğemizin türünü ve bağlama öğemizi nasıl oluşturabileceğimizi tanımlarız. Daha sonra uzantı bölümümüzi aşağıdaki kodda gösterildiği gibi bir yapılandırma dosyasına kaydedebiliriz.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Uzantı, udp'yi aktarım olarak kullanmak için özel bağlamalardan başvurulabilir.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a>Bağlama Bölümü  
 Bölüm, `SampleProfileUdpBindingCollectionElement` yapılandırma `StandardBindingCollectionElement` sistemine `SampleProfileUdpBinding` maruz kalan bir bölümdür. Uygulamanın büyük bir kısmı `SampleProfileUdpBindingConfigurationElement`, ' den `StandardBindingElement`türetilen . Üzerinde `SampleProfileUdpBindingConfigurationElement` özellikleri `SampleProfileUdpBinding`karşılık gelen özelliklere sahip ve `ConfigurationElement` bağlama eşlenecek işlevleri. Son olarak, `OnApplyConfiguration` aşağıdaki örnek `SampleProfileUdpBinding`kodda gösterildiği gibi, bizim yöntemi geçersiz kılın.  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 Bu işleyiciyi yapılandırma sistemine kaydetmek için ilgili yapılandırma dosyasına aşağıdaki bölümü ekliyoruz.  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Daha sonra serviceModel yapılandırma bölümünden başvurulabilir.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a>UDP Test Hizmeti ve İstemci  
 Bu örnek aktarımı kullanmak için test kodu UdpTestService ve UdpTestClient dizinlerinde kullanılabilir. Hizmet kodu iki testten oluşur— bir test koddan bağlamalar ve uç noktalar ayarlar ve diğeri yapılandırma yoluyla yapar. Her iki testde de iki uç nokta kullanılır. Bir uç nokta `SampleUdpProfileBinding` [ \<ile güvenilirSession>'](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) yi `true`kullanır. Diğer uç nokta ile `UdpTransportBindingElement`özel bir bağlama kullanır. Bu, güvenilir `SampleUdpProfileBinding` Oturum>ile `false`kullanmaya eşdeğerdir. [ \<](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) Her iki test de bir hizmet oluşturur, her bağlama için bir bitiş noktası ekler, hizmeti açar ve ardından kullanıcının hizmeti kapatmadan önce ENTER tuşuna basmasını bekler.  
  
 Hizmet testi uygulamasını başlattığınızda aşağıdaki çıktıyı görmeniz gerekir.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Daha sonra test istemcisi uygulamasını yayımlanmış uç noktalara göre çalıştırabilirsiniz. İstemci test uygulaması her bitiş noktası için bir istemci oluşturur ve her bitiş noktasına beş ileti gönderir. Aşağıdaki çıktı istemcidedir.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Aşağıdaki hizmetin tam çıktısi.  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 İstemci uygulamasını yapılandırma kullanılarak yayınlanan uç noktalara göre çalıştırmak için hizmette ENTER tuşuna basın ve test istemcisini yeniden çalıştırın. Hizmette aşağıdaki çıktıyı görmeniz gerekir.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 İstemciyi yeniden çalıştırmak, önceki sonuçlarla aynı verimi verir.  
  
 Svcutil.exe kullanarak istemci kodunu ve yapılandırmasını yeniden oluşturmak için servis uygulamasını başlatın ve ardından aşağıdaki Svcutil.exe'yi örneğin kök dizininden çalıştırın.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Svcutil.exe için bağlayıcı uzantısı yapılandırma oluşturmaz `SampleProfileUdpBinding`unutmayın , bu yüzden el ile eklemeniz gerekir.  
  
```xml
<configuration>  
  <system.serviceModel>
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
2. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
3. Önceki "UDP Test Hizmeti ve İstemci" bölümüne bakın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
