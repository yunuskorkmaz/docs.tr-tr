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
ms.openlocfilehash: 0fae3ac1769163101dcdb183f4c5c2135354b1fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145429"
---
# <a name="application-startup-time"></a>Uygulama Başlangıç Zamanı
Bir WPF uygulamasının başlaması için gereken süre büyük ölçüde değişebilir. Bu konu, bir Windows Sunu Temeli (WPF) uygulaması için algılanan ve gerçek başlangıç süresini azaltmak için çeşitli teknikler açıklar.  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Soğuk Başlangıç ve Sıcak Başlangıç Anlama  
 Soğuk başlatma, uygulamanız bir sistem yeniden başlatıldıktan sonra ilk kez başladığında veya uygulamanızı başlattığınızda, kapatın ve uzun bir süre sonra yeniden başlattığınızda oluşur. Bir uygulama başladığında, gerekli sayfalar (kod, statik veriler, kayıt defteri, vb.) Windows bellek yöneticisinin bekleme listesinde yoksa, sayfa hataları oluşur. Sayfaları belleğe getirmek için disk erişimi gereklidir.  
  
 Sıcak başlatma, ana ortak dil çalışma zamanı (CLR) bileşenlerinin sayfalarının çoğu zaten belleğe yüklendiğinde oluşur ve bu da pahalı disk erişim süresini kurtarır. Bu nedenle yönetilen bir uygulama ikinci kez çalıştığında daha hızlı başlar.  
  
## <a name="implement-a-splash-screen"></a>Sıçrama Ekranı Uygulayın  
 Bir uygulamayı başlatmak ve ilk kullanıcı arasını görüntülemek arasında önemli, kaçınılmaz bir gecikme olduğu durumlarda, *bir sıçrama ekranı*kullanarak algılanan başlangıç süresini optimize edin. Bu yaklaşım, kullanıcı uygulamayı başlattıktan hemen sonra bir görüntü görüntüler. Uygulama ilk kullanıcı kullanıcı kullanıcı sını görüntülemeye hazır olduğunda sıçrama ekranı kaybolur. .NET Framework 3.5 SP1'den başlayarak, <xref:System.Windows.SplashScreen> bir sıçrama ekranı uygulamak için sınıfı kullanabilirsiniz. Daha fazla bilgi için [wpf uygulamasına Sıçrama Ekranı Ekle'ye](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)bakın.  
  
 Ayrıca yerli Win32 grafik kullanarak kendi sıçrama ekranı uygulayabilirsiniz. Yöntem çağrılmadan <xref:System.Windows.Application.Run%2A> önce uygulamanızı görüntüleyin.  
  
## <a name="analyze-the-startup-code"></a>Başlangıç Kodunu Çözümle  
 Yavaş bir soğuk başlangıç nedenini belirleyin. Disk G/Ç sorumlu olabilir, ancak bu her zaman böyle değildir. Genel olarak, ağ, Web hizmetleri veya disk gibi dış kaynakların kullanımını en aza indirmeniz gerekir.  
  
 Sınamadan önce, çalışan başka hiçbir uygulama veya hizmetin yönetilen kod veya WPF kodu kullanmadığını doğrulayın.  
  
 WPF uygulamanızı yeniden başlatmadan hemen sonra başlatın ve görüntülenmesinin ne kadar süreceğini belirleyin. Uygulamanızın sonraki tüm lansmanları (sıcak başlatma) çok daha hızlıysa, soğuk başlangıç sorununuz büyük olasılıkla G/Ç'den kaynaklanır.  
  
 Uygulamanızın soğuk başlatma sorunu G/Ç ile ilgili değilse, uygulamanızın uzun bir başlatma veya hesaplama gerçekleştirmesi, bazı olayın tamamlanmasını beklemesi veya başlangıçta çok sayıda JIT derlemesi gerektirmesi olasıdır. Aşağıdaki bölümlerde bu durumlardan bazıları daha ayrıntılı olarak açıklayınız.  
  
## <a name="optimize-module-loading"></a>Modül Yüklemeyi Optimize Edin  
 Uygulamanızın hangi modülleri yükleşetini belirlemek için Process Explorer (Procexp.exe) ve Tlist.exe gibi araçları kullanın. Komut, `Tlist <pid>` bir işlem tarafından yüklenen tüm modülleri gösterir.  
  
 Örneğin, Web'e bağlanmıyorsanız ve System.Web.dll'nin yüklendiğini görüyorsanız, uygulamanızda bu derlemeye başvuran bir modül vardır. Başvurunun gerekli olduğundan emin olun.  
  
 Uygulamanızda birden çok modül varsa, bunları tek bir modülde birleştirin. Bu yaklaşım daha az CLR montaj yükleme yükü gerektirir. Daha az derleme, CLR'nin daha az durumu koruduğu anlamına da gelir.  
  
