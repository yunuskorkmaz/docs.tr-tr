---
title: DNX'ten .NET Core CLI'ye geçiş
description: DNX takımlarını kullanmaktan .NET Core CLI takımağına geçirin.
ms.date: 06/20/2016
ms.openlocfilehash: 31317f110ae1e8586b78becd757d0a8ff07f1459
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503824"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>DNX'ten .NET Core CLI'ye geçiş (project.json)

## <a name="overview"></a>Genel Bakış
.NET Core ve ASP.NET Core 1.0'ın RC1 sürümü DNX takımlarını tanıttı. .NET Core ve ASP.NET Core 1.0'ın RC2 sürümü DNX'ten .NET Core CLI'ye taşındı.

Hafif bir tazeleyici olarak, DNX hakkında ne olduğunu özetleyelim. DNX bir çalışma zamanı ve .NET Core oluşturmak için kullanılan bir araç kümesi ve daha özel olarak, Core 1.0 uygulamaları ASP.NET. Bu 3 ana parçadan oluşuyordu:

1. DNVM - DNX elde etmek için bir yükleme komut dosyası
2. DNX (Dotnet Yürütme Runtime) - kodunuzu yürüten çalışma zamanı
3. DNU (Dotnet Developer Utility) - bağımlılıkları yönetmek, uygulamalarınızı oluşturmak ve yayınlamak için araç

CLI'nin piyasaya sürülmesiyle birlikte, yukarıdakilerin hepsi artık tek bir araç kümesinin parçası haline gelen bir araç kümesidir. Ancak, DNX RC1 zaman diliminde kullanıma sunulduğundan, yeni CLI aracına geçmek isteyeceğiniz projeler ekiolabilir.

Bu geçiş kılavuzu, dnx ve .NET Core CLI üzerine projelerin nasıl geçirilir temel leri kapsayacaktır. .NET Core'da bir projeye sıfırdan başlıyorsanız, bu belgeyi serbestçe atlayabilirsiniz.

## <a name="main-changes-in-the-tooling"></a>Takımlamadaki temel değişiklikler
Önce ana hatlarıyla belirtilmesi gereken takım bazı genel değişiklikler vardır.

### <a name="no-more-dnvm"></a>Artık DNVM yok
DNVM, *DotNet Version Manager* için kısa bir bash / PowerShell komut makinesi makinenize bir DNX yüklemek için kullanılır. Kullanıcıların belirttikleri akıştan (veya varsayılan akışlardan) gereksinim duydukları DNX'i almalarına ve belirli bir DNX "etkin"i işaretlemelerine yardımcı oldu ve bu da belirli bir oturum için $PATH.'ya koydu. Bu çeşitli araçları kullanmanıza olanak sağlar.

DNVM, özellik kümesi .NET Core CLI'de gelen değişikliklerle gereksiz hale geldiği için durduruldu.

CLI iki ana şekilde paketlenmiş olarak gelir:

1. Belirli bir platform için yerel yükleyiciler
2. Diğer durumlar için komut dosyası yükleme (CI sunucuları gibi)

Bu göz önüne alındığında, DNVM yükleme özellikleri gerekli değildir. Peki ya çalışma zamanı seçim özellikleri?

Bağımlılıklarınıza belirli bir `project.json` sürümün paketini ekleyerek çalışma zamanınıza başvurursunuz. Bu değişiklikle, uygulamanız yeni çalışma zamanı bitlerini kullanabilir. Bu bitleri makinenize almak CLI ile aynıdır: çalışma süresini desteklediği yerel yükleyicilerden biri veya yükleme komut dosyası aracılığıyla yüklersiniz.

### <a name="different-commands"></a>Farklı komutlar
DNX kullanıyorsanız, üç bölümden birinden (DNX, DNU veya DNVM) bazı komutlar kullandınız. CLI ile, bu komutların bazıları değişir, bazıları mevcut değildir ve bazıları aynıdır, ancak biraz farklı semantik vardır.

Aşağıdaki tabloda DNX/DNU komutları ile CLI karşılıkları arasındaki eşleme gösterilmektedir.

