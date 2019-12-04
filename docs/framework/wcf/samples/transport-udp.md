---
title: 'Taşıma: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: f7dea8a95490377226acd09a3463b102d42834d6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711920"
---
# <a name="transport-udp"></a>Taşıma: UDP
UDP taşıma örneği, UDP tek noktaya yayın ve çok noktaya yayının özel bir Windows Communication Foundation (WCF) taşıması olarak nasıl uygulanacağını gösterir. Örnek, kanal çerçevesini ve aşağıdaki WCF en iyi yöntemlerini kullanarak WCF 'de özel bir aktarım oluşturmak için önerilen yordamı açıklar. Özel bir aktarım oluşturma adımları aşağıdaki gibidir:  
  
1. ChannelFactory ve ChannelListener 'ın destekleyeceği kanal [Iletisi değişimi desenlerinin](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel veya IReplyChannel destekleyen desteklenecektir) hangisi olacağına karar verin. Ardından, bu arabirimlerin oturumsuz çeşitlemelerini desteklememeye karar verin.  
  
2. Ileti değişim modelinizi destekleyen bir kanal fabrikası ve dinleyicisi oluşturun.  
  
3. Ağa özgü tüm özel durumların <xref:System.ServiceModel.CommunicationException>uygun türetilmiş sınıfına normalleştirildiğinden emin olun.  
  
