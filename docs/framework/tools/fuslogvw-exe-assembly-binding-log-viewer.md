---
title: Fuslogvw.exe (Derleme Bağlaması Günlük Görüntüleyici)
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b74321ecc5c945aab74ad8678b23eb4a66046d39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779905"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a>Fuslogvw.exe (Derleme Bağlaması Günlük Görüntüleyici)
Derleme Bağlama Kayıt Günlüğü Görüntüleyici derleme bağlamalar için ayrıntıları görüntüler. Bu bilgiler .NET Framework'ün çalışma zamanında niye bir derlemeyi bulamadığını tanılamanıza yardımcı olur. Bu hatalar genellikle derlemenin yanlış yere yayınlanması sonucudur, geçerli olmayan yerel bir resim veya kültürlerin uyuşmayan bir sürüm numarası. Genellikle bir derlemeyi bulmak için ortak dil çalışma zamanının başarısızlığı olarak görünür bir <xref:System.TypeLoadException> uygulamanızdaki.  
  
> [!IMPORTANT]
>  fuslogvw.exe'yi yönetici ayrıcalıklarıyla çalıştırmalısınız.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için geliştirici komut istemi Visual Studio (veya Windows 7'de Visual Studio komut istemi) için yönetici kimlik bilgileriyle kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
```  
fuslogvw  
```  
  
 Görüntüleyici başarısız bağlanan her derleme için bir girdi gösterir. Her bir başarısızlık için, görüntüleyici bağlamayı ilklendirdiği uygulamayı açıklar; derleme isim, versiyon, kültür ve ortak anahtar dahil kördür; ve başarısızlığın tarih ve saati.  
  
### <a name="to-change-the-log-location-view"></a>Günlük konum görünümünü değiştirmek için  
  
1. Seçin **varsayılan** tüm uygulama türleri için bağlama başarısızlıklarını görmek için seçenek düğmesini. Varsayılan olarak, wininet önbelleğinde disk üzerinde her kullanıcı dizini içinde günlük kayıtları depolanır.  
  
2. Seçin **özel** belirttiğiniz özel bir dizinde bağlama başarısızlıklarını görmek için seçenek düğmesini. Özel Günlük konumu ayarlayarak günlükleri depolamak için çalışma zamanı istediğiniz özel bir konum belirtmeniz gerekir **günlük ayarları** iletişim kutusuna geçerli bir dizin adı. Dizin temiz olmalıdır ve sadece çalışma zamanının oluşturduğu dosyaları içermelidir. Eğer günlüğe kaydedilecek hata üreten bir çalıştırılabilir dosya içeriyorsa, başarısızlık günlüğe kaydedilmeyecek çünkü araç çalıştırılabilir olanla aynı isimde bir dizin yaratmaya çalışacaktır. Buna ek olarak, bir yürütülebilir çalıştırma denemesi bu günlük konumunda başarısız olur.  
  
    > [!NOTE]
    >  Varsayılan bağlama konumu özel bağlama konumuna tercih edilir. Wininet önbelleğindeki varsayılan bağlama konumu çalışma zamanını saklar ve otomatik olarak temizler. Eğer özel bir bağlama konumu belirlerseniz, onu temizlemek sizin sorumluluğunuzdadır.  
  
### <a name="to-view-details-about-a-specific-failure"></a>Belirli bir kültür hakkında detayları görüntülemek için  
  
1. Görüntüleyiciden istenen uygulamanın girişini seçin.  
  
2. Tıklayın **Günlüğü Görüntüle** düğmesi. Alternatif olarak, seçili girdiye çift tıklayabilirsiniz.  
  
     Araç seçili bağlama başarısızlığı hakkında aşağıdaki ayrıntıları görüntüler:  
  
    - "Dosya bulunamadı" veya "sürüm uyuşmazlığı" gibi belirli nedenler bağlamayı başarısız yapabilir.  
  
    - Eğer varsa, adını, uygulamanın kök dizinini (AppBase) ve özel arama yolunun bir açıklamasını içeren bağlama ilklendiren uygulama hakkında bilgi.  
  
    - Derlemenin kimliğine araç tarafından bakılıyor.  
  
    - Herhangi bir uygulama, Yayıncı veya Yönetici sürüm ilkeleri açıklamaya uygulanır.  
  
    - Derleme bulunsa da bulunmasa [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md).  
  
    - Tüm algılama URL'lerinin listesi.  
  
 Aşağıdaki örnek günlük girdisi başarısız bir derleme bağlama hakkında ayrıntılı bilgi gösterir.  
  
