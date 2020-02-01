---
title: DNX 'ten .NET Core CLI geçirme
description: DNX Araçları ' i kullanarak .NET Core CLI Araçları ' na geçirin.
ms.date: 06/20/2016
ms.openlocfilehash: e15e7ce10bb7a36deb2acd2abb9a0bd4ec8cd4a9
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920619"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>DNX 'ten .NET Core CLI 'e geçme (Project. JSON)

## <a name="overview"></a>Genel bakış
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

Bağımlılıklarınız için belirli bir sürümün paketini ekleyerek `project.json` bir çalışma zamanına başvurabilirsiniz. Bu değişiklik ile, uygulamanız yeni çalışma zamanı bitlerini kullanabilir. Bu bitlerin makinenize alınması CLı ile aynıdır: çalışma zamanını, desteklediği yerel yükleyicilerden biri aracılığıyla veya yükleme betiği aracılığıyla yüklersiniz.

### <a name="different-commands"></a>Farklı komutlar
DNX kullanıyorsanız, üç parçadan (DNX, DNU veya DNVM) birindeki bazı komutları kullandınız. CLı ile bu komutlardan bazıları değişmez ve bazıları aynı ancak biraz farklı semantiklerdir.

Aşağıdaki tabloda DNX/DNU komutları ve CLı karşılıkları arasındaki eşleme gösterilmektedir.

