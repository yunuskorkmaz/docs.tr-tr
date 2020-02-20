---
title: WCF Kolaylaştırma Özellikleri
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: 28a05053fda8380b55a1a9eee20119b8c4cfccfe
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452662"
---
# <a name="wcf-simplification-features"></a>WCF Kolaylaştırma Özellikleri

Bu konuda, WCF uygulamalarının yazılmasını daha kolay hale getirmek için yeni özellikler açıklanmaktadır.

## <a name="simplified-generated-configuration-files"></a>Basitleştirilmiş olarak oluşturulan yapılandırma dosyaları

Visual Studio 'da bir hizmet başvurusu eklediğinizde veya bir istemci yapılandırma dosyası oluşturulduğunda SvcUtil. exe aracını kullandığınızda. WCF 'nin önceki sürümlerinde bu yapılandırma dosyaları, değeri varsayılan değer olsa bile her bağlama özelliğinin değerini içerir. WCF 4,5 ' de, oluşturulan yapılandırma dosyaları yalnızca varsayılan olmayan bir değere ayarlanmış olan bağlama özelliklerini içerir.

Aşağıda, WCF 3,0 tarafından oluşturulan yapılandırma dosyası örneği verilmiştir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" closeTimeout="00:01:00"
                    openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00"
                    allowCookies="false" bypassProxyOnLocal="false"
                    hostNameComparisonMode="StrongWildcard" maxBufferSize="65536"
                    maxBufferPoolSize="524288" maxReceivedMessageSize="65536"
                    messageEncoding="Text" textEncoding="utf-8" transferMode="Buffered"
                    useDefaultWebProxy="true">
                    <readerQuotas maxDepth="32" maxStringContentLength="8192"
                        maxArrayLength="16384" maxBytesPerRead="4096"
                        maxNameTableCharCount="16384" />
                    <security mode="None">
                        <transport clientCredentialType="None" proxyCredentialType="None"
                            realm="" />
                        <message clientCredentialType="UserName" algorithmSuite="Default" />
                    </security>
                </binding>
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

WCF 4,5 tarafından oluşturulan aynı yapılandırma dosyasının bir örneği aşağıda verilmiştir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" />
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

## <a name="contract-first-development"></a>Sözleşme-Ilk geliştirme

WCF artık sözleşmenin ilk geliştirmeyi destekler. Svcutil. exe aracında bir WSDL belgesinden hizmet ve veri sözleşmeleri oluşturmanıza olanak sağlayan bir/serviceContract anahtarı vardır.

## <a name="add-service-reference-from-a-portable-subset-project"></a>Taşınabilir alt küme projesinden Hizmet Başvurusu Ekle

Taşınabilir alt küme projeleri, .NET derleme programcılarının tek bir kaynak ağacı ve derleme sistemi ile aynı zamanda birden çok .NET uygulaması (Masaüstü, Silverlight, Windows Phone ve Xbox) desteklemeye devam etmektedir. Taşınabilir alt küme projeleri yalnızca .NET uygulamalarında kullanılabilecek derlemeler olan .NET taşınabilir kitaplıklarına başvurur. Geliştirici deneyimi, diğer herhangi bir WCF istemci uygulamasında bir hizmet başvurusu eklemekle aynıdır. Daha fazla bilgi için bkz. [Taşınabilir alt küme projesinde hizmet başvurusu Ekle](add-service-reference-in-a-portable-subset-project.md).

## <a name="aspnet-compatibility-mode-default-changed"></a>ASP.NET uyumluluk modu varsayılan olarak değiştirildi

