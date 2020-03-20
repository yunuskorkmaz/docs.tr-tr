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
ms.openlocfilehash: 2f0018dca6e5add2c5bc531103a4078307a8c8c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129843"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a>Fuslogvw.exe (Derleme Bağlaması Günlük Görüntüleyici)

Derleme Bağlama Kayıt Günlüğü Görüntüleyici derleme bağlamalar için ayrıntıları görüntüler. Bu bilgiler .NET Framework'ün çalışma zamanında niye bir derlemeyi bulamadığını tanılamanıza yardımcı olur. Bu hatalar genellikle derlemenin yanlış yere yayınlanması sonucudur, geçerli olmayan yerel bir resim veya kültürlerin uyuşmayan bir sürüm numarası. Ortak dil çalışma zamanının bir derlemeyi bulamaması genellikle <xref:System.TypeLoadException> uygulamanızda bir derleme olarak gösterilmektedir.

> [!IMPORTANT]
> fuslogvw.exe'yi yönetici ayrıcalıklarıyla çalıştırmalısınız.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials. Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

Komut satırına şunu yazın:

```console
fuslogvw
```

Görüntüleyici başarısız bağlanan her derleme için bir girdi gösterir. Her bir başarısızlık için, görüntüleyici bağlamayı ilklendirdiği uygulamayı açıklar; derleme isim, versiyon, kültür ve ortak anahtar dahil kördür; ve başarısızlığın tarih ve saati.

### <a name="to-change-the-log-location-view"></a>Günlük konum görünümünü değiştirmek için

1. Tüm uygulama türleri için bağlama hatalarını görüntülemek için **Varsayılan** seçeneği düğmesini seçin. Varsayılan olarak, wininet önbelleğinde disk üzerinde her kullanıcı dizini içinde günlük kayıtları depolanır.

2. Bağlama hatalarını belirttiğiniz özel bir dizinde görüntülemek için **Özel** seçeneği düğmesini seçin. **Günlük Ayarları** iletişim kutusundaki özel günlük konumunu geçerli bir dizin adı ile ayarlayarak, çalışma zamanının günlükleri depolamasını istediğiniz özel konumu belirtmeniz gerekir. Dizin temiz olmalıdır ve sadece çalışma zamanının oluşturduğu dosyaları içermelidir. Eğer günlüğe kaydedilecek hata üreten bir çalıştırılabilir dosya içeriyorsa, başarısızlık günlüğe kaydedilmeyecek çünkü araç çalıştırılabilir olanla aynı isimde bir dizin yaratmaya çalışacaktır. Buna ek olarak, bir yürütülebilir çalıştırma denemesi bu günlük konumunda başarısız olur.

    > [!NOTE]
    > Varsayılan bağlama konumu özel bağlama konumuna tercih edilir. Çalışma zamanı varsayılan bağlama konumunu wininet önbelleğinde depolar ve bu nedenle otomatik olarak temizler. Özel bir bağlama konumu belirtirseniz, bu konumu temizlemekten siz sorumlusunuz.

### <a name="to-view-details-about-a-specific-failure"></a>Belirli bir kültür hakkında detayları görüntülemek için

1. Görüntüleyiciden istenen uygulamanın girişini seçin.

2. **Günlük'u Görüntüle** düğmesini tıklatın. Alternatif olarak, seçili girdiye çift tıklayabilirsiniz.

    Araç seçili bağlama başarısızlığı hakkında aşağıdaki ayrıntıları görüntüler:

    - "Dosya bulunamadı" veya "sürüm uyuşmazlığı" gibi belirli nedenler bağlamayı başarısız yapabilir.

    - Eğer varsa, adını, uygulamanın kök dizinini (AppBase) ve özel arama yolunun bir açıklamasını içeren bağlama ilklendiren uygulama hakkında bilgi.

    - Derlemenin kimliğine araç tarafından bakılıyor.

    - Herhangi bir uygulama, Yayıncı veya Yönetici sürüm ilkeleri açıklamaya uygulanır.

    - Derlemenin genel derleme [önbelleğinde](../app-domains/gac.md)bulunup bulunmadığı.

    - Tüm algılama URL'lerinin listesi.

Aşağıdaki örnek günlük girdisi başarısız bir derleme bağlama hakkında ayrıntılı bilgi gösterir.

```output
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

2. Girişi **Sil** düğmesini tıklatın.

### <a name="to-delete-all-entries-from-the-log"></a>Günlükten bütün girdileri silmek için

- **Tümünü Sil** düğmesini tıklatın.

### <a name="to-refresh-the-user-interface"></a>Kullanıcı arabirimini yenilemek için

- **Yenile** düğmesini tıklatın. Görüntüleyici çalışırken yeni günlük girdilerini otomatik olarak algılamaz. Bunları görüntülemek için **Yenile** düğmesini kullanmanız gerekir.

### <a name="to-change-the-log-settings"></a>Günlük ayarlarını değiştirmek için

- **Günlük Ayarları** iletişim kutusunu açmak için **Ayarlar** düğmesini tıklatın.

### <a name="to-view-the-about-dialog"></a>Hakkında iletişim kutusunu görüntülemek için

- **Hakkında** düğmesini tıklatın.

## <a name="binding-logs-for-native-images"></a>Özgün Görüntüler için Bağlama Günlükleri

Varsayılan olarak, Fuslogvw.exe normal derleme bağlama isteklerini günlüğe kaydeder. Alternatif olarak, [Ngen.exe (Yerel Görüntü Oluşturucusu)](ngen-exe-native-image-generator.md)kullanılarak oluşturulan yerel görüntüler için montaj bağlarını günlüğe kaydedebilirsiniz.

#### <a name="to-log-assembly-binds-for-native-images"></a>Özgün görüntüler için derleme bağlamalarını günlüğe kaydetmek için

- Günlük **Kategorileri** grubunda, **Yerel Görseller** seçeneği düğmesini seçin.

Aşağıdaki günlük kaydı uygulama için özgün görüntü oluştuğunda varolmayan bir bağımlılıktan kaynaklı bir başarısızlığı gösterir. Eğer çalışma zamanındaki bağımlılık Ngen.exe çalışırken oluşan bağımlılıktan farklıysa, yerel bir görüntü bağlamaya izin vermez.

```output
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

