---
title: Hangi&#39;s Windows Communication Foundation 4.5'deki yenilikler
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], what's new
- Windows Communication Foundation [WCF], what's new
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
ms.openlocfilehash: 008bfb0042d31c7fbd1e853ba3ead4c1247dfa7c
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027372"
---
# <a name="whats-new-in-windows-communication-foundation-45"></a>Windows Communication Foundation 4.5'teki Yenilikler

Bu konu, Windows Communication Foundation (WCF) sürüm 4.5 için yeni özellikleri açıklar.

## <a name="wcf-simplification-features"></a>WCF Kolaylaştırma Özellikleri
 Kadar iş 4.5 WCF uygulamaları geliştirin ve sürdürmek daha kolay hale getirmek için yapılmıştır. Daha fazla bilgi için [WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md).

### <a name="task-based-async-support"></a>Görev tabanlı zaman uyumsuz desteği
 Varsayılan olarak, görev döndüren zaman uyumsuz hizmet işlemi yöntemleri hizmet Başvurusu Ekle oluşturur. Bu, zaman uyumlu ve zaman uyumsuz yöntemler için gerçekleştirilir. Bu, zaman uyumsuz olarak yeni görev tabanlı zaman uyumsuz programlama modeli kullanarak hizmet işlemlerini aramak üzere sağlar. Oluşturulan proxy yöntemi çağırdığınızda, WCF, görevi döndürür ve zaman uyumsuz işlemi temsil etmek için bir görev nesnesi oluşturur. İşlem tamamlandığında, görev tamamlanır.  Zaman uyumsuz bir işlemi uygulanırken görev tabanlı zaman uyumsuz işlem olarak uygulayabilirsiniz. Daha fazla bilgi edinmek, [zaman uyumlu ve zaman uyumsuz işlemler](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).

### <a name="simplified-generated-configuration-files"></a>Üretilen yapılandırma dosyalarını Basitleştirilmiş
 Visual Studio'da hizmet başvurusu eklemek veya SvcUtil.exe aracını kullandığınızda, bir istemci yapılandırma dosyası oluşturulur. Değerini varsayılan değer olsa bile WCF önceki sürümlerinde, bu yapılandırma dosyaları her bağlama özelliğinin değeri içeriyor. WCF 4.5 içinde oluşturulan yapılandırma dosyaları varsayılan olmayan bir değere ayarlanmış olan bağlama özellikleri içerir.

 Daha fazla bilgi için [WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md)

### <a name="contract-first-development"></a>Sözleşme ilk geliştirmesi
 WCF sözleşme ilk geliştirmesi için destek sunuyor. WSDL belgesinden hizmet ve veri anlaşmaları Oluştur olanak tanıyan bir /serviceContract anahtar svcutl.exe sahiptir.

### <a name="add-service-reference-from-a-portable-subset-project"></a>Bir taşınabilir alt küme projesine hizmet Başvurusu Ekle
 Taşınabilir alt küme projeleri bir tek kaynak ağacının Bakımı ve birden çok .NET Platformu (Masaüstü, Silverlight, Windows Phone ve XBOX) hala desteklerken yapı sistemi .NET derleme programcılar etkinleştirin. Taşınabilir alt küme projeleri yalnızca herhangi bir .NET platformda kullanılabilir bir .NET framework derlemesi olan bir .NET taşınabilir kitaplıklar başvuru. Bir geliştirici deneyimi başka bir WCF istemcisi uygulama içinde bir hizmet başvurusu ekleme aynıdır. Daha fazla bilgi için [içinde bir taşınabilir alt küme projesine hizmet Başvurusu Ekle](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).

