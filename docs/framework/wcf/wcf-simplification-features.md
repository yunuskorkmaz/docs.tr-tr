---
title: WCF Kolaylaştırma Özellikleri
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: e5a18d721ed05bc064abca88768e393748951a5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-simplification-features"></a>WCF Kolaylaştırma Özellikleri
Bu konuda ele alınmıştır WCF yazma sağlayan yeni özellikler daha basit uygulamalar.  
  
## <a name="simplified-generated-configuration-files"></a>Basitleştirilmiş üretilen yapılandırma dosyaları  
 Visual Studio'da hizmet Başvurusu Ekle veya SvcUtil.exe aracını kullandığınızda istemci yapılandırma dosyası oluşturulur. Değerini varsayılan değer olsa bile WCF önceki sürümlerinde bu yapılandırma dosyalarını her bağlama özelliğinin değeri içeriyor. WCF 4.5 üretilen yapılandırma dosyaları için varsayılan olmayan bir değer ayarlandığını bağlama özellikleri içerir.  
  
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
  
 WCF 4.5 ile oluşturulan aynı yapılandırma dosyasının bir örnek verilmiştir.  
  
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
  
## <a name="contract-first-development"></a>Önce anlaşma geliştirme  
 WCF sözleşmesi ilk geliştirme desteği artık sahiptir. Svcutl.exe aracı hizmeti ve veri sözleşmeleri WSDL belgeden oluşturmanıza olanak sağlayan bir /serviceContract anahtar vardır.  
  
## <a name="add-service-reference-from-a-portable-subset-project"></a>Taşınabilir alt küme projesine hizmet Başvurusu Ekle  
 Taşınabilir alt projeleri .NET derleme programcıların tek kaynak ağaç korumak ve birden çok .NET uygulamalarında (Masaüstü, Silverlight, Windows Phone ve XBOX) hala desteklerken oluşturma sistemi etkinleştirin. Taşınabilir alt projeleri üzerinde herhangi bir .NET uygulaması kullanılabilir bir .NET framework derlemesi olan .NET taşınabilir kitaplıklara yalnızca başvuru. Geliştirici deneyimi başka bir WCF istemcisi uygulama içinde bir hizmet başvurusu ekleme aynıdır. Daha fazla bilgi için bkz: [hizmet Başvurusu Ekle taşınabilir alt küme projesine](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).  
  
