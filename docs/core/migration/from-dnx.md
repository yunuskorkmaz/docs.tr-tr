---
title: .NET Core CLI ile DNX'ten geçiş
description: .NET Core CLI araçları için araç DNX geçiş.
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 006e909be03ec3d090135f32f7ba13311201f81e
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845728"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>.NET Core CLI (project.json) için DNX'ten geçiş

## <a name="overview"></a>Genel Bakış
.NET Core ve ASP.NET Core 1.0 RC1 sürümünü DNX araçlar kullanıma sunuldu. .NET Core ve ASP.NET Core 1.0 RC2 sürümünü, .NET Core CLI için DNX'ten taşındı.

Hafif bilgilerinizi tazelemeniz, şimdi hakkında DNX neydi bilgilerin üzerinden geçelim. Bir çalışma zamanı ve .NET Core ve ASP.NET Core 1.0 uygulamaları daha belirgin olarak oluşturmak için kullanılan bir araç takımı DNX oluştu. Bu 3 ana parçalarını almıştır:

1. DNVM - DNX almak için bir yükleme betiği
2. DNX (Dotnet yürütme çalışma zamanı) - kod yürüten çalışma zamanı
3. (Dotnet Geliştirici yardımcı programı) - DNU bağımlılıkları yönetmek, derleme ve uygulamalarınızı yayımlamak için araç kullanımı

CLI'yı sunulmasıyla birlikte, Yukarıdakilerin tümü artık tek bir araç takımı parçasıdır. Ancak, DNX RC1 profilleri'nde kullanılabilir olduğundan, kullanılarak oluşturulan projeler sahip olabileceğiniz yeni CLI kullanımı devre dışı taşımak istediğiniz.

Bu geçiş kılavuzunda projeleri DNX dışına ve .NET Core CLI üzerine geçirme hakkında temel bilgileri ele alınacaktır. Bu belge, ücretsiz, yalnızca bir proje üzerinde .NET Core baştan başlatıyorsanız atlayabilirsiniz.

## <a name="main-changes-in-the-tooling"></a>Ana araç değişiklikleri
İlk özetlenen araç oluşturmada genel bazı değişiklikler vardır.

### <a name="no-more-dnvm"></a>Daha fazla DNVM yok
DNVM kısaltması *DotNet sürüm Yöneticisi* olduğu bir DNX makinenizde yüklemek için kullanılan bir bash/PowerShell Betiği. Bu, bunlar belirtilen akış (veya varsayılan değerleri) yanı sıra belirli bir DNX işaretlemek DNX hangi $PATH üzerinde belirli bir oturum için koyabilirsiniz "etkin", kullanıcıların yardımcı olmuştur. Bu, çeşitli araçları kullanmak izin.

Öğrenerek özellik kümesi .NET Core CLI Araçları'nda gelen değişikliklerden yedekli yapıldığı DNVM ürününde kaldırıldı.

CLI araçları iki ana şekilde paketlenmiş birlikte gelir:

1. Belirli bir platform için yerel yükleyicilerden
2. Diğer durumlarda (örneğin, CI sunucular) için komut dosyası yükleme

Bunu göz önünde bulundurulduğunda, DNVM yükleme özellikleri gerekli değildir. Ancak çalışma zamanı seçimi özellikleri hakkında neler?

Bir çalışma zamanı başvurusu, `project.json` bağımlılıklarınızı için belirli bir sürümü paketi ekleyerek. Bu değişiklik, uygulamanızın yeni bir çalışma zamanı BITS kullanmanız mümkün olacaktır. Bu bit makinenize alma, olduğu gibi CLI ile aynı: destekliyorsa yerel yükleyicilerden birini veya kendi yükleme betiğini yoluyla çalışma zamanını yükleyin.

### <a name="different-commands"></a>Farklı komutları
DNX kullandıysanız, bazı komutlar, üç birinden kullanılan bölümleri (DNX, DNU veya DNVM). CLI ile bu komutlardan bazıları değiştirmek, bazı kullanılamıyor ve bazı aynıdır, ancak biraz farklı semantiğe sahip.

Aşağıdaki tabloda DNX/DNU komutlar ve CLI karşılıkları arasındaki eşlemeyi gösterir.