| DNX komutu                    | CLı komutu    | Açıklama                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| DNX çalıştırma                        | dotnet run     | Kaynaktaki kodu çalıştırın.                                                                                           |
| dnu derlemesi                      | dotnet build   | Kodunuzun bir Il ikilisini oluşturun.                                                                                |
| dnu paketi                       | dotnet pack    | Kodunuzun NuGet paketini paketleyin.                                                                        |
| DNX \[komutu] (örneğin, "DNX Web") | Yok\*          | DNX dünyasında, Project. JSON içinde tanımlandığı şekilde bir komut çalıştırın.                                                     |
| dnu yüklemesi                    | Yok\*          | DNX dünyasında, bir paketi bağımlılık olarak yükler.                                                            |
| dnu geri yükleme                    | dotnet restore | Project. JSON uygulamanızda belirtilen bağımlılıkları geri yükleyin. ([bkz. nota bakın](#dotnet-restore-note))                                                            |
| dnu yayımlama                    | dotnet publish | Uygulamanızı üç formdan birinde dağıtım için yayımlayın (taşınabilir, yerel ve tek başına taşınabilir). |
| dnu kaydırması                       | Yok\*          | DNX Dünyası ' de bir proje. json ' u csproj içinde sarın.                                                                    |
| dnu komutları                   | Yok\*          | DNX dünyasında, genel olarak yüklenen komutları yönetin.                                                           |

(\*)-Bu özellikler, tasarıma göre CLı 'da desteklenmez.

## <a name="dnx-features-that-are-not-supported"></a>Desteklenmeyen DNX özellikleri
Yukarıdaki tabloda gösterildiği gibi, DNX dünyasının, CLı 'de desteklememeye karar verdiğimiz ve en azından süresi için olan özellikler vardır. Bu bölüm, en önemli olanlarından ilerleyenler ve ayrıca, daha sonra ihtiyaç duymaları durumunda bunları desteklememe ve geçici çözümler özetler.

### <a name="global-commands"></a>Genel komutlar
DNU, "genel komutlar" adlı bir kavram ile geldi. Bunlar temelde, uygulamayı çalıştırmak için belirttiğiniz DNX 'i çağıran bir kabuk betiği ile NuGet paketleri olarak paketlenmiş konsol uygulamatı.

CLı bu kavramı desteklemez. Ancak, tanıdık `dotnet <command>` sözdizimi kullanılarak çağrılabilecek proje başına komutları ekleme kavramını destekler.

### <a name="installing-dependencies"></a>Bağımlılıklar yükleniyor
V1 itibariyle, .NET Core CLI bağımlılıkları yüklemek için bir `install` komutu yoktur. NuGet 'den bir paket yüklemek için, `project.json` dosyanıza bir bağımlılık olarak eklemeniz ve sonra `dotnet restore` çalıştırmanız gerekir ([bkz. Note](#dotnet-restore-note)).

### <a name="running-your-code"></a>Kodunuzu çalıştırma
Kodunuzu çalıştırmanın iki ana yolu vardır. Biri kaynaktan, `dotnet run`. `dnx run`aksine, bu, bellek içi derleme kullanmaz. Kodu oluşturmak için gerçekten `dotnet build` çağırır ve sonra oluşturulan ikiliyi çalıştırır.

Kodunuzu çalıştırmak için `dotnet` başka bir şekilde kullanmaktır. Bu, derlemenizin yolunu sağlayarak yapılır: `dotnet path/to/an/assembly.dll`.

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>DNX projenizi .NET Core CLI geçirme
Kodunuzla çalışırken yeni komutların kullanılmasına ek olarak, DNX 'ten geçiş sırasında kalan üç önemli nokta vardır:

1. CLı kullanabilmeniz için `global.json` dosyasını geçirin.
2. Proje dosyasını (`project.json`) CLı araçlarına geçirme.
3. Herhangi bir DNX API 'sini BCL karşılıklarına geçirme.

### <a name="changing-the-globaljson-file"></a>Global. json dosyasını değiştirme
`global.json` dosyası, hem RC1 hem de RC2 (veya üzeri) projeleri için bir çözüm dosyası gibi davranır. RC1 ve sonraki sürümleri birbirinden ayırt etmek için .NET Core CLI (ve Visual Studio 'Nun yanı sıra) için, hangi projenin RC1 veya üzeri olduğunu fark etmek üzere `"sdk": { "version" }` özelliğini kullanırlar. `global.json` bu düğümü hiç içermiyorsa, en son olarak kabul edilir.

`global.json` dosyasını güncelleştirmek için, özelliği kaldırın ya da kullanmak istediğiniz araçların tam sürümüne ayarlayın, bu örnekte **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Proje dosyası geçiriliyor

CLı ve DNX her ikisi de `project.json` dosya tabanlı aynı temel proje sistemini kullanır. Proje dosyasının sözdizimi ve semantiği, senaryolara bağlı olarak küçük farklılıklar sayesinde oldukça kolaydır. Şemada, [şema dosyasında](http://json.schemastore.org/project)görebileceğiniz bazı değişiklikler de vardır.

Bir konsol uygulaması oluşturuyorsanız, proje dosyanıza aşağıdaki kod parçacığını eklemeniz gerekir:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Bu, kodunuzu çalıştırılabilir hale getirerek uygulamanız için bir giriş noktası yayma `dotnet build` söyler. Bir sınıf kitaplığı oluşturuyorsanız yukarıdaki bölümü atlayabilirsiniz. Elbette, `project.json` dosyanıza Yukarıdaki kod parçacığını ekledikten sonra bir statik giriş noktası eklemeniz gerekir. Taşınma DNX ile, sağlanan dı Hizmetleri artık kullanılabilir değil ve bu nedenle temel bir .NET giriş noktası olması gerekir: `static void Main()`.

`project.json`için bir "komutlar" bölümü varsa, bunu kaldırabilirsiniz. Entity Framework CLı komutları gibi DNU komutlarına sahip olmak için kullanılan komutlardan bazıları, CLı 'ye proje başına uzantılar olarak yönlendirilmekte. Projelerinizde kullandığınız komutları kullandıysanız, bunları CLı uzantıları ile değiştirmeniz gerekir. Bu durumda, `project.json` `commands` düğümünün `tools` düğümü tarafından değiştirilmeleri ve araç bağımlılıklarını listemeleri gerekir.

Bu işlemler yapıldıktan sonra, uygulamanız için istediğiniz taşınabilirlik türünü belirlemeniz gerekir. .NET Core ile, aralarından seçim yapabileceğiniz bir taşınabilirlik seçenekleri yelpazesi sunduğumuz için yatırım yaptık. Örneğin, tam olarak *Taşınabilir* bir uygulamaya sahip olmak veya *kendi içinde* olan bir uygulamaya sahip olmak isteyebilirsiniz. Taşınabilir uygulama seçeneği .NET Framework uygulamaların çalışması gibidir: Bu, hedef makinede (.NET Core), paylaşılan bir bileşen tarafından yürütülmesi gerekir. Kendi içinde bulunan uygulama, .NET Core 'un hedefe yüklenmesini gerektirmez, ancak desteklemek istediğiniz her işletim sistemi için bir uygulama oluşturmanız gerekir. Bu taşınabilirlik türleri ve daha fazlası, [uygulama taşınabilirlik türü](../deploying/index.md) belgesinde ele alınmıştır.

İstediğiniz taşınabilirlik türüyle ilgili bir çağrı yaptıktan sonra, hedeflenen çatılarınızı değiştirmeniz gerekir. .NET Core için uygulamalar yazıyorsanız, büyük olasılıkla hedeflenen çatısı olarak `dnxcore50` kullanmıştı. CLı ve yeni [.NET Standard](../../standard/net-standard.md) getirilen değişiklikler ile, Framework 'ün aşağıdakilerden biri olması gerekir:

1. `netcoreapp1.0`-.NET Core üzerinde uygulamalar yazıyorsanız (ASP.NET Core uygulamalar dahil)
2. `netstandard1.6`-.NET Core için sınıf kitaplıkları yazıyorsanız

Diğer `dnx` hedeflerini kullanıyorsanız `dnx451` gibi bunları da değiştirmeniz gerekir. `dnx451` `net451`olarak değiştirilmelidir.
Daha fazla bilgi için lütfen [.NET Standard](../../standard/net-standard.md) konusuna bakın.

`project.json` artık çoğunlukla hazırdır. Özellikle ASP.NET Core bağımlılıklar kullanıyorsanız, bağımlılıklar listenizi gözden geçirmeniz ve bağımlılıklarını daha yeni sürümlere güncelleştirmeniz gerekir. BCL API 'Leri için ayrı paketler kullanıyorsanız, çalışma zamanı paketini [uygulama taşınabilirlik türü](../deploying/index.md) belgesinde açıklandığı şekilde kullanabilirsiniz.

Hazırsanız, `dotnet restore` ile geri yüklemeyi deneyebilirsiniz ([bkz. nota](#dotnet-restore-note)). Eğer NuGet, yukarıda hedeflenen çerçevelerden birinin bağımlılıklarını çözümleyemezse, bağımlılıklarınızın sürümüne bağlı olarak hatalarla karşılaşabilirsiniz. Bu, "bir noktadan noktaya" sorunudur; zaman ilerledikçe, bu çerçeveler için daha fazla ve daha fazla pakete destek dahil edilir. Şimdilik, bu ' de çalıştırırsanız, "Imports" deyimindeki Framework 'ü hedefleyen paketleri geri yüklemesini yapmak üzere `framework` düğümündeki `imports` ifadesini kullanabilirsiniz.
Bu durumda aldığınız geri yükleme hataları, size hangi çerçevelerin içeri aktarılacağını söylemek için yeterli bilgi sağlamalıdır. Bu şekilde biraz kaybolur veya yeni bir kez daha varsa, genel olarak `dnxcore50` belirtmek ve `imports` deyimindeki `portable-net45+win8`, eli yapmanız gerekir. Aşağıdaki JSON kod parçacığı şöyle görünür:

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

`dotnet build` çalıştırmak son derleme hatalarını gösterir, ancak bu çok fazla sayıda olabilir. Kodunuz doğru bir şekilde oluşturup çalıştırdıktan sonra, Çalıştırıcısı ile test edebilirsiniz. `dotnet <path-to-your-assembly>` yürütün ve çalıştırmayı görüntüleyin.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
