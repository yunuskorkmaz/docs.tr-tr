---
title: PII Güvenlik Kilidi
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 64c07825f0756b029781e173eb2098711cdbe60a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600483"
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Tartışma  
 Bu özelliklerin her biri, bir hizmetin güvenliğinin yönlerini denetlemek için ayrı olarak veya birlikte kullanılabilir. Bu bir WCF hizmetini güvenli hale getirmek için kesin bir kılavuz değildir.  
  
 .NET Framework yapılandırma dosyaları, veritabanlarına bağlanmak için bağlantı dizeleri gibi gizli bilgiler içerebilir. Paylaşılan, Web 'de barındırılan senaryolarda, yapılandırma dosyası içinde yer alan verilerin rastgele görüntülemeye dayanıklı olması için bu bilgileri bir hizmetin yapılandırma dosyasında şifrelemek istenebilir. .NET Framework 2,0 ve üzeri, Windows Data Protection uygulama programlama arabirimi (DPAPI) veya RSA şifreleme sağlayıcısını kullanarak yapılandırma dosyasının bölümlerini şifreleyebilme özelliğine sahiptir. DPAPI veya RSA kullanan aspnet_regiis. exe bir yapılandırma dosyasının seçim kısımlarını şifreleyebilir.  
  
 Web 'de barındırılan senaryolarda, diğer hizmetlerin alt dizinlerinde Hizmetleri olması mümkündür. Yapılandırma değerlerini belirlemek için varsayılan anlam, iç dizindeki yapılandırma değerlerini geçersiz kılmak üzere iç içe dizinler içindeki yapılandırma dosyalarının izin verir. Bazı durumlarda bu, çeşitli nedenlerle istenmeyen bir durum olabilir. WCF hizmeti yapılandırması, iç içe geçmiş bir hizmet geçersiz kılınan yapılandırma değerleri kullanılarak çalıştırıldığında, iç içe yapılandırmanın özel durumlar oluşturması için yapılandırma değerlerinin kilitlenmesini destekler.  
  
 Bu örnek, Kullanıcı adı ve parola gibi, izleme ve ileti günlüklerinde bilinen kişisel bilgilerin (PII) günlüğe kaydedilmesini nasıl denetleyeceğinizi gösterir. Varsayılan olarak, bilinen PII günlüğe kaydetme devre dışıdır, ancak bazı durumlarda PII günlüğü, bir uygulamada hata ayıklaması yapmak için önemli olabilir. Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır. Ayrıca, bu örnek izleme ve ileti günlüğe kaydetme kullanır. Daha fazla bilgi için [izleme ve mesaj günlüğü](tracing-and-message-logging.md) örneğine bakın.  
  
## <a name="encrypting-configuration-file-elements"></a>Yapılandırma dosyası öğelerini şifreleme  
 Paylaşılan bir Web barındırma ortamındaki güvenlik amaçları için, gizli bilgiler içerebilen veritabanı bağlantı dizeleri gibi belirli yapılandırma öğelerini şifrelemek istenebilir. Bir yapılandırma öğesi, .NET Framework klasöründe bulunan aspnet_regiis. exe aracı kullanılarak şifrelenmiş olabilir, örneğin,%WINDIR%\Microsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Örnek için Web. config içindeki appSettings bölümündeki değerleri şifrelemek için  
  
1. Başlat->Çalıştır komutunu kullanarak bir komut istemi açın... Yazın `cmd` ve **Tamam**' a tıklayın.  
  
