---
title: WCF Kolaylaştırma Özellikleri
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: ded4fc93e5e8f33d98e58ffcb3cb98c2bff2b410
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083000"
---
# <a name="wcf-simplification-features"></a>WCF Kolaylaştırma Özellikleri
Bu konuda ele alınmıştır WCF yazma sağlayan yeni özellikler daha basit uygulamalar.  
  
## <a name="simplified-generated-configuration-files"></a>Üretilen yapılandırma dosyalarını Basitleştirilmiş  
 Visual Studio'da hizmet başvurusu eklemek veya SvcUtil.exe aracını kullandığınızda, bir istemci yapılandırma dosyası oluşturulur. Değerini varsayılan değer olsa bile WCF önceki sürümlerinde, bu yapılandırma dosyaları her bağlama özelliğinin değeri içeriyor. WCF 4.5 içinde oluşturulan yapılandırma dosyaları varsayılan olmayan bir değere ayarlanmış olan bağlama özellikleri içerir.  
  
 WCF 3.0 tarafından oluşturulan bir yapılandırma dosyası örneği verilmiştir.  
  
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
  
 WCF 4.5 tarafından oluşturulan aynı yapılandırma dosyası örneği verilmiştir.  
  
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
  
## <a name="contract-first-development"></a>Sözleşme ilk geliştirmesi  
 WCF sözleşme ilk geliştirmesi için destek sunuyor. WSDL belgesinden hizmet ve veri anlaşmaları Oluştur olanak tanıyan bir /serviceContract anahtar svcutl.exe araç vardır.  
  
## <a name="add-service-reference-from-a-portable-subset-project"></a>Bir taşınabilir alt küme projesine hizmet Başvurusu Ekle  
 Taşınabilir alt küme projeleri bir tek kaynak ağacının Bakımı ve birden çok .NET uygulamalarını (masaüstünde, Silverlight, Windows Phone ve XBOX) hala desteklerken yapı sistemi .NET derleme programcılar etkinleştirin. Taşınabilir alt küme projeleri yalnızca herhangi bir .NET uygulaması üzerinde kullanılabilen bir .NET framework derlemesi olan bir .NET taşınabilir kitaplıklar başvuru. Bir geliştirici deneyimi başka bir WCF istemcisi uygulama içinde bir hizmet başvurusu ekleme aynıdır. Daha fazla bilgi için [içinde bir taşınabilir alt küme projesine hizmet Başvurusu Ekle](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).  
  
