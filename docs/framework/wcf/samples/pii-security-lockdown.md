---
title: PII Güvenlik Kilidi
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 56c8acbe53f1e0243f7c679da6ef04f7135bcd3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094975"
---
# <a name="pii-security-lockdown"></a>PII Güvenlik Kilidi
Bu örnek, bir Windows Communication Foundation (WCF) hizmetinin güvenlikle ilgili birkaç özelliğinin nasıl kontrol altına alınacağını gösterir:  
  
- Bir hizmetin yapılandırma dosyasındaki hassas bilgileri şifreleme.  
  
- İç içe geçmiş hizmet alt dizinleri ayarları geçersiz kılamaması için yapılandırma dosyasındaki öğeleri kilitleme.  
  
- Kişisel bilgilerin (PII) izleme ve ileti günlüklerinde günlüğe kaydedilmesini denetleme.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Tartışma  
 Bu özelliklerin her biri, bir hizmetin güvenliğinin yönlerini denetlemek için ayrı olarak veya birlikte kullanılabilir. Bu bir WCF hizmetini güvenli hale getirmek için kesin bir kılavuz değildir.  
  
 .NET Framework yapılandırma dosyaları, veritabanlarına bağlanmak için bağlantı dizeleri gibi gizli bilgiler içerebilir. Paylaşılan, Web 'de barındırılan senaryolarda, yapılandırma dosyası içinde yer alan verilerin rastgele görüntülemeye dayanıklı olması için bu bilgileri bir hizmetin yapılandırma dosyasında şifrelemek istenebilir. .NET Framework 2,0 ve üzeri, Windows Data Protection uygulama programlama arabirimi (DPAPI) veya RSA şifreleme sağlayıcısını kullanarak yapılandırma dosyasının bölümlerini şifreleyebilme özelliğine sahiptir. DPAPI veya RSA kullanan aspnet_regiis. exe bir yapılandırma dosyasının seçim kısımlarını şifreleyebilir.  
  
 Web 'de barındırılan senaryolarda, diğer hizmetlerin alt dizinlerinde Hizmetleri olması mümkündür. Yapılandırma değerlerini belirlemek için varsayılan anlam, iç dizindeki yapılandırma değerlerini geçersiz kılmak üzere iç içe dizinler içindeki yapılandırma dosyalarının izin verir. Bazı durumlarda bu, çeşitli nedenlerle istenmeyen bir durum olabilir. WCF hizmeti yapılandırması, iç içe geçmiş bir hizmet geçersiz kılınan yapılandırma değerleri kullanılarak çalıştırıldığında, iç içe yapılandırmanın özel durumlar oluşturması için yapılandırma değerlerinin kilitlenmesini destekler.  
  
 Bu örnek, Kullanıcı adı ve parola gibi, izleme ve ileti günlüklerinde bilinen kişisel bilgilerin (PII) günlüğe kaydedilmesini nasıl denetleyeceğinizi gösterir. Varsayılan olarak, bilinen PII günlüğe kaydetme devre dışıdır, ancak bazı durumlarda PII günlüğü, bir uygulamada hata ayıklaması yapmak için önemli olabilir. Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Ayrıca, bu örnek izleme ve ileti günlüğe kaydetme kullanır. Daha fazla bilgi için [izleme ve mesaj günlüğü](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örneğine bakın.  
  
## <a name="encrypting-configuration-file-elements"></a>Yapılandırma dosyası öğelerini şifreleme  
 Paylaşılan bir Web barındırma ortamındaki güvenlik amaçları için, gizli bilgiler içerebilen veritabanı bağlantı dizeleri gibi belirli yapılandırma öğelerini şifrelemek istenebilir. Bir yapılandırma öğesi, .NET Framework klasöründe bulunan aspnet_regiis. exe aracı kullanılarak şifrelenmiş olabilir, örneğin,%WINDIR%\Microsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Örnek için Web. config içindeki appSettings bölümündeki değerleri şifrelemek için  
  
1. Başlat-> Çalıştır komutunu kullanarak bir komut istemi açın... `cmd` yazın ve **Tamam**' a tıklayın.  
  
2. Şu komutu yayımlayarak geçerli .NET Framework dizinine gidin: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3. Şu komutu yayımlayarak Web. config klasöründeki appSettings yapılandırma ayarlarını şifreleyin: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Yapılandırma dosyalarını şifreleme hakkında daha fazla bilgi, ASP.NET yapılandırmasındaki ([güvenli ASP.NET uygulamalar oluşturma: kimlik doğrulaması, yetkilendirme ve güvenli iletişim](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) ve ASP.NET yapılandırmasında nasıl yapılır RSA ([nasıl yapılır: rsa kullanılarak ASP.NET 2,0 ' de yapılandırma bölümlerini şifreleme](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))) hakkında daha fazla bilgi bulunabilir.  
  
## <a name="locking-configuration-file-elements"></a>Yapılandırma dosyası öğelerini kilitleme  
 Web 'de barındırılan senaryolarda, hizmetlerin alt dizinlerinde Hizmetleri olması mümkündür. Bu durumlarda, alt dizindeki hizmetin yapılandırma değerleri, Machine. config dosyasındaki değerleri inceleyerek ve üst dizinlerdeki herhangi bir Web. config dosyası ile çok büyük bir şekilde birleştirme işlemi, dizin ağacını aşağı doğru ve son olarak birleştirme sırasında hesaplanır. Hizmeti içeren dizinde Web. config dosyası. Çoğu yapılandırma öğesinin varsayılan davranışı, alt dizinlerindeki yapılandırma dosyalarının üst dizinlerde ayarlanan değerleri geçersiz kılmasına izin verdir. Belirli durumlarda, alt dizinlerdeki yapılandırma dosyalarının üst dizin yapılandırmasında ayarlanan değerleri geçersiz kılmasını engellemek istenebilir.  
  
 .NET Framework, kilitli yapılandırma öğelerini geçersiz kılan yapılandırmaların çalışma zamanı özel durumları oluşturması için yapılandırma dosyası öğelerini kilitlemek için bir yol sağlar.  
  
 Yapılandırma öğesi, yapılandırma dosyasındaki bir düğümün `lockItem` özniteliği belirtilerek, örneğin, iç içe yapılandırma dosyalarındaki Hesaplayıcı hizmetlerinin davranışı değiştirememesi için yapılandırma dosyasında bir düğüm için özniteliği belirtilerek kilitlenebilir.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>   
          <serviceBehaviors>   
             <behavior name="CalculatorServiceBehavior" lockItem="true">   
               <serviceMetadata httpGetEnabled="True"/>   
               <serviceDebug includeExceptionDetailInFaults="False" />   
             </behavior>   
          </serviceBehaviors>   
       </behaviors>   
    </system.serviceModel>  
</configuration>  
```  
  
 Yapılandırma öğelerinin kilitlenmesi daha belirgin olabilir. Öğelerin bir listesi, alt öğelerin bir koleksiyonundaki öğelerin bir kümesini kilitlemek için `lockElements` değer olarak belirtilebilir. Bir öğe içindeki bir öznitelik kümesini kilitlemek için `lockAttributes` öznitelik listesi olarak belirtilebilir. Bir düğüm üzerinde `lockAllElementsExcept` veya `lockAllAttributesExcept` öznitelikleri belirtilerek, belirtilen bir liste dışında bir öğe veya öznitelik koleksiyonunun tamamı kilitlenebilir.  
  
## <a name="pii-logging-configuration"></a>PII günlük kaydı yapılandırması  
 PII günlüğü iki anahtarla denetlenir: Machine. config dosyasında bir bilgisayar yöneticisinin PII günlüğe kaydedilmesine izin verilmesini veya reddetmesini sağlayan bir uygulama ayarı ve uygulama yöneticisinin her biri için PII günlüğe kaydedilmesini değiştirmesine izin veren bir uygulama ayarı bulunur. bir Web. config veya App. config dosyasında kaynak.  
  
 Bilgisayar genelindeki ayar, Machine. config içindeki `machineSettings` öğesinde `true` veya `false``enableLoggingKnownPii` ayarlanarak denetlenir. Örneğin, aşağıdakiler uygulamaların PII günlük kaydını açmasına olanak sağlar.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Machine. config dosyası varsayılan bir konuma sahiptir:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Machine. config dosyasında `enableLoggingKnownPii` özniteliği yoksa PII kaydına izin verilmez.  
  
 Bir uygulama için PII günlük kaydının etkinleştirilmesi, kaynak öğenin `logKnownPii` özniteliği Web. config veya App. config dosyasında `true` veya `false` ayarlanarak yapılır. Örneğin, aşağıdaki ileti günlüğe kaydetme ve izleme günlüğü için PII günlüğe kaydedilmesini mümkün bir şekilde sunar.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>   
                ...   
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...   
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 `logKnownPii` özniteliği belirtilmemişse PII günlüğe kaydedilmez.  
  
 PII yalnızca `enableLoggingKnownPii` `true`olarak ayarlanırsa günlüğe kaydedilir ve `logKnownPii` `true`olarak ayarlanır.  
  
> [!NOTE]
> System. Diagnostics, yapılandırma dosyasında listelenenden ilki hariç tüm kaynaklardaki tüm öznitelikleri yoksayar. Yapılandırma dosyasındaki ikinci kaynağa `logKnownPii` özniteliği eklemenin hiçbir etkisi yoktur.  
  
> [!IMPORTANT]
> Bu örneği çalıştırmak için Machine. config dosyasının el ile değiştirilmesi gerekir. Machine. config dosyasının değiştirilmesi hatalı değerler veya sözdizimi olarak değiştirilirken gerçekleştirilmelidir. tüm .NET Framework uygulamalarının çalışmasını engelleyebilir.  
  
 Ayrıca, DPAPI ve RSA kullanılarak yapılandırma dosyası öğelerini şifrelemek mümkündür. Daha fazla bilgi için aşağıdaki bağlantılara bakın:  
  
- [Güvenli ASP.NET uygulamaları oluşturma: kimlik doğrulama, yetkilendirme ve güvenli Iletişim](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [Nasıl yapılır: ASP.NET 2,0 ' de yapılandırma bölümlerini RSA kullanarak şifreleme](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Bunu ayarlamak için örneği oluşturun ve çalıştırın  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. `enableLoggingKnownPii` özniteliğini `true`olarak ayarlamak için Machine. config 'i düzenleyin, gerekirse üst düğümleri ekleyin.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
#### <a name="to-clean-up-the-sample"></a>Örneği temizlemek için  
  
1. Machine. config ' i düzenleyerek `enableLoggingKnownPii` özniteliğini `false`olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