4. Özel aktarımı bir kanal yığınına ekleyen [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin. Daha fazla bilgi için bkz. [bağlama öğesi ekleme](#AddingABindingElement).  
  
5. Yeni bağlama öğesini yapılandırma sistemine göstermek için bağlama öğesi uzantısı bölümü ekleyin.  
  
6. Diğer uç noktalara iletişim kurmak için meta veri uzantıları ekleyin.  
  
7. İyi tanımlanmış bir profile göre bağlama öğeleri yığınını önceden yapılandıran bir bağlama ekleyin. Daha fazla bilgi için bkz. [Standart bağlama ekleme](#AddingAStandardBinding).  
  
8. Yapılandırma sistemine bağlamayı göstermek için bağlama bölümü ve bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için bkz. [yapılandırma desteği ekleme](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>İleti değişimi desenleri  
 Özel bir aktarım yazarken ilk adım, taşıma için hangi Ileti değişim desenlerinin (MEPs) gerekli olduğuna karar vermeye yöneliktir. Aralarından seçim yapabileceğiniz üç/PS vardır:  
  
- Veri birimi (IInputChannel/IOutputChannel)  
  
     Bir veri birimi MEP kullanırken, istemci "yangın ve unut" Exchange kullanarak bir ileti gönderir. Bir ateş ve unutur, başarılı teslimin bant dışı onayını gerektiren bir adım. İleti iletimde kaybolmuş olabilir ve hizmete hiçbir şekilde ulaşamamalıdır. Gönderme işlemi istemci sonunda başarıyla tamamlanırsa, uzak uç noktanın iletiyi aldığını garanti etmez. Bu veri birimi, güvenilir protokoller ve güvenli protokoller de dahil olmak üzere kendi protokollerinizi oluşturabileceğiniz gibi, mesajlaşma için temel bir yapı taşıdır. İstemci veri birimi kanalları, <xref:System.ServiceModel.Channels.IInputChannel> arabirimini uygulayan <xref:System.ServiceModel.Channels.IOutputChannel> arabirimini ve hizmet veri birimi kanallarını uygular.  
  
- İstek-yanıt (IRequestChannel/IReplyChannel destekleyen desteklenecektir)  
  
     Bu MEP 'de bir ileti gönderilir ve bir yanıt alındı. Bu model, istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrısı örnekleri, uzak yordam çağrılardır (RPC) ve tarayıcı alır. Bu model, yarı çift yönlü olarak da bilinir. Bu MEP 'de, istemci kanalları <xref:System.ServiceModel.Channels.IRequestChannel> ve hizmet kanalları uygular <xref:System.ServiceModel.Channels.IReplyChannel>uygular.  
  
- Çift yönlü (IDuplexChannel)  
  
     Çift yönlü MEP, istemci tarafından rastgele sayıda iletinin gönderilmesini ve herhangi bir sırada alınmasını sağlar. Çift yönlü MEP, konuşulan her sözcüğün bir ileti olduğu bir telefon konuşması gibidir. Her iki taraf da bu MEP 'de gönderebildiğinden ve alabileceği için, istemci ve hizmet kanalları tarafından uygulanan arabirim <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Bu MEPs 'lerin her biri, oturumları da destekleyebilir. Oturum kullanan bir kanal tarafından sunulan ek işlevsellik, bir kanalda gönderilen ve alınan tüm iletileri ilişkilendirir. İstek ve yanıt bağıntılı olduğundan, Istek-yanıt deseninin tek başına iki ileti oturumu vardır. Buna karşılık, oturumları destekleyen Istek-yanıt deseninin, o kanaldaki tüm istek/yanıt çiftlerinin birbirleriyle bağıntılı olduğu anlamına gelir. Bu, arasından seçim yapmak için toplam altı adet, veri birimi, Istek-yanıt, çift yönlü, oturumlarla oturum, oturum Isteği ve oturumlarla çift yönlü veri birimi sağlar.  
  
> [!NOTE]
> UDP bir "yangın ve unut" Protokolü olduğundan, UDP taşıması için desteklenen tek MEP yalnızca veri birimi olur.  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>Idimmunicationobject ve WCF nesne yaşam döngüsü  
 WCF, iletişim için kullanılan <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>ve <xref:System.ServiceModel.Channels.IChannelListener> gibi nesnelerin yaşam döngüsünü yönetmek için kullanılan ortak bir durum makinesine sahiptir. Bu iletişim nesnelerinin bulunabileceği beş durum vardır. Bu durumlar <xref:System.ServiceModel.CommunicationState> numaralandırması tarafından temsil edilir ve aşağıdaki gibidir:  
  
- Oluşturuldu: ilk örneği oluşturulduğunda <xref:System.ServiceModel.ICommunicationObject> durumudur. Bu durumda giriş/çıkış (g/ç) oluşmaz.  
  
- Açılıyor: <xref:System.ServiceModel.ICommunicationObject.Open%2A> çağrıldığında nesneler bu duruma geçiş yapılır. Bu noktada özellikler sabit hale getirilir ve giriş/çıkış başlayabilir. Bu geçiş yalnızca oluşturulan durumdan geçerlidir.  
  
- Açıldı: nesneler, açık işlem tamamlandığında bu duruma geçiş yapar. Bu geçiş yalnızca açma durumunda geçerlidir. Bu noktada, nesne aktarım için tamamen kullanılabilir.  
  
- Kapatılıyor: düzgün kapanma için <xref:System.ServiceModel.ICommunicationObject.Close%2A> çağrıldığında nesneler bu duruma geçer. Bu geçiş yalnızca açık durumda geçerlidir.  
  
- Kapalı: kapalı durum nesnelerinde artık kullanılamaz. Genel olarak, çoğu yapılandırmaya hala inceleme için erişilebilir, ancak hiçbir iletişim gerçekleşmez. Bu durum atılmıştı.  
  
- Hatalı: Hatalı durumda, nesnelere denetim için erişilebilir ancak artık kullanılamaz. Kurtarılabilir olmayan bir hata oluştuğunda, nesne bu duruma geçer. Bu durumdan geçerli olan tek geçiş `Closed` durumundadır.  
  
 Her durum geçişi için başlatılan olaylar vardır. <xref:System.ServiceModel.ICommunicationObject.Abort%2A> yöntemi herhangi bir zamanda çağrılabilir ve nesnenin geçerli durumundan kapalı duruma geçmesine neden olur. <xref:System.ServiceModel.ICommunicationObject.Abort%2A> çağrısı tamamlanmamış işleri sonlandırır.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Kanal fabrikası ve kanal dinleyicisi  
 Özel bir aktarım yazarken bir sonraki adım, istemci kanalları için <xref:System.ServiceModel.Channels.IChannelFactory> ve hizmet kanalları için <xref:System.ServiceModel.Channels.IChannelListener> bir uygulama oluşturmaktır. Kanal katmanı, kanal oluşturmak için bir fabrika kalıbı kullanır. WCF bu işlem için temel sınıf yardımcıları sağlar.  
  
- <xref:System.ServiceModel.Channels.CommunicationObject> sınıfı, <xref:System.ServiceModel.ICommunicationObject> uygular ve daha önce 2. adımda açıklanan durum makinesini zorlar. 

- <xref:System.ServiceModel.Channels.ChannelManagerBase> sınıfı <xref:System.ServiceModel.Channels.CommunicationObject> uygular ve <xref:System.ServiceModel.Channels.ChannelFactoryBase> ve <xref:System.ServiceModel.Channels.ChannelListenerBase>için Birleşik bir temel sınıf sağlar. <xref:System.ServiceModel.Channels.ChannelManagerBase> sınıfı, <xref:System.ServiceModel.Channels.IChannel>uygulayan temel bir sınıf olan <xref:System.ServiceModel.Channels.ChannelBase>birlikte çalışıyor.  
  
- <xref:System.ServiceModel.Channels.ChannelFactoryBase> sınıfı <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> uygular ve `CreateChannel` yüklerini tek `OnCreateChannel` soyut bir yöntemde birleştirir.  
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfı <xref:System.ServiceModel.Channels.IChannelListener>uygular. Temel durum yönetiminden çok dikkat edin.  
  
 Bu örnekte, fabrika uygulamasının UdpChannelFactory.cs içinde yer aldığı ve dinleyici uygulamasının UdpChannelListener.cs içinde yer aldığı. <xref:System.ServiceModel.Channels.IChannel> uygulamalar UdpOutputChannel.cs ve UdpInputChannel.cs ' dir.  
  
### <a name="the-udp-channel-factory"></a>UDP kanal fabrikası  
 `UdpChannelFactory` öğesi <xref:System.ServiceModel.Channels.ChannelFactoryBase> öğesinden türer. Örnek, ileti kodlayıcının ileti sürümüne erişim sağlamak için <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> geçersiz kılar. Örnek, durum makinesi geçişi sırasında <xref:System.ServiceModel.Channels.BufferManager> örneğimizi bir şekilde belirleyebilmemiz için <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> de geçersiz kılar.  
  
#### <a name="the-udp-output-channel"></a>UDP çıkış kanalı  
 `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>uygular. Oluşturucu bağımsız değişkenleri doğrular ve geçirilen <xref:System.ServiceModel.EndpointAddress> temel alarak bir hedef <xref:System.Net.EndPoint> nesnesi oluşturur.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanal düzgün şekilde kapatılabilir veya düzgün şekilde kapatılabilir. Kanal düzgün şekilde kapatılırsa yuva kapatılır ve temel sınıf `OnClose` yöntemine bir çağrı yapılır. Bu bir özel durum oluşturursa, kanalın temizlendiğinden emin olmak için altyapı `Abort` çağırır.  
  
```csharp
this.socket.Close(0);  
```  
  
 Daha sonra `Send()` ve `BeginSend()`/`EndSend()`uyguladık. Bu, iki ana bölümde kesilir. İlk olarak, iletiyi bir bayt dizisine serileştirtik.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Sonuç olarak elde edilen verileri tel olarak göndereceğiz.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  
 Örneğin uyguladığı `UdpChannelListener` <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfından türetilir. Veri birimlerini almak için tek bir UDP yuvası kullanır. `OnOpen` yöntemi, UDP yuvasını zaman uyumsuz bir döngüde kullanarak verileri alır. Veriler daha sonra Ileti kodlama çerçevesi kullanılarak iletilere dönüştürülür.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Aynı veri birimi kanalı, bir dizi kaynaktan gelen iletileri temsil ettiğinden `UdpChannelListener` tek bir dinleyici olur. Aynı anda bu dinleyiciyle ilişkili, en fazla bir etkin <xref:System.ServiceModel.Channels.IChannel> vardır. Örnek yalnızca `AcceptChannel` yöntemi tarafından döndürülen bir kanal daha sonra atıldığı takdirde bir tane oluşturur. Bir ileti alındığında, bu Singleton kanalında sıraya alınır.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` sınıfı `IInputChannel`uygular. `UdpChannelListener`yuvası tarafından doldurulan bir gelen ileti kuyruğundan oluşur. Bu iletiler `IInputChannel.Receive` yöntemi tarafından kaldırılır.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Bağlama öğesi ekleme  
 Fabrikalar ve kanallar derlenmesine göre, bunları bir bağlama aracılığıyla ServiceModel çalışma zamanına göstermemiz gerekir. Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğelerinin koleksiyonudur. Yığındaki her öğe bir [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) öğesi tarafından temsil edilir.  
  
 Örnekte, bağlama öğesi, <xref:System.ServiceModel.Channels.TransportBindingElement>türetilen `UdpTransportBindingElement`. Bağlamamız ile ilişkili fabrikaları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
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
  
 Ayrıca, `BindingElement` klonlamamız ve düzen (SOAP. UDP) döndürmek için de üye içerir.  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Bir taşıma bağlama öğesi için meta veri desteği ekleme  
 Aktarımımızı meta veri sistemine tümleştirmek için, hem ilkenin içeri ve dışarı aktarılmasını desteklememiz gerekir. Bu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)aracılığıyla bağlamamız için istemci oluşturmamızı sağlar.  
  
### <a name="adding-wsdl-support"></a>WSDL desteği ekleme  
 Bir bağlamadaki aktarım bağlama öğesi, meta verilerde adres bilgilerinin dışarı ve içeri aktarılmasından sorumludur. SOAP bağlama kullanılırken, aktarım bağlama öğesi meta verilerde doğru bir taşıma URI 'sini de dışarı aktarmalıdır.  
  
#### <a name="wsdl-export"></a>WSDL dışarı aktarma  
 Adres bilgilerini dışarı aktarmak için `UdpTransportBindingElement` `IWsdlExportExtension` arabirimini uygular. `ExportEndpoint` yöntemi, WSDL bağlantı noktasına doğru adres bilgilerini ekler.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `ExportEndpoint` yönteminin `UdpTransportBindingElement` uygulanması, uç nokta bir SOAP bağlama kullandığında bir aktarım URI 'sini de dışarı aktarır.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL Içeri aktarma  
 WSDL içeri aktarma sistemini, adresleri içeri aktarmayı işleyecek şekilde genişletmek için, Svcutil. exe. config dosyasında gösterildiği gibi Svcutil. exe için yapılandırma dosyasına aşağıdaki yapılandırmayı eklememiz gerekir.  
  
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
  
 Svcutil. exe dosyasını çalıştırırken, Svcutil. exe ' nin WSDL içeri aktarma uzantılarını yüklemesi için iki seçenek vardır:  
  
1. Svcutil. exe ' yi,/SvcutilConfig:\<Dosya > kullanarak yapılandırma dosyanıza yazın.  
  
2. Svcutil. exe. config dosyasına, Svcutil. exe ile aynı dizinde yapılandırma bölümünü ekleyin.  
  
 `UdpBindingElementImporter` türü `IWsdlImportExtension` arabirimini uygular. `ImportEndpoint` yöntemi, adresi WSDL bağlantı noktasından içeri aktarır.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Ilke desteği ekleme  
 Özel bağlama öğesi, söz konusu bağlama öğesinin yeteneklerini ifade etmek için bir hizmet uç noktası için WSDL bağlamasındaki ilke onaylamalarını dışarı aktarabilir.  
  
#### <a name="policy-export"></a>İlke dışarı aktarma  
 `UdpTransportBindingElement` türü, ilke dışarı aktarma desteği eklemek için `IPolicyExportExtension` uygular. Sonuç olarak, `System.ServiceModel.MetadataExporter`, kendisini içeren herhangi bir bağlama için ilkenin oluşturulmasına `UdpTransportBindingElement` ekler.  
  
 `IPolicyExportExtension.ExportPolicy`, çok noktaya yayın modundayken UDP ve başka bir onaylama için bir onaylama ekleyeceğiz. Bunun nedeni, çok noktaya yayın modunun iletişim yığınının oluşturulmasını etkilemesi ve bu nedenle her iki taraf arasında koordine olması gerekir.  
  
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
  
 Özel aktarım bağlama öğeleri, adresleme 'yi işlemekten sorumlu olduğundan, `UdpTransportBindingElement` `IPolicyExportExtension` uygulamasının, kullanılan WS-Addressing sürümünü göstermek için uygun WS-Addressing ilke onayları vermeyi de işlemesi gerekir.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>İlke Içeri aktarma  
 Ilke Içeri aktarma sistemini genişletmek için, Svcutil. exe. config dosyasında gösterildiği gibi Svcutil. exe için yapılandırma dosyasına aşağıdaki yapılandırmayı eklememiz gerekir.  
  
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
  
 Ardından, kayıtlı sınıfımızdan `IPolicyImporterExtension` uyguladık (`UdpBindingElementImporter`). `ImportPolicy()`, ad boşluğumuzdaki onaylamaları gözden geçirin ve taşıma işlemini oluşturma ve çok noktaya yayın olup olmadığını denetleme işlemlerini işler. Ayrıca, idare ettiğimiz onayları, bağlama onayları listesinden kaldırdık. Yine, Svcutil. exe dosyasını çalıştırırken, tümleştirme için iki seçenek vardır:  
  
1. Svcutil. exe ' yi,/SvcutilConfig:\<Dosya > kullanarak yapılandırma dosyanıza yazın.  
  
2. Svcutil. exe. config dosyasına, Svcutil. exe ile aynı dizinde yapılandırma bölümünü ekleyin.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Standart bağlama ekleme  
 Binding öðemiz aşağıdaki iki şekilde kullanılabilir:  
  
- Özel bağlama aracılığıyla: özel bir bağlama, kullanıcının rastgele bağlama öğeleri kümesini temel alarak kendi bağlamasını oluşturmalarına olanak sağlar.  
  
- Bağlama öğesini içeren sistem tarafından sağlanmış bir bağlama kullanarak. WCF, `BasicHttpBinding`, `NetTcpBinding`ve `WsHttpBinding`gibi sistem tarafından tanımlanan bu bağlamaları sağlar. Bu bağlamaların her biri iyi tanımlanmış bir profille ilişkilendirilir.  
  
 Örnek, <xref:System.ServiceModel.Channels.Binding>türetilen `SampleProfileUdpBinding`profil bağlamayı uygular. `SampleProfileUdpBinding`, içinde en fazla dört bağlama öğesi içerir: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`ve `ReliableSessionBindingElement`.  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Özel standart bağlama Içeri aktarıcı ekleme  
 Svcutil. exe ve `WsdlImporter` türü, varsayılan olarak sistem tarafından tanımlanan bağlamaları tanır ve içeri aktarır. Aksi takdirde, bağlama bir `CustomBinding` örneği olarak içeri aktarılır. Svcutil. exe ' yi ve `WsdlImporter` `UdpBindingElementImporter` `SampleProfileUdpBinding` içeri aktarmak için bir özel standart bağlama alma işlemi olarak da çalışır.  
  
 Özel standart bağlama İçeri Aktarıcı, belirli bir standart bağlama tarafından oluşturulup oluşturulmayacağını görmek için meta verilerden içeri aktarılan `CustomBinding` örneğini incelemek üzere `IWsdlImportExtension` arabirimindeki `ImportEndpoint` yöntemini uygular.  
  
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
  
 Genellikle, özel bir standart bağlama alma programı uygulamak, yalnızca standart bağlama tarafından ayarlanmış olabilecek özelliklerin değiştiğini ve diğer tüm özelliklerin varsayılan olduğunu doğrulamak için içeri aktarılan bağlama öğelerinin özelliklerinin denetlenmesini içerir. Standart bağlama alma işlemi uygulamaya yönelik temel bir strateji, standart bağlamanın bir örneğini oluşturmaktır, bağlama öğelerinden özellikleri standart bağlamanın desteklediği standart bağlama örneğine yayar ve bağlamayı karşılaştırın İçeri aktarılan bağlama öğeleriyle standart bağlamalardan öğeler.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Aktarımımızı yapılandırma yoluyla göstermek için iki yapılandırma bölümü uygulamamız gerekir. Birincisi, `UdpTransportBindingElement`için bir `BindingElementExtensionElement`. Bu, `CustomBinding` uygulamalarının bağlama öğesine başvurabilmesi için. İkincisi, `SampleProfileUdpBinding`için bir `Configuration`.  
  
### <a name="binding-element-extension-element"></a>Bağlama öğesi uzantı öğesi  
 `UdpTransportElement` bölüm, yapılandırma sistemine `UdpTransportBindingElement` sunan bir `BindingElementExtensionElement`. Birkaç temel geçersiz kılma sayesinde yapılandırma bölüm adı ' nı, bağlama öðemizin türünü ve bağlama öğesini nasıl oluşturacağınız anlatılmaktadır. Ardından, aşağıdaki kodda gösterildiği gibi, uzantı bölümümüzü bir yapılandırma dosyasına kaydedebiliriz.  
  
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
  
 Uzantıya, taşıma olarak UDP 'yi kullanmak için özel bağlamalardan başvurulabilir.  
  
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
  
### <a name="binding-section"></a>Bağlama bölümü  
 `SampleProfileUdpBindingCollectionElement` bölüm, yapılandırma sistemine `SampleProfileUdpBinding` sunan bir `StandardBindingCollectionElement`. Uygulamanın toplu işlemi, `StandardBindingElement`türetilen `SampleProfileUdpBindingConfigurationElement`için temsilci olarak oluşturulur. `SampleProfileUdpBindingConfigurationElement`, `SampleProfileUdpBinding`özelliklere ve `ConfigurationElement` bağlamalarından eşlenecek işlevlere karşılık gelen özelliklere sahiptir. Son olarak, aşağıdaki örnek kodda gösterildiği gibi, `SampleProfileUdpBinding``OnApplyConfiguration` yöntemini geçersiz kılın.  
  
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
  
 Bu işleyiciyi yapılandırma sistemine kaydetmek için ilgili yapılandırma dosyasına aşağıdaki bölümü ekleyeceğiz.  
  
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
  
 Daha sonra serviceModel yapılandırma bölümünden başvurulmalıdır.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>UDP test hizmeti ve Istemcisi  
 Bu örnek taşımanın kullanılması için test kodu, UdpTestService ve UdpTestClient dizinlerinde bulunabilir. Hizmet kodu iki testten oluşur; bir test koddan bağlamaları ve uç noktaları ayarlar ve diğeri de yapılandırma yoluyla yapılır. Her iki test iki uç nokta kullanır. Bir uç nokta, [\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) `true`olarak ayarlanan `SampleUdpProfileBinding` kullanır. Diğer uç nokta `UdpTransportBindingElement`ile özel bir bağlama kullanır. Bu, [\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) `false`olarak ayarlanan `SampleUdpProfileBinding` kullanmakla eşdeğerdir. Her iki test de bir hizmet oluşturur, her bağlama için bir uç nokta ekler, hizmeti açar ve ardından hizmeti kapatmadan önce kullanıcının ENTER tuşuna basmasını bekler.  
  
 Hizmet testi uygulamasını başlattığınızda, aşağıdaki çıktıyı görmeniz gerekir.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Daha sonra, test istemci uygulamasını yayımlanan uç noktalara karşı çalıştırabilirsiniz. İstemci test uygulaması her bir uç nokta için bir istemci oluşturur ve her uç noktaya beş ileti gönderir. Aşağıdaki çıktı istemcide bulunur.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Hizmetin tam çıkışı aşağıda verilmiştir.  
  
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
  
 İstemci uygulamasını yapılandırma kullanılarak yayınlanan uç noktalara karşı çalıştırmak için, hizmette ENTER tuşuna basın ve ardından test istemcisini yeniden çalıştırın. Hizmette aşağıdaki çıktıyı görmeniz gerekir.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 İstemciyi yeniden çalıştırmak, önceki sonuçlarla aynı sonucu verir.  
  
 Svcutil. exe kullanarak istemci kodunu ve yapılandırmayı yeniden oluşturmak için, hizmet uygulamasını başlatın ve ardından örnek kök dizininden aşağıdaki Svcutil. exe dosyasını çalıştırın.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Svcutil. exe ' nin `SampleProfileUdpBinding`için bağlama uzantısı yapılandırması oluşturmadığına, bu nedenle el ile eklemeniz gerekir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
2. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Önceki "UDP test hizmeti ve Istemcisi" bölümüne bakın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