| DNX komutu                    | CLI komutu    | Açıklama                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| dnx çalıştır                        | `dotnet run`     | Kodu kaynaktan çalıştırın.                                                                                           |
| dnu yapı                      | `dotnet build`   | Kodunuzu il ikili oluşturun.                                                                                |
| dnu paketi                       | `dotnet pack`    | Kodunuzu bir NuGet paketini paketle.                                                                        |
| dnx \[komutu] (örneğin, "dnx web") | Yok\*          | DNX dünyasında, project.json'da tanımlandığı şekilde bir komut çalıştırın.                                                     |
| dnu yükleme                    | Yok\*          | DNX dünyasında, bağımlılık olarak bir paket yükleyin.                                                            |
| dnu geri yükleme                    | `dotnet restore` | Projenizde belirtilen bağımlılıkları geri yükleyin.json. ([bkz. not](#dotnet-restore-note))                                                            |
| dnu yayınlamak                    | `dotnet publish` | Dağıtım başvurunuzu üç formdan birinde yayımlayın (taşınabilir, yerel ve bağımsız taşınabilir). |
| dnu sargı                       | Yok\*          | DNX dünyasında, csproj bir project.json sarın.                                                                    |
| dnu komutları                   | Yok\*          | DNX dünyasında, genel olarak yüklenen komutları yönetin.                                                           |

(\*) - Bu özellikler CLI'de tasarım gereği desteklenmez.

## <a name="dnx-features-that-are-not-supported"></a>Desteklenmeyen DNX özellikleri
Yukarıdaki tabloda da görüldüğü gibi, DNX dünyasından en azından şimdilik CLI'de desteklememeye karar verdiğimiz özellikler vardır. Bu bölüm en önemli olanları gözden geçirilecek ve ihtiyacınız varsa onları desteklememek arkasındaki mantığı ve geçici çözümlerini ana hatlar.

### <a name="global-commands"></a>Genel komutlar
DNU "küresel komutlar" adı verilen bir kavram ile geldi. Bunlar, esasen, uygulamayı çalıştırmak için belirttiğiniz DNX'i çağıracak bir kabuk komut dosyasına sahip NuGet paketleri olarak paketlenmiş konsol uygulamalarıydı.

CLI bu kavramı desteklemez. Ancak, tanıdık `dotnet <command>` sözdizimi kullanılarak çağrılabilecek proje başına komut ekleme kavramını destekler.

### <a name="installing-dependencies"></a>Bağımlılıkları yükleme
v1 itibariyle,.NET Core CLI bağımlılıkları `install` yüklemek için bir komut yok. NuGet'den bir paket yüklemek için, dosyanıza bağımlılık olarak eklemeniz ve `dotnet restore` ardından çalıştırmanız `project.json` gerekir[(bkz. not).](#dotnet-restore-note)

### <a name="running-your-code"></a>Kodunuzu çalıştırma
Kodunuzu çalıştırmanın iki ana yolu vardır. Biri kaynaktan, `dotnet run`. Aksine, `dnx run`bu herhangi bir bellek derleme yapmaz. Aslında kodunuzu `dotnet build` oluşturmak ve daha sonra yapılı ikili çalıştırmak için çağırır.

Başka bir yolu `dotnet` kodunuzu çalıştırmak için kendini kullanmaktır. Bu, derlemenize bir yol sağlayarak `dotnet path/to/an/assembly.dll`yapılır: .

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>DNX projenizi .NET Core CLI'ye geçirme
Kodunuzla çalışırken yeni komutlar kullanmanın yanı sıra, DNX'ten geçişte kalan üç önemli şey vardır:

1. CLI `global.json` kullanabilmek için dosyayı geçirin.
2. Proje dosyasını (`project.json`) kendisini CLI aracına geçirme.
3. Herhangi bir DNX API'den BCL karşılıklarına geçiş.

### <a name="changing-the-globaljson-file"></a>global.json dosyasını değiştirme
Dosya, `global.json` hem RC1 hem de RC2 (veya sonraki) projeleri için bir çözüm dosyası gibi davranır. .NET Core CLI'nin (ve Visual Studio'nun) RC1 ve sonraki sürümleri `"sdk": { "version" }` arasında ayrım yapabilmesi için, hangi projenin RC1 veya daha sonraki olduğunu ayrımı yapmak için özelliği kullanırlar. Bu `global.json` düğüm hiç yoksa, en son olduğu varsayılır.

Dosyayı `global.json` güncelleştirmek için, bu durumda **1.0.0-preview2-003121:**

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Proje dosyasını geçirme

CLI ve DNX her ikisi de dosyaya dayalı `project.json` aynı temel proje sistemini kullanır. Proje dosyasının sözdizimi ve anlambilimi hemen hemen aynıdır ve senaryolara dayalı küçük farklılıklar vardır. [Şema dosyasında](http://json.schemastore.org/project)görebileceğiniz şema bazı değişiklikler de vardır.

Bir konsol uygulaması oluşturuyorsanız, proje dosyanıza aşağıdaki snippet'i eklemeniz gerekir:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Bu, `dotnet build` uygulamanız için bir giriş noktası yontarak kodunuzu etkili bir şekilde çalıştırılabilir hale getirmenizi emreder. Bir sınıf kitaplığı oluşturuyorsanız, yukarıdaki bölümü atlayın. Tabii ki, dosyanıza `project.json` yukarıdaki snippet ekledikten sonra, statik bir giriş noktası eklemeniz gerekir. DNX'ten uzaklaşmayla, sağladığı DI hizmetleri artık kullanılamıyor ve bu nedenle bunun temel `static void Main()`bir .NET giriş noktası olması gerekiyor: .

Eğer içinde `project.json`bir "komutlar" bölümü varsa, kaldırabilirsiniz. DNU komutları olarak kullanılan bazı komutlar (Varlık Çerçevesi CLI komutları gibi) CLI'ye proje başına uzantıolarak taşınır. Projelerinizde kullanmakta olduğunuz kendi komutlarınızı oluşturmuşsanız, bunları CLI uzantılarıyla değiştirmeniz gerekir. Bu durumda, `commands` düğüm düğüm `project.json` tarafından `tools` değiştirilmesi gerekir ve araçları bağımlılıkları listelemek gerekir.

Bu işler bittikten sonra, uygulama için istediğiniz taşınabilirlik türüne karar vermeniz gerekir. .NET Core ile, aralarından seçim yapabileceğiniz taşınabilirlik seçenekleri yelpazesi ni sunmak için yatırım yaptık. Örneğin, tamamen *taşınabilir* bir uygulamaya sahip olmak veya *bağımsız* bir uygulama isteyebilirsiniz. Taşınabilir uygulama seçeneği daha çok .NET Framework uygulamalarının çalışması gibidir: hedef makinede (.NET Core) çalıştırmak için paylaşılan bir bileşene ihtiyaç duyar. Bağımsız uygulama,.NET Core'un hedefe yüklenmesini gerektirmez, ancak desteklemek istediğiniz her işletim sistemi için bir uygulama oluşturmanız gerekir. Bu taşınabilirlik türleri ve daha fazlası [uygulama taşınabilirlik türü](../deploying/index.md) belgesinde ele alınmıştır.

Ne tür taşınabilirlik istediğinize ilişkin bir arama yaptıktan sonra, hedeflediğiniz çerçeveyi(ler) değiştirmeniz gerekir. .NET Core için uygulama yazıyorsanız, büyük olasılıkla `dnxcore50` hedeflediğiniz çerçeveyi kullanıyordunuzun. CLI ve yeni [.NET Standardının](../../standard/net-standard.md) getirdiği değişikliklerle çerçevenin aşağıdakilerden biri olması gerekir:

1. `netcoreapp1.0`- .NET Core'da uygulama yazıyorsanız (ASP.NET Çekirdek uygulamaları dahil)
2. `netstandard1.6`- .NET Core için sınıf kitaplıkları yazıyorsanız

Diğer `dnx` hedefleri kullanıyorsanız, `dnx451` bu da değiştirmek gerekir gibi. `dnx451`olarak `net451`değiştirilmelidir.
Daha fazla bilgi için lütfen [.NET Standard](../../standard/net-standard.md) konusuna bakın.

Senin `project.json` şimdi çoğunlukla hazır. Bağımlılıklar listenizi gözden geçirmeniz ve bağımlılıkları yeni sürümlerine güncelleştirmeniz gerekir, özellikle de ASP.NET Temel bağımlılıkları kullanıyorsanız. BCL API'leri için ayrı paketler kullanıyorsanız, [uygulama taşınabilirlik türü](../deploying/index.md) belgesinde açıklandığı gibi çalışma zamanı paketini kullanabilirsiniz.

Hazır olduktan sonra, geri `dotnet restore` ödemeyi deneyebilirsiniz ([bkz. not).](#dotnet-restore-note) Bağımlılıklarınızın sürümüne bağlı olarak, NuGet yukarıdaki hedeflenen çerçevelerden birinin bağımlılıklarını çözemiyorsa hatalarla karşılaşabilirsiniz. Bu bir "nokta-in-time" sorundur; Zaman ilerledikçe, daha fazla paket bu çerçeveler için destek içerecektir. Şimdilik, bu ile çalışırsanız, nuget'e `framework` "içeri alma" deyimi içinde çerçeveyi hedefleyen paketleri geri yükleyebileceğini belirtmek için düğüm içindeki `imports` deyimi kullanabilirsiniz.
Bu durumda elde ettiğiniz geri alma hataları, hangi çerçeveleri içe aktarmanız gerektiğini size bildirmek için yeterli bilgi sağlamalıdır. Eğer biraz kayıp ya da bu yeni iseniz, `dnxcore50` `portable-net45+win8` genel `imports` olarak, belirtme ve deyimi hile yapmalıdır. Aşağıdaki JSON snippet bu nasıl göründüğünü gösterir:

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Çok `dotnet build` fazla olmaması gerekirken, çalıştırma herhangi bir nihai yapı hatası gösterir. Kodunuz düzgün bir şekilde inşa edilip çalıştırıladıktan sonra, koşucuyla test edebilirsiniz. Çalıştırın `dotnet <path-to-your-assembly>` ve çalıştırın bakın.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
