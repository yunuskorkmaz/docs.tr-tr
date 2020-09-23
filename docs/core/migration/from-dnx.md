---
title: DNX 'ten .NET Core CLI geçirme
description: DNX Araçları ' i kullanarak .NET Core CLI Araçları ' na geçirin.
ms.date: 06/20/2016
ms.openlocfilehash: e5ebbab2551cf750a5b1136e7b1d4b67816c3b03
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071124"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>DNX 'ten .NET Core CLI geçirme (project.jsaçık)

## <a name="overview"></a>Genel Bakış

.NET Core 'un RC1 sürümü ve ASP.NET Core 1,0 DNX araçları 'nı kullanıma sunmuştur. .NET Core ve ASP.NET Core 1,0 'nin RC2 sürümü DNX 'ten .NET Core CLI taşındı.

Küçük bir yenileyici olarak DNX 'in hangi amaçla olduğunu görelim. DNX, .NET Core ve daha özel olarak ASP.NET Core 1,0 uygulamaları oluşturmak için kullanılan bir çalışma zamanı ve bir araç takımıdır. 3 ana parçadan oluşur:

1. DNVM-DNX elde etmek için bir Install betiği
2. DNX (DotNet yürütme çalışma zamanı)-kodunuzu yürüten çalışma zamanı
3. DNU (DotNet geliştirici yardımcı programı)-bağımlılıkları yönetmek, uygulamalarınızı oluşturmak ve yayımlamak için araç

CLı 'nin tanıtılmasıyla birlikte yukarıdaki tüm bunlar artık tek bir araç takımının parçasıdır. Ancak DNX, RC1 zaman diliminde kullanıma sunulduğundan, yeni CLı araçlarına taşımak istediğiniz tarafından oluşturulan projelere sahip olabilirsiniz.

Bu geçiş kılavuzu, projelerin DNX ve .NET Core CLI üzerine nasıl geçirileceğiyle ilgili temel bilgileri kapsar. Yalnızca .NET Core üzerinde bir projeyi sıfırdan başlatıyorsanız, bu belgeyi serbestçe atlayabilirsiniz.

## <a name="main-changes-in-the-tooling"></a>Araçdaki ana değişiklikler

Araç üzerinde ilk olarak özetlenen bazı genel değişiklikler vardır.

### <a name="no-more-dnvm"></a>Başka DNVM yok

DNVM, *DotNet sürüm Yöneticisi* için Short, makinenizde DNX yüklemek için kullanılan bir bash/PowerShell betiğiydi. Kullanıcıların, belirtilen oturum için $PATH, belirli bir DNX "etkin" olarak işaretleneceği (veya varsayılan olarak) akışların gereksinim duyduğu DNX 'i almasını ve bu dosyayı verilen oturum için yerleştirmesine yardımcı olur. Bu, çeşitli araçları kullanmanıza olanak sağlar.

DNVM, özellik kümesi .NET Core CLI gelen değişiklikler tarafından yedekli şekilde yapıldığı için kullanımdan kaldırıldı.

CLı iki ana şekilde paketlenmiş olarak sunulur:

1. Belirli bir platform için yerel yükleyiciler
2. Diğer durumlar için betiği (CI sunucuları gibi) yükler

Bu, DNVM yüklemesi özellikleri gerekli değildir. Çalışma zamanı seçim özellikleriyle ilgili ne var?

`project.json`Bağımlılıklarınız için belirli bir sürümün paketini ekleyerek içindeki bir çalışma zamanına başvurabilirsiniz. Bu değişiklik ile, uygulamanız yeni çalışma zamanı bitlerini kullanabilir. Bu bitlerin makinenize alınması CLı ile aynıdır: çalışma zamanını, desteklediği yerel yükleyicilerden biri aracılığıyla veya yükleme betiği aracılığıyla yüklersiniz.

### <a name="different-commands"></a>Farklı komutlar

DNX kullanıyorsanız, üç parçadan (DNX, DNU veya DNVM) birindeki bazı komutları kullandınız. CLı ile bu komutlardan bazıları değişmez ve bazıları aynı ancak biraz farklı semantiklerdir.

Aşağıdaki tabloda DNX/DNU komutları ve CLı karşılıkları arasındaki eşleme gösterilmektedir.

