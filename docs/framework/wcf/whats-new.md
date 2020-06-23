---
title: Windows Communication Foundation 4.5'teki Yenilikler
description: Bu makalede Windows Communication Foundation (WCF) sürüm 4,5 ' in yeni özellikleri ve ek kaynakların bağlantıları açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], what's new
- Windows Communication Foundation [WCF], what's new
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
ms.openlocfilehash: b6ce7fe19a8d7cc00823502e322ee53a1bd0a931
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245628"
---
# <a name="whats-new-in-windows-communication-foundation-45"></a>Windows Communication Foundation 4.5'teki Yenilikler

Bu konuda Windows Communication Foundation (WCF) sürüm 4,5 ' den yeni özellikler açıklanmaktadır.

## <a name="wcf-simplification-features"></a>WCF Kolaylaştırma Özellikleri

WCF 4,5 uygulamalarının geliştirmeyi ve bakımını daha kolay hale getirmek için çok iş yapıldı. Daha fazla bilgi için bkz. [WCF basitleştirme özellikleri](wcf-simplification-features.md).

### <a name="task-based-async-support"></a>Görev tabanlı zaman uyumsuz destek

Varsayılan olarak Hizmet Başvurusu Ekle, görev döndüren zaman uyumsuz hizmet işlemi yöntemleri oluşturur. Bu, hem zaman uyumlu hem de zaman uyumsuz yöntemler için yapılır. Bu, yeni görev tabanlı zaman uyumsuz programlama modelini kullanarak hizmet işlemlerini zaman uyumsuz olarak çağırabilmeniz için izin verir. Oluşturulan proxy yöntemini çağırdığınızda, WCF, zaman uyumsuz işlemi temsil eden bir görev nesnesi oluşturur ve bu görevi size döndürür. İşlem tamamlandığında görev tamamlanır. Zaman uyumsuz bir işlem uygularken, görev tabanlı bir zaman uyumsuz işlem olarak uygulayabilirsiniz. Daha fazla bilgi için bkz. [zaman uyumlu ve zaman uyumsuz işlemler](synchronous-and-asynchronous-operations.md).

### <a name="simplified-generated-configuration-files"></a>Basitleştirilmiş olarak oluşturulan yapılandırma dosyaları

Visual Studio 'da bir hizmet başvurusu eklediğinizde veya SvcUtil.exe aracını kullandığınızda bir istemci yapılandırma dosyası oluşturulur. WCF 'nin önceki sürümlerinde bu yapılandırma dosyaları, değeri varsayılan değer olsa bile her bağlama özelliğinin değerini içerir. WCF 4,5 ' de, oluşturulan yapılandırma dosyaları yalnızca varsayılan olmayan bir değere ayarlanmış olan bağlama özelliklerini içerir.

Daha fazla bilgi için bkz. [WCF basitleştirme özellikleri](wcf-simplification-features.md).

### <a name="contract-first-development"></a>Sözleşme-Ilk geliştirme

WCF artık sözleşmenin ilk geliştirmeyi destekler. svcutil.exe bir WSDL belgesinden hizmet ve veri sözleşmeleri oluşturmanıza olanak sağlayan bir/serviceContract anahtarı vardır.

### <a name="add-service-reference-from-a-portable-subset-project"></a>Taşınabilir alt küme projesinden Hizmet Başvurusu Ekle

Taşınabilir alt küme projeleri, .NET derleme programcılarının tek bir kaynak ağacı ve derleme sistemi ile aynı zamanda birden çok .NET platformunu (Masaüstü, Silverlight, Windows Phone ve Xbox) desteklemeye devam etmektedir. Taşınabilir alt küme projeleri yalnızca .NET platformunda kullanılabilecek derlemeler olan .NET taşınabilir kitaplıklarına başvurur. Geliştirici deneyimi, diğer herhangi bir WCF istemci uygulamasında bir hizmet başvurusu eklemekle aynıdır. Daha fazla bilgi için bkz. [Taşınabilir alt küme projesinde hizmet başvurusu Ekle](add-service-reference-in-a-portable-subset-project.md).

### <a name="aspnet-compatibility-mode-default-changed"></a>ASP.NET uyumluluk modu varsayılan olarak değiştirildi

WCF, geliştiricilere WCF Hizmetleri yazarken ASP.NET HTTP işlem hattının özelliklerine tam erişim sağlamak için ASP.NET uyumluluk modu sağlar. Bu modu kullanmak için, `aspNetCompatibilityEnabled` web.config bölümünde özniteliğini true olarak ayarlamanız gerekir [\<serviceHostingEnvironment>](../configure-apps/file-schema/wcf/servicehostingenvironment.md) . Ayrıca, bu appDomain 'deki herhangi bir hizmetin `RequirementsMode` özelliği <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> veya olarak ayarlanmış olması gerekir <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> . Varsayılan olarak <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> Şu şekilde ayarlanır <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> . Daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](./feature-details/wcf-services-and-aspnet.md).