## <a name="aspnet-compatibility-mode-default-changed"></a>ASP.NET uyumluluğu modu varsayılan değiştirildi  
 WCF geliştiricileri WCF hizmetleri yazarken ASP.NET HTTP ardışık düzen özelliklerine tam erişim vermek için ASP.NET uyumluluk modunun sağlar. Bu modu kullanabilmek için ayarlamanız gerekir `aspNetCompatibilityEnabled` özniteliği true olarak [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) web.config Bölümü. Ayrıca, bu uygulama etki alanında bulunan bir hizmet olması gerekir `RequirementsMode` özelliği, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> kümesine <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Varsayılan olarak <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> artık kümesine <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ve varsayılan WCF hizmet uygulaması şablonu kümeleri `aspNetCompatibilityEnabled` özniteliğini `true`. Daha fazla bilgi için [Windows Communication Foundation 4. 5'deki yenilikler](../../../docs/framework/wcf/whats-new.md) ve [WCF hizmetleri ve ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="streaming-improvements"></a>Akış geliştirmeleri  
  
-   WCF için yeni zaman uyumsuz akış desteği eklendi. Zaman uyumsuz akış etkinleştirmek için eklemeniz <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> kümesini ve hizmet ana bilgisayarı için uç nokta davranışı, <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> özelliğini `true`.  Bir hizmet yavaş okuma için birden çok istemciye akışla alınan iletileri gönderirken bu ölçeklenebilirlik yararlı olabilir. WCF istemci başına tek bir iş parçacığı artık engellemez ve başka bir istemciye hizmet iş parçacığını boş.  
  
-   IIS barındırılan bir hizmet olduğundan, arabelleğe alma iletilerinin etrafında sınırlamalar kaldırıldı. İleti aktarma akışı kullanılan IIS tarafından barındırılan bir hizmet için bir ileti alındığında WCF önceki sürümlerinde, ASP.NET WCF'ye göndermeden önce tüm ileti arabellek. Bu, büyük bellek tüketimi neden olur. .NET 4.5 içinde bu arabelleğe alma kaldırıldı ve böylece doğru akış'ı etkinleştirme tüm ileti alındı önce gelen akış işlemede IIS barındırılan WCF hizmetleri şimdi başlayabilirsiniz. Bu WCF hemen iletilere yanıt verir ve Gelişmiş performans sağlar. Ayrıca, artık için bir değer belirtmek zorunda `maxRequestLength`, gelen istekleri ASP.NET boyutu sınırı. Bu özelliği ayarlarsanız, göz ardı edilir. Hakkında daha fazla bilgi için `maxRequestLength` bkz [ \<httpRuntime > yapılandırma öğesi](https://go.microsoft.com/fwlink/?LinkId=223344). Yine de ihtiyacınız olacak daha fazla bilgi için maxAllowedContentLength yapılandırmak için bkz: [IIS istek sınırları](https://go.microsoft.com/fwlink/?LinkId=225908).  
  
## <a name="new-transport-default-values"></a>Yeni aktarım varsayılan değerler  
 Aşağıdaki tabloda, değişen ayarlar ve ek bilgilerin nerede bulunacağı açıklanır.  
  
|Özellik|Açık|Yeni varsayılan|Daha fazla bilgi|  
|--------------|--------|-----------------|----------------------|  
|ChannelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 saniye|Bu özellik, TCP bağlantısı .net kullanarak kendi kimliğini doğrulamak için ne kadar uzun sürebilir belirler Protokolü çerçeve. Sunucu kimlik doğrulaması gerçekleştirmek için yeterli bilgiye sahip önce bazı ilk veri göndermek bir istemci gerekir. Kimliği doğrulanmamış kötü niyetli kullanıcılar için uzun sunucuya bağlı bağlantılar tutma, bu zaman aşımı kasıtlı olarak ReceiveTimeout (10 dakika) daha küçük yapılır. Varsayılan değer 30 saniyedir. Hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * işlemci sayısı|Bu yuva düzeyinde özelliği "kabul et" sayısını açıklayan istekler kuyruğa alınacak. Dinleme biriktirme listesi sırası dolarsa yeni yuva istekler reddedilir. Hakkında daha fazla bilgi için <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * taşıma için İşlemci sayısı<br /><br /> 4 \* SMSvcHost.exe işlemci sayısı|Bu özellik, sunucunun bir Dinleyicide bekleyen olabilir kanal sayısını sınırlar. MaxPendingAccepts çok düşük olduğunda, küçük bir bekleme kanalları tüm bağlantıları bakım başlatıldığından ancak yeni kanal yok dinleme başlamıştır zaman aralığını olacaktır. Bir bağlantı, bu zaman aralığında gelen ve hiçbir şey için sunucuda beklemesi nedeniyle başarısız olur. Bu özelliği ayarlanarak yapılandırılabilir <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> özelliğini daha büyük bir sayı. Daha fazla bilgi için <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> ve [Net.TCP bağlantı noktası paylaşım hizmetini yapılandırma](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * işlemci sayısı|Bu özellik, bağlantı sayısı, aktarım kabul etti ancak olmayan ServiceModel gönderici tarafından teslim alındı denetler. Bu değeri ayarlamak için kullanın `MaxConnections` bağlama üzerinde veya `maxOutboundConnectionsPerEndpoint` bağlama öğesi üzerinde. Hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 saniye|Bu özellik, temel alınan bağlantılardan bağlantı dağıtımını gerçekleştirme ve TCP çerçeveleme verilerini okumak için zaman aşımını belirtir. Bu, SMSvcHost.exe hizmet gelen bir bağlantıdan giriş verileri okumak katılımcı tutulur süreyi üzerinde bir sınır koymak için bulunmaktadır. Daha fazla bilgi için [Net.TCP bağlantı noktası paylaşım hizmetini yapılandırma](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).|  
  
> [!NOTE]
>  WCF hizmeti bir makinede .NET Framework 4.5 ile dağıtırsanız, bu yeni varsayılan kullanılır. Daha sonra bir makinede .NET Framework 4.0 ile aynı hizmet dağıtırsanız, .NET Framework 4.0 varsayılan değerler kullanılır. Bu ayarları yapılandırmak için önerilen bu gibi durumlarda açıkça.  
  
## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas> XML sözlük okuyucularına olduğu bir ileti oluşturulurken bir kodlayıcı tarafından kullanılan bellek miktarını sınırlamak için yapılandırılabilir kota değerlerini içerir. Bu kotalar yapılandırılabilir olsa da, açıkça ayarlamak için gereken bir geliştirici olasılığını azaltmak için varsayılan değerleri değişti. `MaxReceivedMessageSize` Böylece karmaşıklığı ile ilgilenmenize gerek önleme bellek tüketimi hala sınırlayabilirsiniz kota değiştirilmediğinden <xref:System.Xml.XmlDictionaryReaderQuotas>. Aşağıdaki tabloda, kotalar, yeni varsayılan değerlerine ve kısa bir açıklama her kota ne için kullanıldığını gösterir.  
  
|Kota adı|Varsayılan Değer|Açıklama|  
|----------------|-------------------|-----------------|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|İzin verilen en büyük dizi uzunluğu ayarlar ve alır. Bu kota, bir XML okuyucusu döndüren bayt dizileri de dahil olmak üzere temel elemanlar dizisinde en büyük boyutu sınırlar. Bu kota, XML okuyucusu bellek tüketimini sınırlamaz, ancak okuyucu kullanarak hangi bileşeni. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli bir okuyucu kullanan <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, bayt dizileri bu kotayı daha büyük serisini değil.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|Her okuma için döndürülen en fazla izin verilen bayt ayarlar ve alır. Bu kota, öğe okuma başlattığınızda etiketini ve onun özniteliklerini tek bir okuma işleminde okunan bayt sayısını sınırlar. (Akış olmayan durumlarda, öğe adı kotaya dahil edilmez). Benzersizlik için denetlenecek öznitelik adları olduğundan çok fazla XML özniteliklere sahip orantısız işleme zamanı kullanıyor olabilir. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> Bu tehdidi azaltır.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|ayrıntılı 128 düğüm|Bu kota, XML öğeleri en fazla iç içe geçme derinliği sınırlar.  <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> etkileşime <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>: en yüksek bellek tüketimi Okuyucu için bu iki ayar çarpımını orantılı, bu nedenle okuyucu her zaman veri bellekte geçerli öğenin ve tüm alt öğelerinden tutar. Bir iç içe geçmiş Nesne grafiği işlenirken, seri durumdan çıkarıcı tüm yığını erişip kurtarılamaz bir throw zorlanır <xref:System.StackOverflowException>. XML iç içe geçirme ve nesnenin iç içe her ikisi için de arasında doğrudan bağıntı var. <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer>. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> Bu tehdidi azaltmak için kullanılır.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|Bu kota en fazla bir ad izin verilen karakter sayısını sınırlar. Ad tablosu, bir XML belgesi işleme sırasında karşılaşılan belirli dizeleri (örneğin, ad alanlarını ve önekleri) içerir. Bu dizeler bellekte arabelleğe alınmış olarak bu kotayı akış beklendiğinde aşırı arabelleğe almayı önlemek için kullanılır.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|Bu kota, XML okuyucusu döndüren maksimum dize boyutu sınırlar. Bu kota, XML okuyucusu bellek tüketimini sınırlamaz, ancak okuyucu kullanan bileşen. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli bir okuyucu kullanan <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, dizeleri bu kotayı daha büyük serisini değil.|  
  
> [!IMPORTANT]
>  Altında "Kullanarak XML güvenli bir şekilde için" başvuru [veriler için güvenlik konuları](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md) verilerinizin güvenliğini sağlama hakkında daha fazla bilgi için.  
  
> [!NOTE]
>  WCF hizmeti bir makinede .NET Framework 4.5 ile dağıtırsanız, bu yeni varsayılan kullanılır. Daha sonra bir makinede .NET Framework 4.0 ile aynı hizmet dağıtırsanız, .NET Framework 4.0 varsayılan değerler kullanılır. Bu ayarları yapılandırmak için önerilen bu gibi durumlarda açıkça.  
  
## <a name="wcf-configuration-validation"></a>WCF yapılandırma doğrulama  
 Visual Studio içinden yapı işleminin bir parçası olarak WCF yapılandırma dosyaları artık doğrulanır. Doğrulama hataları veya uyarılar listesini doğrulama başarısız olursa Visual Studio'da görüntülenir.  
  
## <a name="xml-editor-tooltips"></a>XML Düzenleyicisi araç ipuçları  
 Hizmetlerini yapılandırmak için yeni ve var olan WCF hizmet geliştiricileri yardımcı olmak amacıyla, Visual Studio XML Düzenleyicisi artık araç ipuçları her yapılandırma öğesi ve hizmet yapılandırma dosyasının bir parçası olan özellikleri sağlar.  
  
## <a name="basichttpbinding-improvements"></a>BasicHttpBinding geliştirmeleri  
  
1.  Farklı kimlik doğrulama modları için yanıt vermek tek bir WCF uç nokta sağlar.  
  
2.  IIS tarafından denetlenmesi için bir WCF hizmetin güvenlik ayarlarını sağlar
