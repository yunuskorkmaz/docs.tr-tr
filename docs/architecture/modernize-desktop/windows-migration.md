---
title: Windows 10 geçişi
description: Paketleme ve XAML Adaları gibi Windows 10 özelliklerinde derinlemesine bakış.
ms.date: 09/16/2019
ms.openlocfilehash: cd17088b086a32fd3bb37e617d3a1047acedde0e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423210"
---
# <a name="windows-10-migration"></a>Windows 10 geçişi

Aşağıdaki durumu göz önünde bulundurun: Windows 7 gün içinde geliştirilmiş çalışan bir masaüstü uygulamanız var. WPF teknolojisini bu zamanda kullanabilir ve sorunsuz çalışır, ancak Windows 10 ' da çalıştırdığınızda eski bir kullanıcı arabirimi ve davranışları vardır. Matris gibi bir Futuristic filmi izlerken ve Nokia 8110 cihazını kullanarak Neo 'yu görmediğiniz gibidir. Film 20 yıl sonra harika çalışmaktadır, ancak cihaz modernleştirmesinin avantajlarından faydalanacaktır.

Microsoft, Windows 10 ' un piyasaya çıkmasıyla tabletler ve dokunmatik cihazlar gibi senaryoları desteklemek ve şimdiye kadar her zaman bir Microsoft işletim sistemi için en iyi deneyimi sağlamak üzere birçok yenilikler getirmiştir. Örneğin, şunları yapabilirsiniz:

- Windows Hello kullanarak yüzle oturum açın.
- Otomatik olarak tanınan ve dijitalleştirilmiş bir metin çizmek ya da yazmak için bir kalem kullanın.
- Wınml kullanarak bulutta oluşturulmuş yerel olarak özelleştirilmiş AI modellerini çalıştırın.

Bu özelliklerin tümü Windows Çalışma Zamanı (WinRT) kitaplıkları aracılığıyla Windows geliştiricileri için etkinleştirilmiştir. Kitaplıklar hem .NET Framework hem de .NET Core 'a sunulduğundan, mevcut masaüstü uygulamalarınızda bu özelliklerden yararlanabilirsiniz. Kullanıcı arabiriminizi XAML Adaları kullanımıyla bile modernleştirin ve uygulamalarınızın görsellerini ve davranışlarını saatlere göre geliştirebilirsiniz.

Burada dikkat etmeniz gereken önemli bir şey, bu modernleştirme yolunu izlemek için .NET Framework teknolojiden vazgerek kalmaz. .NET Core 'a geçiş yapmak zorunda kalmadan, burada güvenle ve Windows 10 ' un tüm avantajlarına sahip olabilirsiniz. Bu nedenle, modernleştirme yolunu seçmek için hem güç hem de esneklik elde edersiniz.

## <a name="winrt-apis"></a>WinRT API 'Leri

WinRT API 'Leri, Windows 10 geliştiricilerin, işletim sisteminin sunabileceği her şeye erişmesini sağlayan nesne odaklı, iyi yapılandırılmış uygulama programlama arabirimleri (API). WinRT API 'Leri sayesinde anında Iletme bildirimleri, cihaz API 'Leri, Microsoft Ink ve WinML gibi işlevleri, masaüstü uygulamalarınızdaki diğerleri arasında tümleştirebilirsiniz.

Genel olarak, WinRT API 'Leri klasik bir masaüstü uygulamasından çağrılabilir. Ancak, iki ana alan bu kurala özel bir durum sunar:

* Paket kimliği gerektiren API 'Ler.
* XAML veya bileşim gibi görselleştirme gerektiren API 'Ler.

### <a name="universal-windows-platform-uwp-packages"></a>Evrensel Windows Platformu (UWP) paketleri

#### <a name="application-package-identity"></a>Uygulama paketi kimliği