WCF, geliştiricilere WCF Hizmetleri yazarken ASP.NET HTTP işlem hattının özelliklerine tam erişim sağlamak için ASP.NET uyumluluk modu sağlar. Bu modu kullanmak için, Web. config dosyasının [\<serviceHostingEnvironment >](../configure-apps/file-schema/wcf/servicehostingenvironment.md) bölümünde `aspNetCompatibilityEnabled` özniteliğini true olarak ayarlamanız gerekir. Ayrıca, bu appDomain 'deki herhangi bir hizmetin, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>olarak ayarlanmış `RequirementsMode` özelliğine sahip olması gerekir. Varsayılan olarak <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> artık <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> olarak ayarlanır ve varsayılan WCF hizmeti uygulama şablonu `aspNetCompatibilityEnabled` özniteliğini `true`olarak ayarlar. Daha fazla bilgi için bkz. [Windows Communication Foundation 4,5](whats-new.md) ve [WCF Hizmetleri ve ASP.net](./feature-details/wcf-services-and-aspnet.md)yenilikleri.

## <a name="streaming-improvements"></a>Akış geliştirmeleri

- WCF 'ye, zaman uyumsuz akış için yeni destek eklenmiştir. Zaman uyumsuz akışı etkinleştirmek için, hizmet ana bilgisayarına <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> uç noktası davranışını ekleyin ve <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> özelliğini `true`olarak ayarlayın. Bu, bir hizmet, yavaş okuyan birden çok istemciye akış iletileri gönderirken ölçeklenebilirlik sağlayabilir. WCF artık istemci başına bir iş parçacığını engellemez ve başka bir istemciye hizmet vermek için iş parçacığını boşaltacaktır.

- Bir hizmetin IIS 'de barındırıldığı durumlarda iletilerin arabelleğe alınması ile ilgili sınırlamalar kaldırılmıştır. Önceki WCF sürümlerinde, akış ileti aktarımı kullanan IIS tarafından barındırılan bir hizmet için ileti alırken, ASP.NET, WCF 'ye göndermeden önce tüm iletiyi arabelleğe alabilir. Bu, büyük bellek tüketimine neden olur. Bu arabelleğe alma, .NET 4,5 ' de kaldırılmıştır ve artık IIS tarafından barındırılan WCF Hizmetleri, tüm ileti alınmadan önce gelen akışı işlemeye başlayabilir ve böylece gerçek akış de mümkün değildir. Bu, WCF 'nin iletilere anında yanıt vermesini ve gelişmiş performansa izin vermesini sağlar. Ayrıca, artık `maxRequestLength`için bir değer belirtmeniz gerekmez, gelen isteklerde ASP.NET boyut sınırı. Bu özellik ayarlandıysa, yok sayılır. `maxRequestLength` hakkında daha fazla bilgi için bkz. [\<httpRuntime > yapılandırma öğesi](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/e1f13641(v=vs.71)). MaxAllowedContentLength 'ı yapılandırmanız hala gerekir, daha fazla bilgi Için bkz. [IIS Istek sınırları](https://docs.microsoft.com/previous-versions/iis/settings-schema/ms689462(v=vs.90)).

## <a name="new-transport-default-values"></a>Yeni aktarım varsayılan değerleri

Aşağıdaki tablo, değişen ayarları ve ek bilgilerin nerede bulunacağını açıklar.

