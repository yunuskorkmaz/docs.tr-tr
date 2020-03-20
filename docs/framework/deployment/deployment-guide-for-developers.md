---
title: .NET Framework dağıtım kılavuzu geliştiriciler için
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
ms.openlocfilehash: 26c168040b0fa5e975e64a7518b0d0bf250c4711
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628130"
---
# <a name="net-framework-deployment-guide-for-developers"></a>.NET Framework dağıtım kılavuzu geliştiriciler için
Bu konu, .NET Framework 4.5'ten .NET Framework 4.5'e .NET Framework 4.5'in herhangi bir sürümünü kendi uygulamalarına yüklemek isteyen geliştiriciler için [!INCLUDE[net_current](../../../includes/net-current-version.md)] bilgi sağlar.

.NET Framework için yeniden dağıtılabilir paketleri ve dil paketlerini indirme sayfalarından indirebilirsiniz:

- [.NET Çerçeve 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Çerçeve 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Çerçeve 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Çerçeve 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

 Önemli notlar:

- .NET Framework 4.5.1'den .NET [!INCLUDE[net_current](../../../includes/net-current-version.md)] Framework 4.5'e kadar olan .NET Framework'ün sürümleri ,.NET Framework 4.5'in yerinde güncelleştirmeleridir, bu da aynı çalışma zamanı sürümünü kullandıkları anlamına gelir, ancak derleme sürümleri güncelleştirilir ve yeni türler ve üyeler içerir.

- .NET Framework 4.5 ve sonraki sürümler .NET Framework 4 üzerine aşamalı olarak oluşturulur. .NET Framework 4 yüklü bir sisteme .NET Framework 4 veya daha sonraki sürümleri yüklediğinizde, sürüm 4 derlemeleri yeni sürümlerle değiştirilir.

- Uygulamanızda bir Microsoft [bant dışı paketine](../get-started/the-net-framework-and-out-of-band-releases.md) başvuruyorsanız, derleme uygulama paketine dahil edilir.

- .NET Framework 4.5 veya sonraki sürümlerini yüklemek için yönetici ayrıcalıklarına sahip olmalısınız.

- .NET Framework 4.5, Windows 8 ve Windows Server 2012'ye dahildir, bu nedenle uygulamayınızla bu işletim sistemlerinde dağıtmanız gerekmemektedir. Benzer şekilde, .NET Framework 4.5.1 de Windows 8.1 ve Windows Server 2012 R2'ye dahildir. .NET Framework 4.5.2 herhangi bir işletim sistemine dahil değildir. .NET Framework 4.6 Windows 10'a, .NET Framework 4.6.1 Windows 10 Kasım Güncelleştirmesi'ne ve .NET Framework 4.6.2 Windows 10 Anniversary Update'e dahildir.  .NET Framework 4.7, Windows 10 Creators Update'e, .NET Framework 4.7.1 Windows 10 Fall Creators Update'e ve .NET Framework 4.7.2 Windows 10 Ekim 2018 Güncellemesi ve Windows 10 Nisan 2018 Güncellemesi'ne dahildir. .NET Framework 4.8, Windows 10 Mayıs 2019 Güncelleştirmesi'ne dahildir. Donanım ve yazılım gereksinimlerinin tam listesi için [Sistem Gereksinimleri'ne](../get-started/system-requirements.md)bakın.

- .NET Framework 4.5'ten başlayarak, kullanıcılarınız kurulum sırasında çalışan .NET Framework uygulamalarının listesini görüntüleyebilir ve kolayca kapatabilir. Bu, .NET Framework yüklemelerinin neden olduğu sistemin yeniden başlatılmasını önlemeye yardımcı olabilir. Bkz. [Azaltma Sistemi Yeniden Başlatılır.](reducing-system-restarts.md)

- .NET Framework 4.5 veya sonraki sürümlerini kaldırmak da önceden varolan .NET Framework 4 dosyalarını kaldırır. .NET Framework 4'e geri dönmek istiyorsanız, yeniden yüklemeniz ve güncellemeler yapmak gerekir. Bkz. [.NET Framework 4'ün yüklenmesi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).

