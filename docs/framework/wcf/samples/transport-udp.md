---
title: 'Taşıma: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 8d72ab5c7d8c461cd2ce4d4003d449ac9fe7e807
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007727"
---
# <a name="transport-udp"></a>Taşıma: UDP
UDP taşıma örnek nasıl uygulanacağı UDP tek noktaya yayın ve çok noktaya yayın özel bir Windows Communication Foundation (WCF) aktarım olarak gösterir. Örnek kanal çerçevesi kullanarak ve en iyi yöntemleri WCF özel taşıma WCF'de, oluşturmak için önerilen yordamı açıklar. Özel bir taşıma oluşturmak için adımları aşağıdaki gibidir:  
  
1. Kanal karar [ileti Exchange desenleri](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel veya IReplyChannel) ChannelFactory ve ChannelListener destekleyecektir. Ardından bu arabirimlerin kapatamaması çeşitlemeleri destekleyip desteklemeyeceğini karar verin.  
  
2. Kanal fabrikası ve, ileti değişim deseni destekleyen bir dinleyici oluşturun.  
  
3. Ağ özgü özel durumların uygun türetilmiş sınıfa normalleştirilir olun <xref:System.ServiceModel.CommunicationException>.  
  
4. Ekleme bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) özel taşıma için bir kanal yığını ekler öğesi. Daha fazla bilgi için [bir bağlama öğesi ekleme](#AddingABindingElement).  
  
5. Yeni bağlama öğesi yapılandırma sistemi için kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin.  
  
6. Diğer uç nokta Özellikleri iletişim kurmak için meta verileri uzantılar ekleyin.  
  
7. İyi tanımlanmış bir profili göre bağlama öğeleri yığınını önceden yapılandırır bir bağlaması ekleyin. Daha fazla bilgi için [standart bir bağlama ekleme](#AddingAStandardBinding).  
  
8. Bir bağlama bölümü ve bağlama yapılandırma sistemi kullanıma sunmak için bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için [yapılandırma desteği ekleme](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>İleti Exchange desenleri  
 İlk adım karar vermek için özel bir taşıma yazıyor hangi ileti Exchange desenleri (MEPs) taşıma için gereklidir. Aralarından seçim yapabileceğiniz üç MEPs vardır:  
  
- Veri birimi (IInputChannel/IOutputChannel)  
  
     Bir veri birimi MEP kullanırken, bir istemci bir "Başlat ve unut" exchange kullanarak bir ileti gönderir. Bir Başlat ve unut değişimi, başarılı bir teslimat bant dışı onay gerektiren bir. İleti, geçiş sırasında kaybolur ve hiçbir zaman hizmet ulaşın. İstemci sonunda gönderme işlemi başarıyla tamamlarsa, uzak uç noktada bir ileti aldı garanti etmez. Bunun üstünde kurallarınızı oluştururken veri birimi Mesajlaşma için temel yapı taşı olan — güvenilir protokolleri ve güvenli protokolleri dahil. İstemci veri birimi kanalları uygulamak <xref:System.ServiceModel.Channels.IOutputChannel> arabirimi ve hizmet veri birimi kanalları uygulamak <xref:System.ServiceModel.Channels.IInputChannel> arabirimi.  
  
- İstek-yanıt (IRequestChannel/IReplyChannel'ı)  
  
     Bu MEP bir ileti gönderilir ve bir yanıt aldı. Desen, istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrıları örnekleri: uzaktan yordam çağrısı (RPC) ve tarayıcı alır. Bu düzen, yarı çift yönlü da bilinir. Bu MEP içinde istemci kanalları uygulamak <xref:System.ServiceModel.Channels.IRequestChannel> ve hizmet kanalları uygulamak <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
- Çift yönlü (IDuplexChannel)  
  
     Çift yönlü MEP tercihe bağlı sayıda istemci tarafından gönderilen ve alınan herhangi bir sırada iletileri sağlar. Çift yönlü MEP bir telefon konuşması gibi burada konuşulan her bir sözcüğün bir ileti numarasıdır. Her iki tarafında da gönderebilir ve alabilir bu MEP, istemci ve hizmet kanalları tarafından uygulanan arabirimi çünkü <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Ayrıca, her biri bu MEPs oturumları destekleyebilir. Oturum durumunu algılayan bir kanal tarafından sağlanan ek işlevsellik kanalı üzerinden alınan ve gönderilen tüm iletilerin karşılık gelen ' dir. İstek-yanıt desen istek ve yanıt bağıntılı olan bir tek başına iki ileti oturumu aynıdır. Buna karşılık, bu kanal üzerindeki tüm istek/yanıt çifti birbiriyle ilişkilendirilir oturumları destekleyen istek-yanıt deseni gösterir. Bu toplam altı MEPs sağlar — veri birimi, istek-yanıt, çift yönlü, veri birimi oturumla istek-yanıt oturumları içeren ve oturumları ile çift yönlü — seçilecek.  
  
> [!NOTE]
>  UDP kendiliğinden "Başlat ve unut" protokol UDP taşıma için desteklenen tek MEP veri birimi, olduğundan.  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>ICommunicationObject ve WCF nesne yaşam döngüsü  
 WCF sahip gibi nesnelerin ömrünü yönetmek için kullanılan ortak bir Durum makinesi <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, ve <xref:System.ServiceModel.Channels.IChannelListener> iletişim için kullanılır. Bu iletişim nesneleri mevcut beş durum vardır. Bu durumlar tarafından temsil edilen <xref:System.ServiceModel.CommunicationState> numaralandırma ve aşağıdaki gibi şunlardır:  
  
- Oluşturma tarihi: Bu durumda, bir <xref:System.ServiceModel.ICommunicationObject> , ilk oluşturulduğunda. Bu durumda hiçbir giriş/çıkış (g/ç) gerçekleşir.  
  
- Açma: Bu nesneler geçiş durumu <xref:System.ServiceModel.ICommunicationObject.Open%2A> çağrılır. Bu noktada, özellikler sabit yapılır ve giriş/çıkış başlayabilirsiniz. Bu geçiş, yalnızca oluşturulan durumu geçerli değil.  
  
- Açıldı: Bu durum açma işlemi tamamlandığında geçiş nesneleri. Bu geçiş, yalnızca açılış durumu geçerli değil. Bu noktada, nesne aktarımı için tam olarak kullanılabilir.  
  
- Kapatma: Bu nesneler geçiş durumu <xref:System.ServiceModel.ICommunicationObject.Close%2A> normal şekilde kapatılmasını için çağrılır. Bu geçiş, yalnızca açık durumu geçerli değil.  
  
- Kapalı: Kapanış durum nesneleri artık kullanılabilir değildir. Genel olarak, en fazla yapılandırma İnceleme için hala erişilebilir, ancak hiçbir iletişim ortaya çıkabilir. Bu durum atıldı için eşdeğerdir.  
  
- Hatalı: Faulted durumunda nesneleri incelemesi erişebilir, ancak artık kullanılamaz. Nesnesi, bir kurtarılamaz bir hata oluştuğunda, bu duruma geçer. Bu durum yalnızca geçerli geçiş halinde olan `Closed` durumu.  
  
 Her bir durum geçişi için harekete olaylar vardır. <xref:System.ServiceModel.ICommunicationObject.Abort%2A> Yöntemi herhangi bir zamanda çağrılabilir ve nesne geçiş hemen geçerli durumunu kapalı duruma neden olur. Çağırma <xref:System.ServiceModel.ICommunicationObject.Abort%2A> herhangi bir bitmemiş iş sonlandırır.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Kanal fabrikası ve kanal dinleyicisi  
 Sonraki adım özel bir taşıma yazma uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> ve istemci kanallar için <xref:System.ServiceModel.Channels.IChannelListener> hizmet kanalları için. Kanal katmanını kanallar oluşturmak için bir Fabrika deseni kullanır. WCF bu işlem için temel sınıfı Yardımcıları sağlar.  
  
- <xref:System.ServiceModel.Channels.CommunicationObject> Sınıfının Implements <xref:System.ServiceModel.ICommunicationObject> ve 2. adımda daha önce açıklanan Durum makinesi uygular. 

- <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfının Implements <xref:System.ServiceModel.Channels.CommunicationObject> ve birleşik bir temel sınıf için <xref:System.ServiceModel.Channels.ChannelFactoryBase> ve <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı çalışır birlikte <xref:System.ServiceModel.Channels.ChannelBase>, uygulayan bir temel sınıf olan <xref:System.ServiceModel.Channels.IChannel>.  
  
- <xref:System.ServiceModel.Channels.ChannelFactoryBase> Sınıfının Implements <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> ve birleştirir `CreateChannel` aşırı birine `OnCreateChannel` soyut yöntemi.  
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase> Sınıfının Implements <xref:System.ServiceModel.Channels.IChannelListener>. Bu temel durum yönetimini üstlenir.  
  
 Bu örnekte Üreteç uygulaması UdpChannelFactory.cs içinde yer alır ve dinleyici uygulamasına UdpChannelListener.cs içinde yer alır. <xref:System.ServiceModel.Channels.IChannel> Uygulamalarıdır UdpOutputChannel.cs ve UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>UDP kanal fabrikası  
 `UdpChannelFactory` Türetildiği <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Örnek geçersiz kılmalar <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti Kodlayıcı ileti sürümüne erişim sağlamak için. Örnek ayrıca geçersiz kılar <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> böylece biz bizim örneğini yıkılıp <xref:System.ServiceModel.Channels.BufferManager> durum makinesinin zaman geçer.  
  
#### <a name="the-udp-output-channel"></a>UDP Çıkış kanalı  
 `UdpOutputChannel` Uygulayan <xref:System.ServiceModel.Channels.IOutputChannel>. Oluşturucu bağımsız değişkenlerini doğrular ve bir hedef oluşturur <xref:System.Net.EndPoint> nesnesini temel alan <xref:System.ServiceModel.EndpointAddress> olarak geçirilir.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanal ungracefully ya da düzgün biçimde kapatılabilir. Kanal düzgün bir şekilde kapanırsa yuva kapatıldı ve temel sınıf için bir çağrı yapılır `OnClose` yöntemi. Bu bir özel durum oluşturursa, altyapı çağırır `Abort` kanal emin olmak için temizlenir.  
  
```csharp
this.socket.Close(0);  
```  
  
 Ardından uygulama `Send()` ve `BeginSend()` / `EndSend()`. Bu iki ana bölüme ayırır. İlk biz iletinin Bayt dizisine serileştirir.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Daha sonra elde edilen veriler kablo göndereceğiz.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>The UdpChannelListener  
 `UdpChannelListener` Örnek uyguladığını türetildiği <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfı. Veri birimleri almak için tek bir UDP yuva kullanır. `OnOpen` Yöntemi zaman uyumsuz bir döngüde UDP yuvayı kullanan veri alır. Verileri daha sonra ileti kodlama çerçevesini kullanarak iletilere dönüştürülür.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Birçok kaynaktan gelen iletileri aynı veri birimi kanalı temsil ettiğinden `UdpChannelListener` tekil dinleyici. Yoktur, çoğu, bir tane aktif <xref:System.ServiceModel.Channels.IChannel> aynı anda bu dinleyici ile ilişkili. Tarafından döndürülen bir kanal, başka bir örnek oluşturur `AcceptChannel` yöntemi daha sonra atıldı. Bir ileti alındığında bu singleton kanal içine sıraya olur.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` Sınıfının Implements `IInputChannel`. Bir kuyruk tarafından doldurulur gelen iletilerin oluşan `UdpChannelListener`kullanıcının yuva. Bu iletiler tarafından çıkarıldığını `IInputChannel.Receive` yöntemi.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Bir bağlama öğesi ekleniyor  
 Fabrikaları ve kanallar oluşturulur, bunları ServiceModel çalışma zamanı için bir bağlama aracılığıyla kullanıma sunuyoruz gerekir. Bir bağlama temsil eden bir hizmet adresle ilişkilendirilen iletişim yığını bağlama öğelerinin bir koleksiyondur. Yığındaki her bir öğe tarafından temsil edilen bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi.  
  
 Bu örnekte bağlama öğedir `UdpTransportBindingElement`, öğesinden türetildiğini <xref:System.ServiceModel.Channels.TransportBindingElement>. Bu, bizim bağlamayla ilişkili fabrikaları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
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
  
 Kopyalama için de üyeleri içeren `BindingElement` ve bizim (soap.udp) şeması döndürüyor.  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Bir aktarım bağlama öğesi meta veri desteği eklendi  
 Bizim aktarım meta verileri sisteme tümleştirmek için biz içeri aktarma ve dışarı aktarma İlkesi desteklemesi gerekir. Bu bizim bağlama aracılığıyla istemcileri oluşturulacak sağlıyor [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>WSDL desteği ekleme  
 Bir bağlamadaki aktarım bağlama öğesinin dışarı ve içeri aktarma adres bilgilerini meta verilerinde sorumludur. SOAP bağlama kullanırken, aktarım bağlama öğesinin de meta verilerde doğru aktarım URI dışarı aktarmanız gerekir.  
  
#### <a name="wsdl-export"></a>WSDL dışarı aktarma  
 Adresleme bilgilerini dışarı aktarmak için `UdpTransportBindingElement` uygulayan `IWsdlExportExtension` arabirimi. `ExportEndpoint` Yöntemi WSDL bağlantı noktasına doğru adres bilgisi ekler.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Uygulaması `ExportEndpoint` yöntemi uç nokta bir SOAP bağlama kullandığında bir aktarım URI ayrıca verir.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL içeri aktarma  
 Adresleri içeri aktarma işlemek için WSDL içeri aktarma sistemini genişletmek için biz aşağıdaki yapılandırma için yapılandırma dosyası için Svcutil.exe Svcutil.exe.config dosyasında gösterildiği eklemeniz gerekir.  
  
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
  
 Svcutil.exe çalıştırırken, WSDL içeri aktarma uzantıları yüklemek için Svcutil.exe alma iki seçenek vardır:  
  
1. Noktası Svcutil.exe /SvcutilConfig kullanarak bizim yapılandırma dosyasına:\<Dosya >.  
  
2. Yapılandırma bölümü Svcutil.exe.config için Svcutil.exe ile aynı dizinde ekleyin.  
  
 `UdpBindingElementImporter` Yazın uygular `IWsdlImportExtension` arabirimi. `ImportEndpoint` Yöntemi WSDL bağlantı noktasından adresi alır.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>İlke desteği ekleme  
 Özel bağlama öğesi bağlamasında, bağlama öğesi yeteneklerini ifade etmek için WSDL hizmet uç noktası ilke onaylamalarını dışa aktarabilirsiniz.  
  
#### <a name="policy-export"></a>İlkeyi dışarı aktarma  
 `UdpTransportBindingElement` Yazın uygular `IPolicyExportExtension` ilke dışarı aktarma için destek eklemek için. Sonuç olarak, `System.ServiceModel.MetadataExporter` içerir `UdpTransportBindingElement` içerdiği herhangi bir bağlama için ilke oluşturma.  
  
 İçinde `IPolicyExportExtension.ExportPolicy`, biz çok noktaya yayın modunda olduğunda onaylama UDP ve başka bir onaylama için ekleriz. Çok noktaya yayın modu etkilediğinden nasıl iletişim yığını oluşturulur ve bu nedenle her iki tarafın arasında koordine edilmelidir budur.  
  
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
  
 Özel Aktarım bağlama öğeleriyle adresleme, işleme için sorumlu olduğundan `IPolicyExportExtension` mantığınız `UdpTransportBindingElement` WS-Addressing sürümü belirtmek için uygun WS-Addressing ilke onaylamalarını dışa aktarma işlemesi gerekir kullanılan.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>İlke içeri aktarma  
 İlke alma sistemini genişletmek için biz aşağıdaki yapılandırma yapılandırma dosyasına Svcutil.exe.config dosyasında gösterildiği Svcutil.exe için eklemeniz gerekir.  
  
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
  
 Biz uygulamak sonra `IPolicyImporterExtension` bizim kayıtlı sınıfından (`UdpBindingElementImporter`). İçinde `ImportPolicy()`, biz bizim ad alanında bir onayları arayın ve olanları taşıma oluşturmak için işlem ve çok noktaya yayın olup olmadığını denetleyin. İşleri biz hallederiz Onaylamalar da onaylar bağlama listeden kaldırmalısınız. Yeniden Svcutil.exe çalıştırırken tümleştirme için iki seçenek vardır:  
  
1. Noktası Svcutil.exe /SvcutilConfig kullanarak bizim yapılandırma dosyasına:\<Dosya >.  
  
2. Yapılandırma bölümü Svcutil.exe.config için Svcutil.exe ile aynı dizinde ekleyin.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Standart bir bağlaması ekleniyor  
 Bizim bağlama öğesi, aşağıdaki iki şekilde kullanılabilir:  
  
- Özel bağlama üzerinden: Özel bağlama bağlama öğeleri bir rastgele kümesi temel alınarak kendi bağlama oluşturmasına olanak tanır.  
  
- Sistem tarafından sağlanan bir bağlamayı kullanarak, bizim bağlama öğesi içerir. Bu sistem tanımlı bağlamalar sayısı gibi sağlar WCF `BasicHttpBinding`, `NetTcpBinding`, ve `WsHttpBinding`. Her biri bu bağlamaları, iyi tanımlanmış bir profili ile ilişkilidir.  
  
 Örnek profili bağlamasında uygulayan `SampleProfileUdpBinding`, öğesinden türetildiğini <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` İçindeki en fazla dört bağlama öğelerini içeren: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, ve `ReliableSessionBindingElement`.  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Özel standart içeri Aktarıcı bağlama ekleme  
 Svcutil.exe ve `WsdlImporter` türü, varsayılan olarak tanır ve sistem tarafından tanımlanan bağlamaları alır. Aksi takdirde, bağlama olarak içeri aktarılan alır bir `CustomBinding` örneği. Svcutil.exe sağlamak ve `WsdlImporter` içeri aktarmak için `SampleProfileUdpBinding` `UdpBindingElementImporter` da bir standart özel bağlama alıcısı davranır.  
  
 Standart özel bağlama içeri Aktarıcı uygulayan `ImportEndpoint` yöntemi `IWsdlImportExtension` incelemek için arabirimi `CustomBinding` , belirli bir standart bağlama tarafından oluşturulmuş olup olmadığını görmek için meta verileri içeri aktarılan örnek.  
  
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
  
 Genellikle, bir özel standart bağlama içeri Aktarıcı uygulama standart bağlama tarafından ayarlanmış olabilir yalnızca özellikleri değiştirildi ve diğer tüm özellikler varsayılan olduğunu doğrulamak için içeri aktarılan bağlama öğeleri özelliklerini denetleme içerir. Standart bağlama içeri Aktarıcı uygulamak için temel bir strateji olan standart bağlama öğesinin bir örneğini oluşturur, standart bağlamayı destekleyen standart bağlama örneği ve karşılaştırma bağlama öğeleri özelliklerinden bağlama yayma içeri aktarılan bağlama öğeleri standart bağlama öğeleri.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Bizim aktarım yapılandırma aracılığıyla kullanıma sunmak için iki yapılandırma bölümlerini uygulamalıdır. İlki bir `BindingElementExtensionElement` için `UdpTransportBindingElement`. Bu şekilde `CustomBinding` uygulamaları, bizim bağlama öğesi başvurabilir. İkinci bir `Configuration` için sunduğumuz `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Bağlama öğesi uzantı öğesi  
 Bölüm `UdpTransportElement` olduğu bir `BindingElementExtensionElement` kullanıma sunan `UdpTransportBindingElement` yapılandırma sistemi için. Birkaç temel geçersiz kılma ile bizim yapılandırma bölümü adı, bizim bağlama öğesi türü ve bizim bağlama öğesi oluşturulacağını tanımlar. Aşağıdaki kodda gösterildiği gibi bir yapılandırma dosyasında şu uzantı bölümümüzde sonra kaydedebilirsiniz.  
  
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
  
 Uzantı UDP taşıma kullanmak için özel bağlamalar başvurulabilir.  
  
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
  
### <a name="binding-section"></a>Bölüm bağlama  
 Bölüm `SampleProfileUdpBindingCollectionElement` olduğu bir `StandardBindingCollectionElement` kullanıma sunan `SampleProfileUdpBinding` yapılandırma sistemi için. Toplu uygulama için temsilci `SampleProfileUdpBindingConfigurationElement`, öğesinden türetildiğini `StandardBindingElement`. `SampleProfileUdpBindingConfigurationElement` Üzerinde özelliklerine karşılık gelen özelliklerle sahip `SampleProfileUdpBinding`ve eşlenecek işlevleri `ConfigurationElement` bağlama. Son olarak, geçersiz kılma `OnApplyConfiguration` yönteminde bizim `SampleProfileUdpBinding`aşağıdaki örnek kodda gösterildiği gibi.  
  
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
  
 Bu işleyici yapılandırma sistemi ile kaydetmek için biz aşağıdaki bölümde ilgili yapılandırma dosyasına ekleyin.  
  
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
  
 ServiceModel Yapılandırma bölümünden sonra başvurulabilir.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>UDP Test hizmet ve istemci  
 Bu örnek aktarım kullanmak için test kodu UdpTestService ve UdpTestClient dizinler kullanılabilir. İki testleri hizmet kodu içerir — bir test koddan bağlamaları ve uç noktaları ayarlar ve diğer yapılandırma aracılığıyla bunu yapar. Her iki testleri iki uç nokta kullanır. Bir uç nokta kullanan `SampleUdpProfileBinding` ile [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) kümesine `true`. Başka bir uç noktası ile özel bir bağlama kullanan `UdpTransportBindingElement`. Bu kullanmaya eşdeğerdir `SampleUdpProfileBinding` ile [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) kümesine `false`. İki test de bir hizmet oluşturmak, her bağlama için bir uç nokta ekleyin, hizmeti açın ve ardından kullanıcının hizmet kapatmadan önce ENTER tuşuna basın bekleyin.  
  
 Hizmeti test uygulamayı başlattığınızda aşağıdaki çıktıyı görmeniz gerekir.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Bu gibi durumlarda, test istemci uygulaması daha sonra yayımlanan uç noktalarına karşı çalıştırabilirsiniz. İstemci test uygulaması her uç nokta için bir istemci oluşturur ve her bir uç nokta için beş iletileri gönderir. İstemcide aşağıdaki çıkış alınır.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Hizmetin tam çıktı verilmiştir.  
  
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
  
 İstemci uygulama uç noktalarına karşı yapılandırmayla yayımlanan çalıştırmak için hizmette ENTER tuşuna basın ve ardından test istemcisinin yeniden çalıştırın. Hizmette aşağıdaki çıktıyı görmeniz gerekir.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 İstemci yeniden çalıştırmayı aynı önceki sonuçları verir.  
  
 İstemci kodu ve Svcutil.exe kullanarak yapılandırmayı yeniden oluşturmak için hizmet uygulamasını başlatın ve ardından örnek kök dizininden aşağıdaki Svcutil.exe'ı çalıştırın.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Bağlama uzantı yapılandırması için svcutil.exe oluşturmaz Not `SampleProfileUdpBinding`, el ile eklemeniz gerekir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Yukarıdaki "UDP Test hizmet ve istemci" bölümüne bakın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
