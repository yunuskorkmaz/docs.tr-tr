---
title: '&#39; teki Windows Communication Foundation 4.5''deki yenilikler'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], what's new
- Windows Communication Foundation [WCF], what's new
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
caps.latest.revision: "35"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8e023c71cb59948c9d267dc19db62ebbd1b4512a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="what39s-new-in-windows-communication-foundation-45"></a>&#39; teki Windows Communication Foundation 4.5'deki yenilikler
Bu konuda yeni özellikler ele alınmıştır [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## <a name="wcf-simplification-features"></a>WCF Kolaylaştırma Özellikleri  
 Çok iş, WCF 4.5 uygulamaları geliştirmek ve bakımını kolaylaştırmak için yapılır. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### <a name="task-based-async-support"></a>Görev tabanlı zaman uyumsuz desteği  
 Varsayılan olarak, hizmet Başvurusu Ekle görev döndüren zaman uyumsuz hizmet işlemi yöntemleri oluşturur. Bu, zaman uyumlu ve zaman uyumsuz yöntemleri için gerçekleştirilir. Bu, zaman uyumsuz olarak yeni görev tabanlı zaman uyumsuz programlama modeli kullanarak hizmet işlemlerini çağırma olanak sağlar. Oluşturulan proxy yöntemini çağırdığınızda, WCF görev döndürür ve zaman uyumsuz işlem size göstermek için bir görev nesnesi oluşturur. İşlem tamamlandığında görev tamamlar.  Zaman uyumsuz bir işlem uygularken, bir görev tabanlı zaman uyumsuz işlem olarak uygulayabilirsiniz. Daha fazla bilgi için [zaman uyumlu ve zaman uyumsuz işlemleri](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
### <a name="simplified-generated-configuration-files"></a>Basitleştirilmiş üretilen yapılandırma dosyaları  
 Visual Studio'da hizmet Başvurusu Ekle veya SvcUtil.exe Aracı'nı kullandığınızda, bir istemci yapılandırma dosyası oluşturulur. Değerini varsayılan değer olsa bile WCF önceki sürümlerinde bu yapılandırma dosyalarını her bağlama özelliğinin değeri içeriyor. WCF 4.5 üretilen yapılandırma dosyaları için varsayılan olmayan bir değer ayarlandığını bağlama özellikleri içerir.  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md)  
  
### <a name="contract-first-development"></a>Önce anlaşma geliştirme  
 WCF sözleşmesi ilk geliştirme desteği artık sahiptir. Svcutl.exe hizmeti ve veri sözleşmeleri WSDL belgeden oluşturmanıza olanak sağlayan bir /serviceContract anahtar vardır.  
  
### <a name="add-service-reference-from-a-portable-subset-project"></a>Taşınabilir alt küme projesine hizmet Başvurusu Ekle  
 Taşınabilir alt projeleri .NET derleme programcıların tek kaynak ağaç korumak ve birden çok .NET Platformu (Masaüstü, Silverlight, Windows Phone ve XBOX) hala desteklerken oluşturma sistemi etkinleştirin. Taşınabilir alt projeleri yalnızca herhangi bir .NET platformda kullanılabilir bir .NET framework derlemesi olan .NET taşınabilir kitaplıklara başvuru. Geliştirici deneyimi başka bir WCF istemcisi uygulama içinde bir hizmet başvurusu ekleme aynıdır. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Bir taşınabilir alt küme projesine hizmet Başvurusu Ekle](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).  
  
