---
title: .NET Core CLI DNX geçirme
description: .NET Core CLI araç tooling DNX kullanarak geçirin.
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: dd3c31b88b619799e6b2e2596127d64d84918ca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217457"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>.NET Core CLI (project.json) DNX geçirme

## <a name="overview"></a>Genel Bakış
.NET Core ve ASP.NET Core 1.0 RC1 sürümündeki DNX araç sunmuştur. .NET Core ve ASP.NET Core 1.0 RC2 sürümünü DNX .NET Core CLI taşındı.

Hafif bir Yenileyici şimdi hakkında DNX neydi olduðunu. DNX bir çalışma zamanı ve .NET Core ve ASP.NET Core 1.0 uygulamaları daha belirgin olarak oluşturmak için kullanılan bir araç takımı oluştu. 3 ana parçalarını içermektedir:

1. DNVM - DNX almak için bir yükleme komut dosyası
2. DNX (Dotnet yürütme çalışma zamanı) - kodunuzu yürütür çalışma zamanı
3. DNU (Dotnet Geliştirici yardımcı programı) - tooling bağımlılıkları yönetmek, oluşturma ve uygulamalarınızı yayımlamak için

CLI başlanmasıyla Yukarıdakilerin tümü artık tek bir araç takımı parçasıdır. Ancak, DNX RC1 zaman çerçevesinde kullanılabilir olduğundan, bu kullanılarak oluşturulan projeleri olabilir, yeni CLI araçları devre dışı geçmek istiyorsunuz. 

Bu Geçiş Kılavuzu essentials projeleri DNX dışına ve .NET Core CLI üzerine geçirmek nasıl ele alınacaktır. Bu belge ücretsiz olarak, yeni bir proje .NET Core üzerinde baştan başlatıyorsanız atlayabilirsiniz. 

## <a name="main-changes-in-the-tooling"></a>Araç ana değişiklikleri
İlk özetlenen araç oluşturmada genel bazı değişiklikler vardır. 

### <a name="no-more-dnvm"></a>Daha fazla hiçbir DNVM
DNVM, kısaltması *DotNet sürüm Yöneticisi* olan bir DNX makinenize yüklemek için kullanılan bir bash/PowerShell Betiği. Bunlar, belirtilen akışa (veya varsayılan değerleri) gereksinim yanı sıra belirli bir DNX işaretlemek DNX, onu üzerinde $PATH için belirli oturum koyabilirsiniz "etkin", kullanıcıların Yardım. Bu, çeşitli araçları kullanmanıza olanak tanır.

.NET Core CLI araçları gelen değişikliklerden öğrenerek özellik kümesi yedekli yapıldı çünkü DNVM ürününde kaldırıldı.

CLI araçlarını iki ana şekilde paketlenmiş getirir:

1. Belirli bir platform için yerel yükleyicileri
2. Diğer durumlarda (örneğin, CI sunucuları) için komut dosyasını yükleyin

Bu verildiğinde, DNVM yükleme özellikleri gerekli değildir. Ancak çalışma zamanı seçimi özellikleri hakkında neler? 

Çalışma zamanı'nda başvuru, `project.json` , bağımlılıklar için paketi belirli bir sürümü olarak ekleyerek. Bu değişiklikle, uygulamanızın yeni çalışma zamanı BITS kullanmanız mümkün olacaktır. Makinenize bu BITS alma, olduğu gibi CLI ile aynı: destekliyorsa yerel yükleyicileri biri aracılığıyla veya kendi yükleme komut dosyası aracılığıyla çalışma zamanı yükleme. 

### <a name="different-commands"></a>Farklı komutları
DNX kullanıyorsanız, bazı komutlar kendi üç birinden kullanılan bölümleri (DNX, DNU veya DNVM). CLI ile bazı aşağıdaki komutlardan birini değiştirmek, bazı kullanılamıyor ve bazı aynıdır ancak biraz farklı semantiklerine sahip. 

Aşağıdaki tabloda DNX/DNU komutlar ve CLI dekiler arasındaki eşlemeyi gösterir.