UWP uygulamaları, IŞLETIM sisteminin uygulamayı yüklemeyi ve kaldırmayı yönettiği bir dağıtım sistemine sahiptir. Bu, yükleme sırasında hiçbir kullanıcı kodunun yürütülmeyeceği anlamına gelen kurulumun bildirime dayalı olmasını gerektirir. Bunun yerine, uygulama, uygulama bildiriminde belirtilen protokoller, dosya türleri ve uzantılar gibi sistemle tümleştirmek istediği her şey. Dağıtım zamanında, dağıtım işlem hattı Bu tümleştirme noktalarını yapılandırır. İşletim sisteminin tüm bu işlevleri yönetmesi ve takip eden tek yolu, her bir ' Package ' öğesinin bir kimliğe sahip olması ve uygulamanın benzersiz bir tanımlayıcısı olması içindir.

Bazı WinRT API 'Leri, bu paket kimliğinin beklenen şekilde çalışmasını gerektirir. Ancak, yerel C++ veya .NET uygulamaları gibi klasik masaüstü uygulamaları, paket kimliği gerektirmeyen farklı dağıtım sistemleri kullanır. Bu WinRT API 'Lerini masaüstü uygulamanızda kullanmak istiyorsanız, bunları bir paket kimliği sağlamanız gerekir.

Devam etmenin bir yolu ek paketleme projesi oluşturmak. Paketleme projesi içinde orijinal kaynak kodu projesini işaret ettikten sonra sağlamak istediğiniz kimlik bilgilerini belirtirsiniz.Paketi yükler ve yüklü uygulamayı çalıştırırsanız, kimlik gerektiren tüm WinRT API 'Lerini çağırmak için kodunuzun etkinleştirilmesi için otomatik olarak bir tanımlama alır.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

API 'YI içeren türün [Dualapipartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) özniteliğiyle işaretlenip işaretlenmediğini inceleyerek, hangi API 'lerin paketlenmiş uygulama kimliğine ihtiyacı olduğunu kontrol edebilirsiniz.Varsa, paketlenmemiş bir geleneksel masaüstü uygulamasından öğesini çağırabilirsiniz. Aksi halde, bir paketleme projesinin yardımıyla klasik masaüstü uygulamanızı UWP 'e dönüştürmeniz gerekir.

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a>Paketleme avantajları

Bu API 'lere erişim izni verirken aşağıdakiler de dahil olmak üzere masaüstü uygulamanız için bir Windows uygulama paketi oluşturarak bazı ek avantajlar elde edersiniz:

* **Kolaylaştırılmış dağıtım**. Uygulamalar, kullanıcıların bir uygulamayı güvenle yükleyip güncelleştirebilmesini sağlayan harika bir dağıtım deneyimine sahiptir. Kullanıcı uygulamayı kaldırmayı seçerse, Windows Rot sorununa karşı bir izleme kalmadı olmaz tamamen kaldırılır.

* **Otomatik Güncelleştirmeler ve lisanslama**. Uygulamanız Microsoft Store yerleşik lisanslama ve otomatik güncelleştirme tesislerinde yer alabilir. Otomatik güncelleştirme son derece güvenilir ve verimli bir mekanizmadır çünkü yalnızca dosyaların değiştirilen parçaları indirilir.

* **Daha fazla erişim ve Basitleştirilmiş para kazanma**. Büyük bir durumdur, ancak uygulamanızı Microsoft Store aracılığıyla dağıtmayı seçerseniz milyonlarca Windows 10 kullanıcıya ulaşabilirsiniz.

* **UWP özellikleri ekleyin**. Kendi hızınızda, uygulamanızın paketine UWP özellikleri ekleyebilirsiniz.

#### <a name="prepare-for-packaging"></a>Paketleme için hazırlanma

Masaüstü uygulamanızı paketlemenize devam etmeden önce, işlemi başlatmadan önce ele almanız gereken bazı noktaları vardır. Uygulamanız Microsoft Store kurallarından ve ilkelerden herhangi birini dikkate almalıdır ve UWP uygulama modelinde çalıştırılır. Örneğin, .NET Framework 4.6.2 veya üzeri bir sürümde çalışmalıdır ve `HKEY_CURRENT_USER` kayıt defteri kovanına yazar ve AppData klasörleri kullanıcıya özgü bir uygulama yerel konumuna sanallaştırılır.

