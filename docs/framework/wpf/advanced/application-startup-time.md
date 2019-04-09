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
ms.openlocfilehash: 72207861850875f08786401aacf7b911b2a5b1f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173036"
---
# <a name="application-startup-time"></a>Uygulama Başlangıç Zamanı
Bir WPF uygulamasını başlatmak gerekli süreyi büyük ölçüde farklılık gösterebilir. Bu konuda, bir Windows Presentation Foundation (WPF) uygulaması için algılanan ve gerçek başlangıç süresini azaltmak için çeşitli teknikler açıklanır.  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Soğuk başlangıç ve orta Gecikmeli Başlangıç anlama  
 Uygulamanız bir sistem yeniden başlatma işleminden sonra ilk kez başlatıldığında, soğuk başlangıç oluşur veya uygulamanızı başlatın, kapatın ve sonra zaman uzun süre sonra yeniden başlatın. Bir uygulamayı başlatır (kod, statik veriler, kayıt defteri, vb.) gerekli sayfalar Windows Bellek Yöneticisi'nin bekleme listesinde mevcut değilse, sayfa hataları ortaya çıkar. Disk erişimi sayfaları belleğe taşımak için gereklidir.  
  
 Orta Gecikmeli Başlangıç sayfaları ana ortak dil çalışma zamanı (CLR) bileşenleri için birçok pahalı disk erişim süresi kaydeder bellekte zaten yüklenmiş olan oluşur. İkinci kez yürütüldüğünde bir yönetilen uygulama daha hızlı başlatılan nedeni budur.  
  