```output
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

Aşağıdaki eylemleri gerçekleştirmek için **Günlük Ayarları** iletişim kutusunu kullanabilirsiniz.

#### <a name="to-disable-logging"></a>Günlüğe kaydetmeyi devre dışı bırakmak için

- **Engellenen** seçeneğini kaydedin.  Bu seçeneğin varsayılan olarak seçili geldiğini unutmayın.

#### <a name="to-log-assembly-binds-in-exceptions"></a>İstisnalar içinde derleme bağlamalarını günlüğe kaydetmek için

- Özel **durum metin** seçeneğinde Oturum Aç düğmesini seçin. İstisna metninin içinde yalnızca füzyon günlük kaydı bilgileri kaydedilir. Tüm bilgileri görmek için diğer seçeneklerden birini kullanın.

  Etki alanı nötr olarak yüklenen derlemelerle ilgili önemli bir not bırakın.

#### <a name="to-log-assembly-bind-failures"></a>Derleme bağlama başarısızlıklarını günlüğe kaydetmek için

- Disk seçeneği **düğmesine günlük bağlama hatalarını** seçin.

  Etki alanı nötr olarak yüklenen derlemelerle ilgili önemli bir not bırakın.

#### <a name="to-log-all-assembly-binds"></a>Tüm derleme bağlamalarını günlüğe kaydetmek için

- Disk seçeneği **düğmesine tüm bağlanan tüm bağlarını** kaydedin.

  Etki alanı nötr olarak yüklenen derlemelerle ilgili önemli bir not bırakın.

> [!IMPORTANT]
> Bir derleme etki alanı nötr olarak yüklendiğinde, <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> örneğin <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType> <xref:System.AppDomainSetup.LoaderOptimization%2A> özelliği ayarlayarak veya , günlüğe kaydetmeyi açmak bazı durumlarda bellek sızdırabilir. Etki alanı nötr modu bir uygulama etki alanına yüklendiğinde ve uygulama etki alanı boşaltıldığında eğer günlük kaydı girişi yapılmışsa bu olur. Günlük girdisi işlem bitene kadar serbest bırakılmayabilir. Bazı hata ayıklayıcılar otomatik olarak günlüğe kaydetmeyi etkinleştirebilir.

#### <a name="to-enable-a-custom-log-path"></a>Özel bir günlük kaydı yolunu etkinleştirmek için

1. Özel **günlük yolunu etkinleştir** düğmesini seçin.

2. Yolu **Özel günlük yolu** metin kutusuna girin.

> [!NOTE]
> [Derleme Bağlama Günlük Görüntüleyicisi (Fuslogvw.exe),](fuslogvw-exe-assembly-binding-log-viewer.md) bağlama günlüğünü depolamak için Internet Explorer (IE) önbelleğini kullanır. IE önbelleğindeki zaman zaman bozulma nedeniyle, [Derleme Bağlama Günlük Görüntüleyicisi (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) bazen görüntüleme penceresinde yeni bağlama günlükleri göstermeyi durdurabilir. Bu bozulmanın sonucu olarak, .NET bağlama altyapısı (füzyon) bağlama günlüğüne yazamaz veya okuyamaz. (Özel bir günlük yolu kullanıyorsanız bu sorunla karşılaşılmez.)  Bozulmayı düzeltmek ve kaynaşın bağlama günlüklerini yeniden göstermesine izin vermek için, geçici internet dosyalarını IE Internet Seçenekleri iletişim kutusundan silerek IE önbelleğini temizleyin.
>
> Yönetilmeyen uygulamanız `IHostAssemblyManager` ve `IHostAssemblyStore` arabirimleri uygulayarak ortak dil çalışma süresini barındırıyorsa, günlük girişleri wininet önbelleğinde depolanamaz.  Bu arabirimleri uygulayan özel barındırmalar için günlük girdilerini görüntülemek için, alternatif bir günlük yolu belirtmelisiniz.

#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a>Windows uygulama kapsayıcısı içinde çalışan uygulamalar için günlük kaydediciyi etkinleştirmek için

1. Önceki prosedürde açıklandığı gibi özel bir günlük yolunu etkinleştirin. Varsayılan olarak, Windows uygulama kapsayıcı içinde çalışan uygulamaların hard disk erişimi sınırlıdır. Uygulama kapsayıcı içerisindeki bütün uygulamalar için belirlediğiniz dizinin okuma/yazma erişim hakkı vardır.

2. Sürükleyici **günlük onay** kutusunu Etkinleştir'i seçin.

    > [!NOTE]
    > Bu kutu yalnızca Windows 8 veya sonrasında etkindir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.TypeLoadException>
- [Araçlar](index.md)
- [Genel Derleme Önbelleği](../app-domains/gac.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
