---
title: Geliştiriciler için .NET framework Dağıtım Kılavuzu
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4deea506a616a3578261cb85f4d4dd1369f5718e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61873931"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Geliştiriciler için .NET framework Dağıtım Kılavuzu
Bu konu için .NET Framework 4.5 .NET Framework'ün herhangi bir sürümünü yüklemek için isteyen geliştiriciler için bilgi sağlamaktadır [!INCLUDE[net_current](../../../includes/net-current-version.md)] uygulamalarıyla birlikte.

İndirme bağlantıları için konudaki [yeniden dağıtılabilir paketleri](#redistributable-packages). Yeniden dağıtılabilir paketleri ve dil paketlerini bu Microsoft Download Center sayfalarından yükleyebilirsiniz:

- Tüm işletim sistemleri için .NET framework 4.8 ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=2085155) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/?linkid=2088631))

- Tüm işletim sistemleri için .NET framework 4.7.2 ([web yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=863262) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=863265))

- Tüm işletim sistemleri için .NET framework 4.7.1 ([web yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=852095) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=852107))

- Tüm işletim sistemleri için .NET framework 4.7 ([web yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=825299) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=825303))

- Tüm işletim sistemleri için .NET framework 4.6.2 ([web yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=780597) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=780601))

- Tüm işletim sistemleri için .NET framework 4.6.1 ([web yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=671729) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=671744))

- Tüm işletim sistemleri için .NET framework 4.6 ([web yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=528222) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=528232))

- Tüm işletim sistemleri için .NET framework 4.5.2 ([web yükleyicisi](https://go.microsoft.com/fwlink/p/?LinkId=397703) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=397706))

- Tüm işletim sistemleri için .NET framework 4.5.1 ([web yükleyicisi](https://go.microsoft.com/fwlink/p/?LinkId=310158) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=310159))

- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)

 Önemli Notlar:

> [!NOTE]
> .NET Framework 4.5 ve sonraki tüm sürümler için ".NET Framework 4.5 ve nokta sürümleri" ifadesini gösterir.

- Sürümleri .NET Framework 4.5.1 .NET Framework'ten [!INCLUDE[net_current](../../../includes/net-current-version.md)] aynı çalışma zamanı sürümü kullandıkları anlamına gelir, .NET Framework 4.5 için yerinde güncelleştirmelerinin ancak derleme sürümlerini güncelleştirilir ve yeni türleri ve üyeleri içerir.

- .NET framework 4.5 ve nokta sürümleri, .NET Framework 4'te artımlı olarak oluşturulur. .NET Framework 4.5 yüklemek ya da .NET Framework 4'ün yüklü olduğu bir sistemde nokta sürümlerini sürüm 4 derlemeleri yeni sürümleriyle değiştirilir.

- Bir Microsoft başvurduğunuz, [bant dışı paket](../get-started/the-net-framework-and-out-of-band-releases.md) uygulamanızda derleme uygulama paketinde dahil edilir.

- .NET Framework 4.5 yüklemek için yönetici ayrıcalıklarına sahip olmalıdır ve nokta sürümlerini.

- .NET framework 4.5 dahil [!INCLUDE[win8](../../../includes/win8-md.md)] ve [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], bu işletim sistemlerinde uygulama ile dağıtmak gerekmez. Benzer şekilde, .NET Framework 4.5.1 dahil [!INCLUDE[win81](../../../includes/win81-md.md)] ve Windows Server 2012 R2. .NET framework 4.5.2 tüm işletim sistemlerinde yer almıyor. Windows 10'a dahil .NET framework 4.6, .NET Framework 4.6.1, Windows 10 Kasım güncelleştirmesi eklenmiştir ve .NET Framework 4.6.2, Windows 10 Yıldönümü Güncelleştirmesi'nde bulunur.  .NET framework 4.7 Windows 10 Creators Update içinde bulunan, .NET Framework 4.7.1 dahil Windows 10 Fall Creators Update ve .NET Framework 4.7.2 dahil Windows 10 Ekim 2018 güncelleştirmesi ve Windows 10 Nisan 2018 güncelleştirmesi. .NET framework 4.8 dahil Windows 10 Mayıs 2019 güncelleştirin. Donanım ve yazılım gereksinimlerinin tam listesi için bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).

- .NET Framework 4.5 ile başlayarak, kullanıcılarınızın Kurulum sırasında çalışan .NET Framework uygulamalar listesini görüntüleyebilir ve kolayca kapatabilir. Bu, .NET Framework kurulumlarının neden olduğu sistem yeniden başlatmalarını önlemenize yardımcı olabilir. Bkz: [sistem yeniden başlatmalarını azaltma](../../../docs/framework/deployment/reducing-system-restarts.md).

- .NET Framework 4.5 veya onun nokta sürümleri birini kaldırmayı, önceden mevcut olan .NET Framework 4 dosyaları kaldırır. .NET Framework 4'e geri dönmek istiyorsanız, bunu ve tüm güncellemelerini yeniden yüklemeniz gerekir. (Bkz [.NET Framework 4'ü yükleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).)

