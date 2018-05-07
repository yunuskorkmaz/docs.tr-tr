---
title: Uygulama Başlangıç Zamanı
ms.date: 03/30/2017
helpviewer_keywords:
- splash screen [WPF], startup time
- WPF [WPF], startup time
- startup time [WPF]
- application startup [WPF]
- performance [WPF], startup time
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
ms.openlocfilehash: 8452c41bc6d60d18fa058966299e3ca2b989604f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="application-startup-time"></a>Uygulama Başlangıç Zamanı
Bir WPF uygulaması başlatmak gerekli süreyi büyük ölçüde farklılık gösterebilir. Bu konuda, bir Windows Presentation Foundation (WPF) uygulaması için algılanan ve fiili başlangıç zamanını azaltmak için çeşitli teknikleri açıklar.  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Soğuk Başlangıcı ve Sıcak Başlangıcı Anlama  
 Uygulamanızı bir sistem yeniden başlatma işleminden sonra ilk kez başlatıldığında soğuk başlangıç oluşur veya uygulamanızın başlattığınızda kapatın ve sonra yeniden bir uzun süre sonra Başlat. Bir uygulama başlatıldığında gerekli sayfalar (kod, statik verileri, kayıt defteri, vb.) Windows Bellek Yöneticisi'nin bekleme listesinde mevcut değilse, sayfa hataları oluşur. Disk erişimi sayfaları belleğe taşımak için gereklidir.  
  
 Sıcak başlangıç ana ortak dil çalışma zamanı (CLR) bileşenlerini sayfaların çoğu pahalı disk erişim süresini kaydeder bellekte zaten yüklenmiş olan oluşur. İkinci kez çalıştırıldığında bir yönetilen uygulamayı daha hızlı başlamasının nedeni budur.  
  
