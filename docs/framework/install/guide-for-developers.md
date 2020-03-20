---
title: .NET Framework geliştirici paketini veya yeniden dağıtılabilir
description: Geliştiriciler .NET Framework geliştirici paketini ve hedefleme paketini indirebilir ve yükleyebilir. .NET Framework'ün uygulamalarınızla yeniden dağıtılabilir'i ekleyebilirsiniz.
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- .NET Framework redistributable package, downloading
- .NET Framework, installing
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: daf9d9d5-84ac-4bd9-a864-27665ffd0f5c
ms.openlocfilehash: 0a099c5fb0492cd6cb9fd02e2c2ee1af63e7166e
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507002"
---
# <a name="install-the-net-framework-for-developers"></a>Geliştiriciler için .NET Framework'u yükleyin

.NET, Windows'ta çalışan birçok uygulamanın ayrılmaz bir parçasıdır ve bu uygulamaların çalışması için ortak işlevsellik sağlar. Geliştiriciler için .NET Framework, görsel olarak çarpıcı kullanıcı deneyimleri ve sorunsuz ve güvenli iletişim içeren uygulamalar oluşturmak için kapsamlı ve tutarlı bir programlama modeli sağlar.

> [!NOTE]
> Bu konu, .NET Framework'u kendi sistemine yüklemek isteyen veya uygulamalarıyla birlikte yüklemek isteyen **geliştiriciler** için tasarlanmıştır. .NET Framework'u yüklemek isteyen **kullanıcılar** için ,.NET Framework'ün [windows 10 ve Windows Server 2016'ya yükleme](on-windows-10.md)gibi belirli işletim sistemlerine .NET Framework'ün yüklenmesini tartışan tek tek konulara bakın.

Bu makalede, .NET Framework 4.5'ten .NET Framework 4.8'e kadar .NET Framework 4.8'in tüm sürümlerini bilgisayarınıza yüklemek için bağlantılar sağlamaktadır. Geliştiriciyseniz, .NET Framework'ü uygulamalarınız ile indirmek ve yeniden dağıtmak için bu bağlantıları da kullanabilirsiniz. .NET Framework'ün bir sürümünü uygulamanızla dağıtma hakkında daha fazla bilgi için [geliştiriciler için .NET Framework dağıtım kılavuzuna](../deployment/deployment-guide-for-developers.md)bakın.

[!INCLUDE[net-framework-4-versions](../../../includes/net-framework-4x-versions.md)]

.NET Framework sürümleri ve bilgisayarda hangi sürümlerin yüklü olduğunu nasıl belirleyebileceğiniz hakkında daha [How to: Determine Which .NET Framework Versions Are Installed](../migration-guide/how-to-determine-which-versions-are-installed.md)fazla bilgi için, [bkz.](../migration-guide/versions-and-dependencies.md)

> [!NOTE]
> .NET Framework 3.5 hakkında daha fazla bilgi için windows [10, Windows 8.1 ve Windows 8'de .NET Framework 3.5'i yükleyin.](dotnet-35-windows-10.md)

Hızlı bağlantılar için aşağıdaki tabloyu kullanın veya ayrıntılar için daha fazla bilgi edinin. Kurulumdan önce .NET Framework için sistem gereksinimlerini görüntülemek için [Sistem Gereksinimleri'ne](../get-started/system-requirements.md)bakın. Sorun giderme yle ilgili yardım için [Sorun Giderme'ye](troubleshoot-blocked-installations-and-uninstallations.md)bakın.