- .NET Framework 4.5 yeniden dağıtılabilir 2012'de 9 Ekim, dijital imzanın süresinin zamanından önce dolmasına Microsoft tarafından imzalanmış ve üretilen dosyaları neden bir dijital sertifika üzerinde hatalı zaman damgasıyla ilgili sorunu gidermek için güncelleştirildi. Daha önce yeniden dağıtılabilir paket 16 Ağustos 2012 tarihli .NET Framework 4.5 yüklü değilse kopyanızı ile en son yeniden dağıtılabilir Paketle güncelleştirmenizi öneririz [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=245484). Bu sorun hakkında daha fazla bilgi için bkz. [Microsoft Security Advisory 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

Nasıl bir Sistem Yöneticisi .NET Framework ve sistem bağımlılıklarını bir ağ üzerinden dağıtabilirsiniz hakkında daha fazla bilgi için bkz: [Yöneticiler için Dağıtım Kılavuzu](../../../docs/framework/deployment/guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Uygulamanız için dağıtım seçenekleri

Böylece kullanıcılar yükleyebilir, uygulamanızı bir web sunucusu veya başka bir merkezi konumda yayımlamaya hazır olduğunuzda birçok dağıtım yöntemini seçebilirsiniz. Bunlardan bazıları Visual Studio ile sağlanır. Aşağıdaki tabloda, uygulamanız için dağıtım seçeneklerini listeler ve her seçeneği destekleyen .NET Framework dağıtılabilir paketini belirtir. Bunlara ek olarak, uygulamanız için özel kurulum programı yazabilirsiniz; Daha fazla bilgi için konudaki [.NET Framework yüklemesinin uygulamanızın kurulumuna zincirleme](#chaining).

|Uygulamanız için Dağıtım stratejisi|Kullanılabilir dağıtım yöntemleri|Kullanılacak .NET framework yeniden dağıtılabilir|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Web'den yükleme|- [Installaware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [WiX araç takımı](#wix)<br />- [El ile yükleme](#installing_manually)|[Web yükleyicisi](#redistributable-packages)|
|Diskten yükleme|- [Installaware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [WiX araç takımı](#wix)<br />- [El ile yükleme](#installing_manually)|[Çevrimdışı yükleyici](#redistributable-packages)|
|Yerel alan ağı (Kurumsal uygulamaları için) yükleyin|- [ClickOnce](#clickonce-deployment)|Her iki [web yükleyicisi](#redistributable-packages) (bkz [ClickOnce](#clickonce-deployment) kısıtlamaları için) veya [çevrimdışı yükleyici](#redistributable-packages)|

## <a name="redistributable-packages"></a>Yeniden dağıtılabilir paketleri

.NET Framework iki yeniden dağıtılabilir pakette kullanılabilir: web yükleyicisini (Önyükleyici) ve çevrimdışı Yükleyici (tek başına yeniden dağıtılabilir). Aşağıdaki tablo iki paketi karşılaştırır.

||Web yükleyicisi|Çevrimdışı yükleyici|
|-|-------------------|-----------------------|
|Dosya yükleme|.NET framework 4.8: <br/>[ndp48-web.exe](https://go.microsoft.com/fwlink/?LinkId=2085155)<br/><br/>.NET framework 4.7.2: <br/>[NDP472-KB4054531-Web.exe](https://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>.NET framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](https://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>.NET framework 4.7: <br />[NDP47-KB3186500-Web.exe](https://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />.NET framework 4.6.2: <br />[NDP462-KB3151802-Web.exe](https://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> .NET framework 4.6.1:<br />[NDP461-KB3102438-Web.exe](https://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> .NET framework 4.6:<br />[NDP46-KB3045560-Web.exe](https://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](https://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> .NET framework 4.5.1: <br />[NDP451-KB2859818-Web.exe](https://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> .NET framework 4.5: <br />[dotNetFx45_Full_setup.exe](https://go.microsoft.com/fwlink/?LinkId=225704)|.NET framework 4.8: <br/>[NDP48-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?linkid=2088631)<br/><br/>.NET framework 4.7.2: <br/>[NDP472-KB4054530-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>.NET framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET framework 4.7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />.NET framework 4.6.2: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> .NET framework 4.6.1: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> .NET framework 4.6: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> .NET framework 4.5.1: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> .NET framework 4.5: <br />[dotNetFx45_Full_x86_x64.exe](https://go.microsoft.com/fwlink/?LinkId=225702)|
|Internet bağlantısı gerekiyor?|Evet|Hayır|
|İndirme boyutu|Küçük (yalnızca hedef Platform içerir) *|Daha büyük *|
|Dil paketleri|Dahil edilen **|Olmalıdır [ayrı olarak yüklenmiş](#chain_langpack), tüm işletim sistemlerini hedef alan paketi kullanmıyorsanız|
|Dağıtım yöntemi|Tüm yöntemleri destekler:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [Installaware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [El ile yükleme](#installing_manually)<br />- [Özel Kurulum (bağlama)](#chaining)|Tüm yöntemleri destekler:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [Installaware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [El ile yükleme](#installing_manually)<br />- [Özel Kurulum (bağlama)](#chaining)|
|ClickOnce dağıtımı için indirme konumu|Microsoft İndirme Merkezi:<br /><br /> - [.NET framework 4.8](https://go.microsoft.com/fwlink/?LinkId=2085155) <br/> - [.NET framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863262) <br/> - [.NET framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET framework 4.7](https://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET framework 4.6](https://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET framework 4.5.2](https://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [.NET framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|Kendi sunucunuz veya Microsoft Download Center:<br /><br /> - [.NET framework 4.8](https://go.microsoft.com/fwlink/?linkid=2088631)<br /> - [.NET framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863265)<br /> - [.NET framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET framework 4.7](https://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET framework 4.6](https://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [.NET framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|

\* Çevrimdışı yükleyici, tüm hedef platformlar için bileşenleri içerdiğinden daha büyük. Kurulumun çalışması tamamlandığında Windows işletim sistemi yalnızca kullanılan yükleyici önbelleğe alır. Çevrimdışı Yükleyici yükleme işleminden sonra silinirse, kullanılan disk alanı web yükleyicisi tarafından kullanılan aynıdır. Aracı'nı kullanıyorsanız (örneğin, [Installaware](#installaware-deployment) veya [InstallShield](#installshield-deployment)) kurulumundan sonra silinen bir kurulum dosyası klasörü sağlar, uygulamanızın Kurulum programı oluşturun, çevrimdışı yükleyiciyi olabilir Kurulum klasörüne koyarak otomatik olarak silinir.

\*\* Web yükleyicisini özel kurulum ile kullanıyorsanız, kullanıcının çok dilli kullanıcı arabirimi (MUI) ayarları esas alarak varsayılan dil ayarlarını kullanabilirsiniz, veya başka bir dil paketi kullanarak belirtin `/LCID` komut satırı seçeneği. Bölümüne bakın [.NET Framework varsayılan UI kullanarak zincirleme](#chaining_default) örnekler.

## <a name="deployment-methods"></a>Dağıtım yöntemleri

 Dört dağıtım yöntemleri kullanılabilir:

- .NET Framework üzerinde bağımlılık ayarlayabilirsiniz. .NET Framework, aşağıdaki yöntemlerden birini kullanarak uygulamalarınızın yüklemesinde bir önkoşul olarak belirtebilirsiniz:

  - Kullanım [ClickOnce dağıtımı](#clickonce-deployment) (Visual Studio ile kullanılabilir)

  - Oluşturma bir [Installaware proje](#installaware-deployment) (ücretsiz sürüm kullanıcıları için Visual Studio)

  - Oluşturma bir [InstallShield projesi](#installshield-deployment) (Visual Studio ile kullanılabilir)

  - Kullanım [Windows Installer XML (WiX) araç takımı](#wix)

- Kullanıcılarınıza sorabilir [.NET Framework el ile yükleme](#installing_manually).

- Kurulumuna bağlayabilirsiniz (dahil) .NET Framework Kurulum sürecini uygulamanızın kurulumuna ve nasıl .NET Framework Kurulum deneyiminin işlemek istediğinize karar verin:

  - [Varsayılan kullanıcı arabirimini kullanın](#chaining_default). .NET Framework yükleyicisi yükleme deneyimi sağlamasına olanak tanır.

  - [Kullanıcı arabirimini özelleştirme](#chaining_custom) birleştirilmiş yükleme deneyimi sunmak ve .NET Framework Kurulum sürecini izlemek için.

Bu dağıtım yöntemleri aşağıdaki bölümlerde ayrıntılı olarak ele alınmıştır.

## <a name="setting-a-dependency-on-the-net-framework"></a>.NET Framework üzerinde bağımlılık ayarlama

Uygulamanızı dağıtmak için ClickOnce, Installaware, InstallShield veya WiX kullanırsanız, uygulamanızın bir parçası olarak yüklenebilmesi için .NET Framework üzerinde bağımlılık ekleyebilirsiniz.

### <a name="clickonce-deployment"></a>ClickOnce dağıtımı

ClickOnce dağıtımı, Visual Basic ve Visual C# ile oluşturulan projeleri için kullanılabilir ancak Visual C++ için kullanılamaz.

Görsel ClickOnce dağıtımını seçmek ve .NET Framework üzerine bağımlılık eklemek için Studio'yu içinde:

1. Yayımlamak istediğiniz uygulama projesini açın.

2. Çözüm Gezgini'nde projenizin kısayol menüsünü açın ve ardından **özellikleri**.

3. Seçin **Yayımla** bölmesi.

4. Seçin **önkoşulları** düğmesi.

5. İçinde **önkoşulları** iletişim kutusunda, emin olun **Önkoşul bileşenlerini yüklemek için Kurulum programını Oluştur** onay kutusu seçilidir.

6. Önkoşullar listesinde bulun ve projenizi yapılandırmak için kullandığınız .NET Framework sürümünü seçin.

7. Önkoşullar için kaynak konumunu belirtin ve ardından bir seçenek belirleyin **Tamam**.

     .NET Framework indirme konumu için bir URL sağlarsanız, Microsoft Download Center sitesi veya kendinize ait bir site belirtebilirsiniz. Kendi sunucunuza yeniden dağıtılabilir paketi yerleştiriyorsanız, çevrimdışı yükleyici olmalı ve web yükleyicisi olmalıdır. Yalnızca Microsoft Download Center web yükleyicisini bağlayabilirsiniz. URL, kendi uygulamanızı dağıtılmakta bir disk olarak da belirtebilirsiniz.

8. İçinde **özellik sayfaları** iletişim kutusunda **Tamam**.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>Installaware dağıtım

Installaware Windows uygulaması (APPX), Windows Installer (MSI), yerel kod (EXE) ve tek bir kaynaktan App-V (Application Virtualization) paketleri oluşturur. Kolayca [dahil herhangi bir .NET Framework sürümünü](https://www.installaware.com/one-click-pre-requisite-installer.htm) , Kurulum, yükleme sırasında isteğe bağlı olarak özelleştirme [varsayılan komut dosyalarını düzenleme](https://www.installaware.com/msicode.htm). Örneğin, Windows 7, .NET Framework 4.7 kurulum başarısız olduğu sertifikaları Installaware önceden yükler. Installaware hakkında daha fazla bilgi için bkz. [Installaware için Windows Installer](https://www.installaware.com/) Web sitesi.

### <a name="installshield-deployment"></a>InstallShield dağıtımı

Görsel InstallShield dağıtımı seçmek ve .NET Framework üzerine bağımlılık eklemek için Studio'yu içinde:

1. Visual Studio menü çubuğunda **dosya**, **yeni**, **proje**.

2. Sol bölmesinde **yeni proje** iletişim kutusunda **diğer proje türleri**, **Kurulum ve dağıtım**, **InstallShield LE**.

3. İçinde **adı** kutusuna projeniz için bir ad yazın ve ardından **Tamam**.

4. İlk kez kurulum ve dağıtım proje oluşturuyorsanız, seçin **Installshield'e Git** veya **InstallShield Limited Edition'ı Etkinleştir** sürümünüz için InstallShield Limited Edition'ı indirmek için Microsoft Visual Studio. Visual Studio'yu yeniden başlatın.

5. Git **proje Yardımcısı** Sihirbazı'nı seçip **uygulama dosyaları** proje çıktısı eklemek için. Bu sihirbazı kullanarak diğer proje öznitelikleri yapılandırabilirsiniz.

6. Git **yükleme gereksinimlerini** ve işletim sistemleri ve yüklemek istediğiniz .NET Framework sürümünü seçin.

7. Kurulum projeniz için kısayol menüsünü açın ve seçin **yapı**.

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Windows Installer XML (WiX) dağıtımı

Windows Installer XML (WiX) araç takımı XML kaynak kodundan Windows yükleme paketleri oluşturur. WiX, MSI ve MSM kurulum paketleri oluşturmak için derleme sürecinize entegre bir komut satırı ortamını destekler. Wix'i kullanarak şunları yapabilirsiniz [bir önkoşul olarak .NET Framework belirtin](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html), veya [bir bağlayıcı oluşturmak](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) .NET Framework dağıtım deneyimini tam olarak denetlemek için. WiX hakkında daha fazla bilgi için bkz: [Windows Installer XML (WiX) araç takımı](http://wixtoolset.org/) Web sitesi.

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>.NET Framework'ü el ile yükleme

Bazı durumlarda, .NET Framework ile uygulamanızı otomatik olarak yüklemek pratik olmayabilir. Bu durumda, kullanıcılar kendi .NET Framework yüklemeleri olabilir. Yeniden dağıtılabilir paketi kullanılabilir [iki paket](#redistributable-packages). Kurulum sürecinizde kullanıcıların bulun ve bunları nasıl .NET Framework'ü yüklemek için yönergeler sağlar.

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>.NET Framework yüklemesinin uygulamanızın kurulumuna zincirleme

Uygulamanız için özel kurulum programı oluşturuyorsanız, kurulumuna bağlayabilirsiniz (dahil) .NET Framework Kurulum sürecini uygulamanızın Kurulum işlemi. Zincirleme .NET Framework yüklemesi için iki kullanıcı Arabirimi seçeneği sağlar:

- Varsayılan .NET Framework yükleyicisi tarafından sağlanan kullanıcı arabirimini kullanın.

- Uygulamanızın Kurulum programıyla birlikte .NET Framework yükleme tutarlılık için özel kullanıcı Arabirimi oluşturun.

Her iki yöntem de web yükleyicisini veya çevrimdışı yükleyiciyi kullanmanıza olanak sağlar. Her paketin kendine göre avantajları vardır:

- Web yükleyicisi kullanıyorsanız, .NET Framework Kurulum işlemi hangi yükleme paketinin gerekli olduğuna karar indirin ve Web'den o paketi yükleyin.

- Çevrimdışı yükleyiciyi kullanabilir, böylece kullanıcılarınız ek dosyaları Web'den Kurulum sırasında indirmeniz gerekmez .NET Framework yükleme paketler kümesinin tamamını yeniden dağıtımı medyanızı içerebilir.

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>Varsayılan .NET Framework UI kullanarak zincirleme

Sessizce .NET Framwork yükleme işlemini zincir ve .NET Framework kurucusunun kullanıcı arabirimini sağlaması için Kurulum programına aşağıdaki komutu ekleyin:

```
<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>
```

Örneğin, çalıştırılabilir program Contoso.exe ise ve .NET Framework 4.5 çevrimdışı yeniden dağıtılabilir paketini sessizce yüklemek istiyorsanız komutu kullanın:

```
dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso
```

Yüklemeyi özelleştirmek için ek komut satırı seçeneklerini kullanabilirsiniz. Örneğin:

- Sistem yeniden başlatmalarını azaltmak için çalışan .NET Framework uygulamaları kapatmak için kullanıcıları bir yol sağlamak için Pasif modu ayarlamak ve `/showrmui` seçeneğini etkinleştirmelidir:

    ```
    dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso
    ```

     Bu komut, yeniden başlatma Yöneticisi kullanıcılara .NET Framework'ü yüklemeden önce .NET Framework uygulamaları kapatmak için Fırsat veren ileti kutusunu göstermesini sağlar.

- Web yükleyicisi kullanıyorsanız, kullanabileceğiniz `/LCID` dil paketi belirtmek için seçeneği. Örneğin, Contoso Kurulum programınıza için .NET Framework 4.5 web yükleyicisi zincir ve Japonca dil paketini yüklemek için aşağıdaki komutu uygulamanızın Kurulum işlemine ekleyin:

    ```
    dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041
    ```

     Atlarsanız `/LCID` seçeneği, Kurulum kullanıcının MUI ayarlarıyla eşleşen dil paketini yükler.

    > [!NOTE]
    > Farklı dil paketlerinin farklı yayın tarihleri olabilir. Belirttiğiniz dil paketi indirme merkezinde kullanılabilir durumda değilse, Kur, .NET Framework dil paketi olmadan yükleyecektir. .NET Framework kullanıcının bilgisayarında önceden yüklüyse Kurulum sadece dil paketini yükler.

Seçeneklerinin tam listesi için bkz: [komut satırı seçenekleri](#command-line-options) bölümü.

Ortak dönüş kodları için bkz. [dönüş kodları](#return-codes) bölümü.

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Özel bir kullanıcı Arabirimi kullanılarak zincirleme

Özel Kurulum paketiniz varsa, sessizce başlatmak ve kendi görünüm Kurulum sürecinizin gösterirken .NET Framework kurulumunu izlemek isteyebilirsiniz. Bu durumda, kodunuzun aşağıdakini kapsadığından emin olun:

- Denetle [.NET Framework donanım ve yazılım gereksinimleri](../../../docs/framework/get-started/system-requirements.md).

- [Algılama](#detect_net) olup kullanıcının bilgisayarında yüklü .NET Framework'ün doğru sürümü.

    > [!IMPORTANT]
    > .NET Framework'ün doğru sürümü zaten yüklü olup olmadığını belirlerken, denetlemeniz gereken olup olmadığını hedef sürümünüz *veya* değil, hedef sürümü yüklü olup olmadığını sonraki bir sürümü yüklü. Büyüktür veya eşittir, hedef sürümü, sürüm anahtarı kayıt defterinden almak yayın anahtar olup olmadığını başka bir deyişle, değerlendirmelidir *değil* hedef sürümünüz sürüm anahtarı eşit olup olmadığı.

- [Algılama](#detecting-the-language-packs) olup dil paketlerinin kullanıcının bilgisayarında zaten yüklenir.

- Dağıtımı denetlemek istiyorsanız, sessizce başlatmak ve .NET Framework Kurulum sürecini izleyin (bkz [nasıl yapılır: .NET Framework 4.5 yükleyicisinden ilerleme durumunu elde](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)).

- Çevrimdışı yükleyici dağıtıyorsanız [dil paketlerini ayrı olarak zincir](#chain_langpack).

- Kullanarak dağıtımı özelleştirin [komut satırı seçenekleri](#command-line-options). Örneğin, .NET Framework web yükleyicisini bağlıyorsanız, ancak varsayılan dil paketini geçersiz kılmak için kullanmak istediğiniz `/LCID` seçeneği, önceki bölümde açıklandığı gibi.

- [Sorun giderme](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>.NET Framework'ü algılama

.NET Framework yükleyicisi, başarılı olduğunda kurucusu Kayıt anahtarlarını yazar. Denetleyerek .NET Framework 4.5 veya üzeri yüklü olup olmadığını test edebilirsiniz `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klasörü için kayıt defterinde bir `DWORD` değeri `Release`. ("NET Framework Kurulum" nokta ile başlamayacağına dikkat edin.) Bu anahtarın varlığı, .NET Framework 4.5 veya sonraki bir sürümünü bu bilgisayara yüklendiğini belirtir. Değerini `Release` .NET Framework'ün hangi sürümünün yüklü olduğunu gösterir.

> [!IMPORTANT]
> İçin bir değer denetlemelisiniz **büyüktür veya eşittir** belirli bir sürümü mevcut olup olmadığını algılamak çalışırken sürüm anahtar değeri.

|Sürüm|Yayın DWORD değeri|
|-------------|--------------------------------|
|Windows 10'da yüklü .NET framework 4.8 2019 güncelleştirebilir.|528040|
|Windows 10 dışında tüm işletim sistemi sürümleri yüklü .NET framework 4.8 2019 güncelleştirebilir.|528049|
|.NET framework Windows yüklü 4.7.2 10 Nisan 2018 güncelleştirmesi ve Windows Server'da 1803 sürümü|461808|
|.NET framework 4.7.2 Windows dışındaki tüm işletim sistemi sürümleri yüklü 10 Nisan 2018 güncelleştirmesi ve Windows Server sürümü 1803. Bu içeren Windows 10 Ekim 2018 güncelleştirmesi. |461814|
|.NET framework 4.7.1 Windows 10 Fall Creators Update ve Windows Server 1709 sürümü yüklü|461308|
|.NET framework 4.7.1 Windows 10 Fall Creators Update ve Windows Server 1709 sürümü dışındaki tüm işletim sistemi sürümleri yüklü|461310|
|Windows 10 Creators Update üzerinde yüklü olan .NET framework 4.7|460798|
|Windows 10 Creators Update dışındaki tüm işletim sistemi sürümleri yüklü .NET framework 4.7|460805|
|.NET framework 4.6.2, Windows 10 Anniversary Edition ve Windows Server 2016 yüklü|394802|
|.NET framework 4.6.2, Windows 10 Anniversary Edition ve Windows Server 2016 dışındaki tüm işletim sistemi sürümleri yüklü|394806|
|.NET framework 4.6.1 yüklü üzerinde Windows 10 Kasım güncelleştirmesi|394254|
|.NET framework 4.6.1 yüklü Windows 10 Kasım güncelleştirmesi dışındaki tüm işletim sistemi sürümleri|394271|
|Windows 10'da yüklü .NET framework 4.6|393295|
|Windows 10 dışında tüm işletim sistemi sürümleri yüklü .NET framework 4.6|393297|
|.NET Framework 4.5.2|379893|
|.NET framework 4.5.1 ile yüklü [!INCLUDE[win81](../../../includes/win81-md.md)] veya Windows Server 2012 R2|378675|
|.NET framework 4.5.1 yüklü [!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>Dil paketlerini algılama

Hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full kontrol ederek belirli bir dil paketinin yüklü olup olmadığını test edebilirsiniz\\*LCID* klasör adında bir DWORD değeri içinkayıtdefterinde`Release`. ("NET Framework Kurulum" nokta ile başlamayacağına dikkat edin.) *LCID* bir yerel tanıtıcı belirtir; bkz [desteklenen diller](#supported-languages) bunların bir listesi için.

Örneğin, algılamak için mi tam dil paketinin (LCID = 1041) yüklü, aşağıdaki kayıt defteri değerlerini denetle:

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041
Name: Release
Type: DWORD
```

.NET Framework 4.5 4.7.2 üzerinden gelen belirli bir sürümü için bir dil paketinin son sürümü yüklü olup olmadığını belirlemek için önceki bölümde anlatılan RELEASE anahtarı DWORD değerini değerini kontrol edin [.NET algılama Framework](#detect_net).

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Uygulama kurulumunuzu zincirleme dil paketleri

.NET Framework özel kültürler için yerelleştirilmiş kaynakları içeren bir paketi yürütülebilir dosyalar tek başına dil kümesini sağlar. Dil paketlerini Microsoft Download Center'dan gelen mevcuttur:

- [.NET framework 4.8 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=2086170)

- [.NET framework 4.7.2 dil paketleri](https://go.microsoft.com/fwlink/?LinkId=863275)

- [.NET framework 4.7.1 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=852090)

- [.NET framework 4.7 Dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=825306)

- [.NET framework 4.6.2 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=780604)

- [.NET framework 4.6.1 dil paketi](https://go.microsoft.com/fwlink/p/?LinkId=671747)

- [.NET framework 4.6 dil paketi](https://go.microsoft.com/fwlink/p/?LinkId=528314)

- [.NET framework 4.5.2 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=397701)

- [.NET framework 4.5.1 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=322101)

- [.NET framework 4.5 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Dil paketleri, bir uygulamayı çalıştırmak için gereken .NET Framework bileşenlerini içermezler; dil paketini yüklemeden önce web veya çevrimdışı yükleyiciyi kullanarak .NET Framework'ü yüklemeniz gerekir.

.NET Framework 4.5.1 ile başlayarak, paket adları NDP biçiminde <`version`>-KB <`number`>-x86-x64 - AllOS - <`culture`> .exe, burada `version` .NET Framework'ün sürüm numarasıdır `number` olduğu bir Microsoft Bilgi Bankası makale numarası ve `culture` belirtir bir [ülke/bölge](#supported-languages). Bu paketlerin bir örneğini `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Paket adları listelenir [yeniden dağıtılabilir paketleri](#redistributable-packages) bu makalenin önceki kısımlarında bölümü.

Dil paketini .NET Framework çevrimdışı Yükleyici ile yüklemek için uygulamanızın kurulumuna zincirine bağlı olmalıdır. Örneğin, .NET Framework 4.5.1 çevrimdışı yükleyiciyi Japonca dil paketiyle dağıtmak için aşağıdaki komutu kullanın:

```
NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>
```

Web yükleyicisini kullanmak istiyorsanız dil paketlerini bağlamanıza gerek yoktur; Kurulum kullanıcının MUI ayarlarıyla eşleşen dil paketini yükleyecektir. Farklı bir dil yüklemek isterseniz, kullanabileceğiniz `/LCID` dil paketi belirtmek için seçeneği.

Komut satırı seçeneklerinin tam listesi için bkz. [komut satırı seçenekleri](#command-line-options) bölümü.

### <a name="troubleshooting"></a>Sorun giderme

#### <a name="return-codes"></a>Dönüş kodları

Aşağıdaki tablo, .NET Framework yeniden dağıtılabilir yükleyici için en sık karşılaşılan döndürülen kodları listeler. Dönüş kodları yükleyicinin tüm sürümleri için aynıdır. Ayrıntılı bilgi için bağlantılar için sonraki bölüme bakın.

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

- [URL adı hata kodları](https://go.microsoft.com/fwlink/?LinkId=180947)

- [WinHttp hata kodları](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Diğer hata kodları

Aşağıdaki içeriğe bakın:

- [Windows Installer hata kodları](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Windows Update Aracısı sonuç kodları](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>.NET Framework'ün kaldırılması

İle başlayarak [!INCLUDE[win8](../../../includes/win8-md.md)], .NET Framework 4.5 kaldırabilirsiniz veya kendi noktasını birini sürümleri kullanılarak **kapatma Windows özelliklerini açma ve kapatma** Denetim Masası'nda. Eski Windows sürümlerinde, .NET Framework 4.5 kaldırabilirsiniz veya kendi noktasını birini sürümleri kullanılarak **Program Ekle veya Kaldır** Denetim Masası'nda.

> [!IMPORTANT]
> Windows 7 ve önceki işletim sistemlerinde, .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8 kaldırma, .NET Framework 4.5 dosyaları geri yüklemiyor ve kaldırmadan .NET Framework 4.5, .NET Framework 4 dosyaları geri yüklemiyor. Eski sürüme dönmek istiyorsanız onu ve güncellemelerini yeniden yüklemeniz gerekir.

## <a name="appendix"></a>Ek

### <a name="command-line-options"></a>Komut satırı seçenekleri

Aşağıdaki tablo, .NET Framework 4.5 redistributable uygulamanızın kurulumuna bağladığınızda ekleyebileceğiniz seçenekleri listeler.

|Seçenek|Açıklama|
|------------|-----------------|
|**/ CEIPConsent**|Varsayılan davranışını tekrardan yazar ve gelecekteki dağıtım deneyimleri geliştirmek üzere Microsoft'a anonim geri bildirim gönderir. Bu seçenek, yalnızca Kurulum programın rıza istemesine sebep olursa ve kullanıcı anonim görüşlerinizi Microsoft'a göndermek için izin verirse kullanılabilir.|
|**/chainingpackage** `packageName`|Zincirlemeyi yapan yürütülebilir dosya adını belirtir. Gelecekteki dağıtım geliştirmeye yardımcı olmak için anonim görüş deneyimleri olarak bu bilgileri Microsoft'a gönderilmez.<br /><br /> Paket adı boşluk içeriyorsa, sınırlayıcı olarak çift tırnak işareti kullanın. Örneğin: **/chainingpackage "Lucerne Publishing"**. Zincirleme paketi örneği için bkz: [yükleme paketinden ilerleme bilgisi alma](https://go.microsoft.com/fwlink/?LinkId=181926) MSDN Kitaplığı'nda.|
|**/LCID**  `LCID`<br /><br /> Burada `LCID` bir yerel ayar tanımlayıcısını belirtir (bkz [desteklenen diller](#supported-languages))|Tarafından belirtilen dil paketini yükler `LCID` ve sessiz mod ayarlanmadığı sürece görüntülenen kullanıcı Arabirimi o dilde gösterilmesini zorlar.<br /><br /> Web Yükleyicisi için bu seçeneği zinciri-web dil paketini yükler. **Not:**  Bu seçeneği yalnızca web Yükleyicisi ile kullanın.|
|**/log** `file` &#124; `folder`|Günlük dosyasının konumunu belirtir. Varsayılan işlem için geçici bir klasördür ve varsayılan dosya adı pakete dayalıdır. Dosya uzantısı .txt ise, bir metin günlüğü oluşturulur. Başka bir uzantı belirtirseniz veya bir uzantı belirtirseniz, bir HTML günlüğü oluşturulur.|
|**/msioptions**|.Msi ve .msp öğeleri için geçirilecek seçeneklerini belirtir. Örneğin: `/msioptions "PROPERTY1='Value'"`.|
|**/ norestart**|Kurulum programının otomatik olarak yeniden başlatılmasını önler. Bu seçeneği kullanırsanız, zincirleme uygulama döndürülen kodu yakalamak ve yeniden başlatmayı işlemek vardır (bkz [yükleme paketinden ilerleme bilgisi alma](https://go.microsoft.com/fwlink/?LinkId=179606) MSDN Kitaplığı'nda).|
|**/ passive**|Pasif modu ayarlar. Yükleme devam ediyor, ancak hiçbir hızlı cevap yada hata iletilerini kullanıcıya göstermez belirtmek için ilerleme çubuğu görüntüler. Zincirleme paketi bu modda, Kurulum programı tarafından bağlanırsa işlemesi [dönüş kodları](#return-codes).|
|**/pipe**|İlerleme durumunu elde etmek zincirleme bir paket için bir iletişim kanalı oluşturur.|
|**promptrestart**|Sadece pasif modda, Kurulum programı bir yeniden başlatma gerekirse kullanıcıya sorar. Bir yeniden başlatma gerekirse bu seçenek kullanıcı etkileşimini gerektirir.|
|**/q**|Sessiz modu ayarlar.|
|**/ Repair**|Onarma işlevini tetikler.|
|**/serialdownload**|Yüklemeyi yalnızca paket İndirildikten sonra yapılmaya zorlar.|
|**/showfinalerror**|Pasif modu ayarlar. Yalnızca yükleme başarılı değilse hataları görüntüler. Yükleme başarılı değilse, bu seçenek kullanıcı etkileşimini gerektirir.|
|**/showrmui**|Yalnızca kullanılan **/passive** seçeneği. Çalışmakta olan .NET Framework uygulamaları kapatmak için kullanıcıları uyaran bir ileti kutusu görüntüler. Bu ileti kutusu pasif ve pasif olmayan modda aynı şekilde davranır.|
|**/uninstall**|.NET Framework yeniden dağıtılabilirini kaldırır.|

### <a name="supported-languages"></a>Desteklenen diller

Aşağıdaki tablo .NET Framework 4.5 için kullanılabilir olan .NET Framework dil paketlerini listeler ve nokta sürümlerini.

|LCID|Dil-Ülke/bölge|Kültür|
|----------|--------------------------------|-------------|
|1025|Arapça - Suudi Arabistan|ar|
|1028|Çince-Geleneksel|zh-Hant|
|1029|Çekçe|cs|
|1030|Danca|da|
|1031|Almanca – Almanya|de|
|1032|Yunanca|el|
|1035|Fince|Fi|
|1036|Fransızca – Fransa|FR|
|1037|İbranice|He|
|1038|Macarca|hu|
|1040|İtalyanca – İtalya|Bunu|
|1041|Japonca|ja|
|1042|Korece|Ko|
|1043|Felemenkçe – Hollanda|nl|
|1044|Norveççe (Bokmål)|Yok|
|1045|Lehçe|PL|
|1046|Portekizce – Brezilya|pt-BR|
|1049|Rusça|RU|
|1053|İsveççe|sv|
|1055|Türkçe|tr|
|2052|Çince-Basitleştirilmiş|zh-Hans|
|2070|Portekizce – Portekiz|pt-PT|
|3082|İspanyolca - İspanya (Modern sıralama)|ES|

## <a name="see-also"></a>Ayrıca bkz.

- [Yöneticiler için Dağıtım Kılavuzu](../../../docs/framework/deployment/guide-for-administrators.md)
- [Sistem Gereksinimleri](../../../docs/framework/get-started/system-requirements.md)
- [Geliştiriciler için .NET Framework'ü yükleme](../../../docs/framework/install/guide-for-developers.md)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
- [.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma](../../../docs/framework/deployment/reducing-system-restarts.md)
- [Nasıl yapılır: .NET Framework 4.5 yükleyicisinden ilerleme durumunu Al](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