## <a name="implement-a-splash-screen"></a>Uygulama giriş ekranı  
 Kaçınılmaz durumlarda, uygulama başlatma ve ilk kullanıcı arabirimini görüntüleyen arasındaki gecikme, kullanarak algılanan başlangıç zamanını iyileştirme bir *giriş ekranı*. Bu yaklaşım, hemen bir resim görüntüler sonra kullanıcı uygulamayı başlatır. Uygulama ilk kullanıcı arabirimini görüntülemek hazır olduğunda, giriş ekranı belirerek. İtibariyle [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], kullanabileceğiniz <xref:System.Windows.SplashScreen> giriş ekranı uygulamak için sınıfı. Daha fazla bilgi için [WPF uygulamasına giriş ekranı ekleme](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Ayrıca, yerel Win32 grafikler kullanarak kendi giriş ekranı uygulayabilirsiniz. Önce uygulamanızı görüntüleyin <xref:System.Windows.Application.Run%2A> yöntemi çağrılır.  
  
## <a name="analyze-the-startup-code"></a>Başlangıç kodunu çözümleme  
 Yavaş bir soğuk başlangıç nedeni belirleyin. Disk g/ç sorumlu olabilir, ancak bu her zaman böyle değildir. Genel olarak, ağ, Web Hizmetleri veya disk gibi dış kaynakların kullanımını olabildiğince az tutmalısınız.  
  
 Test etmeden önce diğer çalışan uygulamaları veya hizmetleri yönetilen kod veya WPF kod kullandığından emin olun.  
  
 WPF uygulamanızı yeniden başlattıktan sonra hemen Başlat ve görüntülemek için ne kadar süreceğini belirlemek. Tüm sonraki başlatır (Orta Gecikmeli Başlatma), uygulamanızın daha hızlı bir şekilde, soğuk başlangıç sorununuzu g/ç tarafından büyük olasılıkla kaynaklanır.  
  
 Uygulamanızın soğuk, başlangıç sorunu g/ç için bu büyük olasılıkla uygulama bazı uzun başlatma veya tamamlamak bazı olay bekler olan hesaplamayı gerçekleştiren ilişkili değil veya JIT derlemesi başlangıçta çok fazla gerektirir. Aşağıdaki bölümlerde daha ayrıntılı bir şekilde bu durumlardan bazıları açıklanmaktadır.  
  
## <a name="optimize-module-loading"></a>Modül yükleme en iyi duruma getirme  
 Kullanın uygulamanızı Process Explorer (Procexp.exe) ve hangi modüllerin belirlemek için Tlist.exe gibi araçları yükler. Komut `Tlist <pid>` bir işlem tarafından yüklenen modülleri gösterir.  
  
 Örneğin, Web bağlanan System.Web.dll yüklendikten sonra uygulamanızda bir modül olduğunu görürseniz, bu derlemeye başvurur. Başvurunun gerekli olduğundan emin olun.  
  
 Uygulamanız birden çok modül varsa, bunları tek bir modüle birleştirin. Bu yaklaşım, daha az CLR derleme Yükleme ek yükü gerektirir. Daha az derlemeleri CLR'ın daha az durumunu koruyan anlamına gelir.  
  
## <a name="defer-initialization-operations"></a>Başlatma işlemleri erteleme  
 Ana uygulama penceresini oluşturulduğunda kadar başlatma kodunu ertelemeyi düşünün.  
  
 Bir sınıf oluşturucusu içinde başlatma gerçekleştirilebilir ve diğer sınıfları başlatma kodu başvuruda bulunuyorsa, birçok sınıf oluşturucuları yürütüldüğü bir basamaklandırma efektini neden olabilir unutmayın.  
  
## <a name="avoid-application-configuration"></a>Uygulama yapılandırması kaçının  
 Uygulama yapılandırması önleme göz önünde bulundurun. Örneğin, kayıt defteri girdileri veya basit bir INI dosyasını uygulama basit yapılandırma gereksinimleri ve katı başlangıç süresi amaçlarını varsa, daha hızlı bir başlangıç alternatif olabilir.  
  
## <a name="utilize-the-gac"></a>GAC kullanma  
 Bir derlemeyi Genel Derleme Önbelleği'ne (GAC) yüklü değilse, bilgisayar üzerinde o derleme için bir yerel görüntü varsa, karma doğrulaması tanımlayıcı adlı derlemelerin ve Ngen tarafından neden gecikmeler vardır. GAC'de kurulu tüm derlemeler için tanımlayıcı ad doğrulama atlandı. Daha fazla bilgi için [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Ngen.exe kullanın  
 Uygulamanızda Native Image Generator (Ngen.exe) kullanmayı düşünün. Ngen.exe kullanarak, Ngen.exe ile oluşturulan yerel görüntü büyük olasılıkla MSIL görüntüsü daha büyük olduğu için daha fazla disk erişimi için CPU tüketimi alım-satım anlamına gelir.  
  
 Bu uygulama kodunun JIT derlemesi CPU maliyeti önlediği için Orta Gecikmeli Başlangıç süresini artırmak için her zaman Ngen.exe uygulamanızda kullanmanız gerekir.  
  
 Soğuk başlangıç bazı senaryolarda, Ngen.exe kullanarak da yararlı olabilir. Bu durum, JIT derleyicisi (mscorjit.dll) yüklenmesi gerekmez çünkü.  
  
 Ngen hem JIT modülleri sahip, en kötü bir etkisi olabilir. Bu mscorjit.dll yüklenmesi gereken ve JIT derleyicisi kodunuz üzerinde çalışırken, JIT Derleyici derlemelerin meta verilerini okuduğunda Ngen görüntülerinin birçok sayfalarında erişilmelidir olmasıdır.  
  
### <a name="ngen-and-clickonce"></a>Ngen ve ClickOnce  
 Uygulamanızı dağıtmayı planladığınız yolu bir fark yükleme süresi de yapabilirsiniz. [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] Ngen uygulaması dağıtımını desteklemez. Uygulamanız için Ngen.exe kullanmaya karar verirseniz, Windows Installer gibi başka bir dağıtım mekanizmasının kullanılması gerekir.  
  
 Daha fazla bilgi için [Ngen.exe (yerel Görüntü Oluşturucu)](../../tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Yeniden Temellendirme ve DLL adres çakışması  
 Ngen.exe kullanıyorsanız, yerel görüntüler belleğe yüklendiğinde yeniden Temellendirme oluşabileceğini unutmayın. Windows Yükleyici DLL zaten ayrılmış adres aralığı için tercih edilen temel adresinde yüklenmezse, zaman alıcı bir işlem, başka bir adreste yükler.  
  
 Tüm sayfaları özel modüller olup olmadığını denetlemek için sanal adres dökümü (Vadump.exe) aracını kullanabilirsiniz. Bu durumda, modülü farklı bir adres ReBase işlemi gerçekleştirildi. Bu nedenle, sayfalarını paylaşılamaz.  
  
 Temel adresini ayarlama hakkında daha fazla bilgi için bkz. [Ngen.exe (yerel Görüntü Oluşturucu)](../../tools/ngen-exe-native-image-generator.md).  
  
## <a name="optimize-authenticode"></a>Authenticode en iyi duruma getirme  
 Authenticode doğrulama başlangıç zamanına ekler. Authenticode imzalı derlemelerin sertifika yetkilisi (CA) ile doğrulanması gerekir. Geçerli sertifika iptal listeleri indirmek için birkaç kez ağa bağlamak isteyebilirsiniz, çünkü bu doğrulamayı zaman alıcı olabilir. Ayrıca, tam bir güvenilen kök yolu geçerli sertifika zinciri olduğundan emin olur. Derleme yüklenirken bu gecikme birkaç saniye çevirebilir.  
  
 CA sertifika istemci bilgisayara yüklemeyi göz önünde bulundurun ve mümkün olduğunda Authenticode kullanmaktan kaçının. Uygulamanızı yayımcı kanıt gerekmeyen biliyorsanız, imza doğrulama ücreti ödersiniz gerekmez.  
  
 İtibariyle [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], Authenticode doğrulama atlanmasına izin veren bir yapılandırma seçeneği yoktur. Bunu yapmak için aşağıdaki ayarı app.exe.config dosyasına ekleyin:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 Daha fazla bilgi için [ \<generatePublisherEvidence > öğe](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Windows Vista performans karşılaştırın  
 Windows Vista Bellek yöneticisinde hızlı getirme adı verilen bir teknoloji var. Hızlı getirme, belirli bir kullanıcı için en iyi bellek içeriğini belirlemek için zaman içinde bellek kullanım desenlerini analiz eder. Her zaman bu içeriği korumak için sürekli olarak çalışır.  
  
 Bu yaklaşım, veri, kullanım biçimlerini çözümleme olmadan belleğe önceden yükler Windows XP'de kullanılan getirme öncesi teknik farklıdır. Kullanıcı WPF uygulamanızı Windows Vista'da sık kullanıyorsa, zaman içinde uygulamanızın soğuk başlangıç süresini artırabilir.  
  
## <a name="use-appdomains-efficiently"></a>Uygulama etki alanları verimli şekilde kullanma  
 Mümkünse, varsa, yerel görüntü uygulama içinde oluşturulan tüm uygulama etki alanları kullanıldığını emin olmak için bir alan-bağımsız kod alanına derlemeler yükleme.  
  
 En iyi performans için etki alanları arası çağrılar azaltarak verimli etki alanları arası iletişimi uygular. Mümkün olduğunda, çağrıları bağımsız değişkenler olmadan veya ilkel tür bağımsız değişkenleri kullanın.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>NeutralResourcesLanguage özniteliği kullanın  
 Kullanım <xref:System.Resources.NeutralResourcesLanguageAttribute> bağımsız kültür için belirtmek üzere <xref:System.Resources.ResourceManager>. Bu yaklaşım, başarısız derleme aramalarını önler.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>BinaryFormatter sınıfı seri hale getirme için kullanın.  
 Serileştirme kullanmanız gerekirse kullanmak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sınıfı yerine <xref:System.Xml.Serialization.XmlSerializer> sınıfı. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Sınıfı mscorlib.dll derlemesindeki Temel Class Library (BCL) olarak uygulanır. <xref:System.Xml.Serialization.XmlSerializer> Yüklemek için ek bir DLL olabilecek System.xml.dll içinde uygulanır.  
  
 Kullanmanız gerekirse <xref:System.Xml.Serialization.XmlSerializer> sınıfı elde edebileceğiniz daha iyi performans serileştirme bütünleştirilmiş kodu önceden oluşturursanız.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Başlangıcından sonra güncelleştirmeleri denetleme için ClickOnce yapılandırın  
 Uygulamanız kullanıyorsa [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], ağ erişimi başlangıçta yapılandırmamak [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] güncelleştirmeler için dağıtım sitesini uygulama başladıktan sonra denetlemek için.  
  
 XAML tarayıcısı uygulaması (XBAP) modeli kullandığınız aklınızda [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] XBAP zaten kullanımda olsa bile dağıtım sitenin güncelleştirmeleri denetler [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] önbellek. Daha fazla bilgi için [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Otomatik olarak başlatmak için PresentationFontCache hizmetini yapılandırma  
 Yeniden başlatma sonrası çalıştırılacak ilk WPF uygulaması PresentationFontCache hizmetidir. Hizmet sistem yazı tiplerini önbelleğe alır, yazı tipi erişim artırır ve genel performansı artırır. Bir ek hizmeti başlatmayı ve denetlenen bazı ortamlarda, sistem yeniden başladığında otomatik olarak başlayacak şekilde hizmeti yapılandırabilirsiniz.  
  
## <a name="set-data-binding-programmatically"></a>Veri bağlamayı programlı olarak ayarlama  
 Ayarlamak için XAML kullanmak yerine <xref:System.Windows.FrameworkElement.DataContext%2A> bildirimli olarak ana penceresi için programlı olarak ayarlamayı göz önünde bulundurun <xref:System.Windows.Application.OnActivated%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.SplashScreen>
- <xref:System.AppDomain>
- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- <xref:System.Resources.ResourceManager>
- [WPF Uygulamasına Giriş Ekranı Ekleme](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)
- [Ngen.exe (Yerel Görüntü Oluşturucu)](../../tools/ngen-exe-native-image-generator.md)
- [\<generatePublisherEvidence > öğe](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
