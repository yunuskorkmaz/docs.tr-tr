---
title: 'Taşıma: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 44e47dd2d291ffc27d1777a04b645d57984919cd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591442"
---
# <a name="transport-udp"></a>Taşıma: UDP
UDP taşıma örneği, UDP tek noktaya yayın ve çok noktaya yayının özel bir Windows Communication Foundation (WCF) taşıması olarak nasıl uygulanacağını gösterir. Örnek, kanal çerçevesini ve aşağıdaki WCF en iyi yöntemlerini kullanarak WCF 'de özel bir aktarım oluşturmak için önerilen yordamı açıklar. Özel bir aktarım oluşturma adımları aşağıdaki gibidir:  
  
1. ChannelFactory ve ChannelListener 'ın destekleyeceği kanal [Iletisi değişimi desenlerinin](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel veya IReplyChannel destekleyen desteklenecektir) hangisi olacağına karar verin. Ardından, bu arabirimlerin oturumsuz çeşitlemelerini desteklememeye karar verin.  
  
2. Ileti değişim modelinizi destekleyen bir kanal fabrikası ve dinleyicisi oluşturun.  
  
3. Ağa özgü özel durumların, uygun türetilmiş sınıfına normalleştirildiğinden emin olun <xref:System.ServiceModel.CommunicationException> .  
  