## <a name="defer-initialization-operations"></a>Başlatma İşlemlerierteleme  
 Ana uygulama penceresi işlenene kadar başlatma kodunu ertelemeyi düşünün.  
  
 Başlatmanın bir sınıf oluşturucuiçinde gerçekleştirilebileceğini ve başlatma kodu diğer sınıflara başvuruyorsa, birçok sınıf oluşturucunun yürütüldettiği basamaklı bir etkiye neden olabileceğini unutmayın.  
  
## <a name="avoid-application-configuration"></a>Uygulama Yapılandırması kaçının  
 Uygulama yapılandırması kaçınarak düşünün. Örneğin, bir uygulamanın basit yapılandırma gereksinimleri varsa ve katı başlangıç zamanı hedefleri varsa, kayıt defteri girişleri veya basit bir INI dosyası daha hızlı bir başlangıç alternatifi olabilir.  
  
## <a name="utilize-the-gac"></a>GAC'den yararlanın  
 Bir derleme Global Assembly Önbelleğinde (GAC) yüklenmezse, bilgisayarda bu derleme için yerel bir görüntü varsa, güçlü adlandırılmış derlemelerin karma doğrulanması ve Ngen görüntü doğrulamasının neden olduğu gecikmeler vardır. GAC'ye yüklenen tüm derlemeler için güçlü ad doğrulaması atlanır. Daha fazla bilgi için bkz. [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Ngen.exe kullanın  
 Uygulamanızda Yerel Görüntü Jeneratörü 'ni (Ngen.exe) kullanmayı düşünün. Ngen.exe tarafından oluşturulan yerel görüntü MSIL görüntüdaha büyük olması muhtemeldir, çünkü Ngen.exe kullanarak daha fazla disk erişimi için CPU tüketimi ticaret anlamına gelir.  
  
 Sıcak başlangıç süresini iyileştirmek için, uygulama kodunun JIT derlemesinin CPU maliyetini önlediğinden, uygulamanızda her zaman Ngen.exe kullanmanız gerekir.  
  
 Bazı soğuk başlangıç senaryolarında, Ngen.exe'yi kullanmak da yararlı olabilir. Bunun nedeni, JIT derleyicisinin (mscorjit.dll) yüklenmesi gerekmemesidir.  
  
 Hem Ngen hem de JIT modüllerine sahip olmak en kötü etkiyi yaratabilir. Bunun nedeni, mscorjit.dll'nin yüklenmesi ve JIT derleyicisi kodunuz üzerinde çalıştığında, JIT derleyicisi derlemelerin meta verilerini okuduğunda Ngen görüntülerindeki birçok sayfaya erişilmesi gerekir.  
  