### <a name="new-transport-default-values"></a>Yeni aktarım varsayılan değerleri

Yapılandırmayı basitleştirmek için, bir dizi Aktarım özelliği varsayılan değeri değişmiştir. Daha fazla bilgi için bkz. [WCF basitleştirme özellikleri](wcf-simplification-features.md).

### <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas>bir ileti oluştururken kodlayıcı tarafından kullanılan bellek miktarını sınırlayan, XML sözlüğü okuyucuları için yapılandırılabilir kota değerleri içerir. Bu kotalar yapılandırılabilir olsa da, varsayılan değerler bir geliştiricinin bunları açıkça ayarlamak zorunda olma olasılığını azaltmak üzere değiştirilmiştir. Daha fazla bilgi için bkz. [WCF basitleştirme özellikleri](wcf-simplification-features.md).

### <a name="wcf-configuration-validation"></a>WCF yapılandırma doğrulaması

Visual Studio içindeki derleme sürecinin bir parçası olarak, WCF yapılandırma dosyaları artık proje içinde tanımlanan öznitelikler için onaylanır. Doğrulama başarısız olursa, Visual Studio 'da doğrulama hatalarının veya uyarıların bir listesi görüntülenir.

### <a name="xml-editor-tooltips"></a>XML Düzenleyici araç Ipuçları

Yeni ve mevcut WCF hizmeti geliştiricilerinin hizmetlerini yapılandırmasına yardımcı olmak için, Visual Studio XML Düzenleyicisi artık her yapılandırma öğesi ve hizmet yapılandırma dosyasının bir parçası olan özellikleri için araç ipuçları sunmaktadır.

## <a name="streaming-improvements"></a>Akış geliştirmeleri

Gönderme tarafı Okunmayan veya yavaş okuma, bu sayede ölçeklenebilirliği arttıran doğru zaman uyumsuz akışa yönelik destek eklendi. İstemci, IIS tarafından barındırılan bir WCF hizmetine akışlı bir ileti gönderdiğinde ileti arabelleğe alma sınırlaması kaldırılmıştır. Daha fazla bilgi için bkz. [WCF basitleştirme özellikleri](wcf-simplification-features.md).

## <a name="simplifying-exposing-an-endpoint-over-https-with-iis"></a>IIS ile HTTPS üzerinden bir uç noktanın açığa çıkarılması basitleşme

Https üzerinden bir uç noktanın sunulmasını kolaylaştırmak için bir HTTPS protokol eşlemesi eklenmiştir. HTTPS uç noktasını etkinleştirmek için, Web sitenizin yapılandırılmış bir HTTPS bağlaması ve SSL sertifikası olduğundan emin olun ve ardından hizmeti barındıran sanal dizin için HTTPS 'yi etkinleştirin. Hizmet için meta veriler etkinleştirilirse, HTTPS üzerinden de kullanıma sunulacaktır.

## <a name="generating-a-single-wsdl-document"></a>Tek bir WSDL belgesi oluşturma

Bazı üçüncü taraf WSDL işlem yığınları, bir xsd: Import aracılığıyla diğer belgelere bağımlılıkları olan WSDL belgelerini işleyemez. WCF artık tüm WSDL bilgilerinin tek bir belgede döndürülmesini belirtmenizi sağlar. Tek bir WSDL belgesi istemek için, hizmetten meta veriler istenirken URI 'ye "? singleWSDL" ekleyin.

## <a name="websocket-support"></a>WebSocket desteği

WebSockets, TCP 'ye benzer performans özellikleriyle 80 ve 443 bağlantı noktaları üzerinden doğru çift yönlü iletişim sağlayan bir teknolojidir. WebSocket aktarımı üzerinden iletişimi desteklemek için iki yeni bağlama eklenmiştir. <xref:System.ServiceModel.NetHttpBinding> ve <xref:System.ServiceModel.NetHttpsBinding>. Daha fazla bilgi için bkz: [sistem tarafından sunulan bağlamalar](system-provided-bindings.md).

## <a name="new-transport-default-values"></a>Yeni aktarım varsayılan değerleri

Aşağıdaki tablo, değişen ayarları ve ek bilgilerin nerede bulunacağını açıklar.

