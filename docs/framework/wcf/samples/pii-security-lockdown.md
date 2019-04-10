---
title: PII Güvenlik Kilidi
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 13ed280e9b7de2b205e0878761dbf97e168f06d3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326651"
---
# <a name="pii-security-lockdown"></a>PII Güvenlik Kilidi
Bu örnek, bir Windows Communication Foundation (WCF) hizmeti tarafından güvenlikle ilgili çeşitli özelliklerini denetlemek nasıl gösterir:  
  
-   Bir hizmetin yapılandırma dosyasındaki hassas bilgileri şifrelemek üzere.  
  
-   Böylece hizmet alt dizinleri iç içe öğeleri yapılandırma dosyasındaki kilitleme ayarları geçersiz kılamazsınız.  
  
-   İzleme ve ileti günlükleri, kişisel bilgilerin (PII) günlüğüne denetleme.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Tartışma  
 Bu özelliklerin her biri ayrı ayrı veya birlikte bir hizmetin güvenlik denetimi yönleri için olabilir. Bu, bir WCF Hizmeti güvenli hale getirme için kesin bir kılavuz değildir.  
  
 .NET Framework yapılandırma dosyalarının veritabanlarına bağlanmak için bağlantı dizeleri gibi hassas bilgiler içerebilir. Paylaşılan ve Web barındırılan senaryolarda yapılandırma dosyasının içinde yer alan verileri sıradan görüntülemeye dayanıklı olması için bir hizmet yapılandırma dosyasında bu bilgileri şifrelemek için istenebilir. .NET framework 2.0 ve sonraki Windows veri koruma uygulama programlama arabirimi (DPAPI) veya RSA şifreleme sağlayıcısını kullanarak yapılandırma dosyasının bölümlerini şifreler özelliğine sahiptir. Bir yapılandırma dosyası seçme bölümlerini aspnet_regiis.exe DPAPI veya RSA kullanarak şifreleyebilirsiniz.  
  
 Web barındırılan senaryolarda Hizmetleri diğer hizmetlerin dizinlerde olması mümkündür. Varsayılan yapılandırma değerlerini belirlemek için anlamsal üst dizinindeki yapılandırma değerleri geçersiz kılmak için iç içe geçmiş dizinleri yapılandırma dosyalarında sağlar. Belirli durumlarda bu istenmeyen çeşitli nedenlerden dolayı olabilir. WCF hizmeti yapılandırma destekleyen iç içe geçmiş bir hizmet kullanarak çalıştırıldığında yapılandırma değerlerini, böylece yapılandırma iç içe geçmiş kilitleme özel durum oluşturur, yapılandırma değerleri geçersiz.  
  
 Bu örnek, bilinen kişisel bilgilerin (PII) kullanıcı adı ve parola gibi izleme ve ileti günlüklerde günlüğe kaydetmeyi denetlemek nasıl gösterir. Belirli durumlarda PII günlüğe bir uygulamada hata ayıklama içinde önemli olabilir ancak varsayılan olarak, bilinen PII günlüğünü devre dışı. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ayrıca, bu örnek, izleme ve iletileri günlüğe kaydetme kullanır. Daha fazla bilgi için [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek.  
  
## <a name="encrypting-configuration-file-elements"></a>Yapılandırma dosyası öğeleri şifreleme  
 Paylaşılan Web barındırma ortamında güvenlik nedenleriyle, hassas bilgiler içerebilir, veritabanı bağlantı dizeleri gibi belirli yapılandırma öğelerini şifreleme istenebilir. Örneğin, % WINDIR%\Micrsoft.NET\Framework\v4.0.20728 .NET Framework klasörde bulunan aspnet_regiis.exe aracını kullanarak bir yapılandırma öğesi şifrelenmelidir.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Değerleri için örnek Web.config dosyasındaki appSettings bölümündeki şifrelemek için  
  
1. Açık bir komut istemi kullanarak Başlat -> Çalıştır... Yazın `cmd` tıklatıp **Tamam**.  
  
2. Aşağıdaki komutu gönderdikten tarafından geçerli .NET Framework dizinine gidin: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3. Aşağıdaki komutu gönderdikten tarafından Web.config klasöründe appSettings yapılandırma ayarlarını şifrele: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 ASP.NET yapılandırması dpapı'ye bir nasıl yapılır okuyarak yapılandırma dosyalarını bölümlerini şifreleme hakkında daha fazla bilgi bulunabilir ([Güvenli ASP.NET uygulamaları: Kimlik doğrulaması, yetkilendirme ve güvenli iletişimi](https://go.microsoft.com/fwlink/?LinkId=95137)) ve ASP.NET yapılandırma RSA üzerinde bir nasıl yapılır ([nasıl yapılır: ASP.NET 2.0 yapılandırma bölümleri şifrelemek RSA kullanarak](https://go.microsoft.com/fwlink/?LinkId=95138)).  
  
## <a name="locking-configuration-file-elements"></a>Kilitleme yapılandırma dosyası öğeleri  
 Web barındırılan senaryolarda Hizmetleri Hizmetleri dizinlerde olması mümkündür. Bu gibi durumlarda, hizmet alt dizinindeki yapılandırma değerlerini Machine.Config'deki değerlerini inceleme ve sırayla tüm üst dizinlerin dizin ağacında taşıma ve son birleştirme Web.config dosyalarında ile birleştiriliyor hesaplanır Web.config dosyasında hizmet içeren dizin. Çoğu yapılandırma öğeleri için varsayılan davranış, alt üst dizinlerin ayarlanan değerleri geçersiz kılmak için yapılandırma dosyalarında izin vermektir. Belirli durumlarda alt dizinleri yapılandırma dosyalarında üst dizini yapılandırma değerleri geçersiz kılmasını önlemek için istenebilir.  
  
 .NET Framework yapılandırma dosyası öğeleri kilitli yapılandırma öğeleri geçersiz kılan yapılandırmaları çalışma zamanı özel durumlar, kilitlemek için bir yol sağlar.  
  
 Bir yapılandırma öğesi belirterek kilitlenip `lockItem` öznitelik yapılandırma dosyasında bir düğüm için örneğin, böylece hesaplayıcı Hizmetleri'nde yapılandırma dosyalarını içe CalculatorServiceBehavior düğüm yapılandırma dosyasındaki kilitlemek için değişiklik davranışı, aşağıdaki yapılandırma kullanılabilir olamaz.  
  
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
  
 Yapılandırma öğelerini kilitleme daha belirli olabilir. Öğelerinin bir listesini görmek için bir değer olarak belirtilebilir `lockElements` bir dizi öğeleri alt öğelerinin koleksiyonu içinde kilitlenemedi. Özniteliklerin bir listesi için değer olarak belirtilen `lockAttributes` öznitelikleri bir öğe içinde bir dizi kilitlenemiyor. Bir koleksiyonun tamamını öğeler veya öznitelikleri belirterek dışında belirtilen bir liste kilitlenebilir `lockAllElementsExcept` veya `lockAllAttributesExcept` düğümünde öznitelikleri.  
  
## <a name="pii-logging-configuration"></a>PII günlük kaydı yapılandırması  
 PII günlüğe iki anahtar tarafından denetlenir: bilgisayar genelinde bir ayar izin veren veya reddeden PII PII günlüğe her geçiş yapmak bir uygulama Yöneticisi izin veren bir uygulama ayarı ve günlüğe kaydetme için bilgisayar yöneticisi veren Machine.config bulundu Kaynak Web.config veya App.config dosyasında.  
  
 Bilgisayar genelinde ayarı ayarlanmasıyla denetlenir `enableLoggingKnownPii` için `true` veya `false`, `machineSettings` Machine.config öğesinde. Örneğin, aşağıdaki uygulamaların PII, günlüğü etkinleştirmek sağlar.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Machine.config dosyasının varsayılan konum vardır: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Varsa `enableLoggingKnownPii` Machine.config dosyasına öznitelik yoksa, PII günlüğe izin verilmiyor.  
  
 Bir uygulama ayarlayarak yapılır için PII günlüğü etkinleştirme `logKnownPii` için kaynak öğesinin özniteliği `true` veya `false` Web.config veya App.config dosyasında. Örneğin, aşağıdaki PII, hem ileti günlüğe kaydetme ve izleme günlüğü için günlük kaydını etkinleştirir.  
  
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
  
 PII hem de yalnızca oturum `enableLoggingKnownPii` ayarlanır `true`, ve `logKnownPii` ayarlanır `true`.  
  
> [!NOTE]
>  System.Diagnostics yapılandırma dosyasında listelenen ilk öğe dışında tüm kaynaklarında tüm öznitelikler yok sayar. Ekleme `logKnownPii` yapılandırma dosyasındaki ikinci kaynağına özniteliği etkisizdir.  
  
> [!IMPORTANT]
>  Bu örneği çalıştırmak için Machine.config el ile değiştirilmesini içerir. Yanlış değer veya sözdizimi Machine.config değiştirmek tüm .NET Framework uygulamaların çalıştırılmasını engelleyebilir dikkatli olunması.  
  
 Yapılandırma dosyası öğelerini DPAPI ve RSA kullanarak şifreleme de mümkündür. Daha fazla bilgi için aşağıdaki bağlantılara bakın:  
  
-   [Güvenli bir ASP.NET uygulamaları: Kimlik doğrulaması, yetkilendirme ve güvenli iletişim](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [Nasıl yapılır: ASP.NET 2.0 yapılandırma bölümleri şifrelemek RSA kullanarak](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Ayarlanacak Machine.config Düzenle `enableLoggingKnownPii` özniteliğini `true`, gerekirse, üst düğümleri ekleme.  
  
3. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Örneği temizlemek için  
  
1. Ayarlanacak Machine.config Düzenle `enableLoggingKnownPii` özniteliğini `false`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
