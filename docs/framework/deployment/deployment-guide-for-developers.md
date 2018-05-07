---
title: Geliştiriciler için .NET framework Dağıtım Kılavuzu
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14bb5cd242a45b98a23a9d807b22aa4487d2591e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="net-framework-deployment-guide-for-developers"></a>Geliştiriciler için .NET framework Dağıtım Kılavuzu
Bu konu için .NET Framework 4.5 .NET Framework'ün herhangi bir sürümünü yüklemek için isteyen geliştiriciler için bilgi sağlamaktadır [!INCLUDE[net_current](../../../includes/net-current-version.md)] uygulamalarını ile.

Yükleme bağlantıları için bakın [yeniden dağıtılabilir paketleri](#redistributable-packages). Ayrıca bu Microsoft Download Center sayfalarından yeniden dağıtılabilir paketleri ve dil paketlerini yükleyebilirsiniz:

- Tüm işletim sistemleri için .NET framework 4.7.2 ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=863262) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=863265))

- Tüm işletim sistemleri için .NET framework 4.7.1 ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=852095) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=852107))

- Tüm işletim sistemleri için .NET framework 4.7 ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=825299) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=825303))

- [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] tüm işletim sistemleri için ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=780597) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=780601))

- [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] tüm işletim sistemleri için ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=671729) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=671744))

- [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] tüm işletim sistemleri için ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=528222) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=528232))