| DNX komutu                    | CLI komutu    | Açıklama                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| dnx çalıştırın                        | dotnet çalıştırın     | Kaynak kodu çalıştırın.                                                                                           |
| dnu derleme                      | DotNet derleme   | Kodunuzun bir IL ikili oluşturun.                                                                                |
| dnu paketi                       | DotNet paketi    | Kodunuzu bir NuGet paketi için paketi.                                                                        |
| dnx \[komut] (örneğin, "dnx web") | YOK\*          | DNX dünyada, project.json içinde tanımlandığı şekilde bir komut çalıştırın.                                                     |
| dnu yükleme                    | YOK\*          | DNX dünyada, bir bağımlılık olarak bir paket yükleyin.                                                            |
| dnu geri yükleme                    | DotNet restore | Bağımlılıklar, project.json içinde belirtilen geri yükleyin. ([bkz. Not](#dotnet-restore-note))                                                            |
| dnu yayımlama                    | DotNet yayımlama | Uygulamanız için dağıtım üç biçimlerden (taşınabilir, bağımsız ve yerel ile taşınabilir) içinde yayımlayın. |
| dnu kaydırma                       | YOK\*          | DNX dünyada bir project.json packagetargetfallback kaydır.                                                                    |
| dnu komutları                   | YOK\*          | DNX dünyada, genel olarak yüklenmiş komutları yönetin.                                                           |

(\*)-bu özellikler, tasarımı gereği CLI'daki desteklenmez.

## <a name="dnx-features-that-are-not-supported"></a>Desteklenmeyen DNX özellikleri
Yukarıda gösterildiği bir tablo olarak CLI, en azından şimdilik desteklemeyen verdik DNX dünyadan özellikler mevcuttur. Bu bölümde, en önemlileri gidin ve ihtiyacınız varsa, bunların yanı sıra geçici çözümler desteklemediğinden arkasında stratejinin özetler.

### <a name="global-commands"></a>Genel komutları
DNU "Genel komutları" adlı bir kavram ile geldi. Bunlar, esas olarak, uygulamayı çalıştırmak için belirtilen DNX çağıracaktır bir kabuk betiği ile NuGet paketleri olarak paketlenir konsol uygulamaları yoktu.

Bu kavram, CLI'yı desteklemez. Ancak, bilinen kullanılarak etkinleştirilebilir proje başına komutlar ekleme kavramını destekler `dotnet <command>` söz dizimi.

### <a name="installing-dependencies"></a>Bağımlılıklar yükleniyor
V1'den itibaren .NET Core CLI araçlara sahip olmadığınızı bir `install` Bağımlılıkların yüklenmesi için komut. Nuget'ten bir paketi yüklemek için bağımlılık olarak eklemeniz gerekecektir, `project.json` dosya ve ardından çalıştırın `dotnet restore` ([bkz. Not](#dotnet-restore-note)).

### <a name="running-your-code"></a>Kodunuzu çalıştıran
Kodunuzu çalıştırmak için iki ana yolu vardır. İle kaynaktan biridir `dotnet run`. Aksine `dnx run`, herhangi bir bellek içi derleme yapmaz. Aslında çağıracağı `dotnet build` kodunuzu oluşturun ve ardından yerleşik ikili çalıştırın.

Başka bir yolu kullanarak `dotnet` kendi kodunuzu çalıştırmak için. Bu, derleme için bir yol sağlayarak gerçekleştirilir: `dotnet path/to/an/assembly.dll`.

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>DNX projeniz .NET Core CLI sürümüne geçirme
Yeni komutlar, kod ile çalışırken kullanmanın yanı sıra, DNX'ten geçiş içinde kalan üç önemli noktalar vardır:

1. Geçiş `global.json` CLI kullanabilmek için varsa dosya.
2. Proje dosyası geçirme (`project.json`) kendisi için CLI araçları.
3. Tüm DNX API'lerine BCL karşılıkları dışına geçiriliyor.

### <a name="changing-the-globaljson-file"></a>Global.json dosyasını değiştirme
`global.json` Dosya RC1 hem RC2 için bir çözüm dosyası gibi davranır (veya üzeri) projeleri. CLI Araçları (yanı sıra Visual Studio) RC1'de ve sonraki sürümler arasında ayırt etmek için sırada kullandıkları `"sdk": { "version" }` hangi proje ayrım yapma özelliği olan RC1 veya üzeri. Varsa `global.json` bu düğüm yok, en son olarak varsayılır.

Güncelleştirmek için `global.json` kaldırabilir ya da özellik dosyası veya bu durumda, kullanmak istediğiniz araçları tam sürüme ayarlayın **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Proje dosyası geçirme

CLI'yı ve DNX göre aynı temel proje sistemi kullanmak `project.json` dosya. Sözdizimi ve semantiği proje dosyasının tarayıcınızdaki senaryolarını temel alarak küçük farklılıkla aynıdır. De görebileceğiniz gibi şemasında yapılan bazı değişiklikler vardır [şema dosyası](http://json.schemastore.org/project).

Bir konsol uygulaması oluşturuyorsanız proje dosyanıza aşağıdaki kod parçacığını eklemeniz gerekir:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Bu bildirir `dotnet build` etkili bir şekilde kodunuzu çalıştırılabilir yapma, uygulamanız için bir giriş noktası yayılamıyor. Yalnızca bir sınıf kitaplığı oluşturuyorsanız yukarıdaki bölüme atlayın. Elbette, bir kez eklediğiniz için yukarıdaki kod parçacığında, `project.json` dosyası, bir statik giriş noktası eklemeniz gerekir. DNX kapalı taşıma ile sağlanan DI Hizmetleri artık kullanılamaz ve bu nedenle bu temel bir .NET giriş noktası olması gereken: `static void Main()`.

Bir "komutları" bölümü varsa, `project.json`, kaldırabilirsiniz. Entity Framework CLI komutları gibi DNU komutları olarak mevcut için kullanılan komutlardan bazıları CLI için uzantıları proje başına olacak şekilde Taşınmakta. Projelerinizde kullandığınız kendi komutları oluşturulduysa bunları CLI uzantıları ile değiştirmeniz gerekir. Bu durumda, `commands` düğümünde `project.json` tarafından değiştirilmesi gereken `tools` düğüm ve araçları bağımlılıkları listesi gerekiyor.

Bu işlemleri tamamladıktan sonra uygulamanız için istediğiniz taşınabilirlik türünü'ı karar vermeniz gerekir. .NET Core ile biz aralarından seçim yapabileceğiniz taşınabilirlik seçenekleri yelpazesi sağlama içine yatırım yapmış. Örneğin, sahip olmak isteyebilirsiniz bir tam olarak *taşınabilir* uygulama veya sahip olmasını isteyebilir bir *müstakil* uygulama. .NET Framework uygulamaları iş gibi daha fazla taşınabilir uygulama seçeneğini: hedef makinede (.NET Core) yürütmek için paylaşılan bir bileşen gerekir. Kendi içinde uygulama hedefte yüklenmesi .NET Core gerektirmez, ancak desteklemek istediğiniz her bir işletim sistemi için bir uygulama oluşturmak sahip. Bu taşınabilirlik türleri ve daha fazlasını ele alınmıştır [uygulama taşınabilirliği türü](../deploying/index.md) belge.

İstediğiniz taşınabilirlik ne tür bir çağrı yaptıktan sonra hedef çerçeveleri Değiştir gerekir. .NET Core uygulamaları yazıyorsanız, büyük olasılıkla kullanmakta olduğunuz `dnxcore50` , hedeflenen çerçeve. CLI'yı ve değişiklikleri, yeni [.NET Standard](../../standard/net-standard.md) alınırsa, framework aşağıdakilerden biri olması gerekir:

1. `netcoreapp1.0` -.NET Core (ASP.NET Core uygulamaları dahil) uygulamaları yazıyorsanız
2. `netstandard1.6` -sınıf kitaplıkları için .NET Core yazıyorsanız

Diğer kullanıyorsanız `dnx` gibi hedefler `dnx451` olanlar da değiştirmeniz gerekir. `dnx451` değiştirilmelidir `net451`.
Lütfen [.NET Standard](../../standard/net-standard.md) konusuna bakın.

`project.json` Çoğunlukla hazır hale gelir. Özellikle ASP.NET Core bağımlılıkları kullanıyorsanız, bağımlılıkları listesine göz at ve bağımlılıkları daha yeni sürümlerine güncelleştirme gerekir. BCL API için ayrı paketler kullandıysanız, açıklandığı gibi çalışma zamanı paketi kullanabilirsiniz [uygulama taşınabilirliği türü](../deploying/index.md) belge.

Hazır olduğunuzda ile geri yüklemeyi deneyebilirsiniz `dotnet restore` ([bkz. Not](#dotnet-restore-note)). Bağımlılıklarınızı sürümüne bağlı olarak, NuGet bağımlılıklarını yukarıdaki hedeflenen altyapılarından birini çözümleyemezse hatalarla karşılaşabilirsiniz. Bu "-belirli bir noktaya" sorunudur; zaman ilerledikçe daha da fazla paketleri bu çerçeveler için destek içerir. Şimdilik bunu çalıştırırsanız kullanabileceğiniz `imports` deyimi içinde `framework` "alır" deyimi içinde framework hedefleme paketlerinin geri yükleyebilmesi için NuGet belirtmek için düğüm.
Bu durumda aldığınız geri yükleme hataları içeri aktarmanız gerekir hangi çerçeveleri bildirmek için yeterli bilgi vermelidir. Biraz kaybolan ya da bu yeni varsa, genel olarak, belirtme `dnxcore50` ve `portable-net45+win8` içinde `imports` deyimi ux'in yapmak. Aşağıdaki JSON kod parçacığında, bu gibi sistem gösterilmektedir:

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Çalışan `dotnet build` var olmamalıdır ancak çok sayıda nihai derleme hataları gösterir. Kodunuzu oluşturmak ve düzgün çalışan sonra teslim Çalıştırıcısı ile test edebilirsiniz. Yürütme `dotnet <path-to-your-assembly>` ve çalıştırın.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
