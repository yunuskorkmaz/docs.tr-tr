---
title: Geliştiriciler için .NET Framework dağıtım kılavuzu
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
ms.openlocfilehash: 62777356dae6e2dce9753b832f08ab2fa2cb5881
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801880"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Geliştiriciler için .NET Framework dağıtım kılavuzu
Bu konu, .NET Framework 4,5 ' den .NET Framework herhangi bir sürümünü uygulamalarıyla [!INCLUDE[net_current](../../../includes/net-current-version.md)] yüklemek isteyen geliştiriciler için bilgi sağlamaktadır.

İndirme bağlantıları için [yeniden dağıtılabilir paketler](#redistributable-packages)bölümüne bakın. Yeniden dağıtılabilir paketleri ve dil paketlerini bu Microsoft Indirme merkezi sayfalarından de indirebilirsiniz:

- Tüm işletim sistemleri için .NET Framework 4,8 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=2085155) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/?linkid=2088631))

- Tüm işletim sistemleri için .NET Framework 4.7.2 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=863262) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=863265))

- Tüm işletim sistemleri için .NET Framework 4.7.1 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=852095) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=852107))

- Tüm işletim sistemleri için .NET Framework 4,7 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=825299) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=825303))

- Tüm işletim sistemleri için .NET Framework 4.6.2 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=780597) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=780601))

- Tüm işletim sistemleri için .NET Framework 4.6.1 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=671729) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=671744))

- Tüm işletim sistemleri için .NET Framework 4,6 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=528222) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=528232))

- Tüm işletim sistemleri için .NET Framework 4.5.2 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/p/?LinkId=397703) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=397706))

- Tüm işletim sistemleri için .NET Framework 4.5.1 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/p/?LinkId=310158) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=310159))

- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)

 Önemli notlar:

> [!NOTE]
> ".NET Framework 4,5 ve nokta sürümleri" ifadesi, .NET Framework 4,5 ve sonraki tüm sürümleri anlamına gelir.

- .NET Framework 4.5.1 ile [!INCLUDE[net_current](../../../includes/net-current-version.md)] arasındaki .NET Framework sürümleri, .NET Framework 4,5 ' e yönelik yerinde güncellemelerdir, yani aynı çalışma zamanı sürümünü kullanır, ancak derleme sürümleri güncelleştirilir ve yeni türler ve Üyeler dahil edilir.

- .NET Framework 4,5 ve noktası sürümleri artımlı olarak .NET Framework 4 ' te oluşturulmuştur. .NET Framework 4 ' ün yüklü olduğu bir sisteme .NET Framework 4,5 veya Point sürümlerini yüklediğinizde, sürüm 4 derlemeleri daha yeni sürümlerle değiştirilmiştir.

- Uygulamanızda Microsoft ['un bant dışı bir paketine](../get-started/the-net-framework-and-out-of-band-releases.md) başvuruyorsam, derleme uygulama paketine dahil edilir.

- .NET Framework 4,5 ve noktası sürümlerini yüklemek için yönetici ayrıcalıklarına sahip olmanız gerekir.

- .NET Framework 4,5, Windows 8 ve [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]dahil edilmiştir. bu nedenle, uygulamayı bu işletim sistemlerine dağıtmanız gerekmez. Benzer şekilde, .NET Framework 4.5.1 Windows 8.1 ve Windows Server 2012 R2 'ye dahildir. .NET Framework 4.5.2 hiçbir işletim sistemine dahil değildir. .NET Framework 4,6, Windows 10 ' a dahil edilmiştir, .NET Framework 4.6.1 Windows 10 Kasım güncelleştirmesine dahildir ve .NET Framework 4.6.2 Windows 10 yıldönümü güncelleştirmesine dahildir.  .NET Framework 4,7, Windows 10 Creators Update 'e dahildir, .NET Framework 4.7.1 Windows 10 Fall Creators Update 'e dahildir ve .NET Framework 4.7.2 Windows 10 Ekim 2018 güncelleştirmesi ve Windows 10 Nisan 2018 güncelleştirmesine dahildir. .NET Framework 4,8, Windows 10 Mayıs 2019 güncelleştirme ' ye eklenmiştir. Donanım ve yazılım gereksinimlerinin tam listesi için bkz. [sistem gereksinimleri](../get-started/system-requirements.md).

- Kullanıcılarınız .NET Framework 4,5 ' den başlayarak, kurulum sırasında çalışan .NET Framework uygulamalarının bir listesini görüntüleyebilir ve kolayca kapatabilir. Bu, .NET Framework kurulumlarının neden olduğu sistem yeniden başlatmalarını önlemenize yardımcı. Bkz. [sistem yeniden başlatmaları azaltma](reducing-system-restarts.md).

- .NET Framework 4,5 ' nin kaldırılması veya noktası sürümlerinden biri, önceden var olan .NET Framework 4 dosyalarını da kaldırır. .NET Framework 4 ' e geri dönmek istiyorsanız, bu dosyayı ve tüm güncelleştirmeleri yeniden yüklemeniz gerekir. Bkz. [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100))' ü yükleme.