### <a name="aspnet-compatibility-mode-default-changed"></a>ASP.NET uyumluluğu modu varsayılan değiştirildi  
 WCF WCF hizmetleri yazılırken geliştiriciler ASP.NET HTTP ardışık düzen yer alan özelliklerin tam erişim vermek için ASP.NET uyumluluk modu sağlar. Bu modu kullanmak üzere ayarlamalısınız `aspNetCompatibilityEnabled` özniteliğini true [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) web.config Bölümü. Ayrıca, bu appDomain içinde herhangi bir hizmeti olmalıdır `RequirementsMode` özellikte kendi <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> kümesine <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Varsayılan olarak <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> şimdi ayarlamak <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Windows Communication Foundation yenilikler](../../../docs/framework/wcf/whats-new.md) ve [WCF hizmetleri ve ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
### <a name="new-transport-default-values"></a>Yeni aktarım varsayılan değerler  
 Taşıma özelliği varsayılan değerlerinin sayısı değişmiş yapılandırmasını basitleştirmek için. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas>bir ileti oluşturulurken bir kodlayıcı tarafından kullandığı bellek miktarını sınırlamak XML sözlük okuyucular için yapılandırılabilir kota değerlerini içerir. Bu kotalar yapılandırılabilir olsa da, varsayılan değerleri bir geliştirici açıkça tahsis etmek zorunda kalacaksınız olasılığını azaltmak için değiştirilmiştir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### <a name="wcf-configuration-validation"></a>WCF yapılandırmasını doğrulama  
 Visual Studio içinde derleme işleminin bir parçası olarak, WCF yapılandırma dosyalarını proje içinde tanımlanmış öznitelikler için şimdi doğrulanır. Doğrulama başarısız olursa, doğrulama hataları ve Uyarıları listesini Visual Studio'da görüntülenir.  
  
### <a name="xml-editor-tooltips"></a>XML Düzenleyicisi araç ipuçları  
 Hizmetlerini yapılandırmak için yeni ve mevcut WCF Hizmeti geliştiricilere yardımcı olmak için Visual Studio XML düzenleyicisini şimdi araç ipuçları her yapılandırma öğesi ve hizmet yapılandırma dosyasının bir parçası olan özellikleri sağlar.  
  
## <a name="streaming-improvements"></a>Akış geliştirmeleri  
 Doğru zaman uyumsuz olduğu gönderme tarafı şimdi değil alış tarafı değil okuma ise iş parçacığı engellemek veya böylece ölçeklenebilirlik okuma yavaş akış için destek eklendi. Bir istemci akışlı bir ileti bir IIS barındırılan WCF hizmetindeki gönderdiğinde, ileti arabelleğe alma sınırlama kaldırılmıştır. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF kolaylaştırma özellikleri](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
## <a name="simplifying-exposing-an-endpoint-over-https-with-iis"></a>IIS ile HTTPS üzerinden bir uç nokta gösterme basitleştirme  
 HTTPS üzerinden bir uç nokta gösterme basitleştirmek için bir HTTPS protokolü eşlemesi eklendi. Bir HTTPS uç noktasını etkinleştirmek için Web sitenizi bir HTTPS bağlama ve SSL sertifikası yapılandırılmış olduğundan emin olun ve HTTPS hizmeti barındıran bir sanal dizinde yalnızca etkinleştirin. Hizmet için meta veri etkinleştirilirse, bunu HTTPS üzerinden de gösterilir.  
  
## <a name="generating-a-single-wsdl-document"></a>Bir tek WSDL belge oluşturma  
 Bazı üçüncü taraf WSDL işleme yığınları diğer belgelerde bir import aracılığıyla bağımlılıklara sahip WSDL belgeleri işlemek mümkün değildir.  WCF şimdi tüm WSDL bilgileri tek bir belgenin döndürülmesi belirtmenize olanak tanır. Tek bir WSDL belge ekleme istemek için "? singleWSDL" meta veri hizmetinden isterken URI.  
  
## <a name="websocket-support"></a>WebSocket desteği  
 WebSockets TCP'ye benzer performans özellikleri ile 80 ve 443 numaralı bağlantı noktaları üzerinden true çift yönlü iletişimi sağlayan bir teknolojidir. WebSocket aktarımı üzerinden iletişimi desteklemek için iki yeni bağlamalar eklenmiştir. <xref:System.ServiceModel.NetHttpBinding>ve <xref:System.ServiceModel.NetHttpsBinding>. Daha fazla bilgi için bkz: [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="new-transport-default-values"></a>Yeni aktarım varsayılan değerler  
 Aşağıdaki tabloda, değişen ayarlar ve ek bilgiler nerede açıklanmaktadır.  
  
|Özellik|Açık|Yeni varsayılan|Daha fazla bilgi için bkz.|  
|--------------|--------|-----------------|------------------------------|  
|ChannelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 saniye|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 * işlemci sayısı|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * taşıma için İşlemci sayısı<br /><br /> 4 \* SMSvcHost.exe için İşlemci sayısı|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A>[Net.TCP bağlantı noktası hizmetini yapılandırma](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * işlemci sayısı|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 saniye|[Net.TCP bağlantı noktası hizmetini yapılandırma](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
  
## <a name="xml-editor-tooltips"></a>XML Düzenleyicisi araç ipuçları  
 Hizmetlerini yapılandırmak için yeni ve mevcut WCF Hizmeti geliştiricilere yardımcı olmak için Visual Studio XML düzenleyicisini şimdi araç ipuçları her yapılandırma öğesi ve hizmet yapılandırma dosyasının bir parçası olan özellikleri sağlar.  
  
## <a name="configuring-wcf-services-in-code"></a>WCF Hizmetlerini Kodda Yapılandırma  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Yapılandırma dosyalarının veya kod kullanarak hizmetleri yapılandırma yayınlamasına izin verir.  Yapılandırma dosyaları bir hizmet dağıtılan sonra yapılandırılması gerektiğinde faydalıdır. Yapılandırma dosyaları kullanırken, bir BT Uzmanı yapılandırma dosyasını güncelleştirmek yeterlidir, hiçbir yeniden derlenmek gereklidir. Yapılandırma dosyaları, ancak, karmaşık ve korumak zor olabilir. Hata ayıklama yapılandırma dosyaları için desteği yoktur ve yapılandırma öğeleri zor ve hataya yatkın yapılandırma dosyalarını geliştirme kılan adları tarafından başvurulur. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Ayrıca Hizmetleri kodda yapılandırmanıza olanak sağlar. Önceki sürümlerinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 ve önceki) hizmetlerini kodda yapılandırma kendini barındıran senaryolarda kolay <xref:System.ServiceModel.ServiceHost> uç noktaları ve ServiceHost.Open çağırmadan önce davranışları yapılandırmak için sınıfa izin verilmiyor. Webde barındırılan senaryolarda, ancak erişiminiz yok <xref:System.ServiceModel.ServiceHost> sınıfı. Barındırılan hizmeti oluşturmak için gerekli bir web yapılandırmak için bir `System.ServiceModel.ServiceHostFactory` oluşturulan <xref:System.ServiceModel.Activation.ServiceHostFactory> ve gerekli olan herhangi bir yapılandırmaya gerçekleştirilir. .NET 4.5 ile başlayan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] daha kolay bir yolu kendi kendini barındıran her ikisi de yapılandırmak ve web hizmetlerini kodda barındırılan sağlar. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF hizmetlerini kodda yapılandırma](../../../docs/framework/wcf/configuring-wcf-services-in-code.md).  
  
## <a name="channelfactory-caching"></a>ChannelFactory önbelleğe alma  
 WCF istemci uygulamalarını kullanan <xref:System.ServiceModel.ChannelFactory%601> bir WCF Hizmeti ile bir iletişim kanalı oluşturmak için sınıfı.  Oluşturma <xref:System.ServiceModel.ChannelFactory%601> örnekleri aşağıdaki işlemleri içerdiğinden bazı ek yük doğurur:  
  
1.  Oluşturma <xref:System.ServiceModel.Description.ContractDescription> ağacı  
  
2.  Tüm gerekli CLR Türleri yansıtma  
  
3.  Kanal yığın oluşturma  
  
4.  Kaynaklarını atma  
  
 WCF bu yükünü en aza indirmek için bir WCF istemcisi proxy kullanılırken kanal fabrikaları önbelleğe alabilir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Kanal fabrikası ve önbelleğe alma](../../../docs/framework/wcf/feature-details/channel-factory-and-caching.md).  
  
## <a name="compression-and-the-binary-encoder"></a>Sıkıştırma ve ikili kodlama  
 WCF ikili kodlama WCF 4.5 ile başlayan sıkıştırma desteği ekler. Sıkıştırma türünü ile yapılandırılmış <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> özelliği. Hem istemci hem de hizmet yapılandırmalısınız <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> özelliği. Sıkıştırma için HTTP, HTTPS ve TCP protokollerini çalışır. Sıkıştırma kullanmak için bir istemci belirtir ancak hizmet desteklemiyor protokol uyumsuzluğu belirten bir iletişim kuralı özel durum oluşturulur. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][İleti Kodlayıcı seçme](../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
  
## <a name="udp"></a>UDP  
 "Yangın ve unut" kullanan hizmetler yazmak geliştiricilere sağlayan bir UDP taşıma için destek eklenmiştir Mesajlaşma. Bir istemci bir hizmete bir ileti gönderir ve hizmet yanıt bekliyor.  
  
## <a name="multiple-authentication-support"></a>Birden çok kimlik doğrulama desteği  
 Destek HTTP taşıma ve taşıma güvenliği kullanırken bir tek WCF uç noktasında IIS tarafından desteklenen gibi birden çok kimlik doğrulama modları desteklemek için eklenmiştir. IIS sanal dizininde birden çok kimlik doğrulama modları etkinleştirmenize olanak sağlar, bu özellik, WCF Hizmeti barındırıldığı sanal dizin için etkin birden çok kimlik doğrulama modları desteklemek tek bir WCF uç sağlar.  
  
## <a name="idn-support"></a>IDN desteği  
 WCF hizmetleri Uluslararası yapılan etki alanı adları ile izin vermek için destek eklenmiştir. Daha fazla bilgi için bkz: [WCF ve Uluslararası yapılan etki alanı adlarını](../../../docs/framework/wcf/feature-details/wcf-and-internationalized-domain-names.md).  
  
## <a name="httpclient"></a>HttpClient  
 Yeni bir sınıf olarak adlandırılan <xref:System.Net.Http.HttpClient> HTTP isteklerini çalışmak çok daha kolay yapmak için eklendi. Daha fazla bilgi için bkz: [sosyal ve HTTP Hizmetleri ile bağlı apps kılmak](http://go.microsoft.com/fwlink/?LinkId=231886) ve [HTTP istemci örnek](http://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664).  
  
## <a name="configuration-intellisense"></a>Yapılandırma IntelliSense  
 Yapılandırma dosyalarında özel öznitelikler için öznitelik değerlerini projede yapılandırmaları olan ve hızlı ve doğru şekilde çalışan kolaylaştırmak için IntelliSense desteği artık tanımlı.  
  
## <a name="configuration-tooltips"></a>Yapılandırma araç ipuçları  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]öğeleri ve özniteliklerinin şimdi XML Düzenleyicisi'ni ipuçlarında daha kolay zorunda ve doğru bir şekilde öğe veya öznitelik amacını tanımlayın.  
  
## <a name="paste-data-as-classes"></a>Veri sınıflar Yapıştır  
 Bir WCF projesinde XML dosyasında tanımlı veri türleri (bir hizmet olarak gösterilen gibi) doğrudan kod sayfasına yapıştırılabilmesi için. XML türü bir CLR türü olarak yapıştırılan. Bkz: [XML veri türü sınıfları oluşturma](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md) daha fazla ayrıntı için.  
  
## <a name="webservicehost-and-default-endpoints"></a>WebServiceHost ve varsayılan uç noktalar  
 Visual Studio 2010'da, açıkça bir uç nokta veya belirttiğiniz olup olmadığını WebServiceHost varsayılan uç noktası otomatik olarak oluşturulur. Uç nokta yok açıkça eklenirse, Visual Studio 2012 WebServiceHost yalnızca bir varsayılan uç noktası oluşturun. İstemci özellikle yapabilecekleriniz varsayılan uç nokta bir uç nokta ekleyin ve istemci üzerine Bekleniyor durumunda. Alternatif olarak, aşağıdaki ayar, uygulamanın yapılandırma dosyasına ekleyerek önceki davranışa geri dönmek için WCF anlayabilirsiniz.  
  
```xml  
<appSettings>  
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>  
  </appSettings>  
```  
  
## <a name="ihttpcookiecontainermanager"></a>IHttpCookieContainerManager  
 Bu arabirim tarafından kullanıma sunulan, <xref:System.ServiceModel.Channels.IChannelFactory%601>, istemci tarafında tanımlama bilgileriyle çok daha kolay çalışma yapar. AllowCookies ayarlandığında bağlama true, tanımlama bilgileri aşağıdaki kodu kullanarak erişebilirsiniz:  
  
```csharp  
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();   
System.Net.CookieContainer container = cookieManager.CookieContainer;  
```  
  
 Almak veya tanımlama bilgilerini ayarlama <xref:System.Net.CookieContainer>. AllowCookies false olarak ayarlandığında, el ile kullanarak tanımlama bilgilerinizi alabilirsiniz <xref:System.ServiceModel.OperationContext> ve başka bir diğer istekleri gönderme <xref:System.ServiceModel.OperationContext> veya ileti denetleyici. IHttpCookieContainerManager arabirimi, bir hizmet ile bir kullanıcının kimliğini doğrulamak ve diğer hizmetleri ile kimlik doğrulaması için bu hizmet tarafından döndürülen kimlik doğrulama tanımlama bilgisi kullanmanıza olanak sağlar.