## <a name="implement-a-splash-screen"></a>Uygulama giriş ekranı  
 Kaçınılmaz durumlarda, ilk UI görüntüleme ve uygulama başlatma arasında gecikme, algılanan başlangıç zamanını kullanarak iyileştirin bir *ekranı*. Bu yaklaşım görüntüyü hemen görüntüler sonra kullanıcı uygulamayı başlatır. Uygulamayı ilk kullanıcı Arabiriminde görüntülenecek hazır olduğunda, giriş ekranı kaybolur. İtibariyle [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], kullanabileceğiniz <xref:System.Windows.SplashScreen> Karşılama ekranı uygulamak için sınıf. Daha fazla bilgi için bkz: [WPF uygulaması için bir giriş ekranı eklemek](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Ayrıca, yerel Win32 grafiğini kullanarak kendi giriş ekranı uygulayabilirsiniz. Önce uygulamanızı görüntüleyin <xref:System.Windows.Application.Run%2A> yöntemi çağrılır.  
  
## <a name="analyze-the-startup-code"></a>Başlangıç kodu çözümleme  
 Yavaş soğuk başlangıç nedenini belirleyin. Disk g/ç sorumlu olabilir, ancak bu her zaman geçerli değildir. Genel olarak, ağ, Web Hizmetleri veya disk gibi dış kaynakların kullanımını en aza.  
  
 Test önce hiçbir diğer çalışan uygulamalara veya hizmetlere yönetilen kodu veya WPF kodunu kullandığından emin olun.  
  
 WPF uygulamanızı bir yeniden başlatma işleminden hemen sonra başlatmak ve görüntülemek için gereken süreyi belirler. Uygulamanızın (sıcak başlatma) sonraki tüm başlatmaları çok daha hızlı olması durumunda, soğuk başlatma sorunu g/ç tarafından kaynaklanıyordur.  
  
 Uygulamanızın soğuk, başlatma sorununu g/ç için uygulamanızın bazı uzun başlatma veya hesaplama, tamamlamak bazı olay bekler gerçekleştirir olabilir ilişkili değil veya çok sayıda JIT derleme başlangıçta gerektirir. Aşağıdaki bölümlerde bu durumlardan daha ayrıntılı bazıları açıklanmaktadır.  
  
## <a name="optimize-module-loading"></a>Modül yüklemesini iyileştirme  
 Kullanım, uygulamanızın modüllerine belirlemek için işlem Gezgini'ni (Procexp.exe) ve Tlist.exe gibi araçları yükler. Komut `Tlist <pid>` işlemi tarafından yüklenen tüm modülleri gösterir.  
  
 Örneğin, Web bağlanan değil System.Web.dll yüklenir, ardından uygulamanızda bir modül olduğunu görürseniz, bu derlemeye başvurur. Başvuru gerekli olduğundan emin olmak için kontrol edin.  
  
 Uygulamanız birden fazla modülü varsa, bunları tek bir modüle birleştirin. Bu yaklaşım, daha az CLR derleme-yükleme yükü gerektirir. Daha az derleme CLR daha az durumunu koruyan anlamına gelir.  
  
## <a name="defer-initialization-operations"></a>Başlatma işlemlerini erteleme  
 Ana uygulama penceresi işlendikten sonra kadar başlatma kodunu ertelemeyi düşünün.  
  
 Başlatma bir sınıf oluşturucusu içinde gerçekleştirilebilir ve başlatma kodu diğer sınıflara başvurursa, birçok sınıf oluşturucular yürütüldüğü bir efektine neden olabileceğini unutmayın.  
  
## <a name="avoid-application-configuration"></a>Uygulama yapılandırması kaçının  
 Uygulama yapılandırması önleme göz önünde bulundurun. Örneğin, bir uygulama basit yapılandırma gereksinimleri vardır ve katı başlangıç amaçlarına sahipse, kayıt defteri girdileri veya basit INI dosyası daha hızlı bir başlangıç alternatif olabilir.  
  
## <a name="utilize-the-gac"></a>GAC kullanma  
 Bir derlemeyi Genel Derleme Önbelleği'ne (GAC) yüklü değilse bu derleme için doğal bir görüntü bilgisayarda kullanılabilir ise tanımlayıcı adlı derlemeler karma doğrulanması ve Ngen tarafından kaynaklanan gecikmeler vardır. Tanımlayıcı ad doğrulaması GAC'de yüklü tüm derlemeler için atlanır. Daha fazla bilgi için bkz: [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Ngen.exe kullanma  
 Uygulamanızda yerel Görüntü Oluşturucu (Ngen.exe) kullanmayı düşünün. Ngen.exe kullanarak Ngen.exe tarafından oluşturulan yerel görüntü büyük olasılıkla MSIL görüntüden daha büyük olduğu için daha fazla disk erişimi için CPU tüketimi ticaret anlamına gelir.  
  
 Bu uygulama kodunun JIT derleme CPU maliyetini önler çünkü sıcak başlangıç zamanını geliştirmek için her zaman Ngen.exe uygulamanızda kullanmanız gerekir.  
  
 Bazı soğuk başlangıç senaryolarda Ngen.exe kullanarak da yararlı olabilir. JIT Derleyici (mscorjit.dll) yüklenecek olmadığından budur.  
  
 Ngen ve JIT modülleri olan en kötü etkisi olabilir. Mscorjit.dll yüklenmesi gereken ve JIT Derleyici kodunuz üzerinde çalışırken, JIT derleyicisi derlemelerin meta verilerini okuduğunda Ngen görüntülerindeki birçok sayfa erişilmesi gerekir çünkü budur.  
  
### <a name="ngen-and-clickonce"></a>Ngen ve ClickOnce  
 Uygulamanızı dağıtmak için planladığınız yol, yükleme zamanında bir fark de yapabilirsiniz. [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] uygulama dağıtımı Ngen desteklemez. Uygulamanız için Ngen.exe kullanmaya karar verirseniz, Windows Installer gibi başka bir dağıtım mekanizması kullanması gerekir.  
  
 Daha fazla bilgi için bkz: [Ngen.exe (yerel Görüntü Oluşturucu)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Yeniden Temellendirme ve DLL adres çakışması  
 Ngen.exe kullanırsanız, yerel görüntüler belleğe yüklendiğinde yeniden Temellendirme oluşabileceğini unutmayın. Windows Yükleyici adres aralığı zaten ayrılmış olduğundan DLL tercih edilen temel adrese yüklenmezse uzun süren bir işlem olabilir, başka bir adresinde yükler.  
  
 Tüm sayfaları özel modüller olup olmadığını denetlemek için sanal adres dökümü (Vadump.exe) aracını kullanabilirsiniz. Bu durumda, modülü farklı bir adres temellendirilebilir. Bu nedenle, kendi sayfaları paylaşılamaz.  
  
 Temel adres ayarlama hakkında daha fazla bilgi için bkz: [Ngen.exe (yerel Görüntü Oluşturucu)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="optimize-authenticode"></a>Authenticode en iyi duruma getirme  
 Authenticode doğrulaması başlangıç zamanına ekler. Authenticode imzalı derlemelerin sertifika yetkilisi (CA) ile doğrulanması gerekir. Geçerli sertifika iptal listelerini indirmek için birkaç kez ağ bağlantısı gerektirebilir çünkü bu doğrulama zaman alıcı olabilir. Ayrıca, tam bir güvenilen kök yolunda geçerli bir sertifika zinciri olduğundan emin olur. Derleme yüklenirken bu gecikme birkaç saniye çevirebilir.  
  
 CA sertifikasını istemci bilgisayara yüklemeyi göz önünde bulundurun ve mümkün olduğunda Authenticode kullanmaktan kaçının. Uygulamanızın yayımcı kanıt gerekmez biliyorsanız, imza doğrulaması maliyetini ödemeniz gerekmez.  
  
 İtibariyle [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], Authenticode doğrulamasının atlanmasına izin veren bir yapılandırma seçeneği yoktur. Bunu yapmak için app.exe.config dosyasına aşağıdaki ayarı ekleyin:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 Daha fazla bilgi için bkz: [ \<generatePublisherEvidence > öğesi](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Windows Vista performans karşılaştırma  
 Windows Vista Bellek yöneticisinde hızlı getirme adlı bir teknolojiye sahiptir. Hızlı getirme, belirli bir kullanıcı için en iyi bellek içeriğini belirlemek için zaman içinde bellek kullanım desenlerini çözümler. Her zaman bu içeriği korumak için sürekli çalışmaktadır.  
  
 Bu yaklaşım kullanım desenlerini çözümleme olmadan veri belleğe önceden yükler Windows XP'de kullanılan getirme öncesi teknik farklıdır. Kullanıcı, WPF uygulaması Windows Vista'da sık kullanıyorsa, zaman içinde uygulamanızın soğuk başlangıç zamanını artırabilir.  
  
## <a name="use-appdomains-efficiently"></a>Uygulama etki alanları verimli şekilde kullanma  
 Mümkünse, yerel görüntü varsa, uygulama içinde oluşturulan tüm appdomains oluşturuyor kullanıldığını emin olmak için bir etki alanı Tarafsız kodu alanına derlemeler yükleme.  
  
 En iyi performans için etki alanları arası çağrılar azaltarak verimli etki alanları arası iletişimi uygulayın. Mümkün olduğunda, çağrıları bağımsız değişkenler olmadan veya ilkel tür bağımsız değişkeni kullanın.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>NeutralResourcesLanguage özniteliğini kullanın  
 Kullanım <xref:System.Resources.NeutralResourcesLanguageAttribute> için bağımsız kültür belirtmek üzere <xref:System.Resources.ResourceManager>. Bu yaklaşım başarısız derleme aramalarını önler.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Serileştirme için BinaryFormatter sınıfını kullanma  
 Serileştirme kullanmanız gerekiyorsa kullanın <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sınıfının yerine <xref:System.Xml.Serialization.XmlSerializer> sınıfı. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Sınıfı mscorlib.dll derlemesindeki temel sınıf kitaplığı (BCL) içinde uygulanır. <xref:System.Xml.Serialization.XmlSerializer> Yüklemek için ek bir DLL olabilen System.xml.dll içinde uygulanır.  
  
 Kullanmanız gerekiyorsa <xref:System.Xml.Serialization.XmlSerializer> sınıfı, elde edebileceğiniz daha iyi performans serileştirme derlemesini önceden oluşturursanız.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Güncelleştirmeleri denetlemek için ClickOnce başlatma işleminden sonra yapılandırma  
 Uygulamanız kullanıyorsa [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], ağ erişimi başlangıçta yapılandırmamak [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] uygulama başladıktan sonra güncelleştirmeler için dağıtım sitesini denetlemek için.  
  
 XAML tarayıcısı uygulaması (XBAP) modelini kullanırsanız, aklınızda [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] XBAP zaten olsa bile güncelleştirmeler için dağıtım sitesini denetler [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] önbelleği. Daha fazla bilgi için bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Otomatik olarak başlatmak için PresentationFontCache hizmetini yapılandırma  
 Bir yeniden başlatmadan sonra çalıştırmak için ilk WPF uygulaması PresentationFontCache hizmetidir. Hizmetin sistem yazı tiplerini önbellekler, yazı tipi erişimini geliştirir ve genel performansı iyileştirir. Bir ek yük hizmeti başlatılıyor ve denetlenen bazı ortamlarda, hizmeti sistem yeniden başladığında otomatik olarak başlayacak şekilde yapılandırmayı deneyin.  
  
## <a name="set-data-binding-programmatically"></a>Veri bağlamayı programlı olarak ayarlama  
 Ayarlamak için XAML kullanmak yerine <xref:System.Windows.FrameworkElement.DataContext%2A> bildirimli olarak için ana penceresinde, programlı olarak ayarlamayı göz önünde bulundurun <xref:System.Windows.Application.OnActivated%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.SplashScreen>  
 <xref:System.AppDomain>  
 <xref:System.Resources.NeutralResourcesLanguageAttribute>  
 <xref:System.Resources.ResourceManager>  
 [WPF Uygulamasına Giriş Ekranı Ekleme](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)  
 [Ngen.exe (Yerel Görüntü Oluşturucu)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 [\<generatePublisherEvidence > öğesi](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
