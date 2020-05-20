---
title: Masaüstü için .NET Core’da ne gibi yenilikler var?
description: .NET Core, .NET Core ve .NET Framework arasındaki farklar ve eklenen yeni özellikler hakkında bilgi edinin.
ms.date: 05/12/2020
ms.openlocfilehash: 9ec4f3002dc9d9ea80fd2b6db8095930867a5c65
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423266"
---
# <a name="whats-new-with-net-core-for-desktop"></a>Masaüstü için .NET Core’da ne gibi yenilikler var?

.NET Core 3,0 ile başlayarak, .NET Core Windows Forms ve WPF 'yi destekler. Bu nedenle, masaüstü uygulamalarınız için .NET Framework ve .NET Core arasında bir seçeneğiniz vardır. Bu bölümde, .NET Core nedir ve masaüstü uygulamalarına yönelik avantajları açıklanır.

## <a name="the-motivation-behind-net-core"></a>.NET Core arkasındaki mosyon

.NET Framework, 2002 ' de başlatılırken Windows Forms, ASP.NET, Entity Framework, Windows Mağazası ve diğer birçok teknolojiyi desteklemek için yıl içinde gelişmiştir. Bunların hepsi doğası gereği farklıdır. Bu nedenle, Microsoft, .NET Framework parçalarını alarak ve her teknoloji için farklı bir uygulama yığını oluşturarak bu gelişmeye yaklaşmıştı. Bu şekilde, geliştirme özellikleri, her platformun potansiyelini kaplayan belirli bir yığının ihtiyaçları için özelleştirilebilir. Bu, farklı bağımsız takımlar tarafından tutulan .NET Framework sürümleriyle parçalanmaya yol açabilir. Tüm bu yığınların uygulama modeli, çerçeve ve çalışma zamanı içeren ortak bir yapısı vardır, ancak bu bölümlerin her birinin uygulamasında farklılık gösterir.

Bu platformlardan yalnızca birini hedefliyorsanız, bu modeli kullanabilirsiniz. Ancak çoğu durumda, aynı çözümde birden fazla hedef platforma gerek duyabilirsiniz. Örneğin, uygulamanızda bir sunucu üzerinde çalışan arka uç mantığını paylaşan ve hatta bir mobil istemci olan bir masaüstü yönetim parçası olabilir. Bu durumda, tüm bu .NET verticallerine yayılabilen Birleşik bir kodlama deneyimine ihtiyacınız vardır.

Windows 8 ' in piyasaya sürülme zamanına göre, taşınabilir sınıf kitaplıkları (PCLs) kavramı doğuyordu. Başlangıçta .NET Framework, her zaman tek bir birim olarak dağıtılmasının varsayımına göre tasarlandığından, [düzenleme](http://en.wikipedia.org/wiki/Decomposition_(computer_science)) bir sorun olmamıştı. Verticlar arasında kod paylaşımı sorununu çözmek için, itici kuvvet Framework 'ün yeniden nasıl yeniden düzenlenmesi üzerinde oldu. Sözleşmelerin fikri, iyi bir API yüzey alanı sağlamaktır. Sözleşmeler, bunlara göre derleyebileceğiniz derlemelerdir ve bunlar arasındaki bağımlılıklara dikkat etmeniz için uygun düzenleme ile tasarlanmıştır.

Bu, daha önce yaptığımız tek API düzeyinin aksine, derleme düzeyindeki ifade arasındaki API farklılıkları hakkında bilgi almak için yol gösterir. Bu boyut, taşınabilir sınıf kitaplıkları olarak da bilinen birden çok ifade hedefleyebilir bir sınıf kitaplığı deneyimini etkinleştirdi.

![.NET Framework yayın geçmişi](./media/whats-new-dotnet-core/release-history.png)

PCL ile geliştirme deneyimi, API şekline bağlı olarak önem derecesine göre birleştirilmiştir. Ayrıca, farklı verticlar üzerinde çalışan kitaplıklar oluşturmanın en çok yanında da değinilmesi gerekir. Ancak harika bir zorluk vardır: API 'Ler yalnızca uygulama tüm durumlarda ileri doğru taşındığında taşınabilir.

Daha iyi bir yaklaşım, iyi bir şekilde bir görünüm yerine iyi bir şekilde bir uygulama sağlayarak uygulamalar arasındaki uygulamaları birleştirmesidir. Belirli bir bileşene sahip olan her ekibin, en üstte tutarlı bir API yığını daha etkin bir şekilde daha etkin bir şekilde sağlamaya çalışarak API 'Lerinin tüm bölümlerde nasıl çalıştığını düşünmesini istemek çok daha basittir. .NET Standard içinde geldiği yerdir. Sonraki bölümde ayrıntılara bakın.