```  
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll  
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe  
--- A detailed error log follows.   
  
=== Pre-bind state information ===  
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
 (Fully-specified)  
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\  
LOG: Initial PrivatePath = NULL  
LOG: Dynamic Base = NULL  
LOG: Cache Base = NULL  
LOG: AppName = NULL  
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
===  
  
LOG: Processing DEVPATH.  
LOG: DEVPATH is not set. Falling through to regular bind.  
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).  
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.  
LOG: All probing URLs attempted and failed.  
```  
  
### <a name="to-delete-a-single-entry-from-the-log"></a>Günlük kaydından tek bir girdiyi silmek için  
  
1. Görüntüleyicide bir girdi seçin.  
  
2. Tıklayın **girdiyi Sil** düğmesi.  
  
### <a name="to-delete-all-entries-from-the-log"></a>Günlükten bütün girdileri silmek için  
  
- Tıklayın **Tümünü Sil** düğmesi.  
  
### <a name="to-refresh-the-user-interface"></a>Kullanıcı arabirimini yenilemek için  
  
- Tıklayın **Yenile** düğmesi. Görüntüleyici çalışırken yeni günlük girdilerini otomatik olarak algılamaz. Kullanmalısınız **Yenile** bunları görüntülemek için düğme.  
  
### <a name="to-change-the-log-settings"></a>Günlük ayarlarını değiştirmek için  
  
- Tıklayın **ayarları** açmak için düğmeyi **günlük ayarları** iletişim.  
  
### <a name="to-view-the-about-dialog"></a>Hakkında iletişim kutusunu görüntülemek için  
  
- Tıklayın **hakkında** düğmesi.  
  