### <a name="ngen-and-clickonce"></a>Ngen ve ClickOnce  
 Uygulamanızı dağıtmayı planladığınız yol, yükleme süresi açısından da bir fark yaratabilir. ClickOnce uygulama dağıtımı Ngen'i desteklemez. Uygulamanız için Ngen.exe kullanmaya karar verirseniz, Windows Installer gibi başka bir dağıtım mekanizması kullanmanız gerekir.  
  
 Daha fazla bilgi için [Bkz. Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Rebasing ve DLL Adres Çarpışmaları  
 Ngen.exe kullanıyorsanız, yerel görüntüler belleğe yüklendiğinde yeniden basing oluşabilir unutmayın. Bu adres aralığı zaten tahsis edildiği için bir DLL tercih ettiği temel adrese yüklenmezse, Windows yükleyici sormuş başka bir adrese yükler ve bu işlem zaman alan bir işlem olabilir.  
  
 Tüm sayfaların özel olduğu modüller olup olmadığını kontrol etmek için Sanal Adres Dökümü (Vadump.exe) aracını kullanabilirsiniz. Bu durumda, modül farklı bir adrese yeniden uyarlanmış olabilir. Bu nedenle, sayfaları paylaşılamaz.  
  
 Temel adresi ayarlamak hakkında daha fazla bilgi için [Ngen.exe (Yerel Görüntü Üreteci)](../../tools/ngen-exe-native-image-generator.md)bakın.  
  
## <a name="optimize-authenticode"></a>Authenticode'u Optimize Edin  
 Authenticode doğrulama başlangıç saatine ekler. Authenticode imzalı derlemelerin sertifika yetkilisi (CA) ile doğrulanmaları gerekir. Geçerli sertifika iptal listelerini indirmek için ağa birkaç kez bağlanmanız gerekebileceğinden, bu doğrulama zaman alabilir. Ayrıca, güvenilir bir köke giden yolda geçerli sertifikalardan oluşan tam bir zincir olmasını sağlar. Bu, montaj yüklenirken birkaç saniyelik gecikmeye neden olabilir.  
  
 Ca sertifikasını istemci bilgisayara yüklemeyi düşünün veya mümkün olduğunda Authenticode kullanmaktan kaçının. Uygulamanızın yayımcı kanıtına ihtiyacı olmadığını biliyorsanız, imza doğrulama maliyetini ödemeniz gerekmez.  
  
 .NET Framework 3.5'ten başlayarak, Authenticode doğrulamanın atlanmasını sağlayan bir yapılandırma seçeneği vardır. Bunu yapmak için app.exe.config dosyasına aşağıdaki ayarı ekleyin:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>
    </runtime>  
</configuration>  
```  
  
 Daha fazla bilgi için bkz [ \<>.](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)  
  
## <a name="compare-performance-on-windows-vista"></a>Windows Vista'da Performansı Karşılaştır  
 Windows Vista'daki bellek yöneticisinin SuperFetch adında bir teknolojisi vardır. SuperFetch, belirli bir kullanıcı için en uygun bellek içeriğini belirlemek için zaman içinde bellek kullanım düzenlerini analiz eder. Bu içeriği her zaman korumak için sürekli çalışır.  
  
 Bu yaklaşım, kullanım desenlerini çözümlemeden verileri belleğe önceden yükleyen Windows XP'de kullanılan ön getirme tekniğinden farklıdır. Zaman içinde, kullanıcı WPF uygulamanızı Windows Vista'da sık sık kullanırsa, uygulamanızın soğuk başlangıç süresi artabilir.  
  
## <a name="use-appdomains-efficiently"></a>AppDomains'i Verimli Kullanın  
 Mümkünse, yerel görüntünün varsa uygulamada oluşturulan tüm AppDomains'lerde kullanıldığından emin olmak için derlemeleri etki alanından bağımsız bir kod alanına yükleyin.  
  
 En iyi performans için, etki alanları arası çağrıları azaltarak etkili etki alanları arası iletişimi uygulayın. Mümkün olduğunda, bağımsız değişkenler olmadan veya ilkel tür bağımsız değişkenleri ile aramaları kullanın.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>NeutralResourcesLanguage Özniteliğini Kullanma  
 Için <xref:System.Resources.NeutralResourcesLanguageAttribute> nötr kültürü belirtmek için <xref:System.Resources.ResourceManager>kullanın. Bu yaklaşım, başarısız derleme aramalarını önler.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Serialization için BinaryFormatter Sınıfını Kullanma  
 Serileştirme kullanmanız gerekiyorsa, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Xml.Serialization.XmlSerializer> sınıf yerine sınıfı kullanın. Sınıf, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> mscorlib.dll derlemesinde Temel Sınıf Kitaplığı'nda (BCL) uygulanır. System.Xml.dll <xref:System.Xml.Serialization.XmlSerializer> montajında uygulanır, bu da yüklemek için ek bir DLL olabilir.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Sınıfı kullanmanız gerekiyorsa, serileştirme derlemesini önceden oluşturursanız daha iyi performans elde edebilirsiniz.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Başlangıç Tarihinden Sonra Güncelleştirmeleri Denetlemek Için ClickOnce'yi Yapılandır  
 Uygulamanız ClickOnce kullanıyorsa, uygulama başladıktan sonra dağıtım sitesini güncelleştirmeleri denetlemek için ClickOnce'yi yapılandırarak başlangıç tarihinde ağ erişiminden kaçının.  
  
 XAML tarayıcı uygulaması (XBAP) modelini kullanıyorsanız, XBAP clickonce önbelleğinde olsa bile ClickOnce'nin dağıtım sitesini güncelleştirmeler için denetlediğini unutmayın. Daha fazla bilgi için [ClickOnce Güvenlik ve Dağıtım'a](/visualstudio/deployment/clickonce-security-and-deployment)bakın.  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>PresentationFontCache Hizmetini Otomatik Olarak Başlatacak Şekilde Yapılandırın  
 Yeniden başlatıldıktan sonra çalıştırılanacak ilk WPF uygulaması PresentationFontCache hizmetidir. Hizmet, sistem yazı tiplerini önbelleğe alıyor, yazı tipi erişimini geliştirir ve genel performansı artırır. Hizmeti başlatmada bir ek yükü vardır ve bazı denetimli ortamlarda, sistem yeniden başlatıldığında hizmeti otomatik olarak başlatacak şekilde yapılandırmayı düşünün.  
  
## <a name="set-data-binding-programmatically"></a>Veri Bağlamayı Programlı Olarak Ayarlama  
 Ana pencereiçin <xref:System.Windows.FrameworkElement.DataContext%2A> bildirimsel olarak ayarlamak için XAML kullanmak yerine, yöntemde <xref:System.Windows.Application.OnActivated%2A> programlı olarak ayarlamayı düşünün.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.SplashScreen>
- <xref:System.AppDomain>
- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- <xref:System.Resources.ResourceManager>
- [WPF Uygulamasına Giriş Ekranı Ekleme](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)
- [Ngen.exe (Yerel Görüntü Oluşturucu)](../../tools/ngen-exe-native-image-generator.md)
- [\<PublisherEvidence> Öğesi'ni oluşturur](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