- Tüm işletim sistemleri için .NET framework 4.5.2 ([web yükleyicisi](http://go.microsoft.com/fwlink/p/?LinkId=397703) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=397706))

- Tüm işletim sistemleri için .NET framework 4.5.1 ([web yükleyicisi](http://go.microsoft.com/fwlink/p/?LinkId=310158) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=310159))

- [.NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)

 Önemli Notlar:

> [!NOTE]
> Tümcecik " [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve kendi noktası yayımları" başvurduğu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve tüm sonraki sürümler.

- .NET Framework'teki sürümlerini [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] aracılığıyla [!INCLUDE[net_current](../../../includes/net-current-version.md)] yerinde güncelleştirmelerin [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], başka bir deyişle, aynı çalışma zamanı sürümü kullanır, ancak derleme sürümlerini güncelleştirilir ve yeni türleri ve üyeleri içerir.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Ve kendi noktası sürümleri üzerinde artımlı olarak yerleşik [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Yüklediğinizde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya kendi noktası bulunan bir sistemde serbest [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] yüklü sürüm 4 derlemeleri daha yeni sürümleri ile değiştirilir.

- Bir Microsoft başvurduğunuzdan varsa [bant dışı paket](http://msdn.microsoft.com/library/dn151288\(v=vs.110\).aspx) uygulamanızda, uygulama paketi derleme eklenecektir.

- Yüklemek için yönetici ayrıcalıklarına sahip olmalısınız [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve kendi noktası serbest bırakır.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Dahil [!INCLUDE[win8](../../../includes/win8-md.md)] ve [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], böylece uygulamanız bu işletim sistemlerindeki ile dağıtmak gerekmez. Benzer şekilde, [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] dahil [!INCLUDE[win81](../../../includes/win81-md.md)] ve Windows Server 2012 R2. .NET Framework 4.5.2'deki tüm işletim sistemlerinde dahil değildir. [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] Windows 10'da dahil [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Windows 10 Kasım güncelleştirmesine dahil ve [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Windows 10 Anniversary güncelleştirmesine dahil.  .NET Framework 4.7 Windows 10 oluşturucuları güncelleştirmesine dahil, .NET Framework 4.7.1 Windows 10 sonbaharda oluşturucuları güncelleştirmesine dahil ve .NET Framework 4.7.2 Windows'taki 10 Nisan 2018 güncelleştirin. Donanım ve yazılım gereksinimlerinin tam listesi için bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).

- İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kullanıcılarınızın .NET Framework uygulamalarını Kurulum sırasında çalışan listesini görüntüleyebilir ve bunları kolayca kapatın. Bu, .NET Framework yüklemeleri tarafından nedeni sistemin yeniden önlemenize yardımcı. Bkz: [sistem yeniden başlatmalarını azaltma](../../../docs/framework/deployment/reducing-system-restarts.md).

- Kaldırma [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya bir noktasının serbest de önceden mevcut olan kaldırır [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] dosyaları. Geri dönüp istiyorsanız [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]ve bunu herhangi bir güncelleştirme yeniden yüklemeniz gerekir. (Bkz [.NET Framework 4 yükleme](http://msdn.microsoft.com/library/5a4x27ek\(v=vs.100\).aspx).)

- .NET Framework 4.5 yeniden dağıtılabilir 9 Ekim, dijital imza üretilen ve erken sona Microsoft tarafından imzalanmış dosyalarını neden bir dijital sertifika yanlış bir zaman damgasını ilgili bir sorunu gidermek için 2012 güncelleştirildi. .NET Framework 4.5 tarihli 16 Ağustos 2012 yeniden dağıtılabilir paketi daha önce yüklediyseniz en son yeniden dağıtılabilir ile kopyanızı güncelleştirmenizi öneririz [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=245484). Bu sorun hakkında daha fazla bilgi için bkz: [Microsoft güvenlik önerisi 2749655](http://technet.microsoft.com/security/advisory/2749655).

 Nasıl bir Sistem Yöneticisi .NET Framework ve sistem bağımlılıklarını bir ağ üzerinden dağıtabilirsiniz hakkında daha fazla bilgi için bkz: [Yöneticiler için Dağıtım Kılavuzu](../../../docs/framework/deployment/guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Uygulamanız için dağıtım seçenekleri
 Kullanıcıların yükleyebileceğiniz uygulamanızı bir web sunucusu veya başka bir merkezi konuma yayımlamaya hazır olduğunuzda, bazı dağıtım yöntemler arasından seçim yapabilirsiniz. Bunlardan bazıları Visual Studio ile sağlanır. Aşağıdaki tabloda, uygulamanız için dağıtım seçeneklerini listeler ve her seçeneğin destekleyen .NET Framework yeniden dağıtılabilir paketi belirtir. Bunlara ek olarak, uygulamanız için özel kurulum programını yazabilirsiniz; Daha fazla bilgi için bkz [bilgisayarınızı uygulamanın kurulumu .NET Framework yüklemesi zincirleme](#chaining).

|Uygulamanız için Dağıtım stratejisi|Dağıtım yöntemleri kullanılabilir|Kullanmak için .NET framework yeniden dağıtılabilir|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Web'den yükleme|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [WiX toolset](#wix)<br />- [El ile yükleme](#installing_manually)|[Web yükleyicisi](#redistributable-packages)|
|Diskten yükleyin|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [WiX toolset](#wix)<br />- [El ile yükleme](#installing_manually)|[Çevrimdışı yükleyici](#redistributable-packages)|
|Yerel alan ağı (Kurumsal uygulamaları için) yükleyin|- [ClickOnce](#clickonce-deployment)|Her iki [web yükleyicisi](#redistributable-packages) (bkz [ClickOnce](#clickonce-deployment) kısıtlamaları için) veya [çevrimdışı yükleyici](#redistributable-packages)|

## <a name="redistributable-packages"></a>Yeniden dağıtılabilir paketler
 .NET Framework yeniden dağıtılabilir iki paket mevcuttur: web Yükleyicisi (Önyükleyici) ve çevrimdışı Yükleyici (tek başına yeniden dağıtılabilir). Aşağıdaki tabloda iki paket karşılaştırır.

||Web yükleyicisi|Çevrimdışı yükleyici|
|-|-------------------|-----------------------|
|Dosya indirme|.NET framework 4.7.2: <br/>[NDP472 KB4054531 Web.exe](http://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>.NET framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](http://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>.NET framework 4.7: <br />[NDP47-KB3186500-Web.exe](http://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151802-Web.exe](http://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]:<br />[NDP461-KB3102438-Web.exe](http://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]:<br />[NDP46-KB3045560-Web.exe](http://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](http://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2859818-Web.exe](http://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_setup.exe](http://go.microsoft.com/fwlink/?LinkId=225704)|.NET framework 4.7.2: <br/>[NDP472-KB4054530-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>.NET framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET framework 4.7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_x86_x64.exe](http://go.microsoft.com/fwlink/?LinkId=225702)|
|Internet bağlantısı gerekiyor?|Evet|Hayır|
|İndirme boyutu|Küçük (yalnızca hedef platform için yükleyiciyi içerir) *|Daha büyük *|
|Dil paketleri|Dahil edilen **|Olmalıdır [ayrı ayrı yüklenmiş](#chain_langpack), tüm işletim sistemleri hedefler paket kullanmadığınız sürece|
|Dağıtım yöntemi|Tüm yöntemleri destekler:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [El ile yükleme](#installing_manually)<br />- [Özel Kurulum (zincirleme)](#chaining)|Tüm yöntemleri destekler:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [El ile yükleme](#installing_manually)<br />- [Özel Kurulum (zincirleme)](#chaining)|
|ClickOnce dağıtımı için yükleme konumu|Microsoft İndirme Merkezi:<br /><br /> - [.NET framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET framework 4.5.2](http://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [.NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|Kendi sunucunuzu veya Microsoft Download Center:<br /><br /> - [.NET framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET framework 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [.NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|

 \* Çevrimdışı Yükleyici daha büyük olduğundan tüm hedef platformlar için bileşenleri içerir. Kur'u çalıştırmayı tamamladığınızda, Windows işletim sisteminin kullanılan yükleyici önbelleğe alır. Çevrimdışı Yükleyici yükleme sonrasında silinirse, kullanılan disk alanı web yükleyici tarafından kullanılan aynıdır. Aracı kullanıyorsanız (örneğin, [InstallAware](#installaware-deployment) veya [InstallShield](#installshield-deployment)), uygulamanızın Kurulum programı oluşturmak için yüklemeden sonra kaldırılmadan bir kurulum dosyası sağlar, çevrimdışı yükleyici olabilir Kurulum klasörüne yerleştirme tarafından otomatik olarak silinir.

 ** Web yükleyicisi özel kurulum ile kullanıyorsanız, kullanıcının çok dilde kullanıcı arabirimi (MUI) ayarına göre varsayılan dil ayarlarını kullanmak, veya başka bir dil paketini kullanarak belirtin `/LCID` komut satırı seçeneği. Bölümüne bakın [varsayılan .NET Framework UI kullanarak zincirleme](#chaining_default) örnekleri için.

## <a name="deployment-methods"></a>Dağıtım yöntemleri
 Dört dağıtım yöntemleri kullanılabilir:

- .NET Framework üzerinde bir bağımlılık ayarlayabilirsiniz. Aşağıdaki yöntemlerden birini kullanarak, uygulamanızın yüklemede önkoşul olarak .NET Framework belirtebilirsiniz:

    - Kullanım [ClickOnce dağıtımı](#clickonce-deployment) (Visual Studio ile kullanılabilir)

    - Oluşturma bir [InstallAware proje](#installaware-deployment) (ücretsiz sürüm Visual Studio kullanıcılar için kullanılabilir)

    - Oluşturma bir [InstallShield proje](#installshield-deployment) (Visual Studio ile kullanılabilir)

    - Kullanım [Windows Installer XML (WiX) toolset](#wix)

- Kullanıcılarınıza sorabilirsiniz [.NET Framework'ü el ile yüklemek](#installing_manually).

- Zincir (dahil) .NET Framework Kurulum işlemi, uygulamanızın kurulumunda ve .NET Framework yükleme deneyimi işlemek nasıl istediğinize karar verin:

    - [Varsayılan UI kullanmak](#chaining_default). Yükleme deneyimi sağlamak .NET Framework yükleyici olanak tanır.

    - [UI özelleştirme](#chaining_custom) birleşik yükleme deneyimi sunmak için ve .NET Framework yükleme ilerleme durumunu izlemek için.

 Bu dağıtım yöntemleri, aşağıdaki bölümlerde ayrıntılı olarak ele alınmıştır.

## <a name="setting-a-dependency-on-the-net-framework"></a>.NET Framework üzerinde bir bağımlılık ayarlama
Uygulamanızı dağıtmak için ClickOnce, InstallAware, InstallShield veya WiX kullanıyorsanız, uygulamanızı bir parçası olarak yüklenebilmesi için .NET Framework üzerinde bir bağımlılık ekleyebilirsiniz.

### <a name="clickonce-deployment"></a>ClickOnce dağıtımı
 Visual Basic ve Visual C# ile oluşturulan projeleri için ClickOnce dağıtımı kullanılabilir, ancak Visual C++ için kullanılabilir değil.

 ClickOnce dağıtımı seçin ve .NET Framework üzerinde bir bağımlılık eklemek için Visual Studio'yu içinde:

1.  Yayımlamak istediğiniz uygulama projesini açın.

2.  Çözüm Gezgini'nde, projeniz için kısayol menüsünü açın ve ardından **özellikleri**.

3.  Seçin **Yayımla** bölmesi.

4.  Seçin **Önkoşullar** düğmesi.

5.  İçinde **Önkoşullar** iletişim kutusunda, olduğundan emin olun **Önkoşul bileşenlerini yüklemek için Kurulum programını oluşturun** onay kutusu seçilidir.

6.  Önkoşullar listesinde bulun ve projenizi yapılandırmak için kullandığınız .NET Framework sürümünü seçin.

7.  Önkoşullar için kaynak konumu belirtin ve ardından bir seçenek belirleyin **Tamam**.

     .NET Framework indirme konumu için bir URL sağlarsanız, Microsoft Download Center site veya bir site kendi belirtebilirsiniz. Kendi sunucunuzu yeniden dağıtılabilir paketi yerleştirme, çevrimdışı yükleyici ve web yükleyicisi olmalıdır. Yalnızca Microsoft Download Center web yükleyicisini bağlayabilirsiniz. URL, kendi uygulamanızı dağıtılmakta bir disk de belirtebilirsiniz.

8.  İçinde **özellik sayfaları** iletişim kutusunda, seçin **Tamam**.

<a name="installaware"></a> 
### <a name="installaware-deployment"></a>InstallAware dağıtımı
Windows uygulaması (APPX), Windows Installer (MSI), yerel kod (EXE) ve App-V (Application Virtualization) paketleri tek bir kaynaktan InstallAware oluşturur. Kolayca [herhangi bir .NET Framework sürümü dahil](https://www.installaware.com/one-click-pre-requisite-installer.htm) kurulumunuza, isteğe bağlı olarak yükleme tarafından özelleştirme [varsayılan komut dosyalarını düzenleme](https://www.installaware.com/msicode.htm). Örneğin, Windows 7, hangi .NET Framework 4.7 kurulum başarısız sertifikaları InstallAware önceden yükler. InstallAware hakkında daha fazla bilgi için bkz: [InstallAware için Windows Installer](https://www.installaware.com/) Web sitesi.

### <a name="installshield-deployment"></a>InstallShield dağıtım
 Visual InstallShield dağıtımı seçin ve .NET Framework üzerinde bir bağımlılık eklemek için Studio'da:

1.  Visual Studio menü çubuğunda seçin **dosya**, **yeni**, **proje**.

2.  Sol bölmesinde **yeni proje** iletişim kutusunda, seçin **diğer proje türleri**, **Kurulum ve dağıtım**, **InstallShield LE**.

3.  İçinde **adı** kutusunda, projeniz için bir ad yazın ve ardından **Tamam**.

4.  Kurulum ve dağıtım projesi ilk kez oluşturuyorsanız, seçin **InstallShield için Git** veya **etkinleştirmek InstallShield Limited Edition** InstallShield Limited Edition sürümü için karşıdan yüklemek için Microsoft Visual Studio. Visual Studio'yu yeniden başlatın.

5.  Git **proje Yardımcısı** Sihirbazı ve **uygulama dosyaları** proje çıktı eklemek için. Bu sihirbazı kullanarak diğer proje öznitelikleri yapılandırabilirsiniz.

6.  Git **yükleme gereksinimleri** ve işletim sistemleri ve yüklemek istediğiniz .NET Framework sürümünü seçin.

7.  Kurulum projeniz için kısayol menüsünü açın ve seçin **yapı**.
 
<a name="wix"></a> 
### <a name="windows-installer-xml-wix-deployment"></a>Windows Installer XML (WiX) dağıtımı
 Windows Installer XML (WiX) toolset Windows yükleme paketleri XML kaynak kodunu oluşturur. WiX MSI ve MSM kurulum paketleri oluşturmak için yapı işleminize tümleşik bir komut satırı ortamı destekler. WiX kullanarak şunları yapabilirsiniz [bir önkoşul olarak .NET Framework belirtin](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html), veya [bir bağlayıcı oluşturmak](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) .NET Framework dağıtım deneyimi tamamen kontrol etme. WiX hakkında daha fazla bilgi için bkz: [Windows Installer XML (WiX) toolset](http://wixtoolset.org/) Web sitesi.

<a name="installing_manually"></a> 
## <a name="installing-the-net-framework-manually"></a>.NET Framework el ile yükleme
 Bazı durumlarda, .NET Framework ile uygulamanızı otomatik olarak yüklemek için pratik olabilir. Bu durumda, kullanıcıların kendilerini .NET Framework'ü yüklemek olabilir. Yeniden dağıtılabilir paketi kullanılabilir [iki paket](#redistributable-packages). Kurulum işleminize nasıl kullanıcılar bulun ve .NET Framework'ü yüklemek için yönergeler sağlar.

<a name="chaining"></a> 
## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Uygulamanızın kurulumu .NET Framework yüklemesi zincirleme
 Uygulamanız için özel kurulum programını oluşturuyorsanız, zincir (dahil), uygulamanızın Kurulum işlemi .NET Framework Kurulum işleminde. Zincirleme .NET Framework yüklemesi için iki UI seçeneklerini sağlar:

- Varsayılan .NET Framework yükleyici tarafından sağlanan kullanıcı arabirimini kullanın.

- Tutarlılık için .NET Framework yüklemesi için özel bir kullanıcı Arabirimi, uygulamanın Kurulum programının ile oluşturun.

 Her iki yöntem web yükleyicisi veya çevrimdışı yükleyici kullanmanızı sağlar. Her paket, avantajları vardır:

- Web yükleyicisi kullanırsanız, .NET Framework Kurulum işlemi hangi yükleme paketini gereklidir karar indirin ve web sunucusundan yalnızca bu paketi yükleyin.

- Çevrimdışı yükleyici kullanırsanız, böylece kullanıcılarınızın ek dosyalardan Kurulum sırasında Web'den gerekmez, .NET Framework yükleme paketleri tamamını yeniden dağıtımı medyanızı ekleyebilirsiniz.

<a name="chaining_default"></a> 
### <a name="chaining-by-using-the-default-net-framework-ui"></a>Varsayılan .NET Framework UI kullanarak birbirine bağlama
 Sessizce .NET Framework yükleme işlemi zincir ve kullanıcı Arabirimi sağlayan .NET Framework yükleyici izin vermek için Kurulum programı için aşağıdaki komutu ekleyin:

```
<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>
```

 Örneğin, çalıştırılabilir program Contoso.exe ise ve sessiz bir şekilde istiyorsanız yükleyin [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] çevrimdışı yeniden dağıtılabilir paketi, şu komutu kullanın:

```
dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso
```

 Yüklemeyi özelleştirmek için ek komut satırı seçeneklerini kullanabilirsiniz. Örneğin:

- Sistem yeniden başlatmaları en aza indirmek için kullanıcıların çalışan .NET Framework uygulamaları kapatmak için bir yol sağlamak üzere ayarladığınızda Pasif modu ve `/showrmui` gibi seçeneği:

    ```
    dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso
    ```

     Bu komut, .NET Framework yüklemeden önce .NET Framework uygulamaları kapatma fırsatı kullanıcılara bir ileti kutusu görüntülemek yeniden başlatma Yöneticisi sağlar.

- Web yükleyicisi kullanıyorsanız, kullanabileceğiniz `/LCID` seçeneği bir dil paketi belirtin. Örneğin, zinciri için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] web Contoso Kurulum programına yükleyici ve Japonca dil paketini yüklemeniz, uygulamanızın Kurulum işlemi için aşağıdaki komutu ekleyin:

    ```
    dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041
    ```

     Atlarsanız `/LCID` seçeneği, Kurulum kullanıcının MUI ayarını eşleşen dil paketi yükler.

    > [!NOTE]
    > Farklı dil paketleri, farklı bir sürüm tarihleri olabilir. Kurulum, belirttiğiniz dil paketi İndirme Merkezi'nde kullanılabilir durumda değilse, .NET Framework dil paketi olmadan yükleyecek. .NET Framework kullanıcının bilgisayarda zaten yüklüyse, Kurulum yalnızca dil paketi yükleyin.

 Seçenekler tam bir listesi için bkz: [komut satırı seçenekleri](#command-line-options) bölümü.

 Ortak dönüş kodları için bkz: [dönüş kodları](#return-codes) bölümü.

<a name="chaining_custom"></a>
### <a name="chaining-by-using-a-custom-ui"></a>Özel bir kullanıcı arabirimini kullanarak zincirleme
 Özel kurulum paketi varsa, sessiz bir şekilde başlatın ve Kurulum ilerleme kendi görünüm gösterirken .NET Framework kurulumunu izlemek isteyebilirsiniz. Bu durumda, kodunuzu aşağıdakileri kapsayan emin olun:

- Denetleme [.NET Framework donanım ve yazılım gereksinimleri](../../../docs/framework/get-started/system-requirements.md).

- [Algılama](#detect_net) olup kullanıcının bilgisayarında yüklü .NET Framework doğru sürümü.

    > [!IMPORTANT]
    > .NET Framework'ün doğru sürümü zaten yüklü olup olmadığını belirlerken, denetlemelisiniz olup olmadığını hedef sürümünüzü *veya* değil, hedef sürümü yüklü olup olmadığını sonraki bir sürümü yüklü. Kayıt defterinden almak yayın anahtar değerinden büyük veya eşit, hedef sürüm yayın anahtarı olup başka bir deyişle, değerlendirmelidir *değil* olup, hedef sürüm yayın anahtarı eşittir.

- [Algılama](#detecting-the-language-packs) olup dil paketlerini kullanıcının bilgisayarında zaten yüklenir.

- Dağıtım denetlemek istiyorsanız, sessizce başlatın ve .NET Framework Kurulum işlemi izlemek (bkz [nasıl yapılır: .NET Framework 4.5 yükleyici ilerlemesini Al](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)).

- Çevrimdışı yükleyici dağıtıyorsanız [dil paketlerini ayrı olarak zincir](#chain_langpack).

- Dağıtım kullanarak özelleştirebileceğiniz [komut satırı seçenekleri](#command-line-options). Örneğin, .NET Framework web yükleyicisi zincirleme, ancak varsayılan dil paketi geçersiz kılma, kullanmak istediğiniz `/LCID` , önceki bölümde açıklandığı gibi seçeneği.

- [Sorun giderme](#troubleshooting).

<a name="detect_net"></a>
### <a name="detecting-the-net-framework"></a>.NET Framework algılama
 Yükleme başarılı olduğunda .NET Framework yükleyici kayıt defteri anahtarlarını yazar. Test edebilirsiniz olup olmadığını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya üstü denetleyerek yüklü `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klasörü için kayıt defterinde bir `DWORD` adlı değeri `Release`. ("NET Framework Kurulumu" bir nokta ile başlamıyor unutmayın.) Bu anahtar varlığını gösteren [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya sonraki bir sürümü bu bilgisayarda yüklü. Değeri `Release` .NET Framework'ün hangi sürümünün yüklü olduğunu gösterir.

> [!IMPORTANT]
> İçin bir değer denetlemelisiniz **değerinden büyük veya eşit** belirli bir sürümü mevcut olup olmadığını algılamak çalışırken yayın anahtar değeri.

|Sürüm|Yayın DWORD değeri|
|-------------|--------------------------------|
|.NET framework Windows yüklenen 4.7.2 10 Nisan 2018 güncelleştir|461808|
|.NET framework Windows dışındaki tüm işletim sistemi sürümleri yüklü 4.7.2 10 Nisan 2018 güncelleştir|461814|
|.NET framework Windows 10 sonbaharda oluşturucuları Update'te yüklü 4.7.1|461308|
|.NET framework Windows 10 sonbaharda oluşturucuları güncelleştirme dışındaki tüm işletim sistemi sürümleri yüklü 4.7.1|461310|
|.NET framework Windows 10 oluşturucuları Update'te yüklü 4.7|460798|
|.NET framework Windows 10 oluşturucuları güncelleştirme dışındaki tüm işletim sistemi sürümleri yüklü 4.7|460805|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Windows 10 Anniversary Edition üzerinde yüklü|394802|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Windows 10 Anniversary Edition dışında tüm işletim sistemi sürümleri yüklü|394806|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Windows 10 Kasım Update'te yüklü|394254|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Windows 10 Kasım güncelleştirme dışındaki tüm işletim sistemi sürümleri yüklü|394271|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] Windows 10 yüklü|393295|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] Windows 10 dışında tüm işletim sistemi sürümleri yüklü|393297|
|.NET Framework 4.5.2|379893|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ile yüklenen [!INCLUDE[win81](../../../includes/win81-md.md)] veya Windows Server 2012 R2|378675|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] yüklü [!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7|378758|
|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|378389|

### <a name="detecting-the-language-packs"></a>Dil paketlerini algılama
 Belirli bir dil paketinin HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full denetleyerek yüklü olup olmadığını sınayabilirsiniz\\*LCID* klasör adında bir DWORD değeri içinkayıtdefterinde`Release`. ("NET Framework Kurulumu" bir nokta ile başlamıyor unutmayın.) *LCID* bir yerel ayar tanımlayıcısı; belirtir bkz [desteklenen diller](#supported-languages) bunların listesi için.

 Örneğin, algılamak için olup olmadığını tam Japonca dil paketi (LCID 1041 =) yüklü, kayıt defterindeki aşağıdaki değerler denetle:

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041
Name: Release
Type: DWORD
```

 .NET Framework 4.5 4.7.2 aracılığıyla'belirli bir sürümü için bir dil paketi son sürümü yüklü olup olmadığını belirlemek için önceki bölümde açıklanan sürüm anahtarı DWORD değerini değerini denetleyin [.NET algılama Framework](#detect_net).

<a name="chain_langpack"></a> 
### <a name="chaining-the-language-packs-to-your-app-setup"></a>Uygulama kurulumunuzu zincirleme dil paketleri
 .NET Framework belirli kültür için yerelleştirilen kaynaklar içeren paket yürütülebilir dosyaları tek başına dil kümesini sağlar. Dil paketlerini Microsoft Download Center'dan gelen kullanılabilir:

- [.NET framework 4.7.2 dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=863258)

- [.NET framework 4.7.1 dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=852090)

- [.NET framework 4.7 Dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=825306)

- [.NET framework 4.6.2 dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=780604)

- [.NET framework 4.6.1 dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=671747)

- [.NET framework 4.6 dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=528314)

- [.NET framework 4.5.2 dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=397701)

- [.NET framework 4.5.1 dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=322101)

- [.NET framework 4.5 dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Dil paketlerini bir uygulamayı çalıştırmak için gerekli olan .NET Framework bileşenlerini içermeyen; bir dil paketi yüklemeden önce web veya çevrimdışı yükleyici kullanarak .NET Framework yüklemeniz gerekir.

 İle başlayan [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], paket adı NDP'nin biçiminde <`version`>-KB <`number`>-x86-x64 - AllOS - <`culture`> .exe, burada `version` .NET Framework sürüm numarası `number` olan bir Microsoft Bilgi Bankası makalesi numarası ve `culture` belirten bir [ülke/bölge](#supported-languages). Bu paketleri birinin örneğidir `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Paket adları listelenir [yeniden dağıtılabilir paketleri](#redistributable-packages) bu makalenin önceki bölümünde.

 .NET Framework çevrimdışı Yükleyici ile bir dil paketi yüklemek için uygulamanızın Kurulum zincirine bağlı olmalıdır. Örneğin, dağıtmak için [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] çevrimdışı yükleyici Japonca dil paketi ile aşağıdaki komutu kullanın:

```
NDP451-KB2858728-x86-x64-AllOS-JPN.exe/q /norestart /ChainingPackage <ProductName>
```

 Web yükleyicisi kullanırsanız, dil paketlerini zincir gerekmez; Kurulum, kullanıcının MUI ayarını eşleşen dil paketi yükler. Farklı bir dilde yüklemek istiyorsanız, kullanabileceğiniz `/LCID` seçeneği bir dil paketi belirtin.

 Komut satırı seçeneklerinin tam bir listesi için bkz: [komut satırı seçenekleri](#command-line-options) bölümü.

### <a name="troubleshooting"></a>Sorun giderme

#### <a name="return-codes"></a>Dönüş kodları
 Aşağıdaki tabloda en yaygın dönüş kodları için .NET Framework yeniden dağıtılabilir yükleyici listeler. Dönüş kodları yükleyicinin tüm sürümleri için aynıdır. Ayrıntılı bilgi için bağlantılar için sonraki bölüme bakın.

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

- [Arka Plan Akıllı Aktarım Hizmeti (BITS) hata kodları](http://go.microsoft.com/fwlink/?LinkId=180946)

- [URL ad hata kodları](http://go.microsoft.com/fwlink/?LinkId=180947)

- [WinHttp hata kodları](http://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Diğer hata kodları
 Aşağıdaki içeriğe bakın:

- [Windows Installer hata kodları](http://go.microsoft.com/fwlink/?LinkId=180949)

- [Windows Update Aracısı sonuç kodları](http://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>.NET Framework kaldırma
 İle başlayarak [!INCLUDE[win8](../../../includes/win8-md.md)], kaldırabilmek için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya bir noktasının serbest kullanarak **Windows özelliklerini açma ve kapatma** Denetim Masası'nda. Windows'un eski sürümlerinde kaldırmanız [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya bir noktasının serbest kullanarak **Program Ekle veya Kaldır** Denetim Masası'nda.

> [!IMPORTANT]
> Windows 7 ve önceki işletim sistemlerinde, kaldırma için [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2 değil geri [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] dosyaları ve kaldırma [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] geri değil [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] dosyaları. Daha eski bir sürümüne geri dönmek istiyorsanız, bunu ve tüm güncelleştirmeleri yeniden yüklemeniz gerekir.

## <a name="appendix"></a>Ek

### <a name="command-line-options"></a>Komut satırı seçenekleri
 Zincir oluşturduğunuzda, dahil edebileceğiniz seçenekler aşağıdaki tabloda listelenmektedir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] uygulamanızın kurulumu için yeniden dağıtılabilir.

|Seçenek|Açıklama|
|------------|-----------------|
|**/ CEIPConsent**|Varsayılan davranışı geçersiz kılar ve gelecekteki dağıtımı deneyimlerini geliştirmek üzere Microsoft'a anonim geri bildirim gönderir. Bu seçenek, yalnızca onay için Kurulum programı istenirse, ve kullanıcı için Microsoft anonim görüş göndermeyi izin verirse kullanılabilir.|
|**/chainingpackage** `packageName`|Zincirleme yaptığını yürütülebilir dosyanın adını belirtir. Gelecekteki dağıtım geliştirmeye yardımcı olmak için anonim görüş karşılaştığında gibi bu bilgileri Microsoft'a gönderilmez.<br /><br /> Paket adı boşluk içeriyorsa, çift tırnak işaretleri sınırlayıcı olarak alın; Örneğin: **/chainingpackage "Bellek yayımlama"**. Zincirleme paketi örneği için bkz: [ilerleme durumu bilgileri alınırken bir yükleme paketi](http://go.microsoft.com/fwlink/?LinkId=181926) MSDN Kitaplığı'nda.|
|**/ LCID**  `LCID`<br /><br /> Burada `LCID` yerel ayar tanımlayıcısını belirtir (bkz [desteklenen diller](#supported-languages))|Belirtilen dil paketi yükler `LCID` Sessiz modu ayarlanmadığı sürece bu dilde gösterilmesini görüntülenen UI zorlar.<br /><br /> Web Yükleyicisi için bu seçeneği zinciri-Web dil paketi yükler. **Not:** yalnızca web Yükleyicisi ile bu seçeneği kullanın.|
|**/ log** `file`&#124; `folder`|Günlük dosyasının konumunu belirtir. İşlem için geçici bir klasör varsayılandır ve varsayılan dosya adı paketi dayanır. Dosya uzantısı .txt ise, bir metin günlüğü oluşturulur. Başka bir uzantı veya hiçbir uzantı belirtirseniz, bir HTML günlüğü oluşturulur.|
|**/msioptions**|.Msi ve .msp öğeleri için geçirilecek seçeneklerini belirtir; Örneğin: `/msioptions "PROPERTY1='Value'"`.|
|**/ norestart**|Kurulum programı otomatik olarak yeniden başlatılmasını engeller. Bu seçeneği kullanırsanız, dönüş kodu yakalamak ve yeniden işlemek zincirleme uygulama vardır (bkz [ilerleme durumu bilgileri alınırken bir yükleme paketi](http://go.microsoft.com/fwlink/?LinkId=179606) MSDN Kitaplığı'nda).|
|**/ Pasif**|Ayarlar Pasif modu. Yükleme devam ediyor, ancak herhangi bir komut istemlerini veya hata iletileri için kullanıcı görüntülemez belirtmek için ilerleme çubuğu görüntüler. Bu modda, bir Kurulum programı tarafından zincirleme olduğunda zincirleme paket işlemelidir [dönüş kodları](#return-codes).|
|**/pipe**|İlerleme durumunu almak zincirleme bir paket için bir iletişim kanalı oluşturur.|
|**/ promptrestart**|Kurulum programı bir yeniden başlatma gerektiriyorsa yalnızca Pasif modu, kullanıcıya sorar. Bu seçenek, bir yeniden başlatma gerekirse kullanıcı etkileşimi gerektirir.|
|**/q**|Sessiz modu ayarlar.|
|**Repair**|Onar işlevi tetikler.|
|**/serialdownload**|Yalnızca paket yüklendikten sonra gerçekleşecek şekilde yükleme zorlar.|
|**/showfinalerror**|Ayarlar Pasif modu. Yalnızca yükleme başarılı olmazsa hataları görüntüler. Yükleme başarılı olmazsa bu seçenek kullanıcı etkileşimi gerektirir.|
|**/showrmui**|Yalnızca kullanılan **/pasif** seçeneği. Çalışmakta olan .NET Framework uygulamaları kapatmak için kullanıcıların ister bir ileti kutusu görüntüler. Bu ileti kutusu pasif ve pasif olmayan modda aynı şekilde davranır.|
|**/uninstall**|.NET Framework yeniden dağıtılabilir kaldırır.|

### <a name="supported-languages"></a>Desteklenen diller
Aşağıdaki tabloda kullanılabilir .NET Framework dil paketlerini listeler [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve kendi noktası serbest bırakır.

|LCID|Dil – Ülke/bölge|Kültür|
|----------|--------------------------------|-------------|
|1025|Arapça - Suudi Arabistan|ar|
|1028|Geleneksel Çince –|zh-Hant|
|1029|Çekçe|cs|
|1030|Danca|da|
|1031|Almanca – Almanya|de|
|1032|Yunanca|el|
|1035|Fince|Fi|
|1036|Fransızca – Fransa|FR|
|1037|İbranice|Müşterinizle|
|1038|Macarca|hu|
|1040|İtalyanca-İtalya|Bunu|
|1041|Japonca|ja|
|1042|Kore Dili|Ko|
|1043|Felemenkçe-Hollanda|nl|
|1044|Norveççe (Bokmål)|Yok|
|1045|Lehçe|PL|
|1046|Portekizce-Brezilya|pt-BR|
|1049|Rusça|RU|
|1053|İsveç dili|sv|
|1055|Türkçe|tr|
|2052|Basitleştirilmiş Çince –|zh-atanır|
|2070|Portekizce-Portekiz|pt-PT|
|3082|İspanyolca - İspanya (Modern sıralama)|ES|

## <a name="see-also"></a>Ayrıca bkz.
 [Yöneticiler için Dağıtım Kılavuzu](../../../docs/framework/deployment/guide-for-administrators.md)  
 [Sistem Gereksinimleri](../../../docs/framework/get-started/system-requirements.md)  
 [Geliştiriciler için .NET Framework'ü yükleme](../../../docs/framework/install/guide-for-developers.md)  
 [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
 [.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma](../../../docs/framework/deployment/reducing-system-restarts.md)  
 [Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