## <a name="aspnet-compatibility-mode-default-changed"></a>ASP.NET uyumluluğu modu varsayılan değiştirildi  
 WCF WCF hizmetleri yazılırken geliştiriciler ASP.NET HTTP ardışık düzen yer alan özelliklerin tam erişim vermek için ASP.NET uyumluluk modu sağlar. Bu modu kullanmak üzere ayarlamalısınız `aspNetCompatibilityEnabled` özniteliğini true [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) web.config Bölümü. Ayrıca, bu appDomain içinde herhangi bir hizmeti olmalıdır `RequirementsMode` özellikte kendi <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> kümesine <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> veya <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Varsayılan olarak <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> şimdi ayarlamak <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ve WCF varsayılan hizmet uygulama şablonu kümeleri `aspNetCompatibilityEnabled` özniteliğini `true`. Daha fazla bilgi için bkz: [Windows Communication Foundation 4. 5'de](../../../docs/framework/wcf/whats-new.md) ve [WCF hizmetleri ve ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="streaming-improvements"></a>Akış geliştirmeleri  
  
-   WCF için zaman uyumsuz akış için yeni destek eklenmiştir. Zaman uyumsuz akışını etkinleştirmek için ekleme <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> uç noktası davranışı hizmeti ana bilgisayarı ve kümesi için kendi <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> özelliğine `true`.  Bir hizmeti yavaş okuma birden çok istemci için akış iletileri gönderirken bu ölçeklenebilirlik yararlı olabilir. WCF istemci başına tek bir iş parçacığı artık engellemez ve başka bir istemciye hizmet iş parçacığını boş.  
  
-   IIS barındırılan bir hizmet olduğunda iletilerin ara belleğe alma geçici kaldırılan sınırlamaları. İleti aktarma akışı kullanılan IIS tarafından barındırılan bir hizmet için bir ileti alırken WCF önceki sürümlerinde, ASP.NET için WCF göndermeden önce tüm ileti arabellek. Bu, büyük bellek kullanımına neden olur. Bu arabelleğe alma .NET 4. 5 ' kaldırılmıştır ve böylece doğru akış etkinleştirme tüm ileti alındı önce gelen akış işleme IIS barındırılan WCF hizmetleri şimdi başlayabilirsiniz. Bu WCF hemen iletileri yanıtlayın ve performansın olanak sağlar. Ayrıca, artık için bir değer belirtmeniz gerekir `maxRequestLength`, gelen istekleri ASP.NET boyut sınırı. Bu özellik ayarlanırsa, yoksayılır. Hakkında daha fazla bilgi için `maxRequestLength` bkz [ \<httpRuntime > yapılandırma öğesi](http://go.microsoft.com/fwlink/?LinkId=223344). Yine gerekir daha fazla bilgi için maxAllowedContentLength yapılandırmak için bkz: [IIS istek sınırları](http://go.microsoft.com/fwlink/?LinkId=225908).  
  
## <a name="new-transport-default-values"></a>Yeni aktarım varsayılan değerler  
 Aşağıdaki tabloda, değişen ayarlar ve ek bilgiler nerede açıklanmaktadır.  
  
|Özellik|Açık|Yeni varsayılan|Daha fazla bilgi|  
|--------------|--------|-----------------|----------------------|  
|ChannelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 saniye|Bu özellik bir TCP bağlantısı .net kullanarak kendi kimliğini doğrulamak için ne kadar sürebilir belirler çerçeveleme iletişim kuralı. Bir istemci, sunucu kimlik doğrulaması gerçekleştirmek için yeterli bilgiye sahip bazı ilk veri göndermeniz gerekir. Böylece kötü amaçlı kimliği doğrulanmamış istemciler için uzun sunucuya bağlı bağlantılar tutma bu zaman aşımı bilerek ReceiveTimeout (10 dak) daha küçük hale gelir. Varsayılan değer 30 saniyedir. Hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * işlemci sayısı|Bu yuva düzeyi özelliği "kabul et" nesne sayısını açıklayan sıraya istekleri. Dinleme biriktirme listesi sıranın dolarsa yeni yuva istekleri kabul edilmeyecek. Hakkında daha fazla bilgi için <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * taşıma için İşlemci sayısı<br /><br /> 4 \* SMSvcHost.exe için İşlemci sayısı|Bu özellik bir dinleyici bekleyen sunucu olabilir kanal sayısını sınırlar. MaxPendingAccepts çok düşük olduğunda, küçük bir bekleme kanalları tüm bağlantıları bakım başlatıldığından ancak yeni bir kanal yok dinleme başlamıştır zaman aralığı olacaktır. Bağlantı bu zaman aralığında geldiğinde ve hiçbir şey için sunucuda beklediğinden başarısız olur. Bu özelliği ayarlanarak yapılandırılabilir <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> özelliğini daha büyük bir sayı. Daha fazla bilgi için bkz: <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> ve [Net.TCP bağlantı noktası Paylaşımı hizmeti yapılandırma](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * işlemci sayısı|Bu özellik, bir taşıma kabul etti ancak karşılanmadığını kaç bağlantıları ServiceModel gönderici tarafından toplanma denetler. Bu değer ayarlamak için kullanın `MaxConnections` bağlama üzerinde veya `maxOutboundConnectionsPerEndpoint` bağlama öğesi üzerindeki. Hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 saniye|Bu özellik TCP çerçeveleme veri okumak ve temel bağlantılarından bağlantı gönderme gerçekleştirmek için zaman aşımını belirtir. Bu SMSvcHost.exe hizmet gelen bağlantısından giriş verileri okumak katılımcı tutulur süreyi üzerinde bir sınır koymak için bulunmaktadır. Daha fazla bilgi için bkz: [Net.TCP bağlantı noktası Paylaşımı hizmeti yapılandırma](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).|  
  
> [!NOTE]
>  Yalnızca .NET Framework 4.5 olan bir makinede WCF Hizmeti dağıtırsanız, bu yeni varsayılan değerler kullanılır. .NET Framework 4.0 olan bir makinede aynı hizmet dağıtırsanız, .NET Framework 4.0 varsayılan değerler kullanılır. Bu ayarları yapılandırmak için önerilen bu gibi durumlarda açıkça.  
  
## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas> bir ileti oluşturulurken bir kodlayıcı tarafından kullandığı bellek miktarını sınırlamak XML sözlük okuyucular için yapılandırılabilir kota değerlerini içerir. Bu kotalar yapılandırılabilir olsa da, varsayılan değerleri bir geliştirici açıkça ayarlamanız gerekir olasılığını azaltmak için değiştirilmiştir. `MaxReceivedMessageSize` Kota, değil karmaşıklığını ile mücadele etmek size gereken engelliyor bellek tüketimi hala sınırlayabilirsiniz böylece değiştirildi <xref:System.Xml.XmlDictionaryReaderQuotas>. Aşağıdaki tabloda, kotalar, yeni varsayılan değerlerine ve her kota için kullanılır, kısa bir açıklama gösterir.  
  
|Kota adı|Varsayılan Değer|Açıklama|  
|----------------|-------------------|-----------------|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|Alır ve en fazla izin verilen dizi uzunluğu ayarlar. Bu kota bir temel bayt dizileri de dahil olmak üzere XML okuyucuyu döndürür elemanlar dizisinde en büyük boyutu sınırlar. Bu kota XML okuyucusu bellek tüketimini sınırlamaz ancak okuyucu kullanarak hangi bileşeni. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli bir okuyucu kullanan <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, bayt dizileri Bu kota büyük serisi yok.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|Alır ve her okuma için döndürülen en fazla izin verilen bayt ayarlar. Bu kota öğe okuma başlattığınızda etiketini ve onun özniteliklerini, tek bir okuma işleminde okunan bayt sayısını sınırlar. (Akışı dışı durumlarda, öğe adını kota karşı sayılmaz). Öznitelik adları için benzersizlik denetlenecek olduğundan çok fazla XML özniteliklere sahip orantısız işleme zamanı kullanabilir. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> Bu tehdidi azaltır.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|derin 128 düğüm|Bu kota en fazla iç içe geçirme derinliği XML öğelerinin sınırlar.  <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> ile etkileşime giren <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>: okuyucu en fazla bellek tüketimi bu iki ayar ürününe orantılı şekilde okuyucu her zaman veri geçerli öğe ve tüm alt öğelerinden bellekte saklar. İç içe nesne grafiğinin seri durumdan çıkarılırken, seri durumdan çıkarıcının tüm yığın erişmek ve kurtarılamaz bir throw zorlanır <xref:System.StackOverflowException>. XML iç içe geçme ve nesne iç içe geçme her ikisi arasında doğrudan bir ilişki var. <xref:System.Runtime.Serialization.DataContractSerializer> ve <!--zz <xref:System.Runtime.Serialization.XmlSerializer>--> `System.Runtime.Serialization.XmlSerializer`. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> Bu tehdidi azaltmak için kullanılır.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|Bu kota ad tablosu içinde izin verilen karakter sayısının üst sınırını belirler. Ad tablosu bir XML belgesi işleme sırasında karşılaşılan belirli dizeleri (örneğin, ad alanlarını ve önekleri) içerir. Bu dizeler bellekte arabelleğe gibi bu kota akış beklendiğinde aşırı arabelleğe almayı önlemek için kullanılır.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|Bu kota XML okuyucusu döndürür en çok dize boyutu sınırlar. Bu kota XML okuyucusu bellek tüketimini sınırlamaz ancak okuyucu kullanarak bileşeni. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli bir okuyucu kullanan <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, dizeleri Bu kota büyük serisi yok.|  
  
> [!IMPORTANT]
>  "Kullanarak XML güvenle için" altında başvuran [veriler için güvenlik konuları](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md) verilerinizin güvenliğini sağlama hakkında daha fazla bilgi için.  
  
> [!NOTE]
>  Yalnızca .NET Framework 4.5 olan bir makinede WCF Hizmeti dağıtırsanız, bu yeni varsayılan değerler kullanılır. .NET Framework 4.0 olan bir makinede aynı hizmet dağıtırsanız, .NET Framework 4.0 varsayılan değerler kullanılır. Bu ayarları yapılandırmak için önerilen bu gibi durumlarda açıkça.  
  
## <a name="wcf-configuration-validation"></a>WCF yapılandırmasını doğrulama  
 Visual Studio içinde derleme işleminin bir parçası olarak, WCF yapılandırma dosyalarını şimdi doğrulanır. Doğrulama hataları ve Uyarıları listesi doğrulama başarısız olursa Visual Studio'da görüntülenir.  
  
## <a name="xml-editor-tooltips"></a>XML Düzenleyicisi araç ipuçları  
 Hizmetlerini yapılandırmak için yeni ve mevcut WCF Hizmeti geliştiricilere yardımcı olmak için Visual Studio XML düzenleyicisini şimdi araç ipuçları her yapılandırma öğesi ve hizmet yapılandırma dosyasının bir parçası olan özellikleri sağlar.  
  
## <a name="basichttpbinding-improvements"></a>BasicHttpBinding geliştirmeleri  
  
1.  Farklı kimlik doğrulama modları yanıtlamak tek bir WCF uç sağlar.  
  
2.  IIS tarafından denetlenmesi için bir WCF hizmetin güvenlik ayarlarını sağlar