Diğer bir büyük zorluk .NET Framework nasıl dağıtıldığına yönelik olarak yapılmalıdır. .NET Framework, makine genelindeki bir çerçevedir. Üzerinde yapılan tüm değişiklikler, bağımlılığı alan tüm uygulamaları etkiler. Bu dağıtım modelinde disk alanını azaltma ve hizmetlere merkezi erişim gibi birçok avantaj olsa da, bazı tehliklıklar sunulmaktadır.

İle başlamak için, uygulama geliştiricilerinin son yayınlanan bir çerçeveye bağımlılığı olması zordur. Bu uygulamaların en son işletim sistemi üzerinde bir bağımlılığı olması veya .NET Framework uygulamayla birlikte yükleyen bir uygulama yükleyicisi sağlaması gerekir. Bir Web geliştiricisiyseniz, BT departmanı sunucu tarafından desteklenen sürümü kurarken bile bu seçeneğe sahip olmayabilirsiniz.

.NET Framework kurulumunda zincirine bir yükleyici sağlama sorunu hakkında daha fazla bilgi almak isteseniz bile, .NET Framework yükseltmenin diğer uygulamaları kesintiye uğratabilir olduğunu fark edebilirsiniz.

Framework 'ün geriye dönük uyumlu sürümlerini sağlama çabalarına rağmen, uygulamaları kesintiye uğrabilecek uyumlu değişiklikler vardır. Örneğin, var olan bir türe arabirim eklemek, bu türün serileştirilme şeklini değiştirebilir ve var olan koda bağlı olarak sorun oluşmasına neden olabilir. NET Framework yüklü tabanı çok büyük olduğundan, bu son senaryolara karşı mücadele .NET Framework içindeki yeniliklerin hızını yavaşlatır.

Bu sorunları çözmek için, Microsoft .NET platformunun gelişini benimseme konusunda .NET Core 'u geliştirmiştir.

## <a name="introduction-to-net-core"></a>NET Core’a giriş

.NET Core, Microsoft 'un .NET teknolojisinin modüler, platformlar arası, açık kaynak ve buluta hazırlamış bir platforma gelişmektedir. Windows, macOS ve Linux 'ta, Android ve IoT gibi ARM tabanlı mimarilerde de çalışacak planlarla çalışır.

.NET Core 'un amacı, Windows, platformlar arası ve mobil uygulamalar içeren tüm uygulama türleri için birleştirilmiş bir platform sağlamaktır. [.NET Standard](../../standard/net-standard.md) , her uygulama modeline ihtiyacı olan ve herhangi bir uygulama MODELINE özgü API 'yi dışlayarak paylaşılan temel API 'ler sağlayarak bunu sağlar.

Bu çerçeve, farklı desteklenen platformlarda paketlemeyi ve dağıtımı basitleştirerek, verimlilik ve performans açısından uygulamalara birçok avantaj sağlar.

.NET Core 'un avantajları şu üç özelliklerden gelir:

- **Platformlar arası:** Farklı platformlarda uygulama yürütmeye (Windows, macOS ve Linux) izin verir.
- **Açık Kaynak:** .NET Core platformu, GitHub, saydamlık ve topluluk katkılarına yönelik açık kaynaktır ve GitHub aracılığıyla kullanılabilir.
- **Desteklenen:** Microsoft resmi olarak .NET Core ' u destekler.

.NET Core 3,0 ile başlayarak, mevcut Web ve bulut desteğinin yanı sıra masaüstü, IoT ve AI etki alanları için de destek bulunur. Bu Framework için amaç etkileyici: her türde .NET geliştirmenin ve geleceğin hedeflenecek. Microsoft, 2020 sonunda .NET 5 ile bu vizyona tamamlamayı planlamaktadır. "Çekirdek" adı, .NET dünyasında benzersizliği zorlamak için kaldırılmıştır.

