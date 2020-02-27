---
title: Geliştiriciler için .NET Framework dağıtım kılavuzu
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
ms.openlocfilehash: 26c168040b0fa5e975e64a7518b0d0bf250c4711
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628130"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Geliştiriciler için .NET Framework dağıtım kılavuzu
Bu konu, .NET Framework 4,5 ' den .NET Framework herhangi bir sürümünü uygulamalarıyla [!INCLUDE[net_current](../../../includes/net-current-version.md)] yüklemek isteyen geliştiriciler için bilgi sağlamaktadır.

İndirme sayfalarından .NET Framework için yeniden dağıtılabilir paketleri ve dil paketlerini indirebilirsiniz:

- [.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Framework 4,7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4,6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

 Önemli notlar:

- .NET Framework 4.5.1 ile [!INCLUDE[net_current](../../../includes/net-current-version.md)] arasındaki .NET Framework sürümleri, .NET Framework 4,5 ' e yönelik yerinde güncellemelerdir, yani aynı çalışma zamanı sürümünü kullanır, ancak derleme sürümleri güncelleştirilir ve yeni türler ve Üyeler dahil edilir.

- .NET Framework 4,5 ve sonraki sürümler artımlı olarak .NET Framework 4 ' te oluşturulmuştur. .NET Framework 4 ' ün yüklü olduğu bir sisteme .NET Framework 4,5 veya sonraki sürümleri yüklediğinizde, sürüm 4 derlemeleri yeni sürümlerle değiştirilmiştir.

- Uygulamanızda Microsoft ['un bant dışı bir paketine](../get-started/the-net-framework-and-out-of-band-releases.md) başvuruyorsam, derleme uygulama paketine dahil edilir.

- .NET Framework 4,5 veya sonraki sürümleri yüklemek için yönetici ayrıcalıklarına sahip olmanız gerekir.

- .NET Framework 4,5, Windows 8 ve Windows Server 2012 ' de bulunur, bu nedenle uygulamayı bu işletim sistemlerine dağıtmanız gerekmez. Benzer şekilde, .NET Framework 4.5.1 Windows 8.1 ve Windows Server 2012 R2 'ye dahildir. .NET Framework 4.5.2 hiçbir işletim sistemine dahil değildir. .NET Framework 4,6, Windows 10 ' a dahil edilmiştir, .NET Framework 4.6.1 Windows 10 Kasım güncelleştirmesine dahildir ve .NET Framework 4.6.2 Windows 10 yıldönümü güncelleştirmesine dahildir.  .NET Framework 4,7, Windows 10 Creators Update 'e dahildir, .NET Framework 4.7.1 Windows 10 Fall Creators Update 'e dahildir ve .NET Framework 4.7.2 Windows 10 Ekim 2018 güncelleştirmesi ve Windows 10 Nisan 2018 güncelleştirmesine dahildir. .NET Framework 4,8, Windows 10 Mayıs 2019 güncelleştirme ' ye eklenmiştir. Donanım ve yazılım gereksinimlerinin tam listesi için bkz. [sistem gereksinimleri](../get-started/system-requirements.md).

- Kullanıcılarınız .NET Framework 4,5 ' den başlayarak, kurulum sırasında çalışan .NET Framework uygulamalarının bir listesini görüntüleyebilir ve kolayca kapatabilir. Bu, .NET Framework yüklemelerinin neden olduğu sistem yeniden başlatmalarının önlenmesine yardımcı olabilir. Bkz. [sistem yeniden başlatmaları azaltma](reducing-system-restarts.md).

- .NET Framework 4,5 veya sonraki sürümlerin kaldırılması, önceden var olan .NET Framework 4 dosyalarını da kaldırır. .NET Framework 4 ' e geri dönmek istiyorsanız, bu dosyayı ve tüm güncelleştirmeleri yeniden yüklemeniz gerekir. Bkz. [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100))' ü yükleme.

- .NET Framework 4,5 yeniden dağıtılabilir, dijital bir sertifikada yanlış bir zaman damgasıyla ilgili bir sorunu düzeltmek için 9 Ekim 2012 tarihinde güncelleştirildi. Bu, Microsoft tarafından oluşturulan ve imzalanan dosyalardaki dijital imzanın erken süre sonu dolmasına neden olur. Daha önce 16 Ağustos 2012 tarihli .NET Framework 4,5 yeniden dağıtılabilir paketini yüklediyseniz, [.NET Framework indirme sayfasından](https://dotnet.microsoft.com/download/dotnet-framework/net45)kopyanızı en son yeniden dağıtılabilir ile güncelleştirmenizi öneririz. Bu sorun hakkında daha fazla bilgi için bkz. [Microsoft Güvenlik Danışmanlığı 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

Bir sistem yöneticisinin .NET Framework ve sistem bağımlılıklarını bir ağ üzerinden nasıl dağıtabilirim hakkında bilgi için bkz. [Yöneticiler Için dağıtım kılavuzu](guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Uygulamanız için dağıtım seçenekleri

Uygulamanızı bir Web sunucusuna veya başka bir merkezi konuma yayımlamaya, böylece kullanıcıların yükleyebilmeleri için hazırsanız, çeşitli dağıtım yöntemlerinden birini seçebilirsiniz. Bunlardan bazıları Visual Studio ile sunulmaktadır. Aşağıdaki tabloda, uygulamanız için dağıtım seçenekleri listelenmekte ve her bir seçeneği destekleyen .NET Framework yeniden dağıtılabilir paketi belirtilir. Bunlara ek olarak, uygulamanız için özel bir kurulum programı yazabilirsiniz; daha fazla bilgi için [.NET Framework yüklemesini uygulamanızın kurulumuna zincirme](#chaining)bölümüne bakın.

|Uygulamanız için dağıtım stratejisi|Dağıtım yöntemleri kullanılabilir|Kullanmak için yeniden dağıtılabilir .NET Framework|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Web 'den yüklemesi|[InstallAware](#installaware-deployment) - <br />- [InstallShield](#installshield-deployment)<br />[Wix araç takımını](#wix) - <br />[el ile yükleme](#installing_manually) - |[Web Yükleyicisi](#redistributable-packages)|
|Diskten yüklensin|[InstallAware](#installaware-deployment) - <br />- [InstallShield](#installshield-deployment)<br />[Wix araç takımını](#wix) - <br />[el ile yükleme](#installing_manually) - |[Çevrimdışı yükleyici](#redistributable-packages)|
|Yerel bir ağdan (kurumsal uygulamalar için) yükler|- [ClickOnce](#clickonce-deployment)|[Web Yükleyicisi](#redistributable-packages) (kısıtlamalar için bkz. [ClickOnce](#clickonce-deployment) ) veya [çevrimdışı yükleyici](#redistributable-packages)|

## <a name="redistributable-packages"></a>Yeniden dağıtılabilir paketler

.NET Framework iki yeniden dağıtılabilir paket (önyükleyici) ve çevrimdışı yükleyici (tek başına yeniden dağıtılabilir) ile kullanılabilir. Tüm .NET Framework indirmeleri, [indirme .NET Framework sayfasında](https://dotnet.microsoft.com/download/dotnet-framework/)barındırılır. Aşağıdaki tabloda iki paket karşılaştırılmaktadır:

||Web Yükleyicisi|Çevrimdışı yükleyici|
|-|-------------------|-----------------------|
|Internet bağlantısı gerekiyor mu?|Yes|Hayır|
|İndirme boyutu|Daha küçük (yalnızca hedef platform için yükleyiciyi içerir) *|Boyutta|
|Dil paketleri|Dahil * *|Tüm işletim sistemlerini hedefleyen paketi kullanmadığınız takdirde [ayrı olarak yüklenmelidir](#chain_langpack)|
|Dağıtım yöntemi|Tüm yöntemleri destekler:<br /><br />- [ClickOnce](#clickonce-deployment)<br />[InstallAware](#installaware-deployment) - <br />- [InstallShield](#installshield-deployment)<br />- [WINDOWS Installer XML (WiX)](#wix)<br />[el ile yükleme](#installing_manually) - <br />[özel kurulum - (zincirleme)](#chaining)|Tüm yöntemleri destekler:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />[InstallAware](#installaware-deployment) - <br />- [InstallShield](#installshield-deployment)<br />- [WINDOWS Installer XML (WiX)](#wix)<br />[el ile yükleme](#installing_manually) - <br />[özel kurulum - (zincirleme)](#chaining)|

çevrimdışı yükleyici, tüm hedef platformlar için bileşenleri içerdiğinden daha büyük \*. Kurulumu çalıştırmayı tamamladığınızda, Windows işletim sistemi yalnızca kullanılan yükleyiciyi önbelleğe alır. Yükleme sonrasında çevrimdışı yükleyici silinirse kullanılan disk alanı, web yükleyicisinin kullandığı ile aynıdır. Uygulamanızın kurulum programını oluşturmak için kullandığınız araç (örneğin, [InstallAware](#installaware-deployment) veya [InstallShield](#installshield-deployment)), yüklemeden sonra kaldırılan bir kurulum dosyası klasörü sağlıyorsa, çevrimdışı yükleyici, kurulum klasörüne yerleştirerek otomatik olarak silinebilir.

\*\* web yükleyicisini özel kurulumla kullanıyorsanız, kullanıcının çok dilli kullanıcı arabirimi (MUI) ayarını temel alan varsayılan dil ayarlarını kullanabilir veya komut satırındaki `/LCID` seçeneğini kullanarak başka bir dil paketi belirtebilirsiniz. Örnekler için [varsayılan .NET Framework Kullanıcı arabirimini kullanarak zincirleme](#chaining_default) bölümüne bakın.

## <a name="deployment-methods"></a>Dağıtım yöntemleri

 Dört dağıtım yöntemi mevcuttur:

- .NET Framework bir bağımlılık ayarlayabilirsiniz. Aşağıdaki yöntemlerden birini kullanarak .NET Framework uygulamanızın yüklemesinde bir önkoşul olarak belirtebilirsiniz:

  - [ClickOnce dağıtımını](#clickonce-deployment) kullanma (Visual Studio ile kullanılabilir)

  - [InstallAware projesi](#installaware-deployment) oluşturma (Visual Studio kullanıcıları için ücretsiz sürüm)

  - [InstallShield projesi](#installshield-deployment) oluşturma (Visual Studio ile kullanılabilir)

  - [WINDOWS Installer XML (WiX) araç takımını](#wix) kullanın

- Kullanıcılarınızın [.NET Framework el ile yüklemesini](#installing_manually)isteyebilirsiniz.

- .NET Framework kurulum işlemini uygulamanızın kurulumuna zincirleyebilir ve .NET Framework yükleme deneyimini nasıl işlemek istediğinize karar verebilirsiniz:

  - [Varsayılan Kullanıcı arabirimini kullanın](#chaining_default). .NET Framework yükleyicinin yükleme deneyimini sağlamasına izin verin.

  - [Kullanıcı arabirimini](#chaining_custom) Birleşik bir yükleme deneyimi sunmak ve .NET Framework yükleme ilerlemesini Izlemek için özelleştirin.

Bu dağıtım yöntemleri aşağıdaki bölümlerde ayrıntılı olarak ele alınmıştır.

## <a name="setting-a-dependency-on-the-net-framework"></a>.NET Framework bağımlılığı ayarlama

Uygulamanızı dağıtmak için ClickOnce, InstallAware, InstallShield veya WiX kullanıyorsanız, .NET Framework bir bağımlılık ekleyerek uygulamanızın bir parçası olarak yüklenebilmesini sağlayabilirsiniz.

### <a name="clickonce-deployment"></a>ClickOnce dağıtımı

ClickOnce dağıtımı, Visual Basic ve görsele C#oluşturulmuş projeler için kullanılabilir, ancak görsel C++için kullanılamaz.

Visual Studio 'da ClickOnce dağıtımını seçmek ve .NET Framework bir bağımlılık eklemek için:

1. Yayımlamak istediğiniz uygulama projesini açın.

2. Çözüm Gezgini ' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

3. **Yayımla** bölmesini seçin.

4. **Önkoşullar** düğmesini seçin.

5. **Önkoşullar** iletişim kutusunda, **Önkoşul bileşenlerini yüklemek Için Kurulum programı oluştur** onay kutusunun işaretli olduğundan emin olun.

6. Önkoşullar listesinde, projenizi oluşturmak için kullandığınız .NET Framework sürümünü bulun ve seçin.

7. Önkoşulların kaynak konumunu belirtmek için bir seçenek belirleyin ve ardından **Tamam**' ı seçin.

     .NET Framework indirme konumu için bir URL sağlarsanız, .NET Framework indirme sayfasını ya da kendi bir sitesini belirtebilirsiniz. Yeniden dağıtılabilir paketi kendi sunucunuza yerleştiriyorsanız, web yükleyicisinin değil, çevrimdışı yükleyici olmalıdır. Yalnızca .NET Framework indirme sayfasındaki Web yükleyicisine bağlanabilirsiniz. URL aynı zamanda kendi uygulamanızın dağıtıldığı bir disk da belirtebilir.

8. **Özellik sayfaları** Iletişim kutusunda **Tamam**' ı seçin.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>InstallAware dağıtımı

InstallAware, tek bir kaynaktan Windows uygulaması (APPX), Windows Installer (MSI), yerel kod (EXE) ve App-V (uygulama sanallaştırma) paketleri oluşturur. .NET Framework, isteğe bağlı olarak, [varsayılan betikleri düzenleyerek](https://www.installaware.com/msicode.htm)yüklemeyi özelleştirerek, kuruluminizdeki [tüm sürümlerini kolayca ekleyin](https://www.installaware.com/one-click-pre-requisite-installer.htm) . Örneğin, InstallAware Windows 7 ' de sertifikaları önceden yüklerken .NET Framework 4,7 kurulumu başarısız olur. InstallAware hakkında daha fazla bilgi için bkz. [InstallAware for Windows Installer](https://www.installaware.com/) Web sitesi.

### <a name="installshield-deployment"></a>InstallShield dağıtımı

InstallShield, Windows uygulama paketleri (MSIX, APPX), Windows Installer paketleri (MSI) ve yerel kod (EXE) yükleyicileri oluşturur. InstallShield Ayrıca Visual Studio tümleştirmesi de sağlar. Daha fazla bilgi için [InstallShield](https://www.flexerasoftware.com/install/products/installshield.html) Web sitesine bakın.

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Windows Installer XML (WiX) dağıtımı

Windows Installer XML (WiX) araç takımı, XML kaynak kodundan Windows yükleme paketleri oluşturur. WiX, MSI ve MSM kurulum paketleri oluşturmak için yapı süreçlerinizle tümleştirilebilen bir komut satırı ortamını destekler. WiX kullanarak, [.NET Framework bir önkoşul olarak belirtebilir](https://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html)veya .NET Framework dağıtım deneyimini tam olarak denetlemek için [bir bağlayıcı oluşturabilirsiniz](https://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) . WiX hakkında daha fazla bilgi için [WINDOWS Installer XML (WiX) araç takımı](https://wixtoolset.org/) Web sitesine bakın.

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>.NET Framework el ile yükleme

Bazı durumlarda .NET Framework uygulamanıza otomatik olarak yüklemek pratik olabilir. Bu durumda, kullanıcıların .NET Framework kendilerini yüklemesini sağlayabilirsiniz. Yeniden dağıtılabilir paket [iki](#redistributable-packages)pakette kullanılabilir. Kurulum sürecinizdeki kullanıcıların .NET Framework bulması ve yüklemesi için yönergeler sağlayın.

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>.NET Framework yüklemesini uygulamanızın kurulumuna zincirme

Uygulamanız için özel bir kurulum programı oluşturuyorsanız, uygulamanızın Kurulum sürecinde .NET Framework kurulum işlemini zincirleyebilirsiniz (dahil). Zincirleme .NET Framework yüklemesi için iki UI seçeneği sağlar:

- .NET Framework yükleyicisi tarafından belirtilen varsayılan kullanıcı arabirimini kullanın.

- Uygulamanızın kurulum programıyla tutarlı olması için .NET Framework yüklemesi için özel bir kullanıcı arabirimi oluşturun.

Her iki yöntem de web yükleyicisini veya çevrimdışı yükleyiciyi kullanmanıza izin verir. Her paketin avantajları vardır:

- Web yükleyicisini kullanıyorsanız, .NET Framework kurulum işlemi hangi yükleme paketinin gerekli olduğuna karar verir ve yalnızca bu paketi Web 'den indirir ve yükler.

- Çevrimdışı yükleyiciyi kullanıyorsanız, kullanıcılarınızın kurulum sırasında Web 'den başka dosya indirmesini sağlamak için yeniden dağıtım medyanıza sahip .NET Framework yükleme paketlerinin tamamını dahil edebilirsiniz.

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>Varsayılan .NET Framework Kullanıcı arabirimini kullanarak zincirleme

.NET Framework yükleme işlemini sessizce zincirlemek ve .NET Framework yükleyicinin Kullanıcı arabirimini sağlamasına izin vermek için, kurulum programınıza aşağıdaki komutu ekleyin:

`<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>`

Örneğin, yürütülebilir programınız contoso. exe ise ve .NET Framework 4,5 çevrimdışı yeniden dağıtılabilir paketini sessizce yüklemek istiyorsanız şu komutu kullanın:

`dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso`

Yüklemeyi özelleştirmek için ek komut satırı seçeneklerini kullanabilirsiniz. Örnek:

- Kullanıcıların, sistem yeniden başlatmaları en aza indirmek için .NET Framework uygulamaları kapatmalarının bir yolunu sağlamak için, Pasif modu ayarlayın ve `/showrmui` seçeneğini şu şekilde kullanın:

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     Bu komut, kullanıcıların .NET Framework yüklemeden önce .NET Framework uygulamaları kapatma fırsatı veren bir ileti kutusu görüntülemesini sağlar.

- Web yükleyicisini kullanıyorsanız, bir dil paketi belirtmek için `/LCID` seçeneğini kullanabilirsiniz. Örneğin, .NET Framework 4,5 web yükleyicisini contoso kurulum programınıza zincirlemek ve Japonca dil paketini yüklemek için uygulamanızın Kurulum işlemine aşağıdaki komutu ekleyin:

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     `/LCID` seçeneğini atlarsanız, Kurulum kullanıcının MUI ayarıyla eşleşen dil paketini yükler.

    > [!NOTE]
    > Farklı dil paketlerinde farklı sürüm tarihleri olabilir. Belirttiğiniz dil paketi indirme merkezinde yoksa, kurulum .NET Framework dil paketi olmadan yükler. .NET Framework kullanıcının bilgisayarında zaten yüklüyse, kurulum yalnızca dil paketini yükler.

Seçeneklerin tam listesi için [komut satırı seçenekleri](#command-line-options) bölümüne bakın.

Ortak dönüş kodları için [dönüş kodları](#return-codes) bölümüne bakın.

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Özel bir kullanıcı arabirimi kullanarak zincirleme

Özel bir kurulum paketiniz varsa, kurulum ilerleme durumunun kendi görünümünü gösterirken .NET Framework kurulumunu sessizce başlatmak ve izlemek isteyebilirsiniz. Bu durumda, kodunuzun aşağıdakileri kapsadığından emin olun:

- [.NET Framework donanım ve yazılım gereksinimlerini](../get-started/system-requirements.md)denetleyin.

- .NET Framework doğru sürümünün kullanıcının bilgisayarında zaten yüklü olup olmadığını [algılar](#detect_net) .

    > [!IMPORTANT]
    > .NET Framework 'nin doğru sürümünün zaten yüklü olup olmadığını belirlemek için, hedef sürümünüzün yüklenip yüklenmediğini değil, hedef sürümünüzün *veya* sonraki bir sürümünün yüklü olup olmadığını denetlemeniz gerekir. Diğer bir deyişle, kayıt defterinden aldığınız yayın anahtarının hedef sürümünüzün yayın anahtarına eşit olup olmadığını *değil* , hedef sürümünüzün yayın anahtarından büyük veya ona eşit olup olmadığını değerlendirmelisiniz.

- Dil paketlerinin kullanıcının bilgisayarında zaten yüklü olup olmadığını [algılar](#detecting-the-language-packs) .

- Dağıtımı denetlemek isterseniz, .NET Framework kurulum işlemini sessizce başlatın ve izleyin (bkz. [nasıl yapılır: .NET Framework 4,5 Yükleyicisinden Ilerleme durumunu alma](how-to-get-progress-from-the-dotnet-installer.md)).

- Çevrimdışı yükleyiciyi dağıtıyorsanız, [dil paketlerini ayrı olarak zincirleyebilirsiniz](#chain_langpack).

- [Komut satırı seçeneklerini](#command-line-options)kullanarak dağıtımı özelleştirin. Örneğin, .NET Framework web yükleyicisini zincirliyoruz, ancak varsayılan dil paketini geçersiz kılmak istiyorsanız, önceki bölümde açıklandığı gibi `/LCID` seçeneğini kullanın.

- [Sorun giderin](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>.NET Framework algılanıyor

Yükleme başarılı olduğunda .NET Framework yükleyicisi kayıt defteri anahtarlarını yazar. `Release`adlı bir `DWORD` değeri için kayıt defterindeki `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klasörünü denetleyerek .NET Framework 4,5 veya sonraki bir sürümünün yüklü olup olmadığını test edebilirsiniz. ("NET Framework Setup" bir noktayla başlamayacağını unutmayın.) Bu anahtarın varlığı, bu bilgisayarda .NET Framework 4,5 veya sonraki bir sürümün yüklü olduğunu gösterir. `Release` değeri .NET Framework hangi sürümünün yüklendiğini gösterir.

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
| Adı | Yayınla |
| Tür | DWORD |

4,5 ile 4.7.2 arasında .NET Framework belirli bir sürümü için dil paketinin son sürümünün yüklenip yüklenmediğini saptamak için, önceki bölümde açıklanan yayın anahtarı DWORD değerinin değerini denetleyin ve [.NET Framework](#detect_net)tespit edin.

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Dil paketlerini uygulama kuruluma zincirleme

.NET Framework belirli kültürler için yerelleştirilmiş kaynakları içeren tek başına dil paketi yürütülebilir dosyaları kümesi sağlar. Dil paketleri Indir .NET Framework sayfalarından edinilebilir:

- [.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Framework 4,7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4,6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

> [!IMPORTANT]
> Dil paketleri, bir uygulamayı çalıştırmak için gereken .NET Framework bileşenleri içermez; bir dil paketi yüklemeden önce Web veya çevrimdışı yükleyiciyi kullanarak .NET Framework yüklemelisiniz.

.NET Framework 4.5.1 ' den itibaren, paket adları NDP <`version`>-KB <`number`>-x86-x64-Allows-<`culture`>. exe ' dir; burada `version`, .NET Framework sürüm numarasıdır, `number` bir Microsoft Bilgi Bankası makale numarasıdır ve `culture` bir [ülke/bölge](#supported-languages)belirtir. Bu paketlerden birine bir örnek `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Paket adları, bu makalenin önceki bölümlerinde [yeniden dağıtılabilir paketler](#redistributable-packages) bölümünde listelenmiştir.

.NET Framework çevrimdışı yükleyicisiyle bir dil paketi yüklemek için, uygulamayı uygulamanızın kurulumuna zincirmalısınız. Örneğin, 4.5.1 .NET Framework çevrimdışı yükleyiciyi Japonca dil paketiyle dağıtmak için aşağıdaki komutu kullanın:

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

Web yükleyicisini kullanıyorsanız, dil paketlerini zincirlemek zorunda değilsiniz; Kurulum, kullanıcının MUI ayarıyla eşleşen dil paketini yükleyecek. Farklı bir dil yüklemek isterseniz, bir dil paketi belirtmek için `/LCID` seçeneğini kullanabilirsiniz.

Komut satırı seçeneklerinin tam listesi için bkz. [komut satırı seçenekleri](#command-line-options) bölümü.

### <a name="troubleshooting"></a>Sorun giderme

#### <a name="return-codes"></a>Dönüş kodları

Aşağıdaki tabloda .NET Framework yeniden dağıtılabilir yükleyici için en yaygın dönüş kodları listelenmektedir. Dönüş kodları yükleyicinin tüm sürümleri için aynıdır. Ayrıntılı bilgilerin bağlantıları için sonraki bölüme bakın.

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

## <a name="uninstalling-the-net-framework"></a>.NET Framework kaldırılıyor

Windows 8 ' den itibaren, Denetim Masası 'ndaki **Windows özelliklerini aç ve Kapat** ' ı kullanarak .NET Framework 4,5 veya sonraki sürümleri kaldırabilirsiniz. Windows 'un eski sürümlerinde, Denetim Masası 'ndaki **Program Ekle veya Kaldır** 'ı kullanarak .NET Framework 4,5 veya sonraki sürümleri kaldırabilirsiniz.

> [!IMPORTANT]
> Windows 7 ve önceki işletim sistemlerinde, .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 veya 4,8 ' ı kaldırmak .NET Framework 4,5 dosyalarını geri almaz ve .NET Framework 4,5 kaldırıldığında .NET Framework 4 dosyası geri almaz. Eski sürüme geri dönmek istiyorsanız, bu dosyayı ve tüm güncelleştirmeleri yeniden yüklemeniz gerekir.

## <a name="appendix"></a>Ek

### <a name="command-line-options"></a>Komut satırı seçenekleri

Aşağıdaki tabloda, .NET Framework 4,5 yeniden dağıtılabilir öğesini uygulamanızın kurulumuna zincirlerken dahil edilecek seçenekler listelenmektedir.

|Seçenek|Açıklama|
|------------|-----------------|
|**/Ceiponayı**|Varsayılan davranışın üzerine yazar ve gelecekteki dağıtım deneyimlerini geliştirmek üzere Microsoft 'a anonim geri bildirim gönderir. Bu seçenek, yalnızca kurulum programı onay isterse ve Kullanıcı Microsoft 'a anonim geri bildirim gönderme izni veriyorsa kullanılabilir.|
|**/ChainingPackage** `packageName`|Zincirlemeyi yapan yürütülebilir dosyanın adını belirtir. Bu bilgiler, gelecekteki dağıtım deneyimlerini iyileştirmenize yardımcı olmak için anonim geri bildirim olarak Microsoft 'a gönderilir.<br /><br /> Paket adı boşluk içeriyorsa, çift tırnak işaretlerini sınırlayıcılar olarak kullanın; Örneğin: **/chainingpackage "Lucerne Publishing"** . Bir zincir paketi örneği için bkz. [bir yükleme paketinden Ilerleme bilgisi alma](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).|
|**/LCID**`LCID`<br /><br /> Burada `LCID` bir yerel ayar tanımlayıcıyı belirtir (bkz. [desteklenen diller](#supported-languages))|, Sessiz mod ayarlanmadığı takdirde, `LCID` tarafından belirtilen dil paketini ve görüntülenen kullanıcı arabirimini o dilde gösterilecek şekilde zorlar.<br /><br /> Web Yükleyicisi için bu seçenek zinciri, dil paketini Web 'den kurar. **Note:**  Bu seçeneği yalnızca Web yükleyicisiyle kullanın.|
|**/log** `file` &#124; `folder`|Günlük dosyasının konumunu belirtir. Varsayılan, işlemin geçici klasörüdür ve varsayılan dosya adı pakete dayalıdır. Dosya uzantısı. txt ise, bir metin günlüğü üretilir. Başka bir uzantıyı veya uzantıyı belirtirseniz, bir HTML günlüğü oluşturulur.|
|**/msioptions**|. Msi ve. msp öğeleri için geçirilecek seçenekleri belirtir; Örneğin: `/msioptions "PROPERTY1='Value'"`.|
|**/norestart**|Kurulum programının otomatik olarak yeniden başlatılmasını önler. Bu seçeneği kullanırsanız, zincirleme uygulamanın dönüş kodunu yakalaması ve yeniden başlatma işlemini işlemesi gerekir (bkz. [bir yükleme paketinden Ilerleme bilgilerini alma](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))).|
|**/passive**|Pasif modu ayarlar. Yüklemenin devam ettiğini belirten, ancak kullanıcıya hiçbir istem veya hata iletisi görüntülemediğini belirten ilerleme çubuğunu görüntüler. Bu modda, bir kurulum programı tarafından zincirleme yaparken, zincirleme paketi [dönüş kodlarını](#return-codes)işlemelidir.|
|**/Pipe**|Bir zincir oluşturma paketinin ilerlemesini sağlamak için bir iletişim kanalı oluşturur.|
|**/promptrestart**|Yalnızca Pasif mod, Kurulum programı yeniden başlatma gerektiriyorsa, kullanıcıya sorar. Yeniden başlatma gerekirse bu seçenek kullanıcı etkileşimini gerektirir.|
|**anahtarın**|Sessiz modu ayarlar.|
|**/Repair**|Onarma işlevini tetikler.|
|**/serialdownload**|Yüklemeyi yalnızca paket indirildikten sonra gerçekleşecek şekilde zorlar.|
|**/showfinalhatası**|Pasif modu ayarlar. Yalnızca yükleme başarılı olmazsa hataları görüntüler. Yükleme başarılı olmazsa bu seçenek kullanıcı etkileşimini gerektirir.|
|**/showrmuı**|Yalnızca **/passive** seçeneğiyle kullanılır. Kullanıcıların şu anda çalışmakta olan uygulamaları .NET Framework kapatmasını isteyen bir ileti kutusu görüntüler. Bu ileti kutusu pasif ve pasif olmayan modda aynı şekilde davranır.|
|**/uninstall**|Yeniden dağıtılabilir .NET Framework kaldırır.|

### <a name="supported-languages"></a>Desteklenen diller

Aşağıdaki tabloda, .NET Framework 4,5 ve sonraki sürümleri için kullanılabilen dil paketleri listelenmektedir .NET Framework.

|LCID|Dil – ülke/bölge|Kültür|
|----------|--------------------------------|-------------|
|1025|Arapça-Suudi Arabistan|Ar|
|1028|Çince – Geleneksel|zh-Hant|
|1029|Çekçe|'ye|
|1030|Danca|da|
|1031|Almanca – Almanya|de|
|1032|Yunanca|seri|
|1035|Fince|Fi|
|1036|Fransızca – Fransa|kesir|
|1037|İbranice|LIP|
|1038|Macarca|Hu|
|1040|İtalyanca – Italya|içerdiği|
|1041|Japonca|Sofya|
|1042|Korece|dili|
|1043|Felemenkçe – Hollanda|nl|
|1044|Norveççe (Bokmål)|hayır|
|1045|Lehçe|pl|
|1046|Portekizce – Brezilya|pt-BR|
|1049|Rusça|ru|
|1053|İsveççe|sv|
|1055|Türkçe|tr|
|2052|Çince – Basitleştirilmiş|zh-Hans|
|2070|Portekizce – Portekiz|pt-PT|
|3082|İspanyolca-Ispanya (modern sıralama)|es|

## <a name="see-also"></a>Ayrıca bkz.

- [Yöneticiler için Dağıtım Kılavuzu](guide-for-administrators.md)
- [Sistem Gereksinimleri](../get-started/system-requirements.md)
- [Geliştiriciler için .NET Framework yüklemesi](../install/guide-for-developers.md)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../install/troubleshoot-blocked-installations-and-uninstallations.md)
- [.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma](reducing-system-restarts.md)
- [Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](how-to-get-progress-from-the-dotnet-installer.md)