2. Şu komutu yayımlayarak geçerli .NET Framework dizinine gidin: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728` .  
  
3. Aşağıdaki komutu yayımlayarak Web. config klasöründeki appSettings yapılandırma ayarlarını şifreleyin: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"` .  
  
 Yapılandırma dosyalarını şifreleme hakkında daha fazla bilgi, ASP.NET yapılandırmasındaki ([güvenli ASP.NET uygulamalar oluşturma: kimlik doğrulaması, yetkilendirme ve güvenli iletişim](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) ve ASP.NET yapılandırmasında nasıl yapılır RSA ([nasıl yapılır: rsa kullanılarak ASP.NET 2,0 ' de yapılandırma bölümlerini şifreleme](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))) hakkında daha fazla bilgi bulunabilir.  
  
## <a name="locking-configuration-file-elements"></a>Yapılandırma dosyası öğelerini kilitleme  
 Web 'de barındırılan senaryolarda, hizmetlerin alt dizinlerinde Hizmetleri olması mümkündür. Bu durumlarda, alt dizindeki hizmetin yapılandırma değerleri, Machine. config dosyasındaki değerler incelenerek ve üst dizinlerdeki herhangi bir Web. config dosyası ile çok büyük bir şekilde birleştirme işlemi, dizin ağacını aşağı taşıyarak ve son olarak, Web. config dosyasını hizmeti içeren dizinde birleştirerek hesaplanır. Çoğu yapılandırma öğesinin varsayılan davranışı, alt dizinlerindeki yapılandırma dosyalarının üst dizinlerde ayarlanan değerleri geçersiz kılmasına izin verdir. Belirli durumlarda, alt dizinlerdeki yapılandırma dosyalarının üst dizin yapılandırmasında ayarlanan değerleri geçersiz kılmasını engellemek istenebilir.  
  
 .NET Framework, kilitli yapılandırma öğelerini geçersiz kılan yapılandırmaların çalışma zamanı özel durumları oluşturması için yapılandırma dosyası öğelerini kilitlemek için bir yol sağlar.  
  
 Yapılandırma öğesi, yapılandırma dosyasındaki `lockItem` bir düğümün özniteliği belirtilerek, örneğin, iç içe yapılandırma dosyalarındaki Hesaplayıcı hizmetlerinin davranışı değiştirememesi için yapılandırma dosyasında bir düğüm için özniteliği belirtilerek kilitlenebilir.  
  
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
  
 Yapılandırma öğelerinin kilitlenmesi daha belirgin olabilir. Öğe listesi, `lockElements` alt öğeleri koleksiyonundaki öğelerin bir kümesini kilitlemek için öğesine değer olarak belirtilebilir. Bir `lockAttributes` öğe içindeki bir öznitelik kümesini kilitlemek için, bir öznitelik listesi, öğesine değer olarak belirtilebilir. `lockAllElementsExcept`Bir düğüm üzerindeki veya özniteliklerini belirterek, belirtilen bir liste hariç tüm öğe veya öznitelik koleksiyonu kilitlenebilir `lockAllAttributesExcept` .  
  
## <a name="pii-logging-configuration"></a>PII günlük kaydı yapılandırması  
 PII günlüğü iki anahtarla denetlenir: Machine. config dosyasında bir bilgisayar yöneticisinin PII günlüğe kaydedilmesine izin verilmesini veya reddetmesini sağlayan bir uygulama ayarı ve uygulama yöneticisinin bir Web. config veya App. config dosyasındaki her bir kaynak için PII günlüğünü değiştirmesine izin veren bir uygulama ayarı bulunur.  
  
 Bilgisayar genelindeki ayar, `enableLoggingKnownPii` `true` `false` `machineSettings` Machine. config 'deki öğesinde veya olarak ayarlanarak denetlenir. Örneğin, aşağıdakiler uygulamaların PII günlük kaydını açmasına olanak sağlar.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Machine. config dosyası varsayılan bir konuma sahiptir:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 `enableLoggingKnownPii`Özniteliği Machine. config dosyasında yoksa, PII günlüğüne izin verilmez.  
  
 Bir uygulama için PII günlük kaydının etkinleştirilmesi, `logKnownPii` kaynak öğenin özniteliği `true` veya `false` Web. config veya App. config dosyasına ayarlanarak yapılır. Örneğin, aşağıdaki ileti günlüğe kaydetme ve izleme günlüğü için PII günlüğe kaydedilmesini mümkün bir şekilde sunar.  
  
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
  
 `logKnownPii`Öznitelik BELIRTILMEMIŞSE PII günlüğe kaydedilmez.  
  
 PII, her ikisi de olarak `enableLoggingKnownPii` ayarlanmışsa günlüğe kaydedilir `true` ve `logKnownPii` olarak ayarlanır `true` .  
  
> [!NOTE]
> System. Diagnostics, yapılandırma dosyasında listelenenden ilki hariç tüm kaynaklardaki tüm öznitelikleri yoksayar. `logKnownPii`Yapılandırma dosyasındaki ikinci kaynağa özniteliğini eklemek etkisizdir.  
  
> [!IMPORTANT]
> Bu örneği çalıştırmak için Machine. config dosyasının el ile değiştirilmesi gerekir. Machine. config dosyasının değiştirilmesi hatalı değerler veya sözdizimi olarak değiştirilirken gerçekleştirilmelidir. tüm .NET Framework uygulamalarının çalışmasını engelleyebilir.  
  
 Ayrıca, DPAPI ve RSA kullanılarak yapılandırma dosyası öğelerini şifrelemek mümkündür. Daha fazla bilgi için aşağıdaki bağlantılara bakın:  
  
- [Güvenli ASP.NET uygulamaları oluşturma: kimlik doğrulama, yetkilendirme ve güvenli Iletişim](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [Nasıl yapılır: ASP.NET 2,0 ' de yapılandırma bölümlerini RSA kullanarak şifreleme](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Bunu ayarlamak için örneği oluşturun ve çalıştırın  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Özniteliğini ayarlamak için Machine. config dosyasını düzenleyin `enableLoggingKnownPii` `true` , gerekirse üst düğümleri ekleyin.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
#### <a name="to-clean-up-the-sample"></a>Örneği temizlemek için  
  
1. Özniteliğini olarak ayarlamak için Machine. config dosyasını düzenleyin `enableLoggingKnownPii` `false` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