Paketleme için tasarım hedefi, diğer uygulamalarla uyumluluğu sürdürirken uygulama durumunu sistem durumundan ayırmaktır. Windows 10, uygulamayı UWP paketinin içine yerleştirerek bu hedefi gerçekleştirir. Paketleme tarafından sunulan bir uygulamanın güvenilir ve temiz yükleme ve kaldırma davranışının taahhüdünü karşılamak için dosya sistemi ve kayıt defterindeki bazı değişiklikleri algılar ve yeniden yönlendirir.

Masaüstü uygulamanız için oluşturduğunuz paketler, ve ' a yazma işlemleri için uygulamaya hafif sanallaştırma uygulanmış olsa da, yalnızca Masaüstü, tam güven özellikli uygulamalardır `HKCU` `AppData` . Bu sanallaştırma, klasik masaüstü uygulamalarıyla aynı şekilde diğer uygulamalarla etkileşime geçmesini sağlar.

##### <a name="installation"></a>Yükleme

Uygulama paketleri, başlıklı yürütülebilir dosya ile *% ProgramFiles% \\ WindowsApps \\ package_name*altına yüklenir  `app_name.exe` . Her paket klasörü `AppxManifest.xml` , paketlenmiş uygulamalar için özel BIR XML ad alanı içeren bir bildirim (adlandırılmış) içerir. Bu bildirim dosyasının içinde  `<EntryPoint>`   tam güven uygulamasına başvuran bir öğedir. Bu uygulama başlatıldığında, bir uygulama kapsayıcısı içinde çalışmaz, ancak bunun yerine normalde Kullanıcı olarak çalışır.

Dağıtımdan sonra, paket dosyaları salt okunurdur ve işletim sistemi tarafından yoğun olarak kilitlenir. Windows, bu dosyalar ile oynanmışsa uygulamaların başlatılmasını önler.

##### <a name="file-system"></a>Dosya sistemi

İşletim sistemi, klasör konumuna bağlı olarak paketlenmiş masaüstü uygulamaları için farklı düzeylerde dosya sistemi işlemlerini destekler.

Kullanıcının *AppData* klasörüne erişmeye çalışırken, sistem arka planda Kullanıcı başına özel, uygulama başına bir konum oluşturur. Bu, paketlenmiş uygulamanın gerçekten özel bir kopyayı değiştirirken gerçek *AppData* 'yi düzenlediğine ilişkin bir yanılsaması oluşturur. Bu şekilde yazmayı yeniden yönlendirerek, sistem uygulama tarafından yapılan tüm dosya değişikliklerini izleyebilir. Daha sonra, sistemi "Rot" azaltır ve Kullanıcı için daha iyi bir uygulama kaldırma deneyimi sağlayarak bu dosyaları temizleyebilir.

##### <a name="registry"></a>Kayıt Defteri

Uygulama paketleri,  `HKLM\Software` gerçek kayıt defterindeki mantıksal eşdeğeri görevi gören bir Registry. dat dosyası içerir   . Çalışma zamanında, bu sanal kayıt defteri Bu Hive içeriğini yerel sistem kovanına birleştirir ve her ikisinin de tekil bir görünümünü sağlar.

Tüm yazma işlemleri, paket yükseltme sırasında tutulur ve yalnızca uygulama kaldırıldığında silinir.

##### <a name="uninstallation"></a>Kaldırma

Kullanıcı bir paketi kaldırdığında, altında bulunan tüm dosya ve klasörlerin  `C:\Program Files\WindowsApps\package_name` yanı sıra, AppData veya işlem sırasında yakalanan kayıt defteri için yeniden yönlendirilen yazma işlemleri kaldırılır.

Paketlenmiş bir uygulamanın yükleme, dosya erişimi, kayıt defteri ve kaldırma işlemlerinin nasıl ele aldığı hakkında ayrıntılar için bkz <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> ..