| DNX komutu                       | CLI komutu       | Açıklama                                                                                                       |
|--------------------------------   |----------------   |-----------------------------------------------------------------------------------------------------------------  |
| dnx Çalıştır                           | dotnet çalıştırın        | Kod bir kaynaktan çalıştırın.                                                                                             |
| dnu derleme                         | DotNet derleme      | IL ikili kodunuzu derleyin.                                                                                  |
| dnu paketi                          | DotNet paketi       | Bir NuGet paketi kodunuzun paketi.                                                                          |
| dnx \[komutu] (örneğin, "dnx web")   | YOK\*             | DNX dünyada project.json tanımlandığı şekilde bir komutunu çalıştırın.                                                       |
| dnu yükleme                       | YOK\*             | DNX dünyada bağımlılık olarak bir paketini yükleyin.                                                              |
| dnu geri yükleme                       | DotNet geri yükleme    | Project.json içinde belirtilen bağımlılıkları geri yükleyin. ([bkz. Not](#dotnet-restore-note))                                                               |
| dnu yayımlama                       | DotNet yayımlama    | Uygulamanız için dağıtım üç forms (taşınabilir, yerel ve tek başına ile taşınabilir) birinde yayımlayın.    |
| dnu kaydırma                          | YOK\*             | DNX dünyada csproj bir project.json alın.                                                                      |
| dnu komutları                      | YOK\*             | DNX dünyada genel yüklü komutları yönetin.                                                             |

(\*)-bu özellikler tasarım gereği CLI desteklenmez. 

## <a name="dnx-features-that-are-not-supported"></a>Desteklenmeyen DNX özellikleri
Gösterir yukarıdaki tabloda CLI, en az anda için desteklememeye karar DNX dünyadan özellikler vardır. Bu bölümde en önemlileri gidin ve ihtiyacınız varsa, bunların yanı sıra geçici çözümler desteklemediğinden arkasında stratejinin ana hatlarını vermektedir.

### <a name="global-commands"></a>Genel komutlar
DNU "Genel komutları" adlı bir kavramı geldi. Bunlar, esas olarak, uygulamayı çalıştırmak için belirtilen DNX çağıracaktır bir kabuk betiği NuGet paketleri olarak paketlenir konsol uygulamaları yoktu. 

CLI bu kavramı desteklemez. Ancak, bilinen kullanılarak etkinleştirilebilir proje başına komut ekleme kavramını destekler `dotnet <command>` sözdizimi.

### <a name="installing-dependencies"></a>Bağımlılıkların yüklenmesi
V1 itibariyle .NET Core CLI araçlarını olmayan bir `install` bağımlılıklarını yüklemek için komutu. Nuget'ten bir paketi yüklemek için bir bağımlılık olarak eklemek gerekir, `project.json` dosya ve ardından çalıştırın `dotnet restore` ([bkz. Not](#dotnet-restore-note)). 

### <a name="running-your-code"></a>Kodunuzu çalıştırmaya
Kodunuzu çalıştırmak için başlıca iki yolu vardır. İle bir kaynaktan biridir `dotnet run`. Farklı `dnx run`, bellek içi derleme yapmaz. Gerçekte çağıracağı `dotnet build` kodunuzu oluşturun ve ardından yerleşik ikili çalıştırın. 

Başka bir yol kullanarak `dotnet` kendi kodunuzu çalıştırmak için. Bu, derleme için bir yol sağlayarak gerçekleştirilir: `dotnet path/to/an/assembly.dll`. 

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>DNX projeniz .NET Core CLI geçirme
Kodunuzu ile çalışırken, yeni komutları kullanarak ek olarak, DNX geçirme sol üç önemli şeyler vardır:

1. Geçiş `global.json` CLI kullanabilmek için varsa dosya.
2. Proje dosyası geçirme (`project.json`) CLI araç kendisine.
3. BCL dekiler herhangi DNX API'lerine dışına geçirme. 

### <a name="changing-the-globaljson-file"></a>Global.json dosyayı değiştirme
`global.json` Dosya RC1 ve RC2 için çözüm dosyası gibi davranır (veya üstü) projeleri. CLI araçlarını (yanı sıra Visual Studio) RC1 ve sonraki sürümler arasında ayırt etmek için sırayla kullandıkları `"sdk": { "version" }` hangi proje ayrım yapmak için özelliktir RC1 veya sonraki bir sürümü. Varsa `global.json` bu düğüm yok, bu en son olduğu varsayılır. 

Güncelleştirmek için `global.json` dosya, kaldırın veya özellik ya da bu durumda, kullanmak istediğiniz Araçları'nın tam sürümünü ayarlayın **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Proje dosyası geçirme
CLI ve DNX göre aynı temel proje sistemini kullanması `project.json` dosya. Sözdizimi ve proje dosyası semantiği oldukça çok, küçük farklılıklar senaryolarını temel alarak ile aynıdır. Ayrıca hangi görebilirsiniz şemasında yapılan bazı değişiklikler vardır [şema dosyası](http://json.schemastore.org/project).

Bir konsol uygulaması oluşturuyorsanız, proje dosyanıza aşağıdaki kod parçacığında eklemeniz gerekir:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Bu bildirir `dotnet build` etkili bir şekilde kodunuzu runnable yapmadan uygulamanız için bir giriş noktası yaymak üzere. Yalnızca bir sınıf kitaplığı oluşturuluyorsa, yukarıdaki bölümüne atlayın. Elbette, bir kez, eklemek için yukarıdaki kod parçacığında, `project.json` dosyası ihtiyacınız statik giriş noktası eklemek. DNX kapalı taşıma ile sağlanan dı Hizmetleri artık kullanılabilir olduğunu ve bu nedenle bu bir temel .NET giriş noktası olması gerekir: `static void Main()`.

Bir "komutları" bölümü varsa, `project.json`, kaldırabilirsiniz. Bazı Entity Framework CLI komutları gibi DNU komutları olarak mevcut için kullanılan komutlar CLI proje başına uzantıları olması için bağlantı noktası kurulmuş. Projelerinizde kullanarak kendi komutları oluşturulduysa, bunları CLI uzantılarıyla değiştirmeniz gerekiyor. Bu durumda, `commands` düğümünde `project.json` tarafından değiştirilmesi gereken `tools` düğümü ve araçları bağımlılıkları listesinde gerekiyor. 

Bu işlemleri tamamladıktan sonra uygulama için istediğiniz taşınabilirlik hangi tür karar vermeniz gerekir. .NET Core ile biz aralarından seçim yapabileceğiniz taşınabilirlik seçenekleri yelpazesini sağlama içine yatırım yapmış kullanıcılar. Örneğin, sahip olmak isteyebilirsiniz bir tam olarak *taşınabilir* uygulama veya olmasını isteyebilir bir *müstakil* uygulama. Taşınabilir uygulama seçeneğini .NET Framework uygulamaları iş gibi daha fazla: hedef makinede (.NET Core) yürütmek için paylaşılan bir bileşen gerekiyor. Kendi içinde bulunan uygulama .NET Core hedef sunucuda yüklü olmasını gerektirmez, ancak, desteklemek istediğiniz her işletim sistemi için bir uygulama oluşturmak sahip. Bu taşınabilirlik türleri ve daha fazlasını ele alınmıştır [uygulama taşınabilirliği türü](../deploying/index.md) belge. 

İstediğiniz taşınabilirlik ne tür bir çağrı yaptıktan sonra hedeflenen framework(s) değiştirmek gerekir. Uygulamalar için .NET Core yazıyorsanız, büyük olasılıkla kullanmakta olduğunuz `dnxcore50` hedef çerçeveyi olarak. CLI ve değişiklikleri, yeni [.NET standart](../../standard/net-standard.md) alınırsa, framework şunlardan biri olması gerekir:

1. `netcoreapp1.0` -uygulamalar (ASP.NET Core uygulamaları dahil) .NET Core üzerinde yazıyorsanız,
2. `netstandard1.6` -sınıf kitaplıkları için .NET Core yazıyorsanız

Diğer kullanıyorsanız `dnx` gibi hedefler `dnx451` olanlar da değiştirmeniz gerekir. `dnx451` değiştirilmelidir `net451`. Lütfen [.NET standart](../../standard/net-standard.md) konusuna bakın. 

`project.json` Artık çoğunlukla hazırdır. Özellikle ASP.NET Core bağımlılıkları kullanıyorsanız bağımlılıkları listenize gidin ve bağımlılıklarını daha yeni sürümlerine güncelleştirmek gerekir. BCL API'leri için ayrı paketleri kullanıyorsanız, çalışma zamanı paketi açıklandığı gibi kullanabileceğiniz [uygulama taşınabilirliği türü](../deploying/index.md) belge. 

Hazır olduğunuzda ile geri yüklemeyi deneyebilirsiniz `dotnet restore` ([bkz. Not](#dotnet-restore-note)). Bağımlılıklarınız sürümüne bağlı olarak, NuGet yukarıdaki hedeflenen çerçeveleri biri için bağımlılıkları çözemezseniz hatalarla karşılaşabilirsiniz. Bu "noktası zamanında" sorunudur; zaman ilerledikçe daha da fazla paketler bu çerçeveleri için destek içerir. Şu an için bu çalıştırırsanız kullanabileceğiniz `imports` deyimi içinde `framework` düğümü için NuGet "alır" deyimi içinde framework hedefleme paketler geri yükleyebilirsiniz belirtin. Bu durumda aldığınız geri yükleme hataları içeri aktarmanız gerekir hangi çerçeveleri bildirmek için yeterli bilgi vermelidir. Biraz kayıp ya da bu yeni varsa, genel olarak, belirtme `dnxcore50` ve `portable-net45+win8` içinde `imports` deyimi eli yapmanız. Aşağıdaki JSON parçacığında, bu gibi sistem gösterilmektedir:

```json
    "frameworks": {
        "netcoreapp1.0": { 
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Çalışan `dotnet build` döndürmemelidir olması ancak çok sayıda nihai derleme hatalarını gösterir. Kod oluşturma ve düzgün çalışmasını sonra onu Çalıştırıcısı ile test edebilirsiniz. Yürütme `dotnet <path-to-your-assembly>` ve çalışmasını bakın.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]