|Özellik|Açık|Yeni varsayılan|Daha Fazla Bilgi|
|--------------|--------|-----------------|----------------------|
|ChannelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 saniye|Bu özellik, bir TCP bağlantısının, .NET çerçeveleme protokolünü kullanarak kimliğini doğrulamak için ne kadar süreyle işlem yapabileceğini belirler. Sunucunun kimlik doğrulamasını gerçekleştirmek için yeterli bilgi olmadan önce bir istemcinin bazı ilk verileri gönderebilmesi gerekir. Bu zaman aşımı, ReceiveTimeout (10 dak) olarak daha küçük hale getirilir ve böylece kötü kimliği doğrulanmamış istemcilerin bağlantıları uzun süredir sunucuya bağlı tutmaması sağlanır. Varsayılan değer 30 saniyedir. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A> hakkında daha fazla bilgi için|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * işlemci sayısı|Bu yuva düzeyi özelliği, sıraya eklenecek "bekleyen kabul etme" isteklerinin sayısını açıklar. Dinleme biriktirme listesi sırası dolarsa, yeni yuva istekleri reddedilir. <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A> hakkında daha fazla bilgi için|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * aktarım için işlemci sayısı<br /><br /> 4 \* SMSvcHost. exe için işlemci sayısı|Bu özellik, sunucunun bir dinleyici üzerinde bekleyebilen kanal sayısını sınırlar. Maxpendingval çok düşük olduğunda, bekleyen tüm kanalların bağlantı Hizmetleri ile çalışmaya başladığı, ancak hiçbir yeni kanalın dinlemeyi başlattığı küçük bir zaman aralığı olacaktır. Bu süre boyunca bir bağlantı gönderilir ve sunucuda bekleyen bir şey olmadığı için başarısız olur. Bu özellik <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> özelliği daha büyük bir sayı ayarlanarak yapılandırılabilir. Daha fazla bilgi için bkz [. net. TCP bağlantı noktası paylaşım hizmetini](./feature-details/configuring-the-net-tcp-port-sharing-service.md) <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> ve yapılandırma|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * işlemci sayısı|Bu özellik, bir taşımanın kaç bağlantı kabul ettiğini ancak ServiceModel dağıtıcısı tarafından çekilmediğini denetler. Bu değeri ayarlamak için bağlama veya bağlama öğesindeki `maxOutboundConnectionsPerEndpoint` `MaxConnections` kullanın. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> hakkında daha fazla bilgi için|
|receiveTimeout|SMSvcHost.exe|30 saniye|Bu özellik TCP çerçeveleme verilerini okumak ve temel bağlantılardan bağlantı dağıtma işlemini gerçekleştirmek için zaman aşımını belirtir. Bu, SMSvcHost. exe hizmetinin gelen bir bağlantıdan giriş verilerini okumak için boşta tutulduğu zaman miktarına bir sınır koymak için vardır. Daha fazla bilgi için bkz. [net. TCP bağlantı noktası paylaşım hizmetini yapılandırma](./feature-details/configuring-the-net-tcp-port-sharing-service.md).|

> [!NOTE]
> Bu yeni varsayılanlar yalnızca WCF hizmetini .NET Framework 4,5 ile bir makineye dağıtırsanız kullanılır. Aynı hizmeti .NET Framework 4,0 ile bir makineye dağıtırsanız, .NET Framework 4,0 Varsayılanları kullanılır. Böyle durumlarda bu ayarları açıkça yapılandırmak önerilir.

## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas>, bir ileti oluştururken kodlayıcı tarafından kullanılan bellek miktarını sınırlayan XML sözlüğü okuyucuları için yapılandırılabilir kota değerleri içerir. Bu kotalar yapılandırılabilir olsa da, varsayılan değerler bir geliştiricinin bunları açıkça ayarlaması gereksinimini azaltmak üzere değiştirilmiştir. `MaxReceivedMessageSize` kota, <xref:System.Xml.XmlDictionaryReaderQuotas>karmaşıklığıyla ilgilenmenize gerek duymasını engelleyen bellek tüketimini sınırlayabilmesi için değişmemiştir. Aşağıdaki tabloda kotalar, yeni varsayılan değerleri ve her kotanın ne için kullanıldığı hakkında kısa bir açıklama gösterilmektedir.