![.NET 5 ' in tüm etki alanları](./media/whats-new-dotnet-core/all-domains-of-dotnet5.png)

## <a name="net-framework-vs-net-core"></a>.NET Framework ve .NET Core karşılaştırması

.NET Core 'un .NET için Microsoft stratejisi içindeki uygunluğunu anladığınıza göre, .NET Framework ne olduğunu merak ediyor olabilirsiniz. Şu şekilde soru sormanız gerekebilir: iptal etmek istiyor musunuz? Kayboluyor mu? .NET Framework bilgisayarımda bulunan uygulamaları modernleştirin için seçimlerim nelerdir?

2019 ' de **.NET Framework-4,8** ' nin son sürümü yayımlandı. Masaüstü uygulamaları için üç önemli geliştirme içerir:

- **Modern tarayıcı ve medya denetimleri**: bugün, .net masaüstü UYGULAMALARı, HTML ve oynatılan medya dosyalarını göstermek Için Internet Explorer ve Windows Media Player kullanır. Bu eski denetimler en son HTML 'yi göstermeyeceği veya en son medya dosyalarını oynadığından, Microsoft Edge ve en son standartları destekleyen yeni medya oynatıcılarından faydalanan yeni denetimler eklenmiştir.
- **UWP denetimlerine erişim**: UWP, en son Windows özellikleri ve dokunmatik ekranların avantajlarından yararlanan yeni denetimler içerir. Bu yeni özellikleri ve denetimleri kullanmak için uygulamalarınızı yeniden yazmanız gerekmez, bu sayede mevcut WPF veya Windows Forms kodunuzda bu yeni özellikleri kullanabilirsiniz.
- **Yüksek DPI iyileştirmeleri**: ekran çözünürlüğü 4k ve 8k çözünürlükleriyle artmaktadır. Bu nedenle, .NET Framework 4,8, mevcut Windows Forms ve WPF uygulamalarınızın bu yeni ekranlarda harika görünebilmesini sağlamak için yeni HDPı iyileştirmeleri ekliyor.

.NET Framework milyonlarca makineye yüklendiğinden, Microsoft bu uygulamayı desteklemeye devam eder, ancak yeni özellikler eklemez.

.NET Core, .NET 'in açık kaynaklı, platformlar arası ve hızlı hareket eden sürümüdür. Yan yana doğası nedeniyle, herhangi bir uygulamayı bozmadan değişiklikler gerçekleştirebilir. Bu, .NET Core 'un .NET Framework zamana göre yeni API 'Leri ve dil özelliklerini alabileceği anlamına gelir. Ayrıca, **.NET Core** zaten .NET Framework için imkansız olan özellikler içerir, örneğin:

- **.NET desteği Windows Forms ve WPF 'Nin yan yana sürümleri**: Bu, makinenin çerçeve sürümü güncelleştirilirken yan etkileri sorunu çözer. .NET Core 'un birden çok sürümü aynı makineye yüklenebilir ve her bir uygulama .NET Core 'un hangi sürümü kullanması gerektiğini belirtir. Daha da fazla, artık .NET Core üzerinde Windows Forms ve WPF geliştirebilir ve çalıştırabilirsiniz.
- **.NET uygulamasını bir uygulamaya doğrudan ekleyin**: .NET Core uygulamasını uygulama paketinizin bir parçası olarak dağıtabilirsiniz. Bu, belirli bir sürümün makinede yüklü olmasını beklemek zorunda kalmadan en son sürüm, özellik ve API 'lerden yararlanmanızı sağlar.
- .NET Core **özelliklerinden yararlanın**: .NET Core, .net 'in hızlı hareket eden, açık kaynaklı bir sürümüdür. Yan yana doğası, yeni yenilikçi API 'Ler ve temel sınıf kitaplıkları (BCL) geliştirmelerinden uyumluluğu ortadan kaldırma riski olmadan hızlı bir şekilde giriş yapmanıza izin vermez. Artık Windows Forms ve WPF uygulamaları, çalışma zamanı performansı, yüksek DPı desteği vb. için daha temel düzeltmeler de dahil olmak üzere en son .NET Core özelliklerinden faydalanabilir.

Microsoft 'un yol haritasını, geliştiricilerin uygulamaları .NET Core 'a ve gelecekte .NET 5 ' e taşımasına yönelik temel bir parçasıdır. Ancak, .NET Framework uygulamalarınız varsa, .NET Core 'a geçmek için önceden sured kullanmamalısınız. .NET Framework tam olarak desteklenecek ve her zaman Windows 'un bir parçası olacaktır. Ancak, gelecekte en yeni dil özelliklerini ve API 'Leri kullanmak istiyorsanız uygulamalarınızı .NET Core 'a taşımanız gerekir.

Yepyeni masaüstü uygulamalarınız için doğrudan .NET Core üzerinde başlamasını öneririz. Hafif ve platformlar arası, yan yana çalışır, yüksek performansa sahiptir ve kapsayıcılara ve mikro hizmet mimarilerine çok uygun hale gelir.

![En son .NET Framework sürümünü kullanarak .NET Framework uygulamalarınızı güncelleştirebilir veya uygulamalarınızı .NET Core 'a bağlayabilirsiniz.](./media/whats-new-dotnet-core/framework-vs-core.png)

## <a name="net-standard-vs-pcl"></a>.NET Standard vs. PCL

[.NET Standard](../../standard/net-standard.md) , tüm .NET uygulamalarında kullanılabilmesi amaçlanan .NET API 'lerinin resmi bir belirtimidir. .NET Standard arkasındaki mosyon, .NET ekosisteminde daha büyük bir birlik oluşturur. .NET Standard, kodunuzun derlenmesi için tek bir sözleşme kümesi oluşturan .NET API 'lerinin bir belirtimidir. Bu sözleşmeler her bir .NET uygulamasında uygulanır ve bu sayede farklı .NET uygulamalarında taşınabilirliği etkinleştirir.

.NET Standard aşağıdaki temel senaryolara izin vermez:

- İş yüküyle bağımsız olarak uygulanacak tüm .NET uygulamaları için tek bir temel sınıf kitaplığı API kümesini tanımlar.
- Geliştiricilerin aynı API kümesi kullanılarak .NET uygulamalarında kullanılabilir olan taşınabilir kitaplıklar oluşturmasını sağlar.

.NET Standard, PCLs 'in evrimi ve aşağıdaki listede .NET Standard ve PCLs arasındaki temel farklılıklar gösterilmektedir:

- .NET Standard, Microsoft tarafından seçilen, seçkin API 'lerin bir kümesidir. PCLs yok.
- PCL içeren API 'Ler, oluşturduğunuzda hedefleyecek şekilde seçtiğiniz platformlara bağımlıdır. Bu, bir PCL 'yi yalnızca seçtiğiniz belirli hedefler için paylaşılabilir hale getirir.
- .NET Standard, platformdan bağımsız olarak, Windows, macOS, Linux gibi her yerde çalışabilir.
- PCLs, platformlar arası de çalıştırılabilir, ancak daha sınırlı bir erişime sahiptir. PCLs yalnızca sınırlı bir platform kümesini hedefleyebilir.

## <a name="new-desktop-features-in-net-core"></a>.NET Core 'da yeni masaüstü özellikleri

### <a name="support-for-windows-forms-and-wpf"></a>Windows Forms ve WPF desteği

Windows Forms ve WPF, sürüm 3,0 ' den beri .NET Core 'un bir parçasıdır. Her iki sunum çerçevesi de yalnızca Windows içindir, bu nedenle platformlar arası değildir. WPF 'yi DirectX üzerinde zengin bir katman olarak düşünebilirsiniz ve GDI+ üzerinde bir THINNER katmanı olarak Windows Forms. WPF ve Windows Forms Windows 'da Masaüstü uygulama işlevlerinin çoğunu gösterme ve sunma konusunda harika bir iş yapın. Bu nedenle Windows Forms ve WPF .NET Core ve .NET Framework için kullanılabilir. Artık .NET Core ' u hedefleyen yeni masaüstü uygulamalarınızı başlatabilir ve mevcut olanları .NET Framework, .NET Core 'a geçirebilirsiniz.

.NET Standard sürüm 2,1 ' in yeni bir sürümü .NET Core 3,0 ile aynı anda yayımlanmıştır. .NET Core 3. x sürümleri, beklendiği gibi .NET Standard 2,1 ve önceki sürümleri destekler.

Ayrıca, .NET Core için hem Windows Forms hem de WPF uygulamalarının açık kaynak olduğunu fark etmek önemlidir.

### <a name="xaml-islands"></a>XAML Adaları

[Xaml Adaları](/windows/apps/desktop/modernize/xaml-islands) , GELIŞTIRICILERIN geçerli WPF, Windows Forms ve yerel Win32 UYGULAMALARıNDA (MFC gibi) yeni Windows 10 DENETIMLERINI (UWP XAML denetimleri) kullanmasına yönelik bir bileşen kümesidir. UWP XAML denetimlerinin "adamı", Win32 uygulamalarınızın içinde olmasını istediğiniz yere sahip olabilirsiniz.

Windows 10, sürüm 1903, Windows işleyicileri (HWnds) kullanarak Win32 Windows 'da UWP XAML içeriğinin barındırılmasına izin veren bir API kümesi kullanıma sunduğundan bu XAML Adaları mümkündür. Yalnızca Windows 10 1903 ve üzeri sürümlerde çalışan uygulamaların XAML Adaları kullanmasını fark edebilirsiniz.

Windows Forms ve WPF geliştiricileri için XAML Adaları oluşturulmasını kolaylaştırmak için, Windows Community Toolkit çeşitli NuGet paketlerinde bir dizi .NET sarmalayıcıda sunar. Sarmalayıcılar sarmalanmış ve barındırma denetimleridir:

- [WebView](/windows/communitytoolkit/controls/wpf-winforms/webview), [WebViewCompatible](/windows/communitytoolkit/controls/wpf-winforms/webviewcompatible), [InkCanvas](/windows/communitytoolkit/controls/wpf-winforms/inkcanvas), [MediaPlayerElement](/windows/communitytoolkit/controls/wpf-winforms/mediaplayerelement)ve [mapcontrol](/windows/communitytoolkit/controls/wpf-winforms/mapcontrol) SARMALANMıŞ denetimleri, bazı UWP xaml DENETIMLERINI Windows Forms veya WPF denetimlerine sarmalayın ve bu geliştiricilerin UWP kavramlarını gizler.
- Windows Forms ve WPF için [Windowsxamlhost](/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost) denetimi, DIĞER KAYDıRıLMıŞ UWP xaml denetimlerinin ve özel denetimlerin xaml Adası içine yüklenemeyeceğini sağlar.

### <a name="access-to-all-windows-10-apis"></a>Tüm Windows 10 API 'Lerine erişim

Windows 10, geliştiricilerin birlikte çalışması için harika bir API miktarına sahiptir. Bu API 'Ler kimlik doğrulaması, Bluetooth, randevular ve kişiler gibi çok çeşitli işlevlere erişim sağlar. Artık bu API 'Ler .NET Core aracılığıyla kullanıma sunulmuştur ve Windows geliştiricilere Windows 10 ' da bulunan özellikleri kullanarak güçlü masaüstleri uygulamaları oluşturma olanağı sunar.

### <a name="side-by-side-support-and-self-contained-exes"></a>Yan yana destek ve kendi içinde bulunan EXEs

.NET Core dağıtım modeli, Windows Masaüstü geliştiricilerin .NET Core ile deneymesinin en büyük avantajlarından biridir. .NET Core 'u genel olarak yükleme yeteneği, .NET Framework Merkezi yükleme ve bakım avantajlarının çoğunu, yerinde güncelleştirmeler gerektirmeksizin sağlar.

Yeni bir .NET Core sürümü yayınlandığında, diğer uygulamaları etkilemenize gerek kalmadan bir makinedeki her uygulamayı dilediğiniz şekilde güncelleştirebilirsiniz. Yeni .NET Core sürümleri kendi dizinlerinde yüklüdür ve birbirleriyle "yan yana" bulunur.

Yalıtım ile dağıtmanız gerekiyorsa, uygulamanızla .NET Core 'u dağıtabilirsiniz. .NET Core, uygulamanızı .NET Core çalışma zamanına tek bir çalıştırılabilirle göre paketleyip.

Bu dağıtım seçenekleri, geliştiriciler tarafından çok uzun süredir istendi, ancak .NET Framework kullanarak elde edilmesi zor. .NET Core tarafından kullanılan modüler mimari, bu esnek dağıtım seçeneklerini mümkün hale getirir.

### <a name="performance"></a>Performans

Başladıktan sonra, Web ve bulut iş yüklerini hedefleyerek, .NET Core 'un DNA 'ye takılmış olması gerekiyordu. Sunucu tarafı kodu, piyasadaki en iyi performans web platformu olarak yüksek eşzamanlılık senaryolarını ve .NET Core puanlarını karşılamak için yeterince performanslı olmalıdır.

Yeni nesil masaüstü uygulamalarınızı oluşturmak için .NET Core kullandığınızda bu performans iyileştirmelerinden yararlanabilirsiniz.

## <a name="benefits-of-open-source"></a>Açık kaynak avantajları

.NET Core 'un açık kaynak olması hakkında yalnızca birkaç sözcük. Platformlar arası yığın oluşturmak, hedeflenen platformların her birinde özelleştirilmiş takımların etkileşimini gerektiren bir karmaşıkdır. Bu çaba, Microsoft 'un içinden ve dışından çok sayıda işbirliği gerektirir. Açık kaynak yaparak ve bu nedenle ortak işbirliğine açık hale getirerek, en üstün çevik geliştirme tarzına sahip olursunuz. bu yana, sorunlar çok büyük ve etkin bir geliştirici topluluğu tarafından algılandığı için kalite çubuğunu oluşturursunuz.

Bu, daha önce bahsedilen yol haritasını hızlandırmaya devam edecek .NET Core 'un önemli bir başarı etkendir: herhangi bir geliştiricinin herhangi bir uygulamayı oluşturmak için gereken tek .NET platformu olması.

>[!div class="step-by-step"]
>[Önceki](why-modern-applications.md) 
> [Sonraki](migrate-modern-applications.md)
