---
title: PII Güvenlik Kilidi
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ec8af8c7df9335774b1f3953f88c2aad438963b6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809036"
---
# <a name="pii-security-lockdown"></a>PII Güvenlik Kilidi
Bu örnek, bir Windows Communication Foundation (WCF) hizmetiyle güvenlikle ilgili çeşitli özelliklerini denetlemek gösterilmiştir:  
  
-   Bir hizmetin yapılandırma dosyasındaki hassas bilgilere şifreleme.  
  
-   Böylece hizmet alt dizinleri iç içe öğelerin yapılandırma dosyasındaki kilitleme ayarları geçersiz kılamazsınız.  
  
-   İzleme ve ileti günlüklerinde, kişisel bilgilerin (PII) günlük kaydını denetleme.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Tartışma  
 Bu özelliklerin her biri ayrı ayrı veya birlikte bir hizmetin güvenlik denetim konuları için olabilir. Bu bir WCF Hizmeti güvenli hale getirme için eksiksiz bir kılavuz değildir.  
  
 .NET Framework yapılandırma dosyalarını veritabanlarına bağlanmak için bağlantı dizelerini gibi hassas bilgiler içerebilir. Paylaşılan ve Web barındırılan senaryolarda yapılandırma dosyasının içinde bulunan veriler için günlük görüntüleme dayanıklı olmasını sağlamak için bir hizmet yapılandırma dosyasında bu bilgileri şifrelemek için istenebilir. .NET framework 2.0 ve sonraki Windows veri koruma uygulama programlama arabirimi (DPAPI) veya RSA şifreleme sağlayıcısı kullanarak yapılandırma dosyasını bölümlerini şifreleme olanağı vardır. DPAPI veya RSA kullanarak aspnet_regiis.exe bir yapılandırma dosyası seçme bölümlerini şifreleyebilirsiniz.  
  
 Web barındırılan senaryolarda hizmetler diğer hizmetlere dizinlerde olması mümkündür. Varsayılan yapılandırma değerlerini belirlemek için anlamsal üst dizinindeki yapılandırma değerleri geçersiz kılmak için iç içe geçmiş dizinlerdeki yapılandırma dosyaları sağlar. Belirli durumlarda bu çeşitli nedenlerle için istenmeyen olabilir. İç içe geçmiş bir hizmet kullanarak çalıştırıldığında yapılandırma değerlerini, böylece yapılandırma iç içe geçmiş kilitleme özel durumları oluşturur WCF hizmeti yapılandırma destekler yapılandırma değerleri geçersiz.  
  
 Bu örnek, bilinen kişisel bilgilerin (PII) kullanıcı adı ve parola gibi izleme ve ileti günlüklerinde günlük denetim gösterilmiştir. Belirli durumlarda PII günlüğe bir uygulamada hata ayıklama önemli olabilir ancak varsayılan olarak bilinen PII günlüğünü devre dışıdır. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ayrıca, bu örnek, ileti izleme ve kaydetme kullanır. Daha fazla bilgi için bkz: [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek.  
  
## <a name="encrypting-configuration-file-elements"></a>Yapılandırma dosyası öğeleri şifreleme  
 Paylaşılan Web barındırma ortamında güvenlik nedenleriyle, hassas bilgiler içerebilir veritabanı bağlantı dizelerini gibi belirli yapılandırma öğelerini şifreleme istenebilir. Örneğin, % WINDIR%\Micrsoft.NET\Framework\v4.0.20728 .NET Framework klasöründe bulunan aspnet_regiis.exe aracını kullanarak bir yapılandırma öğesi şifrelenmelidir.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Web.config dosyasındaki appSettings bölümünü örnek değerler şifrelemek için  
  
1.  Açık başlangıç kullanarak bir komut istemi -> Çalıştır... Yazın `cmd` tıklatıp **Tamam**.  
  
2.  Aşağıdaki komutu gönderdikten geçerli .NET Framework dizinine gidin: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3.  Aşağıdaki komutu gönderdikten Web.config klasörü appSettings yapılandırma ayarlarında şifrelemek: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 ASP.NET yapılandırma DPAPI üzerinde nasıl yapılır okuyarak yapılandırma dosyalarını bölümlerini şifreleme hakkında daha fazla bilgi bulunabilir ([Güvenli ASP.NET uygulamaları oluşturma: kimlik doğrulama, yetkilendirme ve güvenli iletişim](http://go.microsoft.com/fwlink/?LinkId=95137)) ve ASP.NET yapılandırmasında RSA üzerinde nasıl yapılır ([nasıl yapılır: ASP.NET 2.0 kullanarak RSA şifreleme yapılandırma bölümlerinin](http://go.microsoft.com/fwlink/?LinkId=95138)).  
  
## <a name="locking-configuration-file-elements"></a>Kilitleme yapılandırma dosyası öğeleri  
 Web barındırılan senaryolarda Hizmetleri Hizmetleri dizinlerde olması mümkündür. Bu durumlarda, hizmet alt dizinindeki yapılandırma değerlerini Machine.config değerlerde incelenerek ve dizin ağacında taşıma ve son olarak birleştirme üst dizinlerdeki herhangi Web.config dosyaları ile sırayla birleştirme tarafından hesaplanır Hizmet içeren dizine Web.config dosyasında. Çoğu yapılandırma öğeleri için varsayılan davranış, alt dizinleri üst dizinlerde ayarlanan değerleri geçersiz kılmak için yapılandırma dosyalarında izin vermektir. Belirli durumlarda dizinlerdeki yapılandırma dosyaları üst dizini yapılandırmasında değerleri geçersiz kılmasını önlemek istenebilir.  
  
 .NET Framework çalışma zamanı özel durumlar kilitli yapılandırma öğeleri geçersiz kılma yapılandırmaları oluşturma için yapılandırma dosyası öğelerini kilitlemek için bir yol sağlar.  
  
 Bir yapılandırma öğesi belirterek kilitlenip `lockItem` özniteliği yapılandırma dosyasında bir düğüm için örneğin, böylece hesaplayıcı Hizmetleri'nde yapılandırma dosyalarını iç içe geçmiş yapılandırma dosyasında CalculatorServiceBehavior düğümü kilitlemek için değişiklik davranışı, aşağıdaki yapılandırma kullanılabilir olamaz.  
  
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
  
 Yapılandırma öğeleri kilitleme daha belirli olabilir. Öğelerinin bir listesini değeri olarak belirtilen `lockElements` bir alt öğe koleksiyonunu içinde öğeleri kümesini kilitlenemiyor. Öznitelik listesi değeri olarak belirtilen `lockAttributes` öğe içindeki öznitelikler kümesi kilitlenemiyor. Belirterek dışında belirtilen liste öğelerini veya özniteliklerin tüm bir koleksiyon kilitlenebilir `lockAllElementsExcept` veya `lockAllAttributesExcept` bir düğümde öznitelikleri.  
  
## <a name="pii-logging-configuration"></a>PII günlüğü yapılandırması  
 PII günlüğe iki anahtarları tarafından denetlenir: izin ver veya Reddet günlük PII ve PII günlüğü her geçiş yapmak bir uygulama Yöneticisi sağlayan bir uygulama ayarı için bilgisayar yöneticisi sağlayan Machine.config bilgisayar genelinde bir ayar bulundu Web.config veya App.config dosyasını kaynağında.  
  
 Bilgisayar genelinde ayar ayarlayarak denetlenir `enableLoggingKnownPii` için `true` veya `false`, `machineSettings` Machine.config öğesinde. Örneğin, aşağıdaki uygulamaların PII günlük özelliğini açmak izin verir.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Machine.config dosyasının bir varsayılan konum vardır: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Varsa `enableLoggingKnownPii` özniteliği Machine.config içinde mevcut değil, PII günlüğe izin verilmez.  
  
 Bir uygulama ayarlayarak yapılır için PII günlüğe yazma etkinleştirildikten sonra `logKnownPii` için kaynak öğesinin özniteliği `true` veya `false` Web.config veya App.config dosyasının içinde. Örneğin, aşağıdaki PII günlüğü ileti günlüğe kaydetme ve izleme günlük kaydını etkinleştirir.  
  
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
  
 Varsa `logKnownPii` özniteliği belirtilmezse, ardından PII günlüğe kaydedilmez.  
  
 PII her iki yalnızca oturum `enableLoggingKnownPii` ayarlanır `true`, ve `logKnownPii` ayarlanır `true`.  
  
> [!NOTE]
>  System.Diagnostics tüm öznitelikleri yapılandırma dosyasında listelenen ilk dışındaki tüm kaynaklarında yoksayar. Ekleme `logKnownPii` özniteliği yapılandırma dosyasında ikinci kaynağına etkisi yoktur.  
  
> [!IMPORTANT]
>  Bu örneği çalıştırmak için Machine.config el ile değiştirilmesini içerir. Machine.config yanlış değer veya sözdizimi değiştirmek tüm .NET Framework uygulamaların çalıştırılmasını engelleyebilir zaman dikkatli olunmalıdır.  
  
 Yapılandırma dosyası öğeleri DPAPI ve RSA kullanarak şifrelemek mümkündür. Daha fazla bilgi için aşağıdaki bağlantılara bakın:  
  
-   [Güvenli ASP.NET uygulamaları oluşturma: Kimlik doğrulama, yetkilendirme ve güvenli iletişim](http://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [Nasıl yapılır: ASP.NET 2.0 yapılandırma bölümlerinin şifrelemek RSA kullanma](http://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırma  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Ayarlanacak Machine.config Düzenle `enableLoggingKnownPii` özniteliğini `true`, gerekirse üst düğüm ekleme.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Örnek temizlemek için  
  
1.  Ayarlanacak Machine.config Düzenle `enableLoggingKnownPii` özniteliğini `false`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