## <a name="binding-logs-for-native-images"></a>Özgün Görüntüler için Bağlama Günlükleri  
 Varsayılan olarak, Fuslogvw.exe normal derleme bağlama isteklerini günlüğe kaydeder. Alternatif olarak, kullanılarak oluşturulan yerel görüntüler için derleme bağlamaları oturum [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
#### <a name="to-log-assembly-binds-for-native-images"></a>Özgün görüntüler için derleme bağlamalarını günlüğe kaydetmek için  
  
- İçinde **günlük kategorileri** grubu, select **yerel görüntüleri** seçenek düğmesini.  
  
 Aşağıdaki günlük kaydı uygulama için özgün görüntü oluştuğunda varolmayan bir bağımlılıktan kaynaklı bir başarısızlığı gösterir. Eğer çalışma zamanındaki bağımlılık Ngen.exe çalışırken oluşan bağımlılıktan farklıysa, yerel bir görüntü bağlamaya izin vermez.  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\App.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\App.exe.  
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.  
WRN: No matching native image found.  
LOG: Bind to native image assembly did not succeed. Use IL image.  
```  
  
 Aşağıdaki günlük kaydı yerel görüntünün oluştuğu zamandaki güvenlik ayarlarından farklı bir uygulama çalıştığında bilgisayardaki güvenlik ayarlarından dolayı yerel bir görüntü bağlama başarısız olarak gösterilir.  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80004005. Unspecified error  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\Application101622.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\Application101622.exe.  
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Dependency evaluation succeeded.  
LOG: Validation of dependencies succeeded.  
LOG: Start loading all the dependencies into load context.  
LOG: Loading of dependencies succeeded.  
LOG: Bind to native image succeeded.  
Native image has correct version information.  
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.  
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.  
Discarding native image.  
```  
  
## <a name="the-log-settings-dialog"></a>Günlük Ayarları İletişim Kutusu  
 Kullanabileceğiniz **günlük ayarları** iletişim için aşağıdaki eylemleri gerçekleştirebilirsiniz.  
  
#### <a name="to-disable-logging"></a>Günlüğe kaydetmeyi devre dışı bırakmak için  
  
- Seçin **oturum devre dışı** seçenek düğmesini.  Bu seçeneğin varsayılan olarak seçili geldiğini unutmayın.  
  
#### <a name="to-log-assembly-binds-in-exceptions"></a>İstisnalar içinde derleme bağlamalarını günlüğe kaydetmek için  
  
- Seçin **istisna metninde günlük kaydı** seçenek düğmesini. İstisna metninin içinde yalnızca füzyon günlük kaydı bilgileri kaydedilir. Tüm bilgileri görmek için diğer seçeneklerden birini kullanın.  
  
     Etki alanı nötr olarak yüklenen derlemelerle ilgili önemli bir not bırakın.  
  
#### <a name="to-log-assembly-bind-failures"></a>Derleme bağlama başarısızlıklarını günlüğe kaydetmek için  
  
- Seçin **günlük bağlama başarısızlıklarını diske** seçenek düğmesini.  
  
     Etki alanı nötr olarak yüklenen derlemelerle ilgili önemli bir not bırakın.  
  
#### <a name="to-log-all-assembly-binds"></a>Tüm derleme bağlamalarını günlüğe kaydetmek için  
  
- Seçin **tüm bağlamaları diske oturum** seçenek düğmesini.  
  
     Etki alanı nötr olarak yüklenen derlemelerle ilgili önemli bir not bırakın.  
  
> [!IMPORTANT]
>  Ne zaman bir derleme yüklenen etki alanı nötr, örneğin ayarlayarak <xref:System.AppDomainSetup.LoaderOptimization%2A> özelliğini <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> veya <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, günlüğünün bazı durumlarda bellekte sızıntı. Etki alanı nötr modu bir uygulama etki alanına yüklendiğinde ve uygulama etki alanı boşaltıldığında eğer günlük kaydı girişi yapılmışsa bu olur. Günlük girdisi işlem bitene kadar serbest bırakılmayabilir. Bazı hata ayıklayıcılar otomatik olarak günlüğe kaydetmeyi etkinleştirebilir.  
  
#### <a name="to-enable-a-custom-log-path"></a>Özel bir günlük kaydı yolunu etkinleştirmek için  
  
1. Seçin **etkinleştir özel günlük yolu** seçenek düğmesini.  
  
2. Yolu girin **özel günlük yolu** metin kutusu.  
  
> [!NOTE]
>  [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) saklamak için Internet Explorer (IE) önbelleğini kullanır. IE önbelleğindeki zaman zaman bozulmalar nedeniyle [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) bazen yeni bağlama günlüklerini görüntüleme penceresinde durdurabilir. Bu bozulmanın sonucu olarak, .NET bağlama altyapısı (füzyon) bağlama günlüğüne yazamaz veya okuyamaz. (Eğer özel günlük yolu kullanıyorsanız bu sorunla karşılaşmayabilirsiniz.)  Bozulmayı düzeltmek ve füzyonun bağlama günlük kayıtlarını tekrar göstermesine izin vermek için, IE Internet Seçenekleri iletişim kutusundan geçici internet dosyalarını silerek IE önbelleğini temizleyin.  
>   
>  Uygulama tarafından yönetilmeyen uygulamanız ortak dil çalışma zamanını barındırıyorsa `IHostAssemblyManager` ve `IHostAssemblyStore` arabirimleri, günlük girdileri wininet önbelleğinde saklanamaz depolanamıyor.  Bu arabirimleri uygulayan özel barındırmalar için günlük girdilerini görüntülemek için, alternatif bir günlük yolu belirtmelisiniz.  
  
#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a>Windows uygulama kapsayıcısı içinde çalışan uygulamalar için günlük kaydediciyi etkinleştirmek için  
  
1. Önceki prosedürde açıklandığı gibi özel bir günlük yolunu etkinleştirin. Varsayılan olarak, Windows uygulama kapsayıcı içinde çalışan uygulamaların hard disk erişimi sınırlıdır. Uygulama kapsayıcı içerisindeki bütün uygulamalar için belirlediğiniz dizinin okuma/yazma erişim hakkı vardır.  
  
2. Seçin **modern günlük kaydını etkinleştir** onay kutusu.  
  
    > [!NOTE]
    >  Bu kutu yalnızca Windows 8 veya sonrasında etkindir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.TypeLoadException>
- [Araçlar](../../../docs/framework/tools/index.md)
- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