| .NET Framework sürümü | Yükleyici (Geliştirici Paketi ve Çalışma Süresi) | Platform desteği |
| ---------------------- | -------------------------------------- | ---------------- |
|**4.8**   | [.NET Çerçeve 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)    | **Dahil:**<br/><br/>Windows 10 Mayıs 2019 Güncelleştirmesi<br/>[Visual Studio 2019 (16.3 güncelleme)](https://my.visualstudio.com/Downloads?q=visual%20studio%202017)<br/><br/> **Yükleyebilirsiniz:**<br/><br/>Windows 10 Ekim 2018 Güncellemesi<br/>Windows 10 Nisan 2018 Güncelleştirmesi<br/>Windows 10 Fall Creators Update<br/>Windows 10 Creators Update <br /> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve daha önceki<br /> Windows Server 2019<br/>Windows Server, Sürüm 1809<br/>Windows Server, Sürüm 1803<br /><br/> (tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)||
|**4.7.2** | [.NET Çerçeve 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472) | **Dahil:** <br/><br/>Windows 10 Ekim 2018 Güncellemesi<br/>Windows 10 Nisan 2018 Güncelleştirmesi<br/>Windows Server 2019<br/>Windows Server, Sürüm 1809<br/>Windows Server, Sürüm 1803<br/>[Visual Studio 2017 (15.8 güncelleme)](https://my.visualstudio.com/Downloads?q=visual%20studio%202017)<br/><br/> **Yükleyebilirsiniz:**<br/> <br/>Windows 10 Fall Creators Update<br/>Windows 10 Creators Update <br /> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve daha önceki<br /> Windows Server, sürüm 1709 ve önceki<br /><br/> (tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)||
|**4.7.1** | [.NET Çerçeve 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471) | **Dahil:** <br/><br/>Windows 10 Fall Creators Update<br/>Windows Server, sürüm 1709<br/>[Visual Studio 2017 (15.5 güncelleme)](https://my.visualstudio.com/Downloads?q=visual%20studio%202017)<br/><br/> **Yükleyebilirsiniz:**<br/><br/> Windows 10 Creators Update <br /> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve daha önceki<br /> Windows Server 2016 ve önceki<br /> (tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)||
|**4.7**   | [.NET Çerçeve 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)    | **Dahil:** <br/><br/>Windows 10 Creators Update<br/>[Visual Studio 2017 (15.3 güncelleme)](https://my.visualstudio.com/Downloads?q=visual%20studio%202017)<br/><br/> **Yükleyebilirsiniz:**<br /><br/> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve daha önceki<br /> Windows Server 2016 ve önceki<br /> (tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)||
|**4.6.2** | [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462) | **Dahil:** <br/><br/>Windows 10 Yıldönümü Güncelleştirmesi<br /><br /> **Yükleyebilirsiniz:**<br /><br/> Windows 10 Kasım Güncellemesi <br/> Windows 10 <br /> Windows 8.1 ve daha önceki<br /> Windows Server 2012 R2 ve önceki<br /> (tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)|
|**4.6.1** | [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461) | **Dahil:** <br/><br/>[Visual Studio 2015 Güncelleme 2](https://my.visualstudio.com/Downloads?q=visual%20studio%202015)<br/><br/>**Yükleyebilirsiniz:**<br /><br/> Windows 10 <br /> Windows 8.1 ve daha önceki<br /> Windows Server 2012 R2 ve önceki<br /> (tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)|
|**4.6**   | [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)    | **Dahil:** <br/><br/> Windows 10 <br />[Visual Studio 2015](https://my.visualstudio.com/Downloads?q=visual%20studio%202015)<br /><br /> **Yükleyebilirsiniz:**<br /><br/> Windows 8.1 ve daha önceki<br /> Windows Server 2012 R2 ve önceki<br /> (tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)|
|**4.5.2** | [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452) | **Yükleyebilirsiniz:**<br/><br/> Windows 8.1 ve daha önceki<br /> Windows Server 2012 R2 ve önceki<br /> (tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)|
|**4.5.1** | [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451) | **Dahil:**<br/><br/>Windows 8.1<br /> Windows Server 2012 R2<br /> [Görsel Stüdyo 2013](https://my.visualstudio.com/Downloads?q=visual%20studio%202013)<br /><br /> **Yükleyebilirsiniz:**<br /><br/> Windows 8 ve önceki<br /> Windows Server 2012 ve önceki<br />(tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)|
|**4.5**   | [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)    | **Dahil:** <br/><br/>Windows 8<br /> Windows Server 2012<br /> [Visual Studio 2012](https://my.visualstudio.com/Downloads?q=visual%20studio%202012)<br /><br /> **Yükleyebilirsiniz:**<br/><br /> Windows 7 ve önceki<br /> Windows Server 2008 SP2 ve daha önce<br />(tam liste için [sistem gereksinimlerine](../get-started/system-requirements.md)bakın)|

**Geliştirici Paketini** ,.NET Framework'ün belirli bir sürümü için, varsa, desteklenen tüm platformlara yükleyebilirsiniz.

Web veya **Çevrimdışı yükleyiciyi** şu üzerine yükleyebilirsiniz:

- Windows 8.1 ve daha önceki

- Windows Server 2012 R2 ve önceki

Tam liste için [Sistem Gereksinimleri'ne](../get-started/system-requirements.md)bakın.

Hem kullanıcılar hem de geliştiriciler için .NET Framework'e genel bir giriş için [başlarken](../get-started/index.md)bkz. .NET Framework'ün uygulamanızla dağıtımı hakkında bilgi için [dağıtım kılavuzuna](../deployment/deployment-guide-for-developers.md)bakın. .NET Framework'ün mimarisi ve temel özellikleri hakkında bilgi almak için [genel bakışa](../get-started/overview.md)bakın.

## <a name="installation-choices"></a>Yükleme seçenekleri

Visual Studio'da veya başka bir geliştirme ortamında .NET Framework'ün en son sürümüne karşı geliştirmek için bir geliştirici hedefleme paketi yükleyin veya uygulamanız veya denetiminiz ile dağıtım için yeniden dağıtılabilir .NET Framework'ü indirin.

### <a name="to-install-the-net-framework-developer-pack-or-targeting-pack"></a>.NET Framework Developer Pack veya Hedefleme Paketini yüklemek için

*Hedefleme paketi,* Visual Studio ve diğer bazı geliştirme ortamlarında geliştirirken uygulamanızın .NET Framework'ün belirli bir sürümünü hedeflemesini sağlar. Geliştirici *paketi,* .NET Framework ve beraberindeki SDK'nın belirli bir sürümünü ve ilgili hedefleme paketini içerir.

.NET Framework 4.5.1 veya 4.5.2 için geliştirici paketi, .NET Framework 4.6 için hedefleme paketi ve .NET Framework 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8 için geliştirici paketi, referans derlemelerinin belirli bir .NET Framework sürümünü, dilini sağlar paketleri ve Visual Studio gibi entegre bir geliştirme ortamında kullanılmak üzere IntelliSense dosyaları.  Visual Studio kullanıyorsanız, geliştirici paketi veya hedefleme paketi, yeni bir proje oluştururken hedef seçimlere .NET Framework'ün yüklü sürümünü de ekler.  Aşağıdakilerden birini seçin:

- [.NET Çerçeve 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Çerçeve 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Çerçeve 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Çerçeve 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452) sürüm 4.5.2'yi Windows 8.1 veya önceki sürümlere, Visual Studio 2013'e, Visual Studio 2012'ye veya diğer IDA'lara yüklemek için.
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451) Visual Studio 2012 veya diğer IDA'lara sürüm 4.5.1 yüklemek için.

Geliştirici paketi indirme sayfasından **İndir'i**seçin. Sonra **Çalıştır** veya **Kaydet'i**seçin ve istendiğinde yönergeleri izleyin. Aşağıdaki şekilde gösterdiği gibi, Visual Studio Yükleyici'deki **.NET masaüstü geliştirme** iş yükündeki isteğe bağlı bileşenlerden seçerek geliştirici paketini veya hedefleme paketini .NET Framework'ün belirli bir sürümü için de yükleyebilirsiniz.

   ![.NET masaüstü geliştirme iş yükü ile Visual Studio Yükleyici](./media/visual-studio-installer.jpg)

.NET Framework'ün belirli bir sürümünü hedeflediğinizde, uygulamanız bu sürümün geliştirici paketine dahil olan başvuru derlemeleri kullanılarak oluşturulur. Çalışma zamanında, derlemeler Genel Derleme Önbelleğinden çözülür ve başvuru derlemeleri kullanılmaz.

Visual Studio'dan bir uygulama oluştururken veya komut satırından MSBuild kullanırken, MSBuild hata MSB3644 görüntüleyebilir, "Çerçeve için referans derlemeleri "*framework-version*" bulunamadı." Hatayı gidermek için geliştirici paketini veya .NET Framework'ün bu sürümü için hedefleme paketini indirin.

### <a name="to-install-or-download-the-net-framework-redistributable"></a>.NET Framework yeniden dağıtılabilir'i yüklemek veya indirmek için

Yükleyiciler,.NET Framework'ün bu sürümlerini hedefleyen bir uygulama veya denetim için .NET Framework bileşenlerini indirir. Bu bileşenler, uygulamanın veya denetimin çalıştığı her bilgisayara yüklenmelidir. Bu yükleyiciler yeniden dağıtılabilir, böylece bunları uygulamanızın kurulum programına ekleyebilirsiniz.

İndirme sayfası çeşitli dillerde sağlanır, ancak indirmelerin çoğu yalnızca İngilizce olarak sağlanır. Ek dil desteği için bir dil paketi yüklemeniz gerekir.

Yeniden dağıtılabilir yükleyiciler iki tür kullanılabilir:

- **Web yükleyici** (web bootstrapper) gerekli bileşenleri ve web'den yükleme bilgisayarın işletim sistemi eşleşen dil paketi indirir. Bu paket çevrimdışı yükleyiciden çok daha küçüktür, ancak tutarlı bir Internet bağlantısı gerektirir. Ek dil desteği yüklemek için [bağımsız dil paketlerini](#to-install-language-packs) indirebilirsiniz.

- **Çevrimdışı yükleyici** (bağımsız yeniden dağıtılabilir) .NET Framework'ü yüklemek için gerekli tüm bileşenleri içerir, ancak dil paketleri içermez. Bu indirme web yükleyicisinden daha büyüktür. Çevrimdışı yükleyici Internet bağlantısı gerektirmez. Çevrimdışı yükleyiciyi çalıştırdıktan sonra, dil desteğini yüklemek için [bağımsız dil paketlerini](#to-install-language-packs) indirebilirsiniz. Tutarlı bir Internet bağlantısına güvenmiyorsanız çevrimdışı yükleyiciyi kullanın.

Hem web hem de çevrimdışı yükleyiciler x86 tabanlı ve x64 tabanlı bilgisayarlar için tasarlanmıştır [(sistem gereksinimlerine](../get-started/system-requirements.md)bakın), ancak Itanium tabanlı bilgisayarları desteklemez.

1. Yüklemek istediğiniz .NET Framework sürümünün indirme sayfasını açın:

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

1. İndirme sayfasının dilini seçin. Bu seçenek .NET Framework'ün yerelleştirilmiş kaynaklarını karşıdan yüklemez; yalnızca indirme sayfasında görüntülenen metni etkiler.

1. **İndir'i**seçin.

1. İstenirse, sistem mimarinizle eşleşen karşıdan yüklemeyi seçin ve sonra **İleri'yi**seçin.

1. İndirme istemi görüntülendiğinde aşağıdakilerden **birini** yapın:

   - .NET Framework'u bilgisayarınıza yüklemek istiyorsanız Çalıştır'ı **seçin**ve ardından ekranınızdaki istemleri izleyin.

   - Yeniden dağıtım için .NET Framework'ü indirmek istiyorsanız **Kaydet'i**seçin ve ardından ekranınızdaki istemleri izleyin.

1. Ek diller için kaynak indirmek istiyorsanız, bir veya daha fazla dil paketi yüklemek için sonraki bölümdeki yönergeleri izleyin.

> [!NOTE]
> Yükleme sırasında herhangi bir sorunla karşılaşırsanız, [Sorun Giderme'ye](troubleshoot-blocked-installations-and-uninstallations.md)bakın.

**Yükleme notları:**

- .NET Framework 4.5 ve sonraki sürümler .NET Framework 4.0'ın yerini alır. Bu sürümleri .NET Framework 4 yüklü bir sisteme yüklediğinizde, derlemeler değiştirilir.

- .NET Framework 4.5 veya sonraki sürümlerini kaldırmak da önceden varolan .NET Framework 4 dosyalarını kaldırır. .NET Framework 4'e geri dönmek istiyorsanız, yeniden yüklemeniz ve güncellemeler yapmak gerekir. Bkz. [.NET Framework 4'ün yüklenmesi](https://go.microsoft.com/fwlink/p/?LinkId=230665).

- .NET Framework 4.5 veya sonraki sürümlerini yüklemek için yönetim kimlik bilgilerine sahip olmalısınız.

- .NET Framework 4.5 yeniden dağıtılabilir 9 Ekim 2012 tarihinde dijital bir sertifikaüzerinde yanlış bir zaman damgası ile ilgili bir sorunu düzeltmek için güncellendi, hangi üretilen ve Microsoft tarafından imzalanan dosyalarda dijital imza erken süresi dolmasına neden oldu. 16 Ağustos 2012 tarihli .NET Framework 4.5 yeniden dağıtılabilir paketini daha önce yüklediyseniz, kopyanızı [.NET Framework indirme sayfasından](https://dotnet.microsoft.com/download/dotnet-framework/net45)en son dağıtılabilir paketle güncellemenizi öneririz. Bu sorun hakkında daha fazla bilgi için [Microsoft Security Advisory 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655) ve [Bilgi Bankası makale 2770445'e](https://support.microsoft.com/kb/2770445)bakın.

## <a name="to-install-language-packs"></a>Dil paketlerini yüklemek için

Dil paketleri, desteklenen diller için yerelleştirilmiş kaynakları (çevrilmiş hata iletileri ve Kullanıcı Arabirimi metni gibi) içeren yürütülebilir dosyalardır. Bir dil paketi yüklemezseniz, .NET Framework hata iletileri ve diğer metinler İngilizce olarak görüntülenir.  Web yükleyicinin işletim sisteminizle eşleşen dil paketini otomatik olarak yüklediğini, ancak bilgisayarınıza ek dil paketleri indirebileceğinizi unutmayın. Çevrimdışı yükleyiciler herhangi bir dil paketi içermez.

> [!IMPORTANT]
> Dil paketleri bir uygulamayı çalıştırmak için gereken .NET Framework bileşenlerini içermez, bu nedenle bir dil paketi yüklemeden önce web veya çevrimdışı yükleyiciyi çalıştırmanız gerekir. Bir dil paketini zaten yüklediyseniz, kaldırın, .NET Framework'e yükleyin ve ardından dil paketini yeniden yükleyin.

1. Yüklediğiniz .NET Framework sürümü için dil paketi indirme sayfasını açın:

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

2. Dil listesinde, indirmek istediğiniz dili seçin ve sayfanın bu dilde yeniden yüklenmesi için birkaç saniye bekleyin.

3. **İndir'i**seçin.

Aşağıdaki tabloda desteklenen diller listelenir.

| Dil              | Kültür |
| --------------------- | :-----: |
| Arapça                | Ar      |
| Çekçe                 | Cs      |
| Danca                | Savcı      |
| Felemenkçe                 | Nl      |
| Fince               | ﬁ      |
| İngilizce (ABD)         | tr-TR   |
| Fransızca                | Fr      |
| Almanca                | de      |
| Yunanca                 | El      |
| İbranice                | Hge      |
| Macarca             | Hu      |
| İtalyanca               | bu      |
| Japonca              | Ja      |
| Korece                | ko      |
| Norveççe             | hayır      |
| Lehçe                | Pl      |
| Portekizce (Brezilya)   | pt-BR   |
| Portekizce (Portekiz) | pt-PT   |
| Rusça               | Ru      |
| Basitleştirilmiş Çince    | zh-CHS  |
| İspanyolca               | es      |
| İsveççe               | Sv      |
| Geleneksel Çince   | zh-CHT  |
| Türkçe               | tr      |

## <a name="next-steps"></a>Sonraki adımlar

- .NET Framework'de yeniyseniz, önemli kavramlara ve bileşenlere giriş için [genel bakışa](../get-started/overview.md) bakın.

- .NET Framework 4.5 ve sonraki tüm sürümlerde yeni özellikler ve geliştirmeler için [what's New 's](../whats-new/index.md).

- .NET Framework'ün uygulamanızla dağıtımı hakkında ayrıntılı bilgi için [Geliştiriciler için Dağıtım Kılavuzu'na](../deployment/deployment-guide-for-developers.md)bakın.

- .NET Framework'ün uygulamanızla dağıtımını etkileyen değişiklikler için [bkz.](../deployment/reducing-system-restarts.md)

- Uygulamanızı .NET Framework 4'ten .NET Framework 4.5 veya daha sonraki sürümlere geçirme hakkında bilgi için [geçiş kılavuzuna](../migration-guide/index.md)bakın.

- .NET Framework kaynak koduna çevrimiçi göz atmak için [.NET Framework Referans Kaynağı'na](https://referencesource.microsoft.com/) bakın. Referans kaynağı [github'da](https://github.com/Microsoft/referencesource)da mevcuttur. Hata ayıklama sırasında başvuru kaynağını çevrimdışı görüntüleme için [indirebilir](https://referencesource.microsoft.com/download.html) ve kaynaklara (düzeltme ekindeki düzeltme ekine ve güncelleştirmeler dahil) adım atabilirsiniz. Daha fazla bilgi için blog girişine bakın [.NET Referans Kaynağı için yeni bir görünüm.](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/)

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için Dağıtım Kılavuzu](../deployment/deployment-guide-for-developers.md)
- [Yöneticiler için Dağıtım Kılavuzu](../deployment/guide-for-administrators.md)
- [Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme](dotnet-35-windows-10.md)
- [Sorun Giderme Engellendi .NET Çerçeve Kurulumları ve Kurulumları Kaldırma](troubleshoot-blocked-installations-and-uninstallations.md)