Denetlenecek öğelerin tüm listesini alabilirsiniz <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> .

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a>WinRT API 'Lerini masaüstü projenize ekleme

Bu bölümde, mevcut bir WPF uygulamasında bildirim bildirimlerinin nasıl tümleştirileceği hakkında bir anlatım bulabilirsiniz. Kod perspektifinden basit olsa da, tüm süreci göstermeye yardımcı olur. Bildirimler, .NET uygulamasında kullanabileceğiniz mevcut birçok WinRT API 'Lerinden biridir. Bu durumda, API bir paket kimliği gerektirir. API 'Ler paket kimliği gerektirmiyorsa bu işlem daha basittir.

Dosyaları okuyan ve ekrandaki içeriğini gösteren mevcut bir WPF örnek uygulaması ele alalım. Amaç, uygulama başladığında bir bildirim bildirimi görüntülemektir.

![Çalışan örnek uygulamanın ekran görüntüsü](./media/windows-migration/sample-application.png)

İlk olarak, kullanacağınız Windows 10 API 'sinin bir paket kimliği gerektirip gerektirmediğini aşağıdaki bağlantıyı denetlemeniz gerekir:

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

Örneğimiz, <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> paketlenmiş bir kimlik gerektiren API 'yi kullanacaktır:

![Microsoft belgelerindeki bildirim sınıfı](./media/windows-migration/notification-class-documentation.png)

WinRT API 'sine erişmek için, NuGet paketine bir başvuru ekleyin `Microsoft.Windows.SDK.Contracts`   ve bu paket arka planda Magic 'i (bkz. Ayrıntılara bakın <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> ) oluşturur.

Artık kod eklemeye başlamak için hazır olursunuz.

`ShowToastNotification`Uygulama başlangıcında çağrılacak bir yöntem oluşturun. Yalnızca bir XML düzeninden bildirim oluşturur:

```csharp
private void ShowNotification(string title, string content, string image)
{
    string xmlString = $@"<toast><visual><binding template = 'ToastGeneric'><text>{title}</text><text>{content}</text><image src=>'{image}'</image></binding></visual></toast>";
    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);
    ToastNotification toast = new ToastNotification(toastXml);
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

Proje derlemeseler de, bildirimler API 'SI bir paket kimliği gerektirdiğinden ve bunu sağlamadığınız için hatalar vardır. Çözüme bir Windows paketleme projesi eklendiğinde bu sorun düzeltilir:

![Visual Studio 'da yeni proje Ekle iletişim kutusunun ekran görüntüsü](./media/windows-migration/add-packaging-project.png)

Desteklemek istediğiniz en düşük Windows sürümünü ve hedeflediğiniz sürümü seçin. Tüm Windows 10 sürümlerinde WinRT API 'Leri desteklenmez. Her Windows 10 güncelleştirmesi yalnızca bu sürümden kullanılabilen yeni API 'Ler ekler; alt düzey destek kullanılamıyor.

![En düşük Windows sürümünü seçme](./media/windows-migration/select-versions.png)

Sonraki adım, WPF uygulamasını bir proje başvurusu ekleyerek Windows paketleme projesine eklemektir:

![Windows paketleme projesine WPF uygulaması ekleme](./media/windows-migration/add-application.png)

![Başvuru Yöneticisi](./media/windows-migration/reference-manager.png)

Bir Windows paketleme projesi çeşitli uygulamaları paketleyebilir, bu nedenle hangi hangisinin giriş noktası olduğunu ayarlamanız gerekir:

![Giriş noktası ayarlanıyor](./media/windows-migration/set-entry-point.png)

Sonraki adım, WPF projesini çözüm yapılandırmasında başlangıç projesi olarak ayarlamanıza olanak sağlar. F5 tuşuna basarak sonuçları derleyip oluşturabilir ve görüntüleyebilirsiniz.

![Çalışan ve sonuçları gösteren örnek uygulama](./media/windows-migration/sample-app-result.png)

Uygulamanızı yükleyebilmeniz için paketi oluşturalım. **Mağaza**  >  **uygulama paketleri oluştur**' a sağ tıklayın.

![Uygulama paketleri oluştur iletişim kutusu](./media/windows-migration/create-app-packages.png)

Uygulamayı makinenizden dağıtmak için dışarıdan yükleme seçeneğini belirleyin:

![Dışarıdan yükleme seçeneği seçiliyor](./media/windows-migration/select-sideloading-option.png)

Uygulamanızın uygulama mimarisini seçin:

![Uygulama mimarisini seçme](./media/windows-migration/select-app-architecture.png)

Son olarak, **Oluştur**' a tıklayarak paketi oluşturun.

## <a name="xaml-islands"></a>XAML Adaları

XAML Adaları, Windows Masaüstü geliştiricilerinin Windows Forms ve WPF dahil olmak üzere mevcut Win32 uygulamalarında UWP XAML denetimlerini kullanmasını sağlayan bir bileşen kümesidir.

![XAML Adaları yapısı](./media/windows-migration/xaml-islands.png)

Win32 uygulamanızı standart denetimleriniz ile ve bunlar arasında, modern dünyanın denetimleri içeren UWP Kullanıcı arabiriminin "Adası" olarak görüntüleyebilirsiniz. Kavram, bir Web sayfasının içindeki içeriği gösteren bir iFrame 'e sahip olmaya benzer`different page.`

Windows 10 API 'Lerinden işlevsellik eklemenin yanı sıra, XAML Adaları kullanarak uygulamanızın içine UWP XAML parçaları ekleyebilirsiniz.

Windows 10 1903 güncelleştirmesi, Win32 Windows 'da UWP XAML içeriğinin barındırılmasına izin veren bir API kümesi sunar. Yalnızca Windows 10 1903 üzerinde çalışan uygulamalar XAML Adaları kullanabilir.

### <a name="the-road-to-xaml-islands"></a>XAML Adaları için yol

Microsoft, modernleştirin for the Win32 Apps (Windows Forms, WPF ve yerel Win32 uygulamaları) için bir Framework olarak WinRT API 'Leri kullanıma sunmışsa, XAML Adaları için yol 2012 ' de başlatılır. Ancak, WinRT içindeki yeni UI denetimleri yeni uygulamalar için kullanılabilir ancak mevcut olanlar için geçerli değildir.

2015 ' de, Windows 10 ile birlikte UWP doğdu. UWP, XBox, mobil ve Masaüstü gibi Windows cihazlarında çalışan uygulamalar oluşturmanıza olanak tanır. Bir yıl sonra, Microsoft, masaüstü Köprüsü (eski adıyla proje Centennial) ile duyuruldu. Masaüstü Köprüsü, geliştiricilerin mevcut Win32 uygulamalarını Microsoft Store getirmeye izin veren bir araç kümesidir. 2017 ' ye daha fazla özellik eklenmiştir ve geliştiricilerin, işlem merkezindeki canlı kutucuklar ve bildirimler gibi yeni Windows 10 API 'Lerinden bazılarının Win32 uygulamalarını geliştirmesine olanak tanır. Ancak yine de yeni UI denetimi yoktur.

Derleme 2018 ' de, Microsoft, geliştiricilerin uygulamalarını UWP 'e tamamen geçirmeden yeni Windows 10 XAML denetimlerini geçerli Win32 uygulamalarına kullanması için bir yol duyurmuştur. UWP XAML Adaları olarak markalı.

### <a name="how-it-works"></a>Nasıl çalışır?

Windows 10 1903 güncelleştirmesi çeşitli XAML barındırma API 'Leri sunar. Bunlardan ikisi `WindowsXamlManager`   ve  `DesktopWindowXamlSource` .

 `WindowsXamlManager`   Sınıfı UWP xaml çerçevesini işler. Yöntemi,, `InitializeForCurrentThread` Win32 uygulamasının geçerli iş parçacığının IÇINE UWP xaml çerçevesini yükler.

,  `DesktopWindowXamlSource`   Xaml Adası içeriğinizin örneğidir. `Content`Örneği oluşturma ve ayarlamaktan sorumlu olan özelliği vardır. , `DesktopWindowXamlSource`   Bir HWND 'nin girdisini işler ve alır. Bu, XAML Adası 'nin hangi HWND 'ye iliştirilecektir ve üst öğenin HWND 'sini boyutlandırmaktan ve konumlandırmadan sorumludur.

WPF veya Windows Forms geliştiricileri genellikle kendi kodunun içinde HWND ile ilgilenmemekte olduğundan, HWND işaretçilerini ve temel alınan kablolama işlerini kullanarak Win32 ve UWP Worlds ile iletişim kurma zor olabilir.

#### <a name="the-xaml-islands-net-wrappers"></a>XAML Adaları .NET sarmalayıcıları

Windows Community Toolkit, WPF için XAML Adaları .NET sarmalayıcıları veya XAML Adaları kullanımını kolaylaştıran Windows Forms bir kümesidir. Bu sarmalayıcılar, diğer şeyler arasındaki HWND 'yi, odak yönetimini yönetir. Windows Forms ve WPF geliştiricilerinin bu sarmalayıcıları kullanması gerekir.

Windows topluluk araç seti iki tür denetim sunar: sarmalanmış denetimler ve barındırma denetimleri.

##### <a name="wrapped-controls"></a>Sarmalanan denetimler

Bu Sarmalanan denetimler bazı UWP denetimlerini Windows Forms veya WPF denetimlerine sarmalayın ve bu geliştiricilerin UWP kavramlarını gizler. Bu denetimler şunlardır:

* WebView ve WebViewCompatible
* InkCanvas ve ınktoolbar
* MediaPlayerElement
* MapControl

`Microsoft.Toolkit.Wpf.UI.Controls`Paketi projenize ekleyin, ad alanına başvuruyu ekleyin ve kullanmaya başlayın.

```xml
<Window
        ...
        xmlns:uwpControls="clr-namespace:Microsoft.Toolkit.Wpf.UI.Controls;assembly=Microsoft.Toolkit.Wpf.UI.Controls">
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="\*"/>
    </Grid.RowDefinitions>
    <uwpControls:InkToolbar TargetInkCanvas="{x:Reference Name=inkCanvas}"/>
    <uwpControls:InkCanvas Grid.Row="1" x:Name="inkCanvas" />