### <a name="aspnet-compatibility-mode-default-changed"></a>ASP.NET uyumluluğu modu varsayılan değiştirildi
 WCF geliştiricileri WCF hizmetleri yazarken ASP.NET HTTP ardışık düzen özelliklerine tam erişim vermek için ASP.NET uyumluluk modunun sağlar. Bu modu kullanabilmek için ayarlamanız gerekir `aspNetCompatibilityEnabled` özniteliği true olarak [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) web.config Bölümü. Ayrıca, bu uygulama etki alanında bulunan bir hizmet olması gerekir `RequirementsMode` özelliği, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> kümesine <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Varsayılan olarak <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> artık ayarlanır <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>. Daha fazla bilgi için [Windows Communication Foundation'da yenilikler](../../../docs/framework/wcf/whats-new.md) ve [WCF hizmetleri ve ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).

### <a name="new-transport-default-values"></a>Yeni aktarım varsayılan değerler
 Birkaç aktarım özelliği varsayılan değerleri değiştirilmiş yapılandırma basitleştirmek için. Daha fazla bilgi için [WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md).

### <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
 <xref:System.Xml.XmlDictionaryReaderQuotas> XML sözlük okuyucularına olduğu bir ileti oluşturulurken bir kodlayıcı tarafından kullanılan bellek miktarını sınırlamak için yapılandırılabilir kota değerlerini içerir. Bu kotalar yapılandırılabilir olsa da, açıkça ayarlamak için bir geliştirici olacak olasılığını azaltmak için varsayılan değerleri değişti. Daha fazla bilgi için [WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md).

### <a name="wcf-configuration-validation"></a>WCF yapılandırma doğrulama
 Visual Studio içinden yapı işleminin bir parçası olarak WCF yapılandırma dosyalarının projede tanımlanan öznitelikleri için artık doğrulandı. Doğrulama başarısız olursa doğrulama hataları veya uyarılar listesini Visual Studio'da görüntülenir.

### <a name="xml-editor-tooltips"></a>XML Düzenleyicisi araç ipuçları
 Hizmetlerini yapılandırmak için yeni ve var olan WCF hizmet geliştiricileri yardımcı olmak amacıyla, Visual Studio XML Düzenleyicisi artık araç ipuçları her yapılandırma öğesi ve hizmet yapılandırma dosyasının bir parçası olan özellikleri sağlar.

## <a name="streaming-improvements"></a>Akış geliştirmeleri
 Doğru zaman uyumsuz burada gönderme tarafı artık değil alma tarafında değil okunuyorsa iş parçacığı engelleme veya böylece ölçeklenebilirliği artırır okuma yavaş akış için destek eklendi. Bir istemci akış iletiye bir IIS barındırılan WCF hizmet gönderdiğinde, bir iletiyi arabelleğe sınırlama kaldırılır. Daha fazla bilgi için [WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md).

## <a name="simplifying-exposing-an-endpoint-over-https-with-iis"></a>IIS ile HTTPS üzerinden bir uç nokta gösterme basitleştirme
 Bir uç nokta HTTPS üzerinden gösterme basitleştirmek için bir HTTPS protokolü eşlemesi eklendi. Bir HTTPS uç noktasını etkinleştirmek için Web sitenizi bir HTTPS bağlama ve SSL sertifikası yapılandırılmış olduğundan emin olun ve sonra yalnızca HTTPS hizmetini barındıran sanal dizin için etkinleştirin. Meta veri hizmeti için etkin olduğunda, HTTPS üzerinden de sunulur.

## <a name="generating-a-single-wsdl-document"></a>Tek bir WSDL belgesi oluşturulurken
 Bazı üçüncü taraf WSDL işleme yığınları diğer belgelerde bir import aracılığıyla bağımlılıkları olan WSDL belgeleri işlemek mümkün değildir.  WCF artık tüm WSDL bilgileri tek bir belge içinde döndürülmesi belirtmenize olanak verir. Tek bir WSDL belgesi ekleme istemek için "? singleWSDL" meta veri hizmetinden isterken URI.

## <a name="websocket-support"></a>WebSocket desteği
 WebSockets, 80 ve 443 bağlantı noktaları üzerinden TCP için benzer performans özelliklerini doğru çift yönlü iletişimi sağlayan bir teknolojidir. İki yeni bağlamalar iletişim WebSocket aktarımı üzerinden desteklemek üzere eklendi. <xref:System.ServiceModel.NetHttpBinding> ve <xref:System.ServiceModel.NetHttpsBinding>. Daha fazla bilgi için bkz: [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="new-transport-default-values"></a>Yeni aktarım varsayılan değerler
 Aşağıdaki tabloda, değişen ayarlar ve ek bilgilerin nerede bulunacağı açıklanır.

|Özellik|Açık|Yeni varsayılan|Daha fazla bilgi için bkz|
|--------------|--------|-----------------|------------------------------|
|ChannelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 saniye|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 * işlemci sayısı|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * taşıma için İşlemci sayısı<br /><br /> 4 \* SMSvcHost.exe işlemci sayısı|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> [Net.TCP bağlantı noktası hizmetini yapılandırma](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * işlemci sayısı|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 saniye|[Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|

## <a name="xml-editor-tooltips"></a>XML Düzenleyicisi araç ipuçları
 Hizmetlerini yapılandırmak için yeni ve var olan WCF hizmet geliştiricileri yardımcı olmak amacıyla, Visual Studio XML Düzenleyicisi artık araç ipuçları her yapılandırma öğesi ve hizmet yapılandırma dosyasının bir parçası olan özellikleri sağlar.

## <a name="configuring-wcf-services-in-code"></a>WCF Hizmetlerini Kodda Yapılandırma
 Windows Communication Foundation (WCF) hizmetlerini yapılandırma dosyalarının veya kod kullanarak yapılandırmak geliştiricilerin sağlar.  Yapılandırma dosyalarını, hizmet dağıtıldıktan sonra yapılandırılması gerektiğinde kullanışlıdır. Yapılandırma dosyalarını kullanarak, bir BT Uzmanı yalnızca yapılandırma dosyasını güncelleştirmeniz gerekir, hiçbir yeniden derleme gereklidir. Yapılandırma dosyaları, ancak karmaşık ve sürdürülmesi zor olabilir. Yapılandırma dosyalarında hata ayıklama desteği yoktur ve yapılandırma öğelerini yazma yapılandırma dosyalarını zor ve hata yapmaya açık olmasını sağlayan adlarına göre başvuru yapılır. WCF hizmetlerini kodda yapılandırma sağlar. Önceki sürümlerinde (4.0 ve daha önceki) WCF yapılandırma Hizmetleri kod kendinden senaryolarda kolaydı <xref:System.ServiceModel.ServiceHost> uç noktalar ve davranışlar ServiceHost.Open çağırmadan önce yapılandırmanıza izin sınıfı. Barındırılan web senaryolarda, ancak erişiminiz yoksa <xref:System.ServiceModel.ServiceHost> sınıfı. Barındırılan hizmet oluşturmak için gerekli bir web yapılandırmak için bir `System.ServiceModel.ServiceHostFactory` oluşturulan <xref:System.ServiceModel.Activation.ServiceHostFactory> ve tüm gerekli yapılandırma. .NET 4.5 ile başlayarak, her ikisi de yapılandırmak için daha kolay bir yolu şirket içinde barındırılan ve web hizmetleri kod barındırılan WCF sağlar. Daha fazla bilgi için [yapılandırma WCF hizmetlerini kodda](../../../docs/framework/wcf/configuring-wcf-services-in-code.md).

## <a name="channelfactory-caching"></a>ChannelFactory önbelleğe alma
 WCF istemci uygulamalarının kullanın <xref:System.ServiceModel.ChannelFactory%601> bir WCF Hizmeti ile bir iletişim kanalı oluşturmak için sınıf.  Oluşturma <xref:System.ServiceModel.ChannelFactory%601> örnekleri aşağıdaki işlemleri içerdiğinden bazı ek yük doğurur:

1.  Oluşturma <xref:System.ServiceModel.Description.ContractDescription> ağacı

2.  Tüm gerekli CLR Türleri yansıtma

3.  Kanal yığını oluşturma

4.  Kaynaklarını atma

 WCF bu ek yükü en aza indirmek için bir WCF istemci proxy kullanırken kanal fabrikaları önbelleğe alabilir. Daha fazla bilgi için [kanal fabrikası ve önbelleğe alma](../../../docs/framework/wcf/feature-details/channel-factory-and-caching.md).

## <a name="compression-and-the-binary-encoder"></a>Sıkıştırma ve ikili kodlayıcı
 WCF 4.5 ile başlayarak WCF ikili Kodlayıcı sıkıştırma desteği ekler. Sıkıştırma türünü yapılandırılmış <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> özelliği. Hem istemci hem de hizmet yapılandırmalısınız <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> özelliği. Sıkıştırma için HTTP, HTTPS ve TCP protokollerini çalışır. Sıkıştırma kullanmak için bir istemci belirtiyor, ancak hizmet desteklemiyor, bir protokol uyumsuzluğu belirten bir protokol özel durum oluşturulur. Daha fazla bilgi için [ileti Kodlayıcı seçme](../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)

## <a name="udp"></a>UDP
 Geliştiriciler "Başlat ve unut" kullanan hizmetler yazmasına izin veren bir UDP taşıma için destek eklenmiştir Mesajlaşma. Bir istemci bir hizmete ileti gönderir ve hizmetten yanıt bekliyor.

## <a name="multiple-authentication-support"></a>Çoklu kimlik desteği
 Destek IIS tarafından desteklenen HTTP taşıma ve Taşım güvenliği kullanıldığında tek bir WCF uç nokta üzerinde birden fazla kimlik doğrulama modlarını desteklemek için eklendi. IIS sanal dizininde birden fazla kimlik doğrulama modları etkinleştirmenize olanak sağlar, bu özelliği etkinleştirilmiş WCF Hizmeti barındırıldığı sanal dizin için birden çok kimlik doğrulama modlarını desteklemek tek bir WCF uç nokta sağlar.

## <a name="idn-support"></a>IDN desteği
 Uluslararası yapılan etki alanı adları ile WCF hizmetleri için izin vermek için destek eklendi. Daha fazla bilgi için [WCF ve Uluslararası yapılan etki adlarını](../../../docs/framework/wcf/feature-details/wcf-and-internationalized-domain-names.md).

## <a name="httpclient"></a>HttpClient
 Yeni bir sınıfa <xref:System.Net.Http.HttpClient> HTTP isteklerini çalışmak çok daha kolay hale getirmek için eklendi. Daha fazla bilgi için bkz. [sosyal ve HTTP Hizmetleri ile bağlı uygulama oluşturmaya](https://go.microsoft.com/fwlink/?LinkId=231886) ve [HTTP istemci örneği](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664).

## <a name="configuration-intellisense"></a>Yapılandırma IntelliSense
 Yapılandırma dosyalarında özel öznitelikler için öznitelik değerleri projede yapılandırmaları ile hızlı ve doğru çalışma kolaylaştırmak için IntelliSense desteği artık tanımlanan.

## <a name="configuration-tooltips"></a>Yapılandırma ipuçları
 WCF öğeler ve öznitelikler artık daha kolay XML düzenleyicisinde, araç ipuçları için sahip ve öğe veya öznitelik amacını doğru şekilde belirlemek.

## <a name="paste-data-as-classes"></a>Veri sınıflar Yapıştır
 Bir WCF projesinde XML dosyasında tanımlanan veri türleri (bir hizmet olarak sunulan gibi) doğrudan kod sayfasına yapıştırılabilir. XML türü bir CLR türü olarak yapıştırılır. Bkz: [XML veri türü sınıfları oluşturma](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md) daha fazla ayrıntı için.

## <a name="webservicehost-and-default-endpoints"></a>WebServiceHost ve varsayılan uç noktaları
 Visual Studio 2010'da, açıkça bir uç nokta veya belirttiğiniz olup olmadığını WebServiceHost varsayılan uç noktası otomatik olarak oluşturulur. Uç nokta açıkça eklenirse, Visual Studio 2012 ve sonraki sürümlerinde, WebServiceHost yalnızca bir varsayılan uç noktası oluşturur. İstemciniz, özellikle yapabilecekleriniz varsayılan uç nokta bir uç nokta ekleyin ve istemci üzerine Bekleniyor durumunda. Alternatif olarak, aşağıdaki ayar, uygulamanın yapılandırma dosyasına ekleyerek önceki davranışı için geri dönmek için WCF söyleyebilirsiniz.

```xml
<appSettings>
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>
  </appSettings>
```

## <a name="ihttpcookiecontainermanager"></a>IHttpCookieContainerManager
 Bu arabirim tarafından sunulan, <xref:System.ServiceModel.Channels.IChannelFactory%601>, istemci tarafında tanımlama bilgileriyle çok daha kolay çalışma yapar. AllowCookies ayarlandığında bağlama üzerinde true, tanımlama bilgileri aşağıdaki kodu kullanarak erişebilirsiniz:

```csharp
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();
System.Net.CookieContainer container = cookieManager.CookieContainer;
```

 Ardından alınamıyor veya ayarlanamıyor tanımlama bilgilerini <xref:System.Net.CookieContainer>. AllowCookies false olarak ayarlandığında, el ile kullanarak tanımlama bilgilerinizi alabilirsiniz <xref:System.ServiceModel.OperationContext> ve başka bir diğer isteklerde göndermek <xref:System.ServiceModel.OperationContext> veya ileti denetleyici. IHttpCookieContainerManager arabirimi, bir hizmeti ile bir kullanıcının kimliğini doğrulamak ve diğer hizmetleri ile kimlik doğrulaması için bu hizmet tarafından döndürülen kimlik doğrulama tanımlama bilgisi kullanmanıza olanak sağlar.