|Kota Adı|Varsayılan Değer|Açıklama|
|----------------|-------------------|-----------------|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|İzin verilen en fazla dizi uzunluğunu alır ve ayarlar. Bu kota, bayt dizileri dahil olmak üzere XML okuyucunun döndürdüğü temel elemanların bir dizisinin maksimum boyutunu sınırlandırır. Bu kota, XML okuyucusu üzerinde bellek tüketimini sınırlamaz, ancak okuyucu kullanan herhangi bir bileşende. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>ile güvenli hale getirilmiş bir okuyucu kullandığında, bu kotadan daha büyük bayt dizilerinin serisini kaldırmaz.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|Her okuma için döndürülen izin verilen bayt sayısını alır ve ayarlar. Bu kota, öğe başlangıç etiketi ve özniteliklerini okurken tek bir okuma işleminde okunan bayt sayısını sınırlar. (Akış olmayan durumlarda, öğe adının kendisi kotaya karşı sayılmaz). Öznitelik adlarının benzersizlik için denetlenmesi gerektiğinden, çok fazla XML özniteliği orantısız işleme süresi kullanabilir. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> bu tehdidi azaltır.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|128 düğüm derin|Bu kota, XML öğelerinin en fazla iç içe geçme derinliğini sınırlandırır. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>etkileşimde bulunur: okuyucu, her zaman geçerli öğe ve tüm üst öğelerinden verileri bellekte tutar, böylece okuyucunun maksimum bellek tüketimi bu iki ayar ürünüyle orantılıdır. Derin iç içe geçmiş bir nesne grafiğinin serisi kaldırılırken, seri hale getirici yığının tamamına erişmeye zorlanır ve kurtarılamaz bir <xref:System.StackOverflowException>oluşturur. Hem <xref:System.Runtime.Serialization.DataContractSerializer> hem de <xref:System.Xml.Serialization.XmlSerializer>için XML iç içe geçme ve nesne iç içe geçme arasında doğrudan bağıntı bulunur. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, bu tehdidi azaltmak için kullanılır.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|Bu kota, bir NameTable izin verilen en fazla karakter sayısını sınırlar. NameTable, bir XML belgesi işlenirken karşılaşılan belirli dizeleri (ad alanları ve ön ekler gibi) içerir. Bu dizelerin bellekte ara belleğe alındığından, bu kota, akış beklendiğinde aşırı arabelleğe almayı engellemek için kullanılır.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|Bu kota, XML okuyucunun döndürdüğü en büyük dize boyutunu sınırlandırır. Bu kota, XML okuyucusu içindeki bellek tüketimini, ancak okuyucu kullanan bileşende sınırlamaz. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>ile güvenli hale getirilmiş bir okuyucu kullandığında, bu kotadan daha büyük dizelerin serisini kaldırmaz.|

> [!IMPORTANT]
> Verilerinizin güvenliğini sağlama hakkında daha fazla bilgi için, [verilerin güvenlik açısından dikkat edilmesi gereken](./feature-details/security-considerations-for-data.md) "XML güvenli kullanımı" bölümüne bakın.

> [!NOTE]
> Bu yeni varsayılanlar yalnızca WCF hizmetini .NET Framework 4,5 ile bir makineye dağıtırsanız kullanılır. Aynı hizmeti .NET Framework 4,0 ile bir makineye dağıtırsanız, .NET Framework 4,0 Varsayılanları kullanılır. Böyle durumlarda bu ayarları açıkça yapılandırmak önerilir.

## <a name="wcf-configuration-validation"></a>WCF yapılandırma doğrulaması

Visual Studio içindeki derleme sürecinin bir parçası olarak, WCF yapılandırma dosyaları artık onaylanır. Doğrulama başarısız olursa, Visual Studio 'da doğrulama hatalarının veya uyarıların bir listesi görüntülenir.

## <a name="xml-editor-tooltips"></a>XML Düzenleyici araç Ipuçları

Yeni ve mevcut WCF hizmeti geliştiricilerinin hizmetlerini yapılandırmasına yardımcı olmak için, Visual Studio XML Düzenleyicisi artık her yapılandırma öğesi ve hizmet yapılandırma dosyasının bir parçası olan özellikleri için araç ipuçları sunmaktadır.

## <a name="basichttpbinding-improvements"></a>BasicHttpBinding geliştirmeleri

1. Tek bir WCF uç noktasının farklı kimlik doğrulama modlarına yanıt vermesini sağlar.

2. WCF hizmetinin güvenlik ayarlarının IIS tarafından denetlenmesini sağlar