- .NET Framework 4.5 yeniden dağıtılabilir 9 Ekim 2012 tarihinde dijital bir sertifikaüzerinde yanlış bir zaman damgası ile ilgili bir sorunu düzeltmek için güncellendi, hangi üretilen ve Microsoft tarafından imzalanan dosyalarda dijital imza erken süresi dolmasına neden oldu. 16 Ağustos 2012 tarihli .NET Framework 4.5 yeniden dağıtılabilir paketini daha önce yüklediyseniz, kopyanızı [.NET Framework indirme sayfasından](https://dotnet.microsoft.com/download/dotnet-framework/net45)en son dağıtılabilir paketle güncellemenizi öneririz. Bu sorun hakkında daha fazla bilgi için [Microsoft Güvenlik Danışma 2749655'e](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655)bakın.

Bir sistem yöneticisinin .NET Framework'u ve sistem bağımlılıklarını ağ üzerinden nasıl dağıtabileceği hakkında bilgi [için, Yöneticiler için Dağıtım Kılavuzu'na](guide-for-administrators.md)bakın.

## <a name="deployment-options-for-your-app"></a>Uygulamanız için dağıtım seçenekleri

Uygulamanızı kullanıcıların yükleyebilmeleri için bir web sunucusunda veya diğer merkezi konumda yayımlamaya hazır olduğunuzda, birkaç dağıtım yöntemi arasından seçim yapabilirsiniz. Bunlardan bazıları Visual Studio ile sağlanmaktadır. Aşağıdaki tabloda uygulamanızın dağıtım seçenekleri listeler ve her seçeneği destekleyen .NET Framework yeniden dağıtılabilir paketi belirtilir. Bunlara ek olarak, uygulamanız için özel bir kurulum programı yazabilirsiniz; daha fazla bilgi için [,.NET Framework Kurulumunu Uygulamanızın Kurulumuna Zincirleme bölümüne](#chaining)bakın.

|Uygulamanız için dağıtım stratejisi|Dağıtım yöntemleri kullanılabilir|.NET Framework yeniden kullanılabilir|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Web'den yükleme|- [ınstallaware](#installaware-deployment)<br />- [ınstallshield](#installshield-deployment)<br />- [WiX araç seti](#wix)<br />- [Manuel kurulum](#installing_manually)|[Web yükleyici](#redistributable-packages)|
|Diskten yükleme|- [ınstallaware](#installaware-deployment)<br />- [ınstallshield](#installshield-deployment)<br />- [WiX araç seti](#wix)<br />- [Manuel kurulum](#installing_manually)|[Çevrimdışı yükleyici](#redistributable-packages)|
|Yerel bir ağdan yükleme (kurumsal uygulamalar için)|- [Clickonce](#clickonce-deployment)|[Web yükleyicisi](#redistributable-packages) (kısıtlamalar için [ClickOnce'ye](#clickonce-deployment) bakın) veya [çevrimdışı yükleyici](#redistributable-packages)|

## <a name="redistributable-packages"></a>Yeniden dağıtılabilir paketler

.NET Framework iki yeniden dağıtılabilir paketmevcuttur: web yükleyici (bootstrapper) ve çevrimdışı yükleyici (tek başına yeniden dağıtılabilir). Tüm .NET Framework indirmeleri [İndir .NET Framework sayfasında](https://dotnet.microsoft.com/download/dotnet-framework/)barındırılır. Aşağıdaki tablo iki paketi karşılaştırır:

||Web yükleyici|Çevrimdışı yükleyici|
|-|-------------------|-----------------------|
|İnternet bağlantısı gerekli mi?|Evet|Hayır|
|İndirme boyutu|Daha küçük (yalnızca hedef platform için yükleyici içerir)*|Daha büyük*|
|Dil paketleri|Dahil**|Tüm işletim sistemlerini hedefleyen paketi kullanmadığınız [sürece, ayrı olarak yüklenmelidir](#chain_langpack)|
|Dağıtım yöntemi|Tüm yöntemleri destekler:<br /><br />- [Clickonce](#clickonce-deployment)<br />- [ınstallaware](#installaware-deployment)<br />- [ınstallshield](#installshield-deployment)<br />- [Windows Yükleyici XML (WiX)](#wix)<br />- [Manuel kurulum](#installing_manually)<br />- [Özel kurulum (zincirleme)](#chaining)|Tüm yöntemleri destekler:<br /><br /> - [Clickonce](#clickonce-deployment)<br />- [ınstallaware](#installaware-deployment)<br />- [ınstallshield](#installshield-deployment)<br />- [Windows Yükleyici XML (WiX)](#wix)<br />- [Manuel kurulum](#installing_manually)<br />- [Özel kurulum (zincirleme)](#chaining)|

\*Tüm hedef platformların bileşenlerini içerdiğinden çevrimdışı yükleyici daha büyüktür. Çalıştırmayı bitirdiğinizde, Windows işletim sistemi yalnızca kullanılan yükleyiciyi önbelleğe alar. Yüklemeden sonra çevrimdışı yükleyici silinirse, kullanılan disk alanı web yükleyicitarafından kullanılanla aynıdır. Uygulamanızın kurulum programını oluşturmak için kullandığınız araç (örneğin [InstallAware](#installaware-deployment) veya [InstallShield)](#installshield-deployment)kurulumdan sonra kaldırılan bir kurulum dosyası klasörü sağlıyorsa, çevrimdışı yükleyici kurulum klasörüne yerleştirilerek otomatik olarak silinebilir.

\*\*Web yükleyicisini özel kurulumla kullanıyorsanız, kullanıcının Çok Dilli Kullanıcı Arabirimi (MUI) ayarını temel alan varsayılan dil ayarlarını `/LCID` kullanabilir veya komut satırındaki seçeneği kullanarak başka bir dil paketi belirtebilirsiniz. Örnekler için [Varsayılan .NET Framework UI'yi kullanarak Zincirleme](#chaining_default) bölümüne bakın.

## <a name="deployment-methods"></a>Dağıtım yöntemleri

 Dört dağıtım yöntemi kullanılabilir:

- .NET Framework'e bağımlılık ayarlayabilirsiniz. .NET Framework'ü aşağıdaki yöntemlerden birini kullanarak uygulamanızın kurulumunda ön koşul olarak belirtebilirsiniz:

  - [ClickOnce dağıtımını](#clickonce-deployment) kullanın (Visual Studio ile kullanılabilir)

  - [InstallAware projesi](#installaware-deployment) oluşturun (Visual Studio kullanıcıları için ücretsiz sürüm)

  - [InstallShield projesi](#installshield-deployment) oluşturun (Visual Studio ile kullanılabilir)

  - Windows [Installer XML (WiX) araç setini](#wix) kullanma

- Kullanıcılarınızdan [.NET Framework'ü el ile yüklemelerini](#installing_manually)isteyebilirsiniz.

- Uygulamanızın kurulumunda .NET Framework kurulum işlemini zincirleyebilir (dahil edebilir) ve .NET Framework yükleme deneyimini nasıl işlemek istediğinize karar verebilirsiniz:

  - [Varsayılan UI'yi kullanın.](#chaining_default) .NET Framework yükleyicisinin yükleme deneyimini sağlamasına izin verin.

  - Birleşik bir yükleme deneyimi sunmak ve .NET Framework yükleme ilerlemesini izlemek için [Kullanıcı Birliğini özelleştirin.](#chaining_custom)

Bu dağıtım yöntemleri aşağıdaki bölümlerde ayrıntılı olarak ele alınmıştır.

## <a name="setting-a-dependency-on-the-net-framework"></a>.NET Çerçevesine bağımlılık ayarlama

Uygulamanızı dağıtmak için ClickOnce, InstallAware, InstallShield veya WiX kullanıyorsanız, uygulamanızın bir parçası olarak yüklenebilmek için .NET Framework'e bir bağımlılık ekleyebilirsiniz.

### <a name="clickonce-deployment"></a>ClickOnce dağıtımı

Visual Basic ve Visual C# ile oluşturulan projeler için ClickOnce dağıtımı kullanılabilir, ancak Visual C++için kullanılamaz.

Visual Studio'da ClickOnce dağıtımını seçmek ve .NET Çerçevesine bağımlılık eklemek için:

1. Yayınlamak istediğiniz uygulama projesini açın.

2. Çözüm Gezgini'nde, projenizin kısayol menüsünü açın ve ardından **Özellikler'i**seçin.

3. **Yayımla** bölmesini seçin.

4. **Önkoşullar** düğmesini seçin.

5. **Önkoşullar** iletişim kutusunda, ön koşul bileşenleri **ni yüklemek için kurulum programı oluştur** onay kutusunun seçildiğinden emin olun.

6. Ön koşullar listesinde, projenizi oluşturmak için kullandığınız .NET Framework sürümünü bulun ve seçin.

7. Ön koşullar için kaynak konumu belirtmek için bir seçenek seçin ve ardından **Tamam'ı**seçin.

     .NET Framework indirme konumu için bir URL sağlıyorsanız, .NET Framework indirme sayfasını veya kendi sitenizi belirtebilirsiniz. Yeniden dağıtılabilir paketi kendi sunucunuza yerlikiyorsanız, bu paket web yükleyicideğil, çevrimdışı yükleyici olmalıdır. Yalnızca .NET Framework indirme sayfasındaki web yükleyicisine bağlantı olabilirsiniz. URL ayrıca, kendi uygulamanızın dağıtıldığı bir disk de belirtebilir.

8. Özellik **Sayfaları** iletişim kutusunda **Tamam'ı**seçin.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>InstallAware dağıtım

InstallAware, Windows uygulaması (APPX), Windows Installer (MSI), Native Code (EXE) ve App-V (Application Virtualization) paketlerini tek bir kaynaktan oluşturur. .NET [Framework'ün herhangi bir sürümünü](https://www.installaware.com/one-click-pre-requisite-installer.htm) kurulumunuza kolayca ekleyin ve varsayılan komut [dosyalarını düzenleyerek](https://www.installaware.com/msicode.htm)yüklemeyi isteğe bağlı olarak özelleştirin. Örneğin, InstallAware sertifikaları Windows 7'ye önceden yükler ve bu olmadan .NET Framework 4.7 kurulumu başarısız olur. InstallAware hakkında daha fazla bilgi için [Windows Installer için InstallAware](https://www.installaware.com/) web sitesine bakın.

### <a name="installshield-deployment"></a>InstallShield dağıtımı

InstallShield, Windows uygulama paketleri (MSIX, APPX), Windows Installer paketleri (MSI) ve Yerel Kod (EXE) yükleyicileri oluşturur. InstallShield ayrıca Visual Studio tümleştirmesi de sağlar. Daha fazla bilgi için [InstallShield](https://www.flexerasoftware.com/install/products/installshield.html) web sitesine bakın.

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Windows Installer XML (WiX) dağıtımı

Windows Installer XML (WiX) araç kümesi, Windows yükleme paketlerini XML kaynak kodundan oluşturur. WiX, MSI ve MSM kurulum paketleri oluşturmak için yapı süreçlerinize entegre edilebilen komut satırı ortamını destekler. WiX'i kullanarak [.NET Framework'ü ön koşul olarak belirtebilir](https://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html)veya .NET Framework dağıtım deneyimini tam olarak denetlemek için [bir zincirleyici oluşturabilirsiniz.](https://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) WiX hakkında daha fazla bilgi için [Windows Installer XML (WiX) araç seti](https://wixtoolset.org/) web sitesine bakın.

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>.NET Framework'ün el ile yüklenmesi

Bazı durumlarda,.NET Framework'u uygulamanızla otomatik olarak yüklemek pratik olmayabilir. Bu durumda, kullanıcıların .NET Framework'e kendilerini yüklemelerini sağlayabilirsiniz. Yeniden dağıtılabilir paket [iki paket](#redistributable-packages)halinde mevcuttur. Kurulum işleminizde, kullanıcıların .NET Framework'u nasıl bulup yüklemeleri gerektiğine yönelik yönergeler sağlayın.

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>.NET Framework yüklemesini uygulamanızın kurulumuna zincirleme

Uygulamanız için özel bir kurulum programı oluşturuyorsanız, uygulamanızın kurulum işlemine .NET Framework kurulum işlemini zincirleyebilirsiniz (dahil edebilirsiniz). Zincirleme ,NET Framework yüklemesi için iki kullanıcı arabirimi seçeneği sağlar:

- .NET Framework yükleyicisi tarafından sağlanan varsayılan UI'yi kullanın.

- Uygulamanızın kurulum programıyla tutarlılık için .NET Framework yüklemesi için özel bir kullanıcı arabirimi oluşturun.

Her iki yöntem de web yükleyicisini veya çevrimdışı yükleyiciyi kullanmanıza olanak sağlar. Her paketin avantajları vardır:

- Web yükleyicisini kullanırsanız, .NET Framework kurulum işlemi hangi yükleme paketinin gerekli olduğuna karar verir ve yalnızca bu paketi web'den indirip yükler.

- Çevrimdışı yükleyiciyi kullanıyorsanız, kullanıcılarınızın kurulum sırasında web'den ek dosya indirmek zorunda kalmaması için yeniden dağıtım ortamınıza tam .NET Framework yükleme paketleri kümesini ekleyebilirsiniz.

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>Varsayılan .NET Framework UI kullanarak zincirleme

.NET Framework yükleme işlemini sessizce zincirlemek ve .NET Framework yükleyicisinin UI'yi sağlamasına izin vermek için kurulum programınıza aşağıdaki komutu ekleyin:

`<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>`

Örneğin, çalıştırılabilir programınız Contoso.exe ise ve .NET Framework 4.5 çevrimdışı yeniden dağıtılabilir paketini sessizce yüklemek istiyorsanız, aşağıdaki komutu kullanın:

`dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso`

Yüklemeyi özelleştirmek için ek komut satırı seçeneklerini kullanabilirsiniz. Örnek:

- Kullanıcıların sistemin yeniden başlatılmasını en aza indirmek için çalışan .NET Framework uygulamalarını `/showrmui` kapatmaları için bir yol sağlamak için pasif modu ayarlayın ve seçeneği aşağıdaki gibi kullanın:

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     Bu komut, Yeniden Başlat Yöneticisi'nin kullanıcılara .NET Framework uygulamalarını yüklemeden önce kapatma fırsatı veren bir ileti kutusu görüntülemesine olanak tanır.

- Web yükleyicisini kullanıyorsanız, bir dil `/LCID` paketi belirtme seçeneğini kullanabilirsiniz. Örneğin, .NET Framework 4.5 web yükleyicisini Contoso kurulum programınıza zincirlemek ve Japonca dil paketini yüklemek için uygulamanızın kurulum sürecine aşağıdaki komutu ekleyin:

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     Seçeneği atlarsanız, `/LCID` kurulum kullanıcının MUI ayarına uyan dil paketini yükler.

    > [!NOTE]
    > Farklı dil paketlerinin farklı çıkış tarihleri olabilir. Belirttiğiniz dil paketi indirme merkezinde kullanılamıyorsa, kurulum .NET Framework'ü dil paketi olmadan yükler. .NET Framework kullanıcının bilgisayarına zaten yüklüyse, kurulum yalnızca dil paketini yükler.

Seçeneklerin tam listesi için [Komut Satırı Seçenekleri](#command-line-options) bölümüne bakın.

Ortak iade kodları için [İade Kodları](#return-codes) bölümüne bakın.

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Özel Kullanıcı Arabirimi Kullanarak Zincirleme

Özel bir kurulum paketiniz varsa, kurulum ilerlemesini kendi görünümünüz gösterirken .NET Framework kurulumunu sessizce başlatmak ve izlemek isteyebilirsiniz. Bu durumda, kodunuzu aşağıdakileri kapsadığından emin olun:

- [.NET Framework donanım ve yazılım gereksinimlerini](../get-started/system-requirements.md)denetleyin.

- .NET Framework'ün doğru sürümünün kullanıcının bilgisayarında zaten yüklü olup olmadığını [algıla.](#detect_net)

    > [!IMPORTANT]
    > .NET Framework'ün doğru sürümünün zaten yüklü olup olmadığını belirlerken, *or* hedef sürümünüzün veya sonraki bir sürümün yüklü olup olmadığını kontrol etmelisiniz. Başka bir deyişle, kayıt defterinden aldığınız sürüm anahtarının hedef sürümünüzün sürüm anahtarına eşit olup olmadığını *değil,* hedef sürümünüzün sürüm anahtarından daha büyük mü yoksa eşit mi olduğunu değerlendirmeniz gerekir.

- Dil paketlerinin kullanıcının bilgisayarında zaten yüklü olup olmadığını [algılayın.](#detecting-the-language-packs)

- Dağıtımı denetlemek istiyorsanız, .NET Framework kurulum işlemini sessizce başlatın ve izleyin [(bkz.](how-to-get-progress-from-the-dotnet-installer.md)

- Çevrimdışı yükleyiciyi dağıtıyorsanız, [dil paketlerini ayrı ayrı zincirle.](#chain_langpack)

- [Komut satırı seçeneklerini](#command-line-options)kullanarak dağıtımı özelleştirin. Örneğin, .NET Framework web yükleyicisini zincirliyorsanız, ancak varsayılan dil paketini geçersiz `/LCID` kılmak istiyorsanız, önceki bölümde açıklandığı gibi seçeneği kullanın.

- [Sorun giderme](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>.NET Çerçevesinin Algılanması

.NET Framework yükleyici, yükleme başarılı olduğunda kayıt defteri anahtarlarını yazar. .NET Framework 4.5 veya sonraki bir değer için `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` `DWORD` `Release`kayıt defterinde klasörü denetleyerek yüklenir olup olmadığını test edebilirsiniz. ("NET Framework Setup"ın bir dönemle başlamadığını unutmayın.) Bu anahtarın varlığı, .NET Framework 4.5 veya daha sonraki bir sürümün o bilgisayara yüklendiğini gösterir. .NET `Release` Framework'ün hangi sürümünün yüklü olduğunu gösterir.

> [!IMPORTANT]
> Belirli bir sürümün mevcut olup olmadığını algılamaya çalışırken sürüm anahtar kelime değerinden **daha büyük veya eşit** bir değer olup olmadığını denetlemeniz gerekir.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Sürüm|Yayın DWORD değeri|
|-------------|--------------------------------|
|.NET Framework 4.8 Windows 10 Mayıs 2019 Güncelleştirmesi yüklü|528040|
|.NET Framework 4.8, Windows dışındaki tüm işletim sistemi sürümlerinde yüklü 10 Mayıs 2019 Güncelleştirmesi|528049|
|.NET Framework 4.7.2 Windows 10 Nisan 2018 Güncelleştirmesi ve Windows Server, sürüm 1803 yüklü|461808|
|.NET Framework 4.7.2, Windows 10 Nisan 2018 Güncelleştirmesi dışındaki tüm işletim sistemi sürümlerinde ve Windows Server, sürüm 1803'te yüklenir. Buna Windows 10 Ekim 2018 Güncelleştirmesi dahildir. |461814|
|.NET Framework 4.7.1 Windows 10 Fall Creators Update ve Windows Server, sürüm 1709 yüklü|461308|
|.NET Framework 4.7.1 Windows 10 Fall Creators Update ve Windows Server dışındaki tüm işletim sistemi sürümlerinde yüklü, sürüm 1709|461310|
|.NET Framework 4.7 Windows 10 Creators Update yüklü|460798|
|.NET Framework 4.7, Windows 10 Creators Update dışındaki tüm işletim sistemi sürümlerinde yüklü|460805|
|.NET Framework 4.6.2, Windows 10 Anniversary Edition ve Windows Server 2016'da yüklü|394802|
|.NET Framework 4.6.2, Windows 10 Anniversary Edition ve Windows Server 2016 dışındaki tüm işletim sistemi sürümlerinde yüklü|394806|
|.NET Framework 4.6.1 Windows 10 Kasım Güncelleştirmesi yüklü|394254|
|.NET Framework 4.6.1, Windows 10 Kasım Güncelleştirmesi dışındaki tüm işletim sistemi sürümlerinde yüklü|394271|
|.NET Framework 4.6 Windows 10 yüklü|393295|
|.NET Framework 4.6, Windows 10 dışındaki tüm işletim sistemi sürümlerinde yüklü|393297|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.5.1 Windows 8.1 veya Windows Server 2012 R2 ile yüklü|378675|
|.NET Framework 4.5.1 Windows 8, Windows 7 yüklü|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>Dil paketlerini algılama

Belirli bir dil paketinin HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* klasörünü kayıt defterinde dword değeri `Release`adlı bir DWORD değeri için denetleyerek yüklenediğini sınayabilirsiniz. ("NET Framework Setup"ın bir dönemle başlamadığını unutmayın.) *LCID* bir yerel tanımlayıcı belirtir; bunların listesi için [desteklenen dillere](#supported-languages) bakın.

Örneğin, tam Japonca dil paketinin (LCID=1041) yüklü olup olmadığını algılamak için, kayıt defterinden aşağıdaki adlandırılmış değeri alın:

| | |
|-|-|
| Anahtar | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041 |
| Adı | Yayınla |
| Tür | DWORD |

Bir dil paketinin son sürüm sürümünün .NET Framework'ün belirli bir sürümü için 4,5'ten 4,7.2'ye kadar yüklü olup olmadığını belirlemek için, önceki bölümde açıklanan RELEASE anahtar DWORD değerinin değerini kontrol [edin, .NET Framework'ü algılayın.](#detect_net)

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Dil paketlerini uygulama kurulumunuza zincirleme

.NET Framework, belirli kültürler için yerelleştirilmiş kaynaklar içeren bir dizi bağımsız dil paketi yürütülebilir dosya kümesi sağlar. Dil paketleri Download .NET Framework sayfalarından edinilebilir:

- [.NET Çerçeve 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Çerçeve 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Çerçeve 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Çerçeve 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

> [!IMPORTANT]
> Dil paketleri, bir uygulamayı çalıştırmak için gereken .NET Framework bileşenlerini içermez; bir dil paketi yüklemeden önce web veya çevrimdışı yükleyiciyi kullanarak .NET Framework'u yüklemeniz gerekir.

.NET Framework 4.5.1 ile başlayarak, paket adları `version` NDP<`number`>-KB<>-x86-x64-AllOS-<`culture`>.exe biçimini `number` alır, .NET Framework'ün `culture` sürüm numarası microsoft `version` bilgi bankası makale numarasıdır ve bir [ülke/bölge](#supported-languages)belirtir. Bu paketlerden birine örnek `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`olarak . Paket adları, bu makalenin daha önceki Yeniden [Dağıtılabilir Paketler](#redistributable-packages) bölümünde listelenmiştir.

.NET Framework çevrimdışı yükleyiciiçeren bir dil paketi yüklemek için, bunu uygulamanızın kurulumuna zincirlemeniz gerekir. Örneğin, .NET Framework 4.5.1 çevrimdışı yükleyicisini Japonca dil paketiyle dağıtmak için aşağıdaki komutu kullanın:

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

Web yükleyicisini kullanıyorsanız dil paketlerini zincirlemeniz gerekmez; kurulum, kullanıcının MUI ayarına uyan dil paketini yükler. Farklı bir dil yüklemek istiyorsanız, bir `/LCID` dil paketi belirtmek için seçeneği kullanabilirsiniz.

Komut satırı seçeneklerinin tam listesi için [Komut Satırı Seçenekleri](#command-line-options) bölümüne bakın.

### <a name="troubleshooting"></a>Sorun giderme

#### <a name="return-codes"></a>Dönüş kodları

Aşağıdaki tabloda .NET Framework yeniden dağıtılabilir yükleyici için en yaygın iade kodları listelenir. Dönüş kodları yükleyicinin tüm sürümleri için aynıdır. Ayrıntılı bilgi için bağlantılar için bir sonraki bölüme bakın.

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

- [URL takma hata kodları](https://go.microsoft.com/fwlink/?LinkId=180947)

- [WinHttp hata kodları](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Diğer hata kodları

Aşağıdaki içeriğe bakın:

- [Windows Installer hata kodları](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Windows Update Aracısı sonuç kodları](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>.NET Çerçevesini Kaldırma

Windows 8'den başlayarak,.NET Framework 4.5 veya sonraki sürümlerini Denetim Masası'nda **Windows özelliklerini açıp kapatarak** kaldırabilirsiniz. Windows'un eski sürümlerinde,.NET Framework 4.5 veya sonraki sürümlerini Denetim Masası'nda **Programlar Ekle veya Kaldır'ı** kullanarak kaldırabilirsiniz.

> [!IMPORTANT]
> Windows 7 ve önceki işletim sistemleri için .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7,1, 4.7.2 veya 4.8'i kaldırmaz ve .NET Framework 4.5 dosyalarını geri yüklemez ve .NET Framework 4.5'i kaldırmaz .NET Framework 4 4 dosyalarını geri yüklemez. Eski sürüme geri dönmek istiyorsanız, yeniden yüklemeniz ve herhangi bir güncelleştirmeniz olmalıdır.

## <a name="appendix"></a>Ek

### <a name="command-line-options"></a>Komut satırı seçenekleri

Aşağıdaki tabloda,.NET Framework 4.5'i zinciriniz de ekleyebileceğiniz seçenekler, uygulamanızın kurulumuna yeniden dağıtılabilir.

|Seçenek|Açıklama|
|------------|-----------------|
|**/CEIPConsent**|Varsayılan davranışın üzerine yazar ve gelecekteki dağıtım deneyimlerini geliştirmek için Microsoft'a anonim geri bildirim gönderir. Bu seçenek, yalnızca kurulum programı onay isterse ve kullanıcı Microsoft'a anonim geri bildirim gönderme izni verirse kullanılabilir.|
|**/zincirleme paket**`packageName`|Zincirleme yapan çalıştırılabilirin adını belirtir. Bu bilgiler, gelecekteki dağıtım deneyimlerini geliştirmeye yardımcı olmak için anonim geri bildirim olarak Microsoft'a gönderilir.<br /><br /> Paket adı boşluklar içeriyorsa, sınırlayıcı olarak çift tırnak işaretleri kullanın; örneğin: **/zincirleme paket "Lucerne Yayıncılık"**. Zincirleme paket örneği için [bkz.](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))|
|**/LCID**  `LCID`<br /><br /> yerel `LCID` tanımlayıcıyı belirtir [(desteklenen dillere](#supported-languages)bakın)|Sessiz mod ayarlanmamışsa, belirtilen `LCID` dil paketini yükler ve görüntülenen UI'yi bu dilde gösterilmeye zorlar.<br /><br /> Web yükleyicisi için bu seçenek, dil paketini web'den zincirleme olarak yükler. **Not:**  Bu seçeneği yalnızca web yükleyicisiyle kullanın.|
|**/log** `file` &#124;`folder`|Günlük dosyasının konumunu belirtir. Varsayılan işlem için geçici klasördür ve varsayılan dosya adı paketi temel alır. Dosya uzantısı .txt ise, bir metin günlüğü üretilir. Başka bir uzantı belirtirseniz veya uzantı belirtmezseniz, bir HTML günlüğü oluşturulur.|
|**/msioptions**|.msi ve .msp öğeleri için geçirilecek seçenekleri belirtir; örneğin: `/msioptions "PROPERTY1='Value'"`.|
|**/norestart**|Kurulum programının otomatik olarak yeniden başlatılmasını engeller. Bu seçeneği kullanırsanız, zincirleme uygulamanın iade kodunu yakalaması ve yeniden başlatmayı işlemesi gerekiyor [(bkz.](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))|
|**/pasif**|Pasif modu ayarlar. Yüklemenin devam ettiğini belirtmek için ilerleme çubuğunu görüntüler, ancak kullanıcıya herhangi bir istem veya hata iletisi görüntülemez. Bu modda, bir kurulum programı tarafından zincirlendiğinde, zincirleme paketin [return kodlarını](#return-codes)işlemesi gerekir.|
|**/boru**|İlerleme elde etmek için bir zincirleme paketin etkinleştirmek için bir iletişim kanalı oluşturur.|
|**/promptrestart**|Yalnızca pasif mod, kurulum programı yeniden başlatma gerektiriyorsa, kullanıcıyı ister. Bu seçenek, yeniden başlatma gerekiyorsa kullanıcı etkileşimi gerektirir.|
|**/q**|Sessiz modu ayarlar.|
|**/onarım**|Onarım işlevini tetikler.|
|**/serialdownload**|Yüklemeyi yalnızca paket indirildikten sonra gerçekleştirmeye zorlar.|
|**/showfinalerror**|Pasif modu ayarlar. Hataları yalnızca yükleme başarılı değilse görüntüler. Yükleme başarılı değilse, bu seçenek kullanıcı etkileşimi gerektirir.|
|**/showrmui**|Yalnızca **/pasif** seçeneği ile kullanılır. Kullanıcıların şu anda çalışmakta olan .NET Framework uygulamalarını kapatmalarını sağlayan bir ileti kutusu görüntüler. Bu ileti kutusu pasif ve pasif olmayan modda aynı şekilde hareket eder.|
|**/kaldır**|.NET Framework yeniden dağıtılabilir'i yükler.|

### <a name="supported-languages"></a>Desteklenen diller

Aşağıdaki tabloda .NET Framework 4.5 ve sonraki sürümler için kullanılabilen .NET Framework dil paketleri listelenmektedir.

|LCID|Dil – ülke/bölge|Kültür|
|----------|--------------------------------|-------------|
|1025|Arapça - Suudi Arabistan|Ar|
|1028|Çince – Geleneksel|zh-Hant|
|1029|Çekçe|Cs|
|1030|Danca|Savcı|
|1031|Almanca – Almanya|de|
|1032|Yunanca|El|
|1035|Fince|ﬁ|
|1036|Fransızca - Fransa|Fr|
|1037|İbranice|Hge|
|1038|Macarca|Hu|
|1040|İtalyanca – İtalya|bu|
|1041|Japonca|Ja|
|1042|Korece|ko|
|1043|Hollanda - Hollanda|Nl|
|1044|Norveççe (Bokmål)|hayır|
|1045|Lehçe|Pl|
|1046|Portekizce - Brezilya|pt-BR|
|1049|Rusça|Ru|
|1053|İsveççe|Sv|
|1055|Türkçe|tr|
|2052|Çince – Basitleştirilmiş|zh-Hans|
|2070|Portekizce - Portekiz|pt-PT|
|3082|İspanyolca - İspanya (Modern Sort)|es|

## <a name="see-also"></a>Ayrıca bkz.

- [Yöneticiler için Dağıtım Kılavuzu](guide-for-administrators.md)
- [Sistem Gereksinimleri](../get-started/system-requirements.md)
- [Geliştiriciler için .NET Framework'u yükleyin](../install/guide-for-developers.md)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../install/troubleshoot-blocked-installations-and-uninstallations.md)
- [.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma](reducing-system-restarts.md)
- [Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](how-to-get-progress-from-the-dotnet-installer.md)