| DNX komutu                    | CLı komutu    | Description                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| DNX çalıştırma                        | `dotnet run`     | Kaynaktaki kodu çalıştırın.                                                                                           |
| dnu derlemesi                      | `dotnet build`   | Kodunuzun bir Il ikilisini oluşturun.                                                                                |
| dnu paketi                       | `dotnet pack`    | Kodunuzun NuGet paketini paketleyin.                                                                        |
| DNX \[ komutu] (örneğin, "DNX Web") | Yok\*          | DNX Dünyası ' de, üzerinde project.jstanımlandığı şekilde bir komut çalıştırın.                                                     |
| dnu yüklemesi                    | Yok\*          | DNX dünyasında, bir paketi bağımlılık olarak yükler.                                                            |
| dnu geri yükleme                    | `dotnet restore` | Üzerinde project.jsbelirtilen bağımlılıkları geri yükleyin. ([bkz. nota bakın](#dotnet-restore-note))                                                            |
| dnu yayımlama                    | `dotnet publish` | Uygulamanızı üç formdan birinde dağıtım için yayımlayın (taşınabilir, yerel ve tek başına taşınabilir). |
| dnu kaydırması                       | Yok\*          | DNX Dünyası ' de bir project.jscsproj içinde sarın.                                                                    |
| dnu komutları                   | Yok\*          | DNX dünyasında, genel olarak yüklenen komutları yönetin.                                                           |

( \* )-Bu özellikler, tasarıma göre CLI 'da desteklenmez.

## <a name="dnx-features-that-are-not-supported"></a>Desteklenmeyen DNX özellikleri

Yukarıdaki tabloda gösterildiği gibi, DNX dünyasının, CLı 'de desteklememeye karar verdiğimiz ve en azından süresi için olan özellikler vardır. Bu bölüm, en önemli olanlarından ilerleyenler ve ayrıca, daha sonra ihtiyaç duymaları durumunda bunları desteklememe ve geçici çözümler özetler.

### <a name="global-commands"></a>Genel komutlar

DNU, "genel komutlar" adlı bir kavram ile geldi. Bunlar temelde, uygulamayı çalıştırmak için belirttiğiniz DNX 'i çağıran bir kabuk betiği ile NuGet paketleri olarak paketlenmiş konsol uygulamatı.

CLı bu kavramı desteklemez. Ancak, tanıdık sözdizimi kullanılarak çağrılabilecek proje başına komutları ekleme kavramını destekler `dotnet <command>` .

### <a name="installing-dependencies"></a>Bağımlılıklar yükleniyor

V1 itibariyle, .NET Core CLI `install` bağımlılıkları yüklemek için bir komuta sahip değildir. NuGet 'den bir paket yüklemek için, dosyayı dosyanıza bir bağımlılık olarak eklemeniz `project.json` ve ardından çalıştırmanız gerekir `dotnet restore` ([bkz. Note](#dotnet-restore-note)).

### <a name="running-your-code"></a>Kodunuzu çalıştırma

Kodunuzu çalıştırmanın iki ana yolu vardır. Bunlardan biri, ile kaynağıdır `dotnet run` . Aksine `dnx run` , bu, bellek içi derleme kullanmaz. Gerçekten `dotnet build` kodunuzu derlemek ve sonra oluşturulan ikiliyi çalıştırmak için çağırır.

`dotnet`Kodunuzu çalıştırmak için kendisini başka bir şekilde kullanmaktır. Bu, derlemenizin bir yolu sağlanarak yapılır: `dotnet path/to/an/assembly.dll` .

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>DNX projenizi .NET Core CLI geçirme

Kodunuzla çalışırken yeni komutların kullanılmasına ek olarak, DNX 'ten geçiş sırasında kalan üç önemli nokta vardır:

1. `global.json`CLI kullanabilmeniz için dosyayı geçirin.
2. Proje dosyasını ( `project.json` ) CLI araçlarına geçirme.
3. Herhangi bir DNX API 'sini BCL karşılıklarına geçirme.

### <a name="changing-the-globaljson-file"></a>Dosyadaki global.jsdeğiştirme

`global.json`Dosya, hem RC1 hem de RC2 (veya üzeri) projeleri için bir çözüm dosyası gibi davranır. RC1 ve sonraki sürümleri birbirinden ayırt etmek için .NET Core CLI (ve Visual Studio 'Nun yanı sıra) için, `"sdk": { "version" }` Bu özelliği kullanan PROJENIN RC1 veya sonraki sürümlerini kullanmasını sağlayabilirsiniz. `global.json`Bu düğüm hiç yoksa, en son olarak kabul edilir.

Dosyayı güncelleştirmek için `global.json` , özelliği kaldırın ya da kullanmak istediğiniz araçların tam sürümüne ayarlayın, bu örnekte **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Proje dosyası geçiriliyor

CLı ve DNX, her ikisi de dosya tabanlı aynı temel proje sistemini kullanır `project.json` . Proje dosyasının sözdizimi ve semantiği, senaryolara bağlı olarak küçük farklılıklar sayesinde oldukça kolaydır. Şemada, [şema dosyasında](http://json.schemastore.org/project)görebileceğiniz bazı değişiklikler de vardır.

Bir konsol uygulaması oluşturuyorsanız, proje dosyanıza aşağıdaki kod parçacığını eklemeniz gerekir:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Bu `dotnet build` , uygulamanız için bir giriş noktası yayma, kodunuzu etkin bir şekilde yapmaya olanak verir. Bir sınıf kitaplığı oluşturuyorsanız yukarıdaki bölümü atlayabilirsiniz. Kuşkusuz, dosyanıza Yukarıdaki kod parçacığını ekledikten sonra `project.json` bir statik giriş noktası eklemeniz gerekir. Taşınma DNX ' i ile, sağlanan dı Hizmetleri artık kullanılabilir değildir ve bu nedenle, bu, temel bir .NET giriş noktası olması gerekir: `static void Main()` .

Uygulamanızda bir "komutlar" bölümü varsa `project.json` , bunu kaldırabilirsiniz. Entity Framework CLı komutları gibi DNU komutlarına sahip olmak için kullanılan komutlardan bazıları, CLı 'ye proje başına uzantılar olarak yönlendirilmekte. Projelerinizde kullandığınız komutları kullandıysanız, bunları CLı uzantıları ile değiştirmeniz gerekir. Bu durumda, `commands` içindeki düğümün `project.json` düğüm tarafından değiştirililmesi `tools` ve araç bağımlılıklarını listemeleri gerekir.

Bu işlemler yapıldıktan sonra, uygulamanız için istediğiniz taşınabilirlik türünü belirlemeniz gerekir. .NET Core ile, aralarından seçim yapabileceğiniz bir taşınabilirlik seçenekleri yelpazesi sunduğumuz için yatırım yaptık. Örneğin, tam olarak *Taşınabilir* bir uygulamaya sahip olmak veya *kendi içinde* olan bir uygulamaya sahip olmak isteyebilirsiniz. Taşınabilir uygulama seçeneği .NET Framework uygulamaların çalışması gibidir: Bu, hedef makinede (.NET Core), paylaşılan bir bileşen tarafından yürütülmesi gerekir. Kendi içinde bulunan uygulama, .NET Core 'un hedefe yüklenmesini gerektirmez, ancak desteklemek istediğiniz her işletim sistemi için bir uygulama oluşturmanız gerekir. Bu taşınabilirlik türleri ve daha fazlası, [uygulama taşınabilirlik türü](../deploying/index.md) belgesinde ele alınmıştır.

İstediğiniz taşınabilirlik türüyle ilgili bir çağrı yaptıktan sonra, hedeflenen çatılarınızı değiştirmeniz gerekir. .NET Core için uygulamalar yazıyorsanız, en büyük olasılıkla `dnxcore50` hedeflenen çatısı olarak kullanmıştı. CLı ve yeni [.NET Standard](../../standard/net-standard.md) getirilen değişiklikler ile, Framework 'ün aşağıdakilerden biri olması gerekir:

1. `netcoreapp1.0` -uygulamaları .NET Core 'a yazıyorsanız (ASP.NET Core uygulamalar dahil)
2. `netstandard1.6` -.NET Core için sınıf kitaplıkları yazıyorsanız

Diğer `dnx` hedefleri kullanıyorsanız, gibi `dnx451` bunları da değiştirmeniz gerekir. `dnx451` olarak değiştirilmelidir `net451` .
Daha fazla bilgi için lütfen [.NET Standard](../../standard/net-standard.md) konusuna bakın.

`project.json`Artık çok daha hazır. Özellikle ASP.NET Core bağımlılıklar kullanıyorsanız, bağımlılıklar listenizi gözden geçirmeniz ve bağımlılıklarını daha yeni sürümlere güncelleştirmeniz gerekir. BCL API 'Leri için ayrı paketler kullanıyorsanız, çalışma zamanı paketini [uygulama taşınabilirlik türü](../deploying/index.md) belgesinde açıklandığı şekilde kullanabilirsiniz.

Başlamaya başladıktan sonra geri yüklemeyi deneyebilirsiniz `dotnet restore` ([bkz. Note](#dotnet-restore-note)). Eğer NuGet, yukarıda hedeflenen çerçevelerden birinin bağımlılıklarını çözümleyemezse, bağımlılıklarınızın sürümüne bağlı olarak hatalarla karşılaşabilirsiniz. Bu, "bir noktadan noktaya" sorunudur; zaman ilerledikçe, bu çerçeveler için daha fazla ve daha fazla pakete destek dahil edilir. Şimdilik, bu, ' de çalıştırırsanız, `imports` `framework` "Imports" ifadesinde çerçeveyi hedefleyen paketleri geri yüklemesini yapmak için düğüm içindeki ifadesini kullanabilirsiniz.
Bu durumda aldığınız geri yükleme hataları, size hangi çerçevelerin içeri aktarılacağını söylemek için yeterli bilgi sağlamalıdır. Bu şekilde biraz kaybedilmişse veya yeni bir kez karşılaşırsanız, genel olarak, `dnxcore50` ve `portable-net45+win8` içinde belirtmek, `imports` el ile yapılmalıdır. Aşağıdaki JSON kod parçacığı şöyle görünür:

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Çalışan son `dotnet build` derleme hatalarını gösterir, ancak bu çok fazla sayıda olabilir. Kodunuz doğru bir şekilde oluşturup çalıştırdıktan sonra, Çalıştırıcısı ile test edebilirsiniz. Yürütün `dotnet <path-to-your-assembly>` ve çalışır şekilde görüntüleyin.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