|Özellik|Açık|Yeni varsayılan|Daha fazla bilgi için bkz.|
|--------------|--------|-----------------|------------------------------|
|ChannelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 saniye|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 * işlemci sayısı|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * aktarım için işlemci sayısı<br /><br /> \*SMSvcHost.exe için 4 işlemci sayısı|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> [Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](./feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * işlemci sayısı|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 saniye|[Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](./feature-details/configuring-the-net-tcp-port-sharing-service.md)|

## <a name="xml-editor-tooltips"></a>XML Düzenleyici araç Ipuçları

Yeni ve mevcut WCF hizmeti geliştiricilerinin hizmetlerini yapılandırmasına yardımcı olmak için, Visual Studio XML Düzenleyicisi artık her yapılandırma öğesi ve hizmet yapılandırma dosyasının bir parçası olan özellikleri için araç ipuçları sunmaktadır.

## <a name="configuring-wcf-services-in-code"></a>WCF Hizmetlerini Kodda Yapılandırma

Windows Communication Foundation (WCF), geliştiricilerin yapılandırma dosyalarını veya kodu kullanarak hizmetleri yapılandırmalarına olanak tanır. Yapılandırma dosyaları, bir hizmetin dağıtıldıktan sonra yapılandırılması gerektiğinde faydalıdır. Yapılandırma dosyalarını kullanırken, bir BT uzmanı 'nın yalnızca yapılandırma dosyasını güncelleştirmesi gerekir, yeniden derleme gerekmez. Bununla birlikte yapılandırma dosyaları, karmaşık ve bakım açısından zor olabilir. Yapılandırma dosyalarını hata ayıklama desteği yoktur ve yapılandırma öğeleri, yazma yapılandırma dosyalarını hata-açık ve zor hale getiren adlara göre başvurulur. WCF Ayrıca koddaki Hizmetleri yapılandırmanıza de olanak tanır. WCF 'nin önceki sürümlerinde (4,0 ve önceki sürümler), kodda hizmetleri yapılandırmak kendi kendine barındırılan senaryolarda kolaydır, <xref:System.ServiceModel.ServiceHost> sınıf ServiceHost. Open çağrılmadan önce uç noktaları ve davranışları yapılandırmanıza izin verilir. Ancak, Web 'de barındırılan senaryolarda sınıfına erişiminiz yok <xref:System.ServiceModel.ServiceHost> . Web 'de barındırılan bir hizmeti yapılandırmak için `System.ServiceModel.ServiceHostFactory` , oluşturmuş <xref:System.ServiceModel.Activation.ServiceHostFactory> ve gerekli tüm yapılandırmaları gerçekleştirmiş bir oluşturma gerekiyordu. WCF, .NET 4,5 ile başlayarak, kodda hem şirket içinde barındırılan hem de Web 'de barındırılan Hizmetleri yapılandırmanın daha kolay bir yolunu sunar. Daha fazla bilgi için bkz. [KODDA WCF hizmetlerini yapılandırma](configuring-wcf-services-in-code.md).

## <a name="channelfactory-caching"></a>ChannelFactory önbelleğe alma

WCF istemci uygulamaları, <xref:System.ServiceModel.ChannelFactory%601> BIR WCF hizmeti ile iletişim kanalı oluşturmak için sınıfını kullanır. <xref:System.ServiceModel.ChannelFactory%601>Aşağıdaki işlemleri içerdiğinden örnek oluşturma bazı ek yük doğurur:

1. Ağacı oluşturma <xref:System.ServiceModel.Description.ContractDescription>

2. Tüm gerekli CLR türlerini yansıtma

3. Kanal yığınını oluşturma

4. Kaynakları elden atma

Bu ek yükü en aza indirmenize yardımcı olmak için WCF istemci ara sunucusu kullanırken WCF kanal fabrikalarını önbelleğe alabilir. Daha fazla bilgi için bkz. [kanal fabrikası ve önbelleğe alma](./feature-details/channel-factory-and-caching.md).

## <a name="compression-and-the-binary-encoder"></a>Sıkıştırma ve Ikili kodlayıcı

WCF ikili Kodlayıcısı 4,5 ile başlayarak sıkıştırma için destek ekler. Sıkıştırma türü, özelliği ile yapılandırılır <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> . Hem istemci hem de hizmetin özelliği yapılandırması gerekir <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> . Sıkıştırma, HTTP, HTTPS ve TCP protokolleri için çalışacaktır. Bir istemci sıkıştırma kullanmayı belirtirse, ancak hizmet bunu desteklemiyorsa protokol uyuşmazlığını gösteren bir protokol özel durumu oluşturulur. Daha fazla bilgi için bkz. [Ileti Kodlayıcısı seçme](./feature-details/choosing-a-message-encoder.md).

## <a name="udp"></a>UDP

, Geliştiricilerin "yangın ve unut" iletilerini kullanan hizmetler yazmasına olanak tanıyan bir UDP taşıması için destek eklenmiştir. İstemci, hizmete bir ileti gönderir ve hizmetten yanıt vermez.

## <a name="multiple-authentication-support"></a>Çoklu kimlik doğrulama desteği

HTTP taşıma ve aktarım güvenliği kullanılırken tek bir WCF uç noktasında IIS tarafından desteklenen birden çok kimlik doğrulama modunu desteklemek için destek eklenmiştir. IIS, bir sanal dizinde birden çok kimlik doğrulama modunu etkinleştirmenizi sağlar, bu özellik tek bir WCF uç noktasının, WCF hizmetinin barındırıldığı sanal dizin için etkinleştirilmiş birden çok kimlik doğrulama modunu desteklemesini sağlar.

## <a name="idn-support"></a>IDN desteği

Uluslararası etki alanı adlarıyla WCF hizmetlerine izin vermek için destek eklenmiştir. Daha fazla bilgi için bkz. [WCF ve uluslararası etki alanı adları](./feature-details/wcf-and-internationalized-domain-names.md).

## <a name="httpclient"></a>HttpClient

<xref:System.Net.Http.HttpClient>Http istekleriyle çalışmayı çok daha kolay hale getirmek için çağrılan yeni bir sınıf eklenmiştir. Daha fazla bilgi için bkz. [Uygulamaları Sosyal ve HTTP Hizmetleri ile bağlantılı hale getirme](https://channel9.msdn.com/Events/BUILD/BUILD2011/PLAT-581T) ve [http istemci örneği](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664).

## <a name="configuration-intellisense"></a>Yapılandırma IntelliSense

Projede tanımlanan özel özniteliklerin yapılandırma dosyalarındaki öznitelik değerleri artık yapılandırma ve doğru şekilde çalışmayı kolaylaştırmak için IntelliSense 'i desteklemektedir.

## <a name="configuration-tooltips"></a>Yapılandırma araç ipuçları

WCF öğeleri ve öznitelikleri artık XML düzenleyicisinde araç ipuçlarında olduğundan, öğe veya özniteliğin amacını daha kolay ve doğru bir şekilde tanımlayabilir.

## <a name="paste-data-as-classes"></a>Verileri sınıf olarak Yapıştır

Bir WCF projesinde, XML 'de tanımlanan veri türleri (örneğin, bir hizmette gösterilir) doğrudan bir kod sayfasına yapıştırılabilir. XML türü bir CLR türü olarak yapıştırılacaktır. Daha fazla ayrıntı için bkz. [XML 'Den veri türü sınıfları oluşturma](generating-data-type-classes-from-xml.md) .

## <a name="webservicehost-and-default-endpoints"></a>WebServiceHost ve varsayılan uç noktalar

Visual Studio 2010 ' de WebServiceHost, açıkça bir uç nokta belirtmeksizin otomatik olarak varsayılan bir uç nokta oluşturmuştur. Visual Studio 2012 ve sonraki sürümlerde WebServiceHost yalnızca bir uç nokta açıkça eklendiyse varsayılan bir uç nokta oluşturur. İstemciniz varsayılan uç noktayı bekliyorsanız, açıkça bir uç nokta ekleyebilir ve istemciye işaret edebilirsiniz. Alternatif olarak, uygulamanızın yapılandırma dosyasına aşağıdaki ayarı ekleyerek WCF 'ye önceki davranışa geri geri dönmesini söyleyebilirsiniz.

```xml
<appSettings>
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>
  </appSettings>
```

## <a name="ihttpcookiecontainermanager"></a>Ihttppişiriecontainermanager

Tarafından sunulan bu arabirim, <xref:System.ServiceModel.Channels.IChannelFactory%601> istemci tarafında tanımlama bilgileriyle çalışmayı çok daha kolay hale getirir. AllowCookies bağlamada true olarak ayarlandığında, aşağıdaki kodu kullanarak tanımlama bilgilerine erişebilirsiniz:

```csharp
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();
System.Net.CookieContainer container = cookieManager.CookieContainer;
```

Daha sonra içinden tanımlama bilgilerini alabilir veya ayarlayabilirsiniz <xref:System.Net.CookieContainer> . AllowCookies false olarak ayarlandığında, kullanarak tanımlama bilgilerini el ile alabilir <xref:System.ServiceModel.OperationContext> ve başka bir <xref:System.ServiceModel.OperationContext> veya ileti denetçisi kullanarak diğer isteklere gönderebilirsiniz. Ihttpcookie ıecontainermanager arabirimi, bir hizmetin Kullanıcı kimliğini doğrulayabilmeniz ve diğer hizmetlerle kimlik doğrulaması yapmak için bu hizmet tarafından döndürülen kimlik doğrulama tanımlama bilgisini kullanmanıza olanak sağlar.
