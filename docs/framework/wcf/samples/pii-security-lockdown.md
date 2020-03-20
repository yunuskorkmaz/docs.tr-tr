---
title: PII Güvenlik Kilidi
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144272"
---
# <a name="pii-security-lockdown"></a>PII Güvenlik Kilidi
Bu örnek, bir Windows Communication Foundation (WCF) hizmetinin güvenlikle ilgili çeşitli özelliklerinin nasıl denetlenir olduğunu gösterir:  
  
- Bir hizmetin yapılandırma dosyasındaki hassas bilgileri şifreleme.  
  
- İç içe hizmet alt dizinlerinin ayarları geçersiz kılamaması için yapılandırma dosyasındaki öğeleri kilitleme.  
  
- İzleme ve ileti günlüklerinde Kişisel Olarak Tanımlanabilir Bilgilerin (PII) günlüğe kaydedilmesini denetleme.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Tartışma  
 Bu özelliklerin her biri, bir hizmetin güvenliğinin yönlerini denetlemek için ayrı ayrı veya birlikte kullanılabilir. Bu, bir WCF hizmetini güvence altına almak için kesin bir kılavuz değildir.  
  
 .NET Framework yapılandırma dosyaları veritabanlarına bağlanmak için bağlantı dizeleri gibi hassas bilgiler içerebilir. Paylaşılan, Web tarafından barındırılan senaryolarda, yapılandırma dosyasında bulunan verilerin gündelik görüntülemeye karşı dayanıklı olması için bu bilgileri bir hizmet için yapılandırma dosyasında şifrelemek istenebilir. .NET Framework 2.0 ve daha sonra Windows Veri Koruma uygulama programlama arabirimi (DPAPI) veya RSA Şifreleme sağlayıcısı kullanarak yapılandırma dosyasının bölümlerini şifreleme yeteneğine sahiptir. DPAPI veya RSA kullanan aspnet_regiis.exe, yapılandırma dosyasının belirli bölümlerini şifreleyebilir.  
  
 Web tarafından barındırılan senaryolarda, diğer hizmetlerin alt dizilişlerinde hizmetlerin olması mümkündür. Yapılandırma değerlerini belirlemek için varsayılan anlamsal, iç içe alınan dizinlerde bulunan yapılandırma dosyalarının üst dizindeki yapılandırma değerlerini geçersiz kılmasına olanak tanır. Bazı durumlarda bu çeşitli nedenlerle istenmeyen olabilir. WCF hizmet yapılandırması yapılandırma değerlerinin kilitlenmesini destekler, böylece iç içe geçmiş yapılandırma, iç içe geçmiş bir hizmet geçersiz yapılandırma değerleri kullanılarak çalıştırıldığında özel durumlar oluşturur.  
  
 Bu örnek, kullanıcı adı ve parola gibi izleme ve ileti günlüklerinde bilinen Kişisel Tanıtıcı Bilgilerin (PII) günlüğe kaydetmenin nasıl denetlenir olduğunu gösterir. Varsayılan olarak, bilinen KIŞISEL Bilgiler'in günlüğe kaydedilmesi devre dışı bırakılır, ancak bazı durumlarda kişisel bilgi nin günlüğe kaydedilmesi bir uygulamanın hata ayıklanmasında önemli olabilir. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır. Buna ek olarak, bu örnek izleme ve ileti günlüğe kaydetme kullanır. Daha fazla bilgi için [İzleme ve İleti Günlüğü](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örneğine bakın.  
  
## <a name="encrypting-configuration-file-elements"></a>Yapılandırma Dosya Öğelerini Şifreleme  
 Paylaşılan bir Web barındırma ortamındaki güvenlik amacıyla, hassas bilgiler içerebilecek veritabanı bağlantı dizeleri gibi belirli yapılandırma öğelerini şifrelemek isteolabilir. Bir yapılandırma öğesi .NET Framework klasöründe bulunan aspnet_regiis.exe aracı kullanılarak şifrelenebilir Örneğin, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Örnek için Web.config'deki uygulama Ayarlar bölümündeki değerleri şifrelemek için  
  
1. Başlat->Çalıştır'ı kullanarak komut istemini açın.... Yazın `cmd` ve **Tamam'ı**tıklatın.  
  
2. Aşağıdaki komutu vererek geçerli .NET Framework dizinine `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`gidin: .  
  
3. Aşağıdaki komutu vererek Web.config klasöründeki uygulama Ayarları `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`ayarlarını şifreleyin: .  
  
 Yapılandırma dosyalarının bölümlerini şifreleme hakkında daha fazla bilgi, ASP.NET yapılandırmada DPAPI'de nasıl yapılır[(Güvenli ASP.NET Uygulamaları Oluşturma: Kimlik Doğrulama, Yetkilendirme ve Güvenli İletişim)](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))ve ASP.NET yapılandırmada RSA'da nasıl yapılır[(2.0'da yapılandırma bölümlerini ASP.NET'da nasıl şifrelenir) okuyarak](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))bulunabilir.  
  