</Grid>
```

##### <a name="hosting-controls"></a>Barındırma denetimleri

XAML Adaları 'nin gücü, tam işlevli Kullanıcı arabirimiyle "Adaları" olarak Windows Forms ve WPF ile tümleştirilebilen, UWP için geliştirilen ilk taraf denetimlerin, üçüncü taraf denetimlerinin ve özel denetimlerin çoğunu genişletir. `WindowsXamlHost`WPF ve Windows Forms için denetim bunun yapılmasına izin verir.

Örneğin, `WindowsXamlHost` WPF 'de denetimi kullanmak için, `Microsoft.Toolkit.Wpf.UI.XamlHost` Windows Community Toolkit tarafından sunulan pakete bir başvuru ekleyin.

`WindowsXamlHost`Kullanıcı arabirimi kodunuza yerleştirdikten sonra, HANGI UWP türünü yüklemek istediğinizi belirtin. `Button`Özel BIR UWP denetimi olan birkaç farklı denetim tarafından oluşturulmuş bir veya daha karmaşık bir denetim gibi kaydırılmış bir denetim kullanmayı seçebilirsiniz.

Aşağıdaki örnek, UWP nasıl ekleneceğini göstermektedir `Button` :

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

Bunun nasıl yaklaşımıyla ilgili net bir öneri vardır ve bir tek ve daha büyük XAML Adası, her birinde tek bir denetimle birden fazla adamla sahip olacak şekilde, özel bir bileşik denetim içeren tek ve daha büyük bir XAML Adası olması

XAML 'in temel özelliklerinden biri bağlamadır ve Win32 kodunuz ile Adası arasında çalışmaktadır. Bu nedenle, örneğin, UWP ile bir Win32 ile bağlanabilir `Textbox` `Textbox` . Dikkate almanız gereken önemli nokta, Bu bağlamaların UWP 'den Win32 'e kadar tek yönlü bağlamalardır, yani `Textbox` xaml Adası içinde güncelleştirirseniz Win32 metin kutusu güncelleştirilecek ancak başka bir şekilde değil.

XAML Adaları kullanımı hakkında bir anlatım görmek için bkz.:

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a>UWP XAML özel denetimleri ekleme

XAML özel denetimi siz veya üçüncü taraflar tarafından oluşturulan bir denetimdir (veya kullanıcı denetimidir) (WinUI 2. x denetimleri dahil). Bir Windows Forms veya WPF uygulamasında özel bir UWP denetimi barındırmak için şunlar gerekir:

- `WindowsXamlHost`.NET Core 3. x uygulamanızda UWP denetimini kullanmak için.
- Bir nesneyi tanımlayan UWP uygulama projesi oluşturmak için `XamlApplication` .

WPF veya Windows Forms projenizin `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` , Windows topluluk araç seti tarafından sunulan bir sınıfın örneğine erişimi olmalıdır. Bu nesne, uygulamanızın geçerli dizinindeki derlemelerdeki özel UWP XAML türleri için meta verileri yüklemek üzere bir kök meta veri sağlayıcısı işlevi görür. Bunu yapmanın önerilen yolu, WPF veya Windows Forms projeniz ile aynı çözüme bir boş uygulama (Evrensel Windows) projesi eklemek ve bu projedeki varsayılan uygulama sınıfını düzeltmenin bir yoludur.

Özel UWP XAML denetimi, bu UWP uygulamasına veya WPF veya Windows Forms projenizle aynı çözüme başvurduğunuz bağımsız bir UWP sınıf kitaplığı projesine dahil edilebilir.

Ayrıntılı bir adım adım işlem açıklamasını şu adreste denetleyebilirsiniz:

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a>Windows Kullanıcı arabirimi kitaplığı (WinUI 2)

Aynı UWP XAML ekibi, işletim sistemi ile birlikte gelen gelen kutusu Windows 10 denetimlerinin yanı sıra Windows Kullanıcı arabirimi kitaplığı 'nda da ek denetimler de (**WinUI 2**) sağlar. WinUI 2, Windows UWP uygulamaları için resmi yerel Microsoft UI denetimleri ve özellikleri sağlar ve bu denetimler XAML Adaları içinde kullanılabilir.

WinUI 2 açık kaynaktır ve bilgi edinebilirsiniz <https://github.com/microsoft/microsoft-ui-xaml> .

Aşağıdaki makalede, WinUI 2 kitaplığından UWP XAML denetimini barındırma gösterilmektedir:<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

### <a name="do-you-need-xaml-islands"></a>XAML Adaları gerekiyor

XAML Adaları, uygulamanın tam yeniden yazma olmadan yeni UWP denetimleri ve davranışları kullanarak kendi kullanıcı deneyimlerini geliştirmek isteyen mevcut Win32 uygulamalarına yöneliktir.  [Windows 10 API 'lerinden](/windows/uwp/porting/desktop-to-uwp-enhance)zaten faydalanabilirsiniz, ancak xaml Adaları 'e kadar, yalnızca kullanıcı arabirimi Ile Ilgili API 'leri kullanabilirsiniz.

Yeni bir Windows uygulaması geliştiriyorsanız, bir [UWP uygulaması](/windows/uwp/get-started/universal-application-platform-guide)   muhtemelen doğru yaklaşımda.

### <a name="the-road-ahead-xaml-islands-winui-30"></a>Yol ileri XAML Adaları: WinUI 3,0

Windows 8 ' den itibaren, XAML UI çerçevesi, görsel bileşim katmanı ve giriş işleme dahil olmak üzere Windows Kullanıcı arabirimi platformu Windows 'un bir integral parçası olarak gönderilmiştir. Bu, UI teknolojilerinin en son geliştirmelerinden faydalanmak için, Kullanıcı arabiriminin en son sürümüne yükseltmeniz gerekir, uygulamalarınızı geliştirirken geliştirmelerin hızını yavaşlatır. Bu iki gelişme döngüsünü ve Foster yeniliklerini ayırmak için Microsoft, WinUI projesi üzerinde etkin bir şekilde çalışır.

Microsoft, 2018 ' de WinUI 2 ' den itibaren, bazı yeni XAML kullanıcı arabirimi denetimlerini ve özelliklerini UWP SDK 'sının üzerine oluşturan ayrı NuGet paketleri olarak göndermeyi başlattı.

![WinUI 2,0 yapısı](./media/windows-migration/winui2.png)

WinUI 3, etkin geliştirme aşamasındadır ve tam UI platformunu dahil etmek için WinUI kapsamını büyük ölçüde genişleterek UWP SDK 'dan tamamen ayrılmış olur:

![WinUI 3,0 yapısı](./media/windows-migration/winui3.png)

XAML çerçevesi artık GitHub 'da geliştirilir ve NuGet paketleri olarak bant dışına sevk edilir [NuGet](/nuget/what-is-nuget)   .

İşletim sisteminin bir parçası olarak gönderilen mevcut UWP XAML API 'Leri artık yeni özellik güncelleştirmeleri almaz. Windows 10 destek yaşam döngüsüne göre güvenlik güncelleştirmeleri ve kritik düzeltmeler almaya devam eder.

Evrensel Windows Platformu, yalnızca XAML çerçevesini (örneğin, uygulama ve güvenlik modeli, medya işlem hattı, Xbox ve Windows 10 Shell tümleştirmeleri, geniş cihaz desteği) içerir ve gelişmeye devam eder. Tüm yeni XAML özellikleri yalnızca WinUI 'nin bir parçası olarak geliştirilir ve gönderilir.

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a>Masaüstü uygulamasında WinUI 3 ve WinUI XAML Adaları

Gördüğünüz gibi, WinUI 3, UWP XAML 'in gelişmidir ve UWP uygulama modeli ve tüm gereksinimleri (MSIX paketlenmiş KIMLIĞI, korumalı alan, CoreWindow vb.) içinde doğal olarak çalışmaktadır. Yalnızca WinUI 3 ' ü bir Win32 uygulama modelinde kullanmak için WinUI içeriği, **WINUı xaml Adaları**kullanılarak başka bir kullanıcı arabirimi çerçevesi (WINDOWS Forms, WPF vb.) tarafından barındırılmalıdır. Uygulamanızı geliştirmek ve teknolojileri karıştırmak istiyorsanız bu doğru yoldur. Ancak, tüm eski Kullanıcı arabirimini WinUI için değiştirmek istiyorsanız, uygulamanızın kullanıcı arabirimi çerçevelerini yalnızca WinUI barındırması için yüklemesi gerekmez.

WinUI 3, **masaüstü uygulamalarında WinUI**ekleyen bu kritik geri bildirimi ele alacak. Bu, Win32 uygulamalarının tek başına UI çerçevesi olarak WinUI 3 ' ü kullanmasına izin verir; Windows Forms veya WPF yüklemeye gerek yoktur.

Bu toplamada, WinUI 3, geliştiricilerin doğru birleşimini kolayca karıştırabilmesini ve eşleşmesini sağlar:

* Uygulama modeli: UWP, Win32
* Platform: .NET Core veya native
* Dil: .NET (C \# , Visual Basic), standart C++
* Paketleme: MSIX, Microsoft Store için AppX, paketlenmiş değil
* Birlikte çalışma: WinUI XAML Adaları kullanarak mevcut WPF, WinForms ve MFC uygulamalarını genişletmek için WinUI 3 kullanın.

Daha fazla bilgi edinmek istiyorsanız, Microsoft bu yol haritasını ' de paylaşıyor <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> .

>[!div class="step-by-step"]
>[Önceki](migrate-modern-applications.md) 
> [Sonraki](example-migration-core.md)