4. [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)Özel aktarımı bir kanal yığınına ekleyen bir öğe ekleyin. Daha fazla bilgi için bkz. [bağlama öğesi ekleme](#AddingABindingElement).  
  
5. Yeni bağlama öğesini yapılandırma sistemine göstermek için bağlama öğesi uzantısı bölümü ekleyin.  
  
6. Diğer uç noktalara iletişim kurmak için meta veri uzantıları ekleyin.  
  
7. İyi tanımlanmış bir profile göre bağlama öğeleri yığınını önceden yapılandıran bir bağlama ekleyin. Daha fazla bilgi için bkz. [Standart bağlama ekleme](#AddingAStandardBinding).  
  
8. Yapılandırma sistemine bağlamayı göstermek için bağlama bölümü ve bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için bkz. [yapılandırma desteği ekleme](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a>İleti değişimi desenleri  
 Özel bir aktarım yazarken ilk adım, taşıma için hangi Ileti değişim desenlerinin (MEPs) gerekli olduğuna karar vermeye yöneliktir. Aralarından seçim yapabileceğiniz üç/PS vardır:  
  
- Veri birimi (IInputChannel/IOutputChannel)  
  
     Bir veri birimi MEP kullanırken, istemci "yangın ve unut" Exchange kullanarak bir ileti gönderir. Bir ateş ve unutur, başarılı teslimin bant dışı onayını gerektiren bir adım. İleti iletimde kaybolmuş olabilir ve hizmete hiçbir şekilde ulaşamamalıdır. Gönderme işlemi istemci sonunda başarıyla tamamlanırsa, uzak uç noktanın iletiyi aldığını garanti etmez. Bu veri birimi, güvenilir protokoller ve güvenli protokoller de dahil olmak üzere kendi protokollerinizi oluşturabileceğiniz gibi, mesajlaşma için temel bir yapı taşıdır. İstemci veri birimi kanalları arabirimini <xref:System.ServiceModel.Channels.IOutputChannel> uygulayan arabirimi ve hizmet veri birimi kanallarını uygular <xref:System.ServiceModel.Channels.IInputChannel> .  
  
- İstek-yanıt (IRequestChannel/IReplyChannel destekleyen desteklenecektir)  
  
     Bu MEP 'de bir ileti gönderilir ve bir yanıt alındı. Bu model, istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrısı örnekleri, uzak yordam çağrılardır (RPC) ve tarayıcı alır. Bu model, yarı çift yönlü olarak da bilinir. Bu MEP 'de, istemci kanalları <xref:System.ServiceModel.Channels.IRequestChannel> ve hizmet kanalları uygular <xref:System.ServiceModel.Channels.IReplyChannel> .  
  
- Çift yönlü (IDuplexChannel)  
  
     Çift yönlü MEP, istemci tarafından rastgele sayıda iletinin gönderilmesini ve herhangi bir sırada alınmasını sağlar. Çift yönlü MEP, konuşulan her sözcüğün bir ileti olduğu bir telefon konuşması gibidir. Her iki taraf da bu MEP 'de gönderebildiğinden ve alabileceği için, istemci ve hizmet kanalları tarafından uygulanan arabirim <xref:System.ServiceModel.Channels.IDuplexChannel> .  
  
 Bu MEPs 'lerin her biri, oturumları da destekleyebilir. Oturum kullanan bir kanal tarafından sunulan ek işlevsellik, bir kanalda gönderilen ve alınan tüm iletileri ilişkilendirir. İstek ve yanıt bağıntılı olduğundan, Istek-yanıt deseninin tek başına iki ileti oturumu vardır. Buna karşılık, oturumları destekleyen Istek-yanıt deseninin, o kanaldaki tüm istek/yanıt çiftlerinin birbirleriyle bağıntılı olduğu anlamına gelir. Bu, arasından seçim yapmak için toplam altı adet, veri birimi, Istek-yanıt, çift yönlü, oturumlarla oturum, oturum Isteği ve oturumlarla çift yönlü veri birimi sağlar.  
  
> [!NOTE]
> UDP bir "yangın ve unut" Protokolü olduğundan, UDP taşıması için desteklenen tek MEP yalnızca veri birimi olur.  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>Idimmunicationobject ve WCF nesne yaşam döngüsü  
 WCF,, ve gibi nesnelerin yaşam döngüsünü yönetmek için kullanılan, <xref:System.ServiceModel.Channels.IChannel> <xref:System.ServiceModel.Channels.IChannelFactory> ve iletişim için kullanılan bir ortak durum makinesine sahiptir <xref:System.ServiceModel.Channels.IChannelListener> . Bu iletişim nesnelerinin bulunabileceği beş durum vardır. Bu durumlar, sabit listesi tarafından temsil edilir <xref:System.ServiceModel.CommunicationState> ve aşağıdaki gibidir:  
  
- Oluşturuldu: Bu, ilk örneği oluşturulduğunda bir durumudur <xref:System.ServiceModel.ICommunicationObject> . Bu durumda giriş/çıkış (g/ç) oluşmaz.  
  
- Açılıyor: çağrıldığında nesneler bu duruma geçiş <xref:System.ServiceModel.ICommunicationObject.Open%2A> yapılır. Bu noktada özellikler sabit hale getirilir ve giriş/çıkış başlayabilir. Bu geçiş yalnızca oluşturulan durumdan geçerlidir.  
  
- Açıldı: nesneler, açık işlem tamamlandığında bu duruma geçiş yapar. Bu geçiş yalnızca açma durumunda geçerlidir. Bu noktada, nesne aktarım için tamamen kullanılabilir.  
  
- Kapatılıyor: nesneler <xref:System.ServiceModel.ICommunicationObject.Close%2A> düzgün kapanma için çağrıldığında bu duruma geçiş yapılır. Bu geçiş yalnızca açık durumda geçerlidir.  
  
- Kapalı: kapalı durum nesnelerinde artık kullanılamaz. Genel olarak, çoğu yapılandırmaya hala inceleme için erişilebilir, ancak hiçbir iletişim gerçekleşmez. Bu durum atılmıştı.  
  
- Hatalı: Hatalı durumda, nesnelere denetim için erişilebilir ancak artık kullanılamaz. Kurtarılabilir olmayan bir hata oluştuğunda, nesne bu duruma geçer. Bu durumdan geçerli olan tek geçiş `Closed` durumunda olur.  
  
 Her durum geçişi için başlatılan olaylar vardır. <xref:System.ServiceModel.ICommunicationObject.Abort%2A>Yöntemi herhangi bir zamanda çağrılabilir ve nesnenin geçerli durumundan Kapalı durumuna geçmesine neden olur. Çağırma, <xref:System.ServiceModel.ICommunicationObject.Abort%2A> tamamlanmamış işleri sonlandırır.  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a>Kanal fabrikası ve kanal dinleyicisi  
 Özel bir aktarım yazarken bir sonraki adım, <xref:System.ServiceModel.Channels.IChannelFactory> İstemci kanalları ve hizmet kanalları için bir uygulama oluşturmaktır <xref:System.ServiceModel.Channels.IChannelListener> . Kanal katmanı, kanal oluşturmak için bir fabrika kalıbı kullanır. WCF bu işlem için temel sınıf yardımcıları sağlar.  
  
- <xref:System.ServiceModel.Channels.CommunicationObject>Sınıfı, <xref:System.ServiceModel.ICommunicationObject> daha önce 2. adımda açıklanan durum makinesini uygular ve uygular.

- <xref:System.ServiceModel.Channels.ChannelManagerBase>Sınıfı, <xref:System.ServiceModel.Channels.CommunicationObject> ve için Birleşik bir temel sınıf sağlar <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelListenerBase> . <xref:System.ServiceModel.Channels.ChannelManagerBase>Sınıfı ile birlikte çalışarak <xref:System.ServiceModel.Channels.ChannelBase> , uygulayan bir temel sınıf olan <xref:System.ServiceModel.Channels.IChannel> .  
  
- <xref:System.ServiceModel.Channels.ChannelFactoryBase>Sınıfı, <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` yüklerini tek bir soyut yöntemde uygular ve birleştirir `OnCreateChannel` .  
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase>Sınıfı uygular <xref:System.ServiceModel.Channels.IChannelListener> . Temel durum yönetiminden çok dikkat edin.  
  
 Bu örnekte, fabrika uygulamasının UdpChannelFactory.cs içinde yer aldığı ve dinleyici uygulamasının UdpChannelListener.cs içinde yer aldığı. <xref:System.ServiceModel.Channels.IChannel>Uygulamalar UdpOutputChannel.cs ve UdpInputChannel.cs ' dir.  
  
### <a name="the-udp-channel-factory"></a>UDP kanal fabrikası  
 `UdpChannelFactory`Öğesinden türetilir <xref:System.ServiceModel.Channels.ChannelFactoryBase> . Örnek, <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti kodlayıcının ileti sürümüne erişim sağlamak için geçersiz kılar. Örnek ayrıca <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> <xref:System.ServiceModel.Channels.BufferManager> durum makinesi geçişi sırasında örneğimizi daha fazla belirleyebilmemiz için geçersiz kılar.  
  
#### <a name="the-udp-output-channel"></a>UDP çıkış kanalı  
 `UdpOutputChannel`Uygular <xref:System.ServiceModel.Channels.IOutputChannel> . Oluşturucu bağımsız değişkenleri doğrular ve geçirilen öğesine bağlı olarak bir hedef <xref:System.Net.EndPoint> nesnesi oluşturur <xref:System.ServiceModel.EndpointAddress> .  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanal düzgün şekilde kapatılabilir veya düzgün şekilde kapatılabilir. Kanal kapalıysa, yuva kapanır ve temel sınıf yöntemine bir çağrı yapılır `OnClose` . Bu, bir özel durum oluşturursa, `Abort` kanalın temizlendiğinden emin olmak için altyapı çağrılır.  
  
```csharp
this.socket.Close(0);  
```  
  
 Ardından `Send()` , ve ' i uyguladık `BeginSend()` / `EndSend()` . Bu, iki ana bölümde kesilir. İlk olarak, iletiyi bir bayt dizisine serileştirtik.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Sonuç olarak elde edilen verileri tel olarak göndereceğiz.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  
 `UdpChannelListener`Örneğin uyguladığı örnek sınıfından türetiliyor <xref:System.ServiceModel.Channels.ChannelListenerBase> . Veri birimlerini almak için tek bir UDP yuvası kullanır. `OnOpen`Yöntemi, UDP yuvasını zaman uyumsuz bir döngüde kullanarak verileri alır. Veriler daha sonra Ileti kodlama çerçevesi kullanılarak iletilere dönüştürülür.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Aynı veri birimi kanalı, bir dizi kaynaktan gelen iletileri temsil ettiğinden, `UdpChannelListener` tek bir dinleyici olur. En çok, bu dinleyiciyle aynı anda bir tane olmak üzere bir etkin <xref:System.ServiceModel.Channels.IChannel> . Örnek, yalnızca yöntemi tarafından döndürülen bir kanal `AcceptChannel` daha sonra atıldığı takdirde bir tane oluşturur. Bir ileti alındığında, bu Singleton kanalında sıraya alınır.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel`Sınıfı uygular `IInputChannel` . Bu, kendi yuvası tarafından doldurulan bir gelen ileti kuyruğundan oluşur `UdpChannelListener` . Bu iletiler yöntemi tarafından kaldırılır `IInputChannel.Receive` .  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a>Bağlama öğesi ekleme  
 Fabrikalar ve kanallar derlenmesine göre, bunları bir bağlama aracılığıyla ServiceModel çalışma zamanına göstermemiz gerekir. Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğelerinin koleksiyonudur. Yığındaki her öğe bir öğesi tarafından temsil edilir [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .  
  
 Örnekte, bağlama öğesi `UdpTransportBindingElement` öğesinden türetilir <xref:System.ServiceModel.Channels.TransportBindingElement> . Bağlamamız ile ilişkili fabrikaları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
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
  
 Ayrıca, `BindingElement` klonımızın (SOAP. UDP) kopyalanması ve döndürülmesi için Üyeler de bulunur.  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Bir taşıma bağlama öğesi için meta veri desteği ekleme  
 Aktarımımızı meta veri sistemine tümleştirmek için, hem ilkenin içeri ve dışarı aktarılmasını desteklememiz gerekir. Bu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)aracılığıyla bağlamamız için istemci oluşturmamızı sağlar.  
  
### <a name="adding-wsdl-support"></a>WSDL desteği ekleme  
 Bir bağlamadaki aktarım bağlama öğesi, meta verilerde adres bilgilerinin dışarı ve içeri aktarılmasından sorumludur. SOAP bağlama kullanılırken, aktarım bağlama öğesi meta verilerde doğru bir taşıma URI 'sini de dışarı aktarmalıdır.  
  
#### <a name="wsdl-export"></a>WSDL dışarı aktarma  
 Adres bilgilerini dışarı aktarmak için `UdpTransportBindingElement` arabirimini uygular `IWsdlExportExtension` . `ExportEndpoint`Yöntemi, wsdl bağlantı noktasına doğru adres bilgilerini ekler.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 Ayrıca, bu, `UdpTransportBindingElement` `ExportEndpoint` uç nokta bir soap bağlama kullandığında, yönteminin uygulanması bir aktarım URI 'sini dışa aktarır.  
  
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
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Svcutil. exe dosyasını çalıştırırken, Svcutil. exe ' nin WSDL içeri aktarma uzantılarını yüklemesi için iki seçenek vardır:  
  
1. /Svcutılconfig: komutunu kullanarak Svcutil. exe ' yi yapılandırma dosyanıza yazın \<file> .  
  
2. Svcutil. exe. config dosyasına, Svcutil. exe ile aynı dizinde yapılandırma bölümünü ekleyin.  
  
 `UdpBindingElementImporter`Türü, arabirimini uygular `IWsdlImportExtension` . `ImportEndpoint`YÖNTEMI wsdl bağlantı noktasından adresi içeri aktarır.  
  
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
 `UdpTransportBindingElement`Türü, `IPolicyExportExtension` ilke dışarı aktarma desteği eklemek için uygular. Sonuç olarak, `System.ServiceModel.MetadataExporter` `UdpTransportBindingElement` onu içeren herhangi bir bağlama için ilke oluşturmaya dahildir.  
  
 İçinde `IPolicyExportExtension.ExportPolicy` , çok noktaya yayın MODUNDAYKEN UDP ve başka bir onaylama için bir onaylama ekleyeceğiz. Bunun nedeni, çok noktaya yayın modunun iletişim yığınının oluşturulmasını etkilemesi ve bu nedenle her iki taraf arasında koordine olması gerekir.  
  
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
  
 Özel aktarım bağlama öğeleri, adresleme 'nin işlenmesinden sorumlu olduğundan, `IPolicyExportExtension` üzerindeki uygulamanın, `UdpTransportBindingElement` kullanılan ws-Addressing sürümünü göstermek IÇIN uygun ws-Addressing ilke onayları vermeyi de işlemesi gerekir.  
  
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
  
 Ardından, `IPolicyImporterExtension` kayıtlı sınıfımızdan () uyguladık `UdpBindingElementImporter` . ' De `ImportPolicy()` , ad boşluğumuzdaki onaylamaları inceleyerek, nakliyenizi oluşturmak ve çok noktaya yayın olup olmadığını denetlemek için bunları işletireceğiz. Ayrıca, idare ettiğimiz onayları, bağlama onayları listesinden kaldırdık. Yine, Svcutil. exe dosyasını çalıştırırken, tümleştirme için iki seçenek vardır:  
  
1. /Svcutılconfig: komutunu kullanarak Svcutil. exe ' yi yapılandırma dosyanıza yazın \<file> .  
  
2. Svcutil. exe. config dosyasına, Svcutil. exe ile aynı dizinde yapılandırma bölümünü ekleyin.  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a>Standart bağlama ekleme  
 Binding öðemiz aşağıdaki iki şekilde kullanılabilir:  
  
- Özel bağlama aracılığıyla: özel bir bağlama, kullanıcının rastgele bağlama öğeleri kümesini temel alarak kendi bağlamasını oluşturmalarına olanak sağlar.  
  
- Bağlama öğesini içeren sistem tarafından sağlanmış bir bağlama kullanarak. WCF,, ve gibi bu sistem tarafından tanımlanan bağlamaları sağlar `BasicHttpBinding` `NetTcpBinding` `WsHttpBinding` . Bu bağlamaların her biri iyi tanımlanmış bir profille ilişkilendirilir.  
  
 Örnek, ' de `SampleProfileUdpBinding` ' den türetilen profil bağlamasını uygular <xref:System.ServiceModel.Channels.Binding> . , `SampleProfileUdpBinding` İçinde en fazla dört bağlama öğesi içerir: `UdpTransportBindingElement` , `TextMessageEncodingBindingElement CompositeDuplexBindingElement` ve `ReliableSessionBindingElement` .  
  
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
 Svcutil. exe ve `WsdlImporter` türü varsayılan olarak sistem tarafından tanımlanan bağlamaları tanır ve içeri aktarır. Aksi takdirde, bağlama bir örnek olarak içeri aktarılır `CustomBinding` . Svcutil. exe ' yi etkinleştirmek ve `WsdlImporter` içeri aktarmak için `SampleProfileUdpBinding` `UdpBindingElementImporter` özel bir standart bağlama İçeri Aktarıcı işlevi de çalışır.  
  
 Özel standart bağlama İçeri Aktarıcı, `ImportEndpoint` `IWsdlImportExtension` `CustomBinding` belirli bir standart bağlama tarafından oluşturulup oluşturulmayacağını görmek için meta verilerden içeri aktarılan örneği incelemek üzere arabirimindeki yöntemi uygular.  
  
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
  
 Genellikle, özel bir standart bağlama alma programı uygulamak, yalnızca standart bağlama tarafından ayarlanmış olabilecek özelliklerin değiştiğini ve diğer tüm özelliklerin varsayılan olduğunu doğrulamak için içeri aktarılan bağlama öğelerinin özelliklerinin denetlenmesini içerir. Standart bağlama İçeri Aktarıcı uygulamaya yönelik temel bir strateji, standart bağlamanın bir örneğini oluşturmaktır, özellikleri bağlama öğelerinden standart bağlamanın desteklediği standart bağlama örneğine yayar ve içeri aktarılan bağlama öğeleriyle standart bağlamalardan bağlama öğelerini karşılaştırın.  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Aktarımımızı yapılandırma yoluyla göstermek için iki yapılandırma bölümü uygulamamız gerekir. Birincisi `BindingElementExtensionElement` için bir `UdpTransportBindingElement` . Bu, `CustomBinding` uygulamaların bağlama öğesine başvurabilmesi için kullanılır. İkincisi, bizim için bir ' dir `Configuration` `SampleProfileUdpBinding` .  
  
### <a name="binding-element-extension-element"></a>Bağlama öğesi uzantı öğesi  
 Bu bölüm, `UdpTransportElement` `BindingElementExtensionElement` `UdpTransportBindingElement` yapılandırma sistemine yönelik bir ' dır. Birkaç temel geçersiz kılma sayesinde yapılandırma bölüm adı ' nı, bağlama öðemizin türünü ve bağlama öğesini nasıl oluşturacağınız anlatılmaktadır. Ardından, aşağıdaki kodda gösterildiği gibi, uzantı bölümümüzü bir yapılandırma dosyasına kaydedebiliriz.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
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
 Bu bölüm, `SampleProfileUdpBindingCollectionElement` `StandardBindingCollectionElement` `SampleProfileUdpBinding` yapılandırma sistemine yönelik bir ' dır. Uygulamanın toplu işlemi, `SampleProfileUdpBindingConfigurationElement` ' den türetilen öğesine Temsilcili `StandardBindingElement` . , `SampleProfileUdpBindingConfigurationElement` Üzerinde özelliklerine karşılık gelen özelliklerine `SampleProfileUdpBinding` ve bağlamadan eşlenecek işlevlere sahiptir `ConfigurationElement` . Son olarak, `OnApplyConfiguration` `SampleProfileUdpBinding` Aşağıdaki örnek kodda gösterildiği gibi, sitemizdeki yöntemi geçersiz kılın.  
  
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
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
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
 Bu örnek taşımanın kullanılması için test kodu, UdpTestService ve UdpTestClient dizinlerinde bulunabilir. Hizmet kodu iki testten oluşur; bir test koddan bağlamaları ve uç noktaları ayarlar ve diğeri de yapılandırma yoluyla yapılır. Her iki test iki uç nokta kullanır. Bir uç nokta `SampleUdpProfileBinding` ile [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) olarak ayarlanmış öğesini kullanır `true` . Diğer uç nokta ile özel bir bağlama kullanır `UdpTransportBindingElement` . Bu, `SampleUdpProfileBinding` olarak ayarlandığı ile eşdeğerdir [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) `false` . Her iki test de bir hizmet oluşturur, her bağlama için bir uç nokta ekler, hizmeti açar ve ardından hizmeti kapatmadan önce kullanıcının ENTER tuşuna basmasını bekler.  
  
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
  
 Svcutil. exe ' nin için bağlama uzantısı yapılandırması oluşturmadığına `SampleProfileUdpBinding` , bu nedenle el ile eklemeniz gerekir.  
  
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
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
2. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Önceki "UDP test hizmeti ve Istemcisi" bölümüne bakın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