## <a name="locking-configuration-file-elements"></a>Yapılandırma dosya öğelerini kilitleme  
 Web tarafından barındırılan senaryolarda, hizmetlerin alt dizilişlerinde hizmetlerin olması mümkündür. Bu gibi durumlarda, alt dizindeki hizmetin yapılandırma değerleri Machine.config'deki değerler incelenerek hesaplanır ve ana dizinlerde herhangi bir Web.config dosyasıyla art arda birleştirilerek dizin ağacından aşağı iner ve son olarak Hizmeti içeren dizindeki Web.config dosyası. Yapılandırma öğelerinin çoğu için varsayılan davranış, alt dizinlerde yapılandırma dosyalarının üst dizinlerde ayarlanan değerleri geçersiz kılmasına izin vermektir. Bazı durumlarda, alt dizinlerde yapılandırma dosyalarının üst dizin yapılandırmasında ayarlanan değerleri geçersiz kılmasından öngörmek istenebilir.  
  
 .NET Framework, kilitli yapılandırma öğelerini geçersiz kılan yapılandırmaların çalışma zamanı özel durumları atmasını sağlayacak şekilde yapılandırma dosya öğelerini kilitlemenin bir yolunu sağlar.  
  
 Yapılandırma öğesi, iç içe olan `lockItem` yapılandırma dosyalarındaki hesap makinesi hizmetlerinin davranışı değiştirememesi için yapılandırma dosyasındaki Hesap Makinesi Davranışı düğümünü kilitlemek için yapılandırma dosyasındaki bir düğümün özniteliğini belirterek kilitlenebilir, aşağıdaki yapılandırma kullanılabilir.  
  
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
  
 Yapılandırma öğelerinin kilitlenme daha spesifik olabilir. Öğelerin listesi, alt öğeler koleksiyonundaki `lockElements` bir öğe kümesini kilitlemek için gereken değer olarak belirtilebilir. Özniteliklerin listesi, bir öğe içindeki `lockAttributes` öznitelikler kümesini kilitlemek için gereken değer olarak belirtilebilir. Bir düğüm üzerinde `lockAllElementsExcept` öznitelikleri belirterek belirli bir liste dışında `lockAllAttributesExcept` öğeler in tüm bir koleksiyon kilitlenebilir.  
  
## <a name="pii-logging-configuration"></a>PII Günlük Yapılandırması  
 KIŞISEL Bilgiler'in günlüğe kaydetmesi iki anahtarla denetlenir: Machine.config'de bulunan ve bilgisayar yöneticisinin KIŞISEL Bilgiler günlüğe kaydetmesine veya reddetmesine olanak tanıyan bilgisayar çapında bir ayar ve uygulama yöneticisinin her biri için kişisel bilgi günleme günlemasını geçişini sağlayan bir uygulama ayarı bir Web.config veya App.config dosyasında kaynak.  
  
 Bilgisayar genelindeayar, `enableLoggingKnownPii` Machine.config'deki `true` `false` `machineSettings` elemana ayarlayarak veya , Örneğin, aşağıdaki uygulamaların KIŞISEL Bilgiler günlüğe kaydetmeyi açmasına olanak tanır.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Machine.config dosyası varsayılan bir konuma sahiptir: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 `enableLoggingKnownPii` Özellik Machine.config'de yoksa, KIŞISEL Bilgiler'in günlüğe kaydetmesine izin verilmez.  
  
 Bir uygulama için KIŞISEL Bilgiler'in günlüğe `logKnownPii` kaydedilmesini etkinleştirme, `true` `false` kaynak öğenin özniteliğini Web.config veya App.config dosyasına veya bu dosyaya ayarlayarak yapılır. Örneğin, aşağıdaki, hem ileti günlüğe kaydetme hem de izleme günlüğü için KIŞISEL Bilgiler günlüğe kaydetmeyi sağlar.  
  
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
  
 `logKnownPii` Öznitelik belirtilmemişse, kişisel bilgiler günlüğe kaydedilmez.  
  
 Kişisel Bilgiler yalnızca her `enableLoggingKnownPii` ikisi de `true`ayarlanmışsa `logKnownPii` `true`ve .'ye ayarlanmışsa günlüğe kaydedilir.  
  
> [!NOTE]
> System.Diagnostics, yapılandırma dosyasında listelenen ilk i `logKnownPii` Yapılandırma dosyasındaki ikinci kaynağa öznitelik eklemenin hiçbir etkisi yoktur.  
  
> [!IMPORTANT]
> Bu örneği çalıştırmak için Machine.config manuel modifikasyon içerir. Machine.config'i yanlış değerler veya sözdizimi olarak değiştirirken tüm .NET Framework uygulamalarının çalışmasını engelleyebilir.  
  
 DPAPI ve RSA kullanarak yapılandırma dosya öğelerini şifrelemek de mümkündür. Daha fazla bilgi için aşağıdaki bağlantılara bakın:  
  
- [Bina Güvenli ASP.NET Uygulamaları: Kimlik Doğrulama, Yetkilendirme ve Güvenli İletişim](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [Nasıl YapılSın: RSA kullanarak ASP.NET 2.0'da Yapılandırma Bölümlerini Şifreleme](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Gerekirse ana düğümleri ekleyerek `enableLoggingKnownPii` özniteliği `true`ayarlamak için Machine.config'i edin.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
4. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
#### <a name="to-clean-up-the-sample"></a>Örneği temizlemek için  
  
1. Özniteliğini ayarlamak `enableLoggingKnownPii` için Machine.config'i `false`edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
