---
title: "Taşıma: UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
caps.latest.revision: "48"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc30a755278251ac9e06f2ddd56e2c369b950af4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transport-udp"></a>Taşıma: UDP
UDP taşıma örnek UDP tek noktaya yayın ve çok noktaya yayın özel olarak uygulamak gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] taşıma. Örnek olarak özel bir taşıma oluşturmak için önerilen yordamı açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], kanal çerçevesi kullanarak ve aşağıdaki [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en iyi uygulamalar. Özel bir taşıma oluşturmaya yönelik adımlar aşağıdaki gibidir:  
  
1.  Kanal karar [ileti Exchange desenleri](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel veya IReplyChannel) ChannelFactory ve ChannelListener destekleyecektir. Daha sonra bu arabirimleri süre sonuyla varyasyonları destekleyecek olup olmadığını karar verin.  
  
2.  Bir kanal fabrikası ve ileti değişim deseni destekleyen dinleyici oluşturun.  
  
3.  Ağa özgü özel durumlar için uygun olan türetilmiş sınıf normalleştirilmiş emin olun <xref:System.ServiceModel.CommunicationException>.  
  
4.  Ekleme bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) bir kanal yığınına özel taşıma ekler öğesi. Daha fazla bilgi için bkz: [bir bağlama öğesi ekleme](#AddingABindingElement).  
  
5.  Yapılandırma sistemi için yeni bir bağlama öğesi kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin.  
  
6.  Diğer uç noktalara Özellikleri iletişim kurmak için meta verileri uzantıları ekleyin.  
  
7.  Bağlama öğeleri iyi tanımlanmış bir profili göre yığınını önceden yapılandırır bir bağlaması ekleyin. Daha fazla bilgi için bkz: [standart bağlama ekleme](#AddingAStandardBinding).  
  
8.  Bir bağlama bölümü ve yapılandırma sistemi bağlamayı kullanıma sunmak için bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için bkz: [yapılandırma desteği ekleme](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>İleti Exchange desenleri  
 İlk adım karar vermek için özel bir taşıma yazılırken hangi ileti Exchange desenleri (MEPs) taşıma için gereklidir. Aralarından seçim yapabileceğiniz üç MEPs vardır:  
  
-   Veri birimi (IInputChannel/IOutputChannel)  
  
     Veri birimi MEP kullanırken, bir istemci "yangın ve unut" exchange kullanarak bir ileti gönderir. A yangın ve exchange başarılı teslimat bant dışı onay gerektiren bir tane olduğunu unutmayın. İleti, geçiş sırasında kaybolur ve hiçbir zaman hizmete erişmek. Gönderme işlemi istemci sonunda başarıyla tamamlarsa, uzak uç noktada bir ileti aldı garanti etmez. Veri birimi üzerine kurallarınızı oluşturabilirsiniz Mesajlaşma için temel yapı bloğu aynıdır — güvenilir protokolleri ve güvenli iletişim kuralları da dahil olmak üzere. İstemci veri birimi kanalları uygulamak <xref:System.ServiceModel.Channels.IOutputChannel> arabirimi ve hizmet veri birimi kanallar uygulamak <xref:System.ServiceModel.Channels.IInputChannel> arabirimi.  
  
-   İstek-yanıt (IRequestChannel/IReplyChannel)  
  
     Bu MEP bir ileti gönderilir ve bir yanıt aldı. Desen istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrıları örnekler uzaktan yordam çağrısı (RPC) ve tarayıcı alır. Bu desen yarı çift yönlü da bilinir. Bu MEP, istemci kanalları uygulamak <xref:System.ServiceModel.Channels.IRequestChannel> ve hizmet kanalları uygulamak <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Çift yönlü (IDuplexChannel)  
  
     Çift yönlü MEP bir rastgele bir istemci tarafından gönderilen ve herhangi bir sırada alınan ileti sayısı için sağlar. Çift yönlü MEP bir telefon konuşması gibi konuşulan her sözcüğün bir ileti olduğu. Her iki tarafında da gönderebilir ve bu MEP alabilir, istemci ve hizmet kanalları tarafından uygulanan arabirimi çünkü <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Her bu MEPs oturumları da destekleyebilir. Oturum durumunu algılayan bir kanal tarafından sağlanan eklenen bir kanalda alınıp gönderilen tüm iletiler karşılık gelen bir işlevdir. İstek-yanıt düzeni istek ve yanıt bağıntısı tek başına iki ileti oturum aynıdır. Buna karşılık, oturumlar destekleyen istek-yanıt düzeni bu kanalda tüm istek/yanıt çiftleri birbiriyle ilişkili anlamına gelir. Bu altı MEPs toplam verir — veri birimi, istek-yanıt, çift yönlü, oturumu, istek-yanıt oturumu, veri birimi ve oturumları ile çift yönlü — aralarından seçim yapabileceğiniz.  
  
> [!NOTE]
>  UDP kendiliğinden "yangın ve unut" protokol UDP taşıma için desteklenen tek MEP Datagram, olduğundan.  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>ICommunicationObject ve WCF nesne yaşam döngüsü  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]yaşam döngüsü gibi nesneleri yönetmek için kullanılan yaygın bir durum makinesinin sahip <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, ve <xref:System.ServiceModel.Channels.IChannelListener> iletişimi için kullanılır. Bu iletişimi nesneleri var olabilir beş durumlar vardır. Bu durumu tarafından temsil edilen <xref:System.ServiceModel.CommunicationState> numaralandırma ve aşağıdaki gibi şunlardır:  
  
-   Oluşturulan: Bu durumda bir <xref:System.ServiceModel.ICommunicationObject> olduğunda, ilk örneği. Bu durumda hiçbir giriş/çıkış (g/ç) oluşur.  
  
-   Açılış: Bu nesneler geçiş durumu ne zaman <xref:System.ServiceModel.ICommunicationObject.Open%2A> olarak adlandırılır. Bu noktada özellikleri değişmez yapılır ve giriş/çıkış başlayabilirsiniz. Bu geçiş oluşturulan durumundan yalnızca geçerli değil.  
  
-   Açılmış: Nesneleri geçiş açma işlemi tamamlandığında bu durumu. Bu geçiş yalnızca açılış durumundan geçerli değil. Bu noktada, nesne aktarımı için tam olarak kullanılabilir.  
  
-   Kapatma: Bu nesneler geçiş durumu ne zaman <xref:System.ServiceModel.ICommunicationObject.Close%2A> normal olarak kapatmak için çağrılır. Bu geçiş yalnızca açık durumundan geçerli değil.  
  
-   Kapalı: kapalı durum nesneleri artık kullanılabilir. Genel olarak, çoğu yapılandırma İnceleme için hala erişilebilir, ancak hiçbir iletişimi ortaya çıkabilir. Bu durum, atıldı için eşdeğerdir.  
  
-   Faulted: Faulted, nesneleri incelemesi için erişilebilir ancak artık kullanılamaz durumda. Nesne bir kurtarılamaz bir hata oluştuğunda, bu duruma geçer. Bu durum yalnızca geçerli geçiş halinde olan `Closed` durumu.  
  
 Her durum geçişi için yangın olay vardır. <xref:System.ServiceModel.ICommunicationObject.Abort%2A> Yöntemi herhangi bir zamanda çağrılabilir ve nesne geçişi hemen geçerli durumunu kapalı duruma neden olur. Çağırma <xref:System.ServiceModel.ICommunicationObject.Abort%2A> tamamlanmamış işlerinizi sonlandırır.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Kanal fabrikası ve kanal dinleyicisi  
 Özel bir taşıma yazma sonraki adım uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> ve istemci kanallar için <xref:System.ServiceModel.Channels.IChannelListener> hizmet kanalları. Kanal katmanını kanallar oluşturmak için bir Fabrika desen kullanır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu işlem için temel sınıfı Yardımcıları sağlar.  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Uygulayan sınıf <xref:System.ServiceModel.ICommunicationObject> ve 2. adımda daha önce açıklanan durum makinesinin uygular. 

-   ''<xref:System.ServiceModel.Channels.ChannelManagerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.CommunicationObject> ve birleştirilmiş bir temel sınıf sağlar <xref:System.ServiceModel.Channels.ChannelFactoryBase> ve <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı çalışır birlikte <xref:System.ServiceModel.Channels.ChannelBase>, uygulayan bir temel sınıfı olan <xref:System.ServiceModel.Channels.IChannel>.  
  
-   ''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> ve birleştirir `CreateChannel` overloads birine `OnCreateChannel` soyut yöntemi.  
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.IChannelListener>. Bu temel durum yönetimini mvc'deki.  
  
 Bu örnekte Üreteç uygulaması UdpChannelFactory.cs içinde yer alır ve dinleyici uygulama UdpChannelListener.cs içinde yer alır. <xref:System.ServiceModel.Channels.IChannel> Uygulamalarıdır UdpOutputChannel.cs ve UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>UDP kanal fabrikası  
 `UdpChannelFactory` Türetilen <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Örnek geçersiz kılmaları <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti Kodlayıcı ileti sürümü erişim sağlamak için. Örnek ayrıca geçersiz kılar <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> böylece biz bizim örneğini kesmeden <xref:System.ServiceModel.Channels.BufferManager> zaman durum makinesinin geçer.  
  
#### <a name="the-udp-output-channel"></a>UDP çıktı kanalı  
 `UdpOutputChannel` Uygulayan <xref:System.ServiceModel.Channels.IOutputChannel>. Oluşturucu bağımsız değişkenleri doğrular ve bir hedef oluşturur <xref:System.Net.EndPoint> nesne temel alarak <xref:System.ServiceModel.EndpointAddress> olarak geçirilir.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanal düzgün biçimde veya ungracefully kapatılabilir. Kanal düzgün biçimde kapalıysa yuva kapatılır ve taban sınıfı için bir çağrı yapılır `OnClose` yöntemi. Bu bir özel durum oluşturursa, altyapı çağırır `Abort` kanal emin olmak için temizlendi.  
  
```csharp
this.socket.Close(0);  
```  
  
 Ardından uygulamak `Send()` ve `BeginSend()` / `EndSend()`. Bu iki ana bölüme parçalara ayırır. İlk biz ileti bir bayt dizisine serileştirir.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Ardından size sonuç verileri kablo göndereceğiz.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  
 '' Örnek uygulayan UdpChannelListener türer <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfı. Veri birimleri almak için tek bir UDP yuva kullanır. `OnOpen` Yöntemi zaman uyumsuz bir döngü UDP yuvaya kullanarak verileri alır. Veri kodlaması ileti Framework kullanarak iletilere sonra dönüştürülür.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Bir dizi kaynaktan, gelen iletileri aynı veri birimi kanal olabilmesinden dolayı `UdpChannelListener` bir singleton dinleyicisi. Yoktur, çoğu, bir etkin <xref:System.ServiceModel.Channels.IChannel>'' aynı anda bu dinleyicisi ile ilişkilendirilmiş. Tarafından döndürülen bir kanal, başka bir örnek oluşturur `AcceptChannel` yöntemi sonradan atıldı. Bir ileti alındığında, sıraya alınan bu singleton kanal içine var.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` Uygulayan sınıf `IInputChannel`. Tarafından doldurulur gelen iletileri kuyruğunu oluşan `UdpChannelListener`kullanıcının yuva. Tarafından bu iletilerin kuyruktan çıkarıldı `IInputChannel.Receive` yöntemi.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Bir bağlama öğesi ekleme  
 Fabrikaları ve kanallar yerleşik, biz bunları ServiceModel çalışma zamanı için bir bağlama aracılığıyla kullanıma gerekir. Bir bağlama hizmeti adresi ile ilişkili iletişim yığını temsil eden bağlama öğelerinin bir koleksiyondur. Yığındaki her öğe tarafından temsil edilen bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi.  
  
 Örnekte, bağlama öğedir `UdpTransportBindingElement`, den türetilen <xref:System.ServiceModel.Channels.TransportBindingElement>. Bu bizim bağlama ile ilişkili oluşturucuları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
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
  
 Kopyalama için de üyeleri içeren `BindingElement` ve bizim düzenini (soap.udp) döndürüyor.  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Bağlama öğesi bir taşıma için meta verileri desteği ekleme  
 Bizim aktarım meta verileri sistemle tümleştirmek için biz içeri ve dışarı aktarma İlkesi desteklemesi gerekir. Bu bizim bağlama aracılığıyla istemcileri oluşturmak için bize sağlar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>WSDL desteği ekleme  
 Bir bağlama aktarım bağlama öğe meta verileri adresleme bilgilerini alma ve verme sorumludur. SOAP bağlama kullanırken, aktarım bağlama öğesi de meta verilerde doğru taşıma URI dışarı aktarmanız gerekir.  
  
#### <a name="wsdl-export"></a>WSDL dışarı aktarma  
 Adresleme bilgilerini dışarı aktarmak için `UdpTransportBindingElement` uygulayan `IWsdlExportExtension` arabirimi. `ExportEndpoint` Yöntemi WSDL bağlantı noktasına doğru adresleme bilgilerini ekler.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Uyarlamasını `ExportEndpoint` yöntemi uç nokta bir SOAP bağlama kullandığında taşıma URI ayrıca verir.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL içe aktarma  
 Adres alma işlemek için WSDL içe aktarma sistemini genişletmek için size aşağıdaki yapılandırma yapılandırma dosyasına için Svcutil.exe Svcutil.exe.config dosyasında gösterildiği gibi eklemeniz gerekir.  
  
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
  
 Svcutil.exe çalıştırırken WSDL içe aktarma Uzantıları'nı yüklemek için Svcutil.exe alma için iki seçeneğiniz vardır:  
  
1.  /SvcutilConfig kullanarak bizim yapılandırma dosyasına noktası Svcutil.exe:\<Dosya >.  
  
2.  Yapılandırma bölümü için Svcutil.exe.config Svcutil.exe ile aynı dizinde ekleyin.  
  
 `UdpBindingElementImporter` Yazın uygulayan `IWsdlImportExtension` arabirimi. `ImportEndpoint` Yöntemi WSDL bağlantı noktasından adresi alır.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>İlke desteği ekleme  
 Özel bağlama öğesi bu bağlama öğesi özelliklerini ifade etmek için bir hizmet uç noktası için WSDL bağlama ilke onaylamalarını dışa aktarabilirsiniz.  
  
#### <a name="policy-export"></a>İlke verme  
 `UdpTransportBindingElement` Yazın uygulayan `IPolicyExportExtension` İlkesi dışarı aktarma desteği eklemek için. Sonuç olarak, `System.ServiceModel.MetadataExporter` içeren `UdpTransportBindingElement` içerdiği bağlama için ilke oluşturma.  
  
 İçinde `IPolicyExportExtension.ExportPolicy`, biz çok noktaya yayın modunda olduğunda bir onaylama UDP ve başka bir onaylama için ekleriz. Çok noktaya yayın modu etkilediğinden nasıl iletişim yığını oluşturulur ve böylece her iki yüz arasındaki Eşgüdümlü olmalıdır budur.  
  
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
  
 Özel Aktarım bağlama öğeleriyle adresleme, işleme için sorumlu olduğu için `IPolicyExportExtension` mantığınız `UdpTransportBindingElement` WS adresleme sürümünü belirtmek için uygun WS adresleme ilke onaylamalarını dışa aktarma işlemesi gerekir kullanılan.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>İlke içeri aktarma  
 İlke içeri aktarma sistemini genişletmek için size aşağıdaki yapılandırma yapılandırma dosyasına Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için eklemeniz gerekir.  
  
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
  
 Biz uygulamak sonra `IPolicyImporterExtension` bizim kayıtlı sınıfından (`UdpBindingElementImporter`). İçinde `ImportPolicy()`, biz onaylar bizim ad alanında arayın ve taşıma oluşturmak için olanları işlemek ve çok noktaya yayın olup olmadığını denetleyin. İşleme onaylar de onaylar bağlama listeden kaldırmalısınız. Yeniden Svcutil.exe çalıştırırken, tümleştirme için iki seçenek vardır:  
  
1.  /SvcutilConfig kullanarak bizim yapılandırma dosyasına noktası Svcutil.exe:\<Dosya >.  
  
2.  Yapılandırma bölümü için Svcutil.exe.config Svcutil.exe ile aynı dizinde ekleyin.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Standart bir bağlama ekleme  
 Bizim bağlama öğesi aşağıdaki iki yolla kullanılabilir:  
  
-   Özel bağlama üzerinden: özel bağlama bağlama öğelerinin bir rastgele kümesini temel alan kendi bağlama oluşturmasına olanak tanır.  
  
-   Sistem tarafından sağlanan bir bağlamayı kullanarak, bizim bağlama öğesi içerir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu sistem tarafından tanımlanan bağlama sayısı gibi sağlar `BasicHttpBinding`, `NetTcpBinding`, ve `WsHttpBinding`. Bu bağlamaların her iyi tanımlanmış bir profili ile ilişkilendirilmiş.  
  
 Örnek profil bağlamasında uygulayan `SampleProfileUdpBinding`, den türetilen <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` İçindeki en fazla dört bağlama öğeleri içerir: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, ve `ReliableSessionBindingElement`.  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>İçeri Aktarıcı bağlama özel bir standart ekleme  
 Svcutil.exe ve `WsdlImporter` türü, varsayılan olarak, tanır ve sistem tanımlı bağlamalar alır. Aksi takdirde, bağlama içeri alır bir `CustomBinding` örneği. Svcutil.exe etkinleştirmek için ve `WsdlImporter` almak için `SampleProfileUdpBinding` `UdpBindingElementImporter` da özel standart bağlama alıcısı davranır.  
  
 Özel standart bağlama alma uygulayan `ImportEndpoint` yöntemi `IWsdlImportExtension` incelemek için arabirimi `CustomBinding` , belirli bir standart bağlama tarafından oluşturulmuş olup olmadığını görmek için meta verileri içe örneği.  
  
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
  
 Genellikle, özel standart bağlama alma uygulama standart bağlama tarafından ayarlayabilirsiniz yalnızca özellikleri değişti ve diğer tüm özellikleri varsayılanlarına olduğunu doğrulamak için içe aktarılan bağlama öğeleri özelliklerini denetleme içerir. Standart bağlama alma uygulamak için bir temel stratejidir standart bağlama örneği oluşturmak için bağlama öğeleri özelliklerinden standart bağlama destekler standart bağlama örneği ve karşılaştırmak için bağlama yayma içeri aktarılan bağlama öğeleri ile standart bağlama öğeleri.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Bizim aktarım yapılandırma yoluyla kullanıma sunmak için iki yapılandırma bölümlerinin uygulamalıdır. İlki bir `BindingElementExtensionElement` için `UdpTransportBindingElement`. Bu şekilde `CustomBinding` uygulamaları bizim bağlama öğesi başvurusu. İkinci bir `Configuration` için bizim `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Bağlama öğesi uzantısı öğesi  
 Bölüm `UdpTransportElement` olan bir `BindingElementExtensionElement` kullanıma sunan `UdpTransportBindingElement` yapılandırma sistemi. Birkaç temel geçersiz kılmalar, bizim yapılandırma bölümü adı, bizim bağlama öğesi türü ve bizim bağlama öğesi oluşturmak nasıl tanımlayın. Aşağıdaki kodda gösterildiği gibi bir yapılandırma dosyasına biz bizim uzantısı bölümüne sonra kaydedebilirsiniz.  
  
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
  
 Uzantı UDP taşıma olarak kullanmak için özel bağlamalar başvurulabilir.  
  
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
 Bölüm `SampleProfileUdpBindingCollectionElement` olan bir `StandardBindingCollectionElement` kullanıma sunan `SampleProfileUdpBinding` yapılandırma sistemi. Uygulama toplu temsilci için `SampleProfileUdpBindingConfigurationElement`, den türetilen `StandardBindingElement`. `SampleProfileUdpBindingConfigurationElement` Özellikler üzerinde karşılık gelen özelliklere sahip `SampleProfileUdpBinding`ve eşlenecek işlevleri `ConfigurationElement` bağlama. Son olarak, geçersiz kılma `OnApplyConfiguration` yönteminde bizim `SampleProfileUdpBinding`, aşağıdaki örnek kodda gösterildiği gibi.  
  
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
  
 Bu işleyici yapılandırma sistemi ile kaydetmek için aşağıdaki bölümde ilgili yapılandırma dosyasına ekleriz.  
  
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
  
 ServiceModel yapılandırması bölümünden sonra başvuruda bulunulabilir.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>İstemci ve UDP Test hizmeti  
 Bu örnek aktarım kullanmak için test kodu UdpTestService ve UdpTestClient dizinler kullanılabilir. Hizmet koduna iki sınamaları oluşur — bir test koddan bağlamalar ve uç noktaları ayarlar ve diğer yapılandırma aracılığıyla yapar. Her iki testleri iki uç nokta kullanın. Bir uç nokta kullanan `SampleUdpProfileBinding` ile [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) kümesine `true`. Diğer uç nokta ile özel bağlama kullanan `UdpTransportBindingElement`. Bu kullanmaya eşdeğerdir `SampleUdpProfileBinding` ile [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) kümesine `false`. Her iki testleri bir hizmet oluşturmak, her bağlama için bir uç nokta ekleyin, hizmeti açın ve sonra kullanıcıya hizmet kapatmadan önce ENTER tuşuna basın bekler.  
  
 Hizmet test uygulaması başlattığınızda aşağıdaki çıktı görmeniz gerekir.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Bu gibi durumlarda, sınama istemci uygulaması sonra yayımlanan uç noktalarına karşı çalıştırabilirsiniz. İstemci test uygulaması her uç nokta için bir istemci oluşturur ve beş iletileri her uç noktasına gönderir. Aşağıdaki çıkış istemcide ' dir.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Hizmet tam çıktı verilmiştir.  
  
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
  
 İstemci uygulaması yapılandırması'nı kullanarak yayımlanan uç noktalarına karşı çalıştırmak için hizmeti üzerinde ENTER tuşuna basın ve test istemcisi yeniden çalıştırın. Hizmette şu çıktı görmeniz gerekir.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 İstemci yeniden çalışan aynı önceki sonuçları verir.  
  
 İstemci kodu ve Svcutil.exe kullanarak yapılandırmayı yeniden oluşturmak için hizmet uygulamasını başlatın ve sonra aşağıdaki Svcutil.exe örnek kök dizininden çalıştırın.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Svcutil.exe bağlama uzantısı yapılandırması oluşturmaz Not `SampleProfileUdpBinding`, el ile eklemeniz gerekir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Yukarıdaki "UDP Test hizmet ve istemci" bölümüne bakın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