- .NET Framework 4.5 yeniden dağıtılabilir, Microsoft tarafından üretilen ve imzalanan dosyalardaki dijital imzanın süresinin zamanından önce dolmasına neden olan ve bir dijital sertifika üzerinde bulunan hatalı zaman damgasıyla ilgili sorunu gidermek amacıyla 9 Ekim 2012 tarihinde güncellenmiştir. Daha önce 16 Ağustos 2012 tarihli .NET Framework 4,5 yeniden dağıtılabilir paketini yüklediyseniz, [Microsoft Indirme merkezi](https://go.microsoft.com/fwlink/p/?LinkId=245484)'ndeki kopyanızı en son yeniden dağıtılabilir ile güncelleştirmenizi öneririz. Bu sorun hakkında daha fazla bilgi için bkz. [Microsoft Güvenlik Danışmanlığı 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

Bir sistem yöneticisinin .NET Framework ve sistem bağımlılıklarını bir ağ üzerinden nasıl dağıtabilirim hakkında bilgi için bkz. [Yöneticiler Için dağıtım kılavuzu](guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Uygulamanız için dağıtım seçenekleri

Kullanıcıların yüklemesi için uygulamanızı web sunucusunda ya da başka bir merkezi konumda yayımlamaya hazır olduğunuzda birçok dağıtım yöntemini seçebilirsiniz. Bunlardan bazıları Visual Studio ile sağlanır. Aşağıdaki tabloda, uygulamanız için dağıtım seçenekleri listelenmekte ve her bir seçeneği destekleyen .NET Framework yeniden dağıtılabilir paketi belirtilir. Bunlara ek olarak, uygulamanız için özel bir kurulum programı yazabilirsiniz; daha fazla bilgi için [.NET Framework yüklemesini uygulamanızın kurulumuna zincirme](#chaining)bölümüne bakın.

|Uygulamanız için dağıtım stratejisi|Dağıtım yöntemleri|Kullanılacak .NET Framework yeniden dağıtılabiliri|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Web'den yükleme|[InstallAware](#installaware-deployment) - <br />- [InstallShield](#installshield-deployment)<br />[Wix araç takımını](#wix) - <br />[el ile yükleme](#installing_manually) - |[Web Yükleyicisi](#redistributable-packages)|
|Diskten yükleme|[InstallAware](#installaware-deployment) - <br />- [InstallShield](#installshield-deployment)<br />[Wix araç takımını](#wix) - <br />[el ile yükleme](#installing_manually) - |[Çevrimdışı yükleyici](#redistributable-packages)|
|Yerel alan ağından yükleme (ticari uygulamalar için)|- [ClickOnce](#clickonce-deployment)|[Web Yükleyicisi](#redistributable-packages) (kısıtlamalar için bkz. [ClickOnce](#clickonce-deployment) ) veya [çevrimdışı yükleyici](#redistributable-packages)|

## <a name="redistributable-packages"></a>Yeniden dağıtılabilir Paketleri

.NET Framework iki yeniden dağıtılabilir pakette kullanılabilir: web yükleyicisi (önyükleyici) ve çevrimdışı yükleyici (tek başına yeniden dağıtılabilir). Aşağıdaki tablo iki paketi karşılaştırır.

||Web Yükleyici|Çevrimdışı yükleyici|
|-|-------------------|-----------------------|
|Dosyayı indir|.NET Framework 4,8: <br/>[ndp48-Web. exe](https://go.microsoft.com/fwlink/?LinkId=2085155)<br/><br/>.NET Framework 4.7.2: <br/>[NDP472-KB4054531-Web. exe](https://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>.NET Framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](https://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>.NET Framework 4,7: <br />[NDP47-KB3186500-Web.exe](https://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />.NET Framework 4.6.2: <br />[NDP462-KB3151802-Web.exe](https://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> .NET Framework 4.6.1:<br />[NDP461-KB3102438-Web.exe](https://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> .NET Framework 4,6:<br />[NDP46-KB3045560-Web.exe](https://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](https://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> .NET Framework 4.5.1: <br />[NDP451-KB2859818-Web.exe](https://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> .NET Framework 4,5: <br />[dotNetFx45_Full_setup.exe](https://go.microsoft.com/fwlink/?LinkId=225704)|.NET Framework 4,8: <br/>[NDP48-x86-x64-AllOS-ENU. exe](https://go.microsoft.com/fwlink/?linkid=2088631)<br/><br/>.NET Framework 4.7.2: <br/>[NDP472-KB4054530-x86-x64-AllOS-ENU. exe](https://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>.NET Framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET Framework 4,7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />.NET Framework 4.6.2: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU. exe](https://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> .NET Framework 4.6.1: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU. exe](https://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> .NET Framework 4,6: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> .NET Framework 4.5.1: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> .NET Framework 4,5: <br />[dotNetFx45_Full_x86_x64.exe](https://go.microsoft.com/fwlink/?LinkId=225702)|
|Internet bağlantısı gerekiyor?|Evet|Hayır|
|İndirme boyutu|Daha küçük (yalnızca hedef platform kurulumu içerir) *|Daha büyük*|
|Dil paketleri|Dahil**|Tüm işletim sistemlerini hedefleyen paketi kullanmadığınız takdirde [ayrı olarak yüklenmelidir](#chain_langpack)|
|Dağıtım yöntemi|Tüm yöntemleri destekler:<br /><br />- [ClickOnce](#clickonce-deployment)<br />[InstallAware](#installaware-deployment) - <br />- [InstallShield](#installshield-deployment)<br />- [WINDOWS Installer XML (WiX)](#wix)<br />[el ile yükleme](#installing_manually) - <br />[özel kurulum - (zincirleme)](#chaining)|Tüm yöntemleri destekler:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />[InstallAware](#installaware-deployment) - <br />- [InstallShield](#installshield-deployment)<br />- [WINDOWS Installer XML (WiX)](#wix)<br />[el ile yükleme](#installing_manually) - <br />[özel kurulum - (zincirleme)](#chaining)|
|ClickOnce dağıtımı için indirme konumu|Microsoft Yükleme Merkezi:<br /><br /> - [.NET Framework 4,8](https://go.microsoft.com/fwlink/?LinkId=2085155) <br/> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863262) <br/> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET Framework 4,7](https://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET Framework 4,6](https://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [.NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|Kendi sunucunuz veya Microsoft Yükleme Merkezi:<br /><br /> - [.NET Framework 4,8](https://go.microsoft.com/fwlink/?linkid=2088631)<br /> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863265)<br /> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET Framework 4,7](https://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET Framework 4,6](https://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [.NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|

çevrimdışı yükleyici, tüm hedef platformlar için bileşenleri içerdiğinden daha büyük \*. Kurulumun çalışması tamamlandığında, Windows işletim sistemi yalnızca kullanılan kurulumu önbelleğe alır. Çevrimdışı yükleyici yükleme işleminden sonra silinirse, disk alanı web yükleyicisi tarafından kullanıldığı gibi kullanılır. Uygulamanızın kurulum programını oluşturmak için kullandığınız araç (örneğin, [InstallAware](#installaware-deployment) veya [InstallShield](#installshield-deployment)), yüklemeden sonra kaldırılan bir kurulum dosyası klasörü sağlıyorsa, çevrimdışı yükleyici, kurulum klasörüne yerleştirerek otomatik olarak silinebilir.

\*\* web yükleyicisini özel kurulumla kullanıyorsanız, kullanıcının çok dilli kullanıcı arabirimi (MUI) ayarını temel alan varsayılan dil ayarlarını kullanabilir veya komut satırındaki `/LCID` seçeneğini kullanarak başka bir dil paketi belirtebilirsiniz. Örnekler için [varsayılan .NET Framework Kullanıcı arabirimini kullanarak zincirleme](#chaining_default) bölümüne bakın.

## <a name="deployment-methods"></a>Dağıtım yöntemleri

 Dört dağıtım yöntemi mevcuttur:

- .NET Framework üzerinde bağımlılık ayarlayabilirsiniz. .NET Framework'ü aşağıdaki yöntemlerden birini kullanarak uygulamalarınızın yüklemesinde bir önkoşul olarak belirtebilirsiniz:

  - [ClickOnce dağıtımını](#clickonce-deployment) kullanma (Visual Studio ile kullanılabilir)

  - [InstallAware projesi](#installaware-deployment) oluşturma (Visual Studio kullanıcıları için ücretsiz sürüm)

  - [InstallShield projesi](#installshield-deployment) oluşturma (Visual Studio ile kullanılabilir)

  - [WINDOWS Installer XML (WiX) araç takımını](#wix) kullanın

- Kullanıcılarınızın [.NET Framework el ile yüklemesini](#installing_manually)isteyebilirsiniz.

- .NET Framework kurulum sürecini uygulamanızın kurulumuna bağlayabilirsiniz (dahil edebilirsiniz) ve .NET Framework kurulum deneyiminin nasıl üstesinden gelmek istediğinize karar verebilirsiniz.

  - [Varsayılan Kullanıcı arabirimini kullanın](#chaining_default). .NET Framework kurucusunun yükleme deneyimi sağlamasına izin verin.

  - [Kullanıcı arabirimini](#chaining_custom) Birleşik bir yükleme deneyimi sunmak ve .NET Framework yükleme ilerlemesini Izlemek için özelleştirin.

Bu dağıtım yöntemleri aşağıdaki bölümlerde ayrıntılı olarak ele alınmıştır.

## <a name="setting-a-dependency-on-the-net-framework"></a>.NET Framework bağımlılığı ayarlama

Uygulamanızı dağıtmak için ClickOnce, InstallAware, InstallShield veya WiX kullanıyorsanız, .NET Framework bir bağımlılık ekleyerek uygulamanızın bir parçası olarak yüklenebilmesini sağlayabilirsiniz.

### <a name="clickonce-deployment"></a>ClickOnce dağıtımı

ClickOnce dağıtımı, Visual Basic ve Visual C# ile oluşturulan projeleri için kullanılabilir, ancak Visual C++ için kullanılamaz.

Visual Studio'da ClickOnce dağıtımını seçmek ve .NET Framework üzerine bağımlılık eklemek için:

1. Yayımlamak istediğiniz uygulama projesini açın.

2. Çözüm Gezgini ' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

3. **Yayımla** bölmesini seçin.

4. **Önkoşullar** düğmesini seçin.

5. **Önkoşullar** iletişim kutusunda, **Önkoşul bileşenlerini yüklemek Için Kurulum programı oluştur** onay kutusunun işaretli olduğundan emin olun.

6. Önkoşullar listesinde, projenizi oluşturmak için kullandığınız .NET Framework sürümünü bulun ve seçin.

7. Önkoşulların kaynak konumunu belirtmek için bir seçenek belirleyin ve ardından **Tamam**' ı seçin.

     .NET Framework indirme konumu için bir URL sağlarsanız, Microsoft Download Center sitesini veya kendi sitenizin birini belirtebilirsiniz. Kendi sunucunuza yeniden dağıtılabilir paketi yerleştiriyorsanız, çevrimdışı yükleyici olmalı ve web yükleyicisi olmamalıdır. Microsoft İndirme Merkezi'nden yalnızca web yükleyicisini bağlayabilirsiniz. URL aynı zamanda dağıtılmakta olan uygulamanızın olduğu diski tanımlayabilir.

8. **Özellik sayfaları** Iletişim kutusunda **Tamam**' ı seçin.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>InstallAware dağıtımı

InstallAware, tek bir kaynaktan Windows uygulaması (APPX), Windows Installer (MSI), yerel kod (EXE) ve App-V (uygulama sanallaştırma) paketleri oluşturur. .NET Framework, isteğe bağlı olarak, [varsayılan betikleri düzenleyerek](https://www.installaware.com/msicode.htm)yüklemeyi özelleştirerek, kuruluminizdeki [tüm sürümlerini kolayca ekleyin](https://www.installaware.com/one-click-pre-requisite-installer.htm) . Örneğin, InstallAware Windows 7 ' de sertifikaları önceden yüklerken .NET Framework 4,7 kurulumu başarısız olur. InstallAware hakkında daha fazla bilgi için bkz. [InstallAware for Windows Installer](https://www.installaware.com/) Web sitesi.

### <a name="installshield-deployment"></a>InstallShield dağıtımı

InstallShield dağıtımı seçmek ve .net Framework üzerine bağımlılık eklemek için Visual Studio'yu içinde:

1. Visual Studio menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

2. **Yeni proje** iletişim kutusunun sol bölmesinde **diğer proje türleri**, **Kurulum ve dağıtım**, **InstallShield Le**' yi seçin.

3. **Ad** kutusuna projeniz için bir ad yazın ve ardından **Tamam**' ı seçin.

4. İlk kez bir kurulum ve dağıtım projesi oluşturuyorsanız, **InstallShield 'A git** ' i veya Microsoft Visual Studio sürümünüze ait InstallShield Limited Edition 'ı Indirmek Için **InstallShield Limited Edition 'ı etkinleştirin** . Visual Studio'yu yeniden başlatın.

5. Proje çıktısını eklemek için **Proje Yardımcısı** sihirbazına gidin ve **uygulama dosyalarını** seçin. Bu sihirbazı kullanarak diğer proje öznitelikleri yapılandırabilirsiniz.

6. **Yükleme gereksinimleri** ' ne gidin ve işletim sistemlerini ve yüklemek istediğiniz .NET Framework sürümünü seçin.

7. Kurulum projeniz için kısayol menüsünü açın ve **Oluştur**' a tıklayın.

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Windows Installer XML (WiX) dağıtımı

Windows Installer xml (WiX) araç takımı XML kaynak kodundan Windows yükleme paketleri oluşturur. WiX, MSI ve MSM kurulum paketleri oluşturmak için derleme sürecinize entegre bir komut satırı ortamını destekler. WiX kullanarak, [.NET Framework bir önkoşul olarak belirtebilir](https://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html)veya .NET Framework dağıtım deneyimini tam olarak denetlemek için [bir bağlayıcı oluşturabilirsiniz](https://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) . WiX hakkında daha fazla bilgi için [WINDOWS Installer XML (WiX) araç takımı](https://wixtoolset.org/) Web sitesine bakın.

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>.NET Framework el ile yükleme

Bazı durumlarda, uygulamanızla birlikte .NET Framework 'ü otomatik olarak yüklemek pratik olmayabilir. Bu durumda, kullanıcıların .NET Framework'ü kendilerinin kurmalarını isteyebilirsiniz. Yeniden dağıtılabilir paket [iki](#redistributable-packages)pakette kullanılabilir. Kurulum sürecinizde kullanıcıların .NET Framework'ü nasıl bulacakları ve yükleyecekleri hakkında yönergeler sağlar.

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>.NET Framework yüklemesini uygulamanızın kurulumuna zincirme

Uygulamanız için özel kurulum programı oluşturuyorsanız, uygulamanızın kurulum sürecine .NET Framework kurulum sürecini bağlayabilirsiniz(ekleyebilirsiniz). Bağlama .NET Framework yüklemesi için iki kullanıcı Arabirimi seçeneği sağlar:

- .NET Framework yükleyicisi tarafından sağlanan varsayılan kullanıcı arabirimini kullanın.

- Tutarlılık için uygulamanızın kurulum programıyla birlikte .NET Framework kurulumuna göre özel kullanıcı arabirimi oluşturun.

Her iki yöntem de web yükleyicisini veya çevrimdışı yükleyiciyi kullanmanıza olanak sağlar Her paketin kendine göre avantajları vardır:

- Web yükleyicisini kullanırsanız, .NET Framework Kurulum işlemi hangi yükleme paketinin gerekli olduğuna karar verecek ve Web'den o paketi indirip yükleyecektir.

- Kullanıcılarınız kurulum sürecinde Web'den başka dosyaları indirmek zorunda kalmamaları için çevrimdışı yükleyiciyi kullanabilir, yeniden dağıtım ortamınız için .NET Framework yükleme paketler setini ekleyebilirsiniz.

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>Varsayılan .NET Framework Kullanıcı arabirimini kullanarak zincirleme

.NET Framwork yükleme işlemini sessizce bağlamak ve .NET Framework kurucusunun kullanıcı arabirimini sağlaması için, kurulum programına aşağıdaki komutu ekleyin:

`<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>`

Örneğin, yürütülebilir programınız contoso. exe ise ve .NET Framework 4,5 çevrimdışı yeniden dağıtılabilir paketini sessizce yüklemek istiyorsanız şu komutu kullanın:

`dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso`

Yüklemeyi özelleştirmek için ek komut satırı seçeneklerini kullanabilirsiniz. Örneğin:

- Sistem yeniden başlatmalarını en aza indirmek için kullanıcıların çalışan .net Framework uygulamaları kapatmak için bir yol sağlamak için pasif modu ayarlayın ve aşağıdaki gibi `/showrmui` seçeneğini kullanın.

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     Bu komut, kullanıcıların .NET Framework yüklemeden önce .NET Framework uygulamaları kapatma fırsatı veren bir ileti kutusu görüntülemesini sağlar.

- Web yükleyicisi kullanıyorsanız, dil paketi belirtmek için `/LCID` seçeneğini kullanabilirsiniz. Örneğin, .NET Framework 4,5 web yükleyicisini contoso kurulum programınıza zincirlemek ve Japonca dil paketini yüklemek için uygulamanızın Kurulum işlemine aşağıdaki komutu ekleyin:

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     `/LCID` seçeneğini atlarsanız, Kurulum kullanıcının MUI ayarını eşleştiren dil paketini yükleyecektir.

    > [!NOTE]
    > Farklı dil paketlerinin farklı yayın tarihleri olabilir. Belirttiğiniz dil paketi indirme merkezinde bulunmuyorsa kurulum .NET Framework'ü dil paketi olmadan yükleyecektir. .NET Framework kullanıcının bilgisayarında önceden yüklüyse kurulum sadece dil paketini yükleyecektir.

Seçeneklerin tam listesi için [komut satırı seçenekleri](#command-line-options) bölümüne bakın.

Ortak dönüş kodları için [dönüş kodları](#return-codes) bölümüne bakın.

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Özel bir kullanıcı Arabirimi kullanılarak zincirleme

Özel kurulum paketiniz varsa, kurulum sürecinizin görüntüsünü gösterirken .NET Framework kurulumunu sessizce başlatmak ve izlemek isteyebilirsiniz. Bu durumda, kodunuzun aşağıdakini kapsadığından emin olun:

- [.NET Framework donanım ve yazılım gereksinimlerini](../get-started/system-requirements.md)denetleyin.

- .NET Framework doğru sürümünün kullanıcının bilgisayarında zaten yüklü olup olmadığını [algılar](#detect_net) .

    > [!IMPORTANT]
    > .NET Framework 'nin doğru sürümünün zaten yüklü olup olmadığını belirlemek için, hedef sürümünüzün yüklenip yüklenmediğini değil, hedef sürümünüzün *veya* sonraki bir sürümünün yüklü olup olmadığını denetlemeniz gerekir. Diğer bir deyişle, kayıt defterinden aldığınız yayın anahtarının hedef sürümünüzün yayın anahtarına eşit olup olmadığını *değil* , hedef sürümünüzün yayın anahtarından büyük veya ona eşit olup olmadığını değerlendirmelisiniz.

- Dil paketlerinin kullanıcının bilgisayarında zaten yüklü olup olmadığını [algılar](#detecting-the-language-packs) .

- Dağıtımı denetlemek isterseniz, .NET Framework kurulum işlemini sessizce başlatın ve izleyin (bkz. [nasıl yapılır: .NET Framework 4,5 Yükleyicisinden Ilerleme durumunu alma](how-to-get-progress-from-the-dotnet-installer.md)).

- Çevrimdışı yükleyiciyi dağıtıyorsanız, [dil paketlerini ayrı olarak zincirleyebilirsiniz](#chain_langpack).

- [Komut satırı seçeneklerini](#command-line-options)kullanarak dağıtımı özelleştirin. Örneğin, .NET Framework web yükleyicisini bağlıyorsanız, ancak varsayılan dil paketini geçersiz kılmak istiyorsanız önceki bölümde anlatıldığı şekilde `/LCID` seçeneğini kullanın.

- [Sorun giderin](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>.NET Framework algılama

.NET Framework yükleyicisi başarılı olduğunda kurucusu kayıt anahtarlarını yazar. `Release`adlı bir `DWORD` değeri için kayıt defterindeki `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klasörünü denetleyerek .NET Framework 4,5 veya sonraki bir sürümünün yüklü olup olmadığını test edebilirsiniz. ("NET Framework Setup" bir noktayla başlamayacağını unutmayın.) Bu anahtarın varlığı, bu bilgisayarda .NET Framework 4,5 veya sonraki bir sürümün yüklü olduğunu gösterir. `Release` değeri hangi .NET Framework sürümünün yüklü olduğunu gösterir.

> [!IMPORTANT]
> Belirli bir sürümün mevcut olup olmadığını algılamaya çalışırken Release anahtar sözcüğünün değerinden **büyük veya ona eşit** bir değer olup olmadığını denetlemeniz gerekir.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Sürüm|Yayın DWORD değeri|
|-------------|--------------------------------|
|.NET Framework 4,8, Windows 10 2019 Mayıs ' de yüklüdür|528040|
|Windows 10 Mayıs 2019 ' den farklı tüm işletim sistemi sürümlerine .NET Framework 4,8 yüklendi güncelleştirme|528049|
|Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803 ' de yüklü .NET Framework 4.7.2|461808|
|Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803 dışındaki tüm işletim sistemi sürümlerinde yüklü olan 4.7.2 .NET Framework. Buna Windows 10 Ekim 2018 güncelleştirmesi dahildir. |461814|
|Windows 10 Fall Creators Update ve Windows Server, sürüm 1709 ' de yüklü .NET Framework 4.7.1|461308|
|Windows 10 Fall Creators Update ve Windows Server, sürüm 1709 dışındaki tüm işletim sistemi sürümlerinde yüklü olan .NET Framework 4.7.1|461310|
|.NET Framework 4,7 Windows 10 Creators Update 'e yüklendi|460798|
|Windows 10 Creators Update dışındaki tüm işletim sistemi sürümlerinde 4,7 .NET Framework yüklendi|460805|
|Windows 10 yıldönümü Edition 'da ve Windows Server 2016 ' de yüklü .NET Framework 4.6.2|394802|
|Windows 10 yıldönümü sürümü ve Windows Server 2016 dışındaki tüm işletim sistemi sürümlerinde yüklü olan .NET Framework 4.6.2|394806|
|.NET Framework 4.6.1 Windows 10 Kasım güncelleştirmesine yüklendi|394254|
|Windows 10 Kasım güncelleştirmesi dışındaki tüm işletim sistemi sürümlerinde yüklü olan .NET Framework 4.6.1|394271|
|.NET Framework 4,6 Windows 10 ' da yüklü|393295|
|Windows 10 dışındaki tüm işletim sistemi sürümlerinde 4,6 .NET Framework yüklendi|393297|
|.NET Framework 4.5.2|379893|
|Windows 8.1 veya Windows Server 2012 R2 ile yüklenen .NET Framework 4.5.1|378675|
|Windows 8, Windows 7 ' de yüklü .NET Framework 4.5.1|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>Dil paketleri algılanıyor

`Release`adlı bir DWORD değeri için kayıt defterindeki HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* klasörünü denetleyerek belirli bir dil paketinin yüklenip yüklenmediğini test edebilirsiniz. ("NET Framework Setup" bir noktayla başlamayacağını unutmayın.) *LCID* bir yerel ayar tanımlayıcıyı belirtir; Bunların listesi için [desteklenen diller](#supported-languages) bölümüne bakın.

Örneğin, tam Japonca dil paketinin (LCıD = 1041) yüklü olup olmadığını algılamak için, kayıt defterinden aşağıdaki adlandırılmış değeri alın:

| | |
|-|-|
| Anahtar | HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041 |
| Name | Sürüm |
| Tür | DWORD |

4,5 ile 4.7.2 arasında .NET Framework belirli bir sürümü için dil paketinin son sürümünün yüklenip yüklenmediğini saptamak için, önceki bölümde açıklanan yayın anahtarı DWORD değerinin değerini denetleyin ve [.NET Framework](#detect_net)tespit edin.

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Dil paketlerini uygulama kuruluma zincirleme

.NET Framework özel kültürler için yerelleştirilmiş kaynakları içeren bağımsız dil paketi yürütülebilir dosyalar setini sağlar. Dil paketleri, Microsoft İndirme Merkezi'nden edinilebilir:

- [.NET Framework 4,8 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=2086170)

- [.NET Framework 4.7.2 dil paketleri](https://go.microsoft.com/fwlink/?LinkId=863275)

- [.NET Framework 4.7.1 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=852090)

- [.NET Framework 4,7 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=825306)

- [.NET Framework 4.6.2 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=780604)

- [.NET Framework 4.6.1 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=671747)

- [.NET Framework 4,6 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=528314)

- [.NET Framework 4.5.2 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=397701)

- [.NET Framework 4.5.1 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=322101)

- [.NET Framework 4,5 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Dil paketleri, bir uygulamayı çalıştırmak için gereken .NET Framework bileşenlerini içermezler; bir dil paketi yüklemeden önce web veya çevrimdışı yükleyiciyi kullanarak .NET Framework'ü yüklemeniz gerekir.

.NET Framework 4.5.1 ' den itibaren, paket adları NDP <`version`>-KB <`number`>-x86-x64-Allows-<`culture`>. exe ' dir; burada `version`, .NET Framework sürüm numarasıdır, `number` bir Microsoft Bilgi Bankası makale numarasıdır ve `culture` bir [ülke/bölge](#supported-languages)belirtir. Bu paketlerin bir örneği `NDP452-KB2901907-x86-x64-AllOS-JPN.exe` 'dir. Paket adları, bu makalenin önceki bölümlerinde [yeniden dağıtılabilir paketler](#redistributable-packages) bölümünde listelenmiştir.

Dil paketini .NET Framework çevrimdışı yükleyici ile yüklemek için uygulamanızın kurulumuna eklemelisiniz. Örneğin, 4.5.1 .NET Framework çevrimdışı yükleyiciyi Japonca dil paketiyle dağıtmak için aşağıdaki komutu kullanın:

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

Web yükleyicisini kullanmak istiyorsanız dil paketlerini bağlamanıza gerek yoktur, kurulum kullanıcının MUI ayarlarıyla eşleşen dil paketlerini yükleyecektir. Farklı bir dil yüklemek isterseniz, dil paketi belirtmek için `/LCID` 'yi kullanabilirsiniz.

Komut satırı seçeneklerinin tam listesi için bkz. [komut satırı seçenekleri](#command-line-options) bölümü.

### <a name="troubleshooting"></a>Sorun giderme

#### <a name="return-codes"></a>Dönüş kodları

Aşağıdaki tablo .NET Framework yeniden dağıtılabilir yükleyici için en sık karşılaşılan döndürülen kodları listeler. Dönüş kodları yükleyicinin tüm sürümleri için aynıdır. Ayrıntı bilgi linkleri için sonraki bölüme bakın.

|Dönüş kodu|Açıklama|
|-----------------|-----------------|
|0|Yükleme başarıyla tamamlandı.|
|1602|Kullanıcı yüklemeyi iptal etti.|
|1603|Yükleme sırasında ciddi bir hata oluştu.|
|1641|Yüklemenin tamamlanması için yeniden başlatma gereklidir. Bu ileti başarılı olduğunu gösterir.|
|3010|Yüklemenin tamamlanması için yeniden başlatma gereklidir. Bu ileti başarılı olduğunu gösterir.|
|5100|Kullanıcının bilgisayarı sistem gereksinimlerini karşılamıyor.|

#### <a name="download-error-codes"></a>İndirme hatası kodları

Aşağıdaki içeriğe bakın:

- [Arka Plan Akıllı Aktarım Hizmeti (BITS) hata kodları](https://go.microsoft.com/fwlink/?LinkId=180946)

- [URL bilinen adı hata kodları](https://go.microsoft.com/fwlink/?LinkId=180947)

- [WinHttp hata kodları](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Diğer hata kodları

Aşağıdaki içeriğe bakın:

- [Windows Installer hata kodları](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Windows Update Aracısı sonuç kodları](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>.NET Framework'ün kaldırılması

Windows 8 ' den itibaren, Denetim Masası 'ndaki **Windows özelliklerini aç ve Kapat** ' ı kullanarak, .NET Framework 4,5 veya kendi nokta sürümlerinden birini kaldırabilirsiniz. Windows 'un eski sürümlerinde, Denetim Masası 'ndaki **Program Ekle veya Kaldır** ' ı kullanarak .NET Framework 4,5 ' i veya nokta sürümlerinden birini kaldırabilirsiniz.

> [!IMPORTANT]
> Windows 7 ve önceki işletim sistemlerinde, .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 veya 4,8 ' ı kaldırmak .NET Framework 4,5 dosyalarını geri almaz ve .NET Framework 4,5 kaldırıldığında .NET Framework 4 dosyası geri almaz. Eski sürüme dönmek istiyorsanız, eski sürümü ve tüm güncellemelerini yeniden yüklemeniz gerekir.

## <a name="appendix"></a>Ek

### <a name="command-line-options"></a>Komut satırı seçenekleri

Aşağıdaki tabloda, .NET Framework 4,5 yeniden dağıtılabilir öğesini uygulamanızın kurulumuna zincirlerken dahil edilecek seçenekler listelenmektedir.

|Seçenek|Açıklama|
|------------|-----------------|
|**/Ceiponayı**|Varsayılan davranışını tekrardan yazar ve gelecekteki dağıtım deneyimleri geliştirmek üzere Microsoft'a anonim geri bildirim gönderir. Bu seçenek, kurulum programın rıza istemesine sebep olursa ve kullanıcı anonim görüşlerinizi Microsoft'a göndermek için izin verirse kullanılabilir.|
|**/ChainingPackage** `packageName`|Bağlama yapman çalıştırılabilirin adını belirtir. Gelecekteki dağıtım deneyimlerini iyileştirilmesine yardımcı olmak için anonim görüş deneyimleri olarak bu bilgiler Microsoft'a gönderilir.<br /><br /> Paket adı boşluk içeriyorsa, çift tırnak işaretlerini sınırlayıcılar olarak kullanın; Örneğin: **/chainingpackage "Lucerne Publishing"** . Bir zincir paketi örneği için bkz. MSDN kitaplığındaki [bir yükleme paketinden Ilerleme bilgisi alma](https://go.microsoft.com/fwlink/?LinkId=181926) .|
|**/LCID**`LCID`<br /><br /> Burada `LCID` bir yerel ayar tanımlayıcıyı belirtir (bkz. [desteklenen diller](#supported-languages))|`LCID` tarafından belirtilen dil paketini yükler ve sessiz mod ayarlanmadığı sürece görüntülenen kullanıcı arabirimi o dilde gözükmesi için zorlar.<br /><br /> Web yükleyicisi için bu seçenek dil paketini webden yüklemek için bağlayıcı yükleme yapar. **Note:**  Bu seçeneği yalnızca Web yükleyicisiyle kullanın.|
|**/log** `file` &#124; `folder`|Günlük dosyasının konumunu belirtir. Varsayılan işlem için geçici dosyadır ve varsayılan dosya ismi pakete dayalıdır. Dosya uzantısı .txt ise, metin günlüğü oluşturulur. Başka bir uzantı belirtirseniz veya bir uzantı belirtmezseniz, bir html günlüğü oluşturulur.|
|**/msioptions**|.msi ve .msp öğeleri için geçirilecek seçeneklerini belirtir; Örneğin: `/msioptions "PROPERTY1='Value'"`.|
|**/ norestart**|Kurulum programının otomatik olarak yeniden başlatılmasını önler. Bu seçeneği kullanırsanız, zincirleme uygulamanın dönüş kodunu yakalaması ve yeniden başlatma işlemini işlemesi gerekir (bkz. MSDN kitaplığındaki [bir yükleme paketinden Ilerleme bilgilerini alma](https://go.microsoft.com/fwlink/?LinkId=179606) ).|
|**/ passive**|Pasif modu ayarlar. Yüklemenin sürdürüldüğünü belirtmek için ilerleme çubuğunu gösterir ama hiçbir hızlı cevap yada hata iletilerini kullanıcıya göstermez. Bu modda, bir kurulum programı tarafından zincirleme yaparken, zincirleme paketi [dönüş kodlarını](#return-codes)işlemelidir.|
|**/Pipe**|İlerleme durumunu elde etmek zincirleme bir paket için bir iletişim kanalı oluşturur.|
|**/promptrestart**|Sadece pasif modda, kurulum programı yeniden başlatma gerekirse kullanıcıya hızlı bir cevap verir. Yeniden başlatma gerekirse bu seçenek kullanıcı etkileşimini gerektirir.|
|**/q**|Sessiz modu ayarlar.|
|**/ Repair**|Onarma işlevini tetikler.|
|**/serialdownload**|Yüklemeyi yalnızca paket indirildikten sonra yapılmaya zorlar.|
|**/showfinalhatası**|Pasif modu ayarlar. Yalnızca yükleme başarılı değilse hataları görüntüler. Yükleme başarılı değilse, bu seçenek kullanıcı etkileşimini gerektirir.|
|**/showrmuı**|Yalnızca **/passive** seçeneğiyle kullanılır. Çalışmakta olan .NET Framework uygulamaları kapatmak için kullanıcıları uyaran bir ileti kutusu görüntüler. Bu ileti kutusu pasif ve pasif olmayan modda aynı şekilde davranır.|
|**/uninstall**|.NET Framework yeniden dağıtılabilirini kaldırır.|

### <a name="supported-languages"></a>Desteklenen diller

Aşağıdaki tabloda, .NET Framework 4,5 ve nokta sürümleri için kullanılabilen dil paketleri listelenmektedir .NET Framework.

|LCID|Dil - ülke/bölge|Kültür|
|----------|--------------------------------|-------------|
|1025|Arapça-Suudi Arabistan|Ar|
|1028|Çince - Geleneksel|zh-Hant|
|1029|Çekçe|cs|
|1030|Danca|da|
|1031|Almanca – Almanya|de|
|1032|Yunanca|el|
|1035|Fince|fi|
|1036|Fransızca – Fransa|fr|
|1037|İbranice|LIP|
|1038|Macarca|hu|
|1040|İtalyanca – İtalya|it|
|1041|Japonca|ja|
|1042|Korece|ko|
|1043|Felemenkçe – Hollanda|nl|
|1044|Norveççe (Bokmål)|hayır|
|1045|Lehçe|pl|
|1046|Portekizce – Brezilya|pt-BR|
|1049|Rusça|ru|
|1053|İsveççe|sv|
|1055|Türkçe|tr|
|2052|Çince - Basitleştirilmiş|zh-Hans|
|2070|Portekizce – Portekiz|pt-PT|
|3082|İspanyolca - İspanya (Modern sıralama)|es|

## <a name="see-also"></a>Ayrıca bkz.

- [Yöneticiler için Dağıtım Kılavuzu](guide-for-administrators.md)
- [Sistem Gereksinimleri](../get-started/system-requirements.md)
- [Geliştiriciler için .NET Framework yüklemesi](../install/guide-for-developers.md)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../install/troubleshoot-blocked-installations-and-uninstallations.md)
- [.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma](reducing-system-restarts.md)
- [Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](how-to-get-progress-from-the-dotnet-installer.md)
