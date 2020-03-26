---
title: .NET Framework ile başlayın
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: cd27f2fb893def9e186504cc9973bae71473f005
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248914"
---
# <a name="get-started-with-net-framework"></a>.NET Framework ile başlayın

.NET Framework, .NET Framework'u hedefleyen uygulamaları yöneten bir yürütme ortamıdır. Bellek yönetimi ve diğer sistem hizmetleri sağlayan ortak dil çalışma süresi ve programcıların uygulama geliştirmenin tüm önemli alanları için sağlam ve güvenilir koddan yararlanmalarını sağlayan kapsamlı bir sınıf kitaplığından oluşur.

> [!NOTE]
> .NET Framework yalnızca Windows sistemlerinde kullanılabilir. Windows, MacOS ve Linux'ta uygulama geliştirmek ve çalıştırmak için [.NET Core'u](../../core/index.md) kullanabilirsiniz.

## <a name="what-is-net-framework"></a>.NET Framework nedir?

.NET Framework, windows için çalışan uygulamalarına çeşitli hizmetler sağlayan yönetilen bir yürütme ortamıdır. İki ana bileşenden oluşur: çalışan uygulamaları işleyen yürütme motoru olan ortak dil çalışma süresi (CLR) ve geliştiricilerin kendi uygulamalarından arayabildiği test edilmiş, yeniden kullanılabilir kod kitaplığı sağlayan .NET Framework Class Library. .NET Framework'ün çalışan uygulamalara sağladığı hizmetler şunlardır:

- Hafıza yönetimi. Birçok programlama dilinde, programcılar bellek ayırma ve serbest bırakmak ve nesne yaşam sürelerini işlemek için sorumludur. .NET Framework uygulamalarında CLR bu hizmetleri uygulama adına sağlar.

- Ortak bir tür sistemi. Geleneksel programlama dillerinde, temel türler derleyici tarafından tanımlanır ve bu da diller arası birlikte çalışabilirliği karmaşıklaştırır. .NET Framework'de temel türler .NET Framework türü sistemi tarafından tanımlanır ve .NET Framework'u hedefleyen tüm dillerde yaygındır.

- Geniş bir sınıf kütüphanesi. Programcılar, ortak düşük düzeyli programlama işlemlerini işlemek için büyük miktarda kod yazmak yerine, .NET Framework Class Kitaplığı'ndan kolayca erişilebilen bir tür kitaplığı ve üyeleri kullanır.

- Geliştirme çerçeveleri ve teknolojileri. .NET Framework, web uygulamaları için ASP.NET, veri erişimi ADO.NET, hizmet odaklı uygulamalar için Windows Communication Foundation ve Windows Masaüstü uygulamaları için Windows Presentation Foundation gibi uygulama geliştirmenin belirli alanları için kitaplıklar içerir.

- Dil birlikte çalışabilirlik. .NET Framework'ü hedefleyen dil derleyicileri, ortak dil çalışma zamanı tarafından çalışma zamanında derlenen Ortak Ara Dil (CIL) adlı bir ara kod yayır. Bu özellik sayesinde, bir dilde yazılmış yordamlar diğer diller tarafından erişilebilir ve programcılar tercih ettikleri dillerde uygulama oluşturmaya odaklanırlar.

- Sürüm uyumluluğu. Nadir durumlar dışında, .NET Framework'ün belirli bir sürümünü kullanarak geliştirilen uygulamalar daha sonraki bir sürümde değişiklik yapılmadan çalıştırılır.

- Yan yana yürütme. .NET Framework, ortak dil çalışma zamanının birden çok sürümünün aynı bilgisayarda bulunmasına izin vererek sürüm çakışmalarının giderilmesine yardımcı olur. Bu, uygulamaların birden çok sürümünün bir arada bulunabileceği ve bir uygulamanın .NET Framework sürümünde oluşturulabileceği anlamına gelir. .NET Framework sürüm grupları 1.0/1.1, 2.0/3.0/3.5 ve 4/4.5.x/4.6.x/4.7.x/4.8 için yan yana yürütme uygulanır.

- Çoklu hedef. [.NET Standard'ı](../../standard/net-standard.md)hedefleyen geliştiriciler, standardın bu sürümü tarafından desteklenen birden çok .NET Framework platformunda çalışan sınıf kitaplıkları oluşturur. Örneğin, .NET Standart 2.0'ı hedefleyen kitaplıklar,.NET Framework 4.6.1, .NET Core 2.0 ve UWP 10.0.16299'u hedefleyen uygulamalar tarafından kullanılabilir.

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Kullanıcılar için .NET Çerçevesi

.NET Framework uygulamaları geliştirmez, ancak bunları kullanırsanız, .NET Framework veya çalışması hakkında özel bilgilere sahip olmak gerekmez. Çoğunlukla, çerçeve tamamen kullanıcılara şeffaftır.

Windows işletim sistemini kullanıyorsanız, .NET Framework bilgisayarınıza zaten yüklenmiş olabilir. Ayrıca, .NET Framework gerektiren bir uygulama yüklerseniz, uygulamanın kurulum programı çerçevenin belirli bir sürümünü bilgisayarınıza yükleyebilir. Bazı durumlarda, .NET Framework'e yüklemenizi isteyen bir iletişim kutusu görebilirsiniz. Bu iletişim kutusu göründüğünde bir uygulamayı çalıştırmayı denediyseniz ve bilgisayarınızda internet erişimi varsa, .NET Framework'ün eksik sürümünü yüklemenize olanak tanıyan bir web sayfasına gidebilirsiniz. Daha fazla bilgi için [Yükleme kılavuzuna](../install/index.md)bakın.

Genel olarak, bilgisayarınıza yüklenen .NET Framework sürümlerini kaldırmamalısınız. Bunun iki nedeni vardır:

- Kullandığınız bir uygulama .NET Framework'ün belirli bir sürümüne bağlıysa, bu sürüm kaldırılırsa bu uygulama kırılabilir.

- .NET Framework'ün bazı sürümleri, önceki sürümlere yer güncelleştirmeleridir. Örneğin, .NET Framework 3.5 sürüm 2.0'a yerinde bir güncelleştirmedir ve .NET Framework 4.8 4 ile 4.7.2 sürümlerine yerinde güncelleştirmedir. Daha fazla bilgi için [bkz.](../migration-guide/versions-and-dependencies.md)

Windows 8'den önceki Windows sürümlerinde ,.NET Framework'u kaldırmayı seçerseniz, kaldıran Programları **ve Özellikleri** Her zaman Denetim Masası'ndan kullanın. .NET Framework'ün bir sürümünü asla el ile kaldırmayınız. Windows 8 ve üzeri üzerinde ,NET Framework bir işletim sistemi bileşenidir ve bağımsız olarak kaldırılamaz.

.NET Framework'ün birden çok sürümü aynı anda tek bir bilgisayarda bir arada bulunabilir. Bu, daha sonraki bir sürümü yüklemek için önceki sürümleri kaldırmanız gerekolmadığı anlamına gelir.

## <a name="net-framework-for-developers"></a>.NET Çerçevesi geliştiriciler için

Geliştiriciyseniz, uygulamalarınızı oluşturmak için .NET Framework'u destekleyen herhangi bir programlama dilini seçin. .NET Framework dil bağımsızlığı ve birlikte çalışabilirlik sağladığından, geliştirildikleri dilden bağımsız olarak diğer .NET Framework uygulamaları ve bileşenleriyle etkileşime geçersiniz.

.NET Framework uygulamaları veya bileşenleri geliştirmek için aşağıdakileri yapın:

1. İşletim sisteminizde önceden yüklenmemişse, uygulamanızın hedefalacağı .NET Framework sürümünü yükleyin. En son üretim sürümü .NET Framework 4.8'dir. Windows 10 Mayıs 2019 Güncelleştirmesi'nde önceden yüklenmiş ve Windows işletim sisteminin önceki sürümlerinde indirilebilir. .NET Framework sistem gereksinimleri için [Sistem Gereksinimleri'ne](system-requirements.md)bakın. .NET Framework'ün diğer sürümlerini yükleme hakkında daha fazla bilgi için [Yükleme Kılavuzu'na](../install/guide-for-developers.md)bakın. Ek .NET Framework paketleri bantdışında serbest bırakılır, bu da herhangi bir normal veya planlanmış sürüm döngüsü dışında piyasaya sürülebilecekleri anlamına gelir. Bu paketler hakkında bilgi için [.NET Framework ve Out-of-Band Bültenleri](the-net-framework-and-out-of-band-releases.md)bölümüne bakın.

2. Uygulamalarınızı geliştirmek için kullanmayı planladığınız .NET Framework sürümü tarafından desteklenen dili veya dili seçin. [Microsoft'tan Visual Basic,](../../visual-basic/index.yml) [C#](../../csharp/index.yml), [F#](../../fsharp/index.yml)ve [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) gibi birçok dil kullanılabilir. (.NET Framework için uygulamalar geliştirmenize olanak tanıyan bir programlama [dili, Ortak Dil Altyapısı (CLI) belirtimine](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)bağlıdır.)

3. Uygulamalarınızı oluşturmak için kullanılacak ve seçili programlama dilinizi veya dillerinizi destekleyen geliştirme ortamını seçin ve yükleyin. .NET Framework uygulamaları için Microsoft entegre geliştirme ortamı (IDE) [Visual Studio'dur.](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) Birkaç sürümde mevcuttur.

.NET Framework'u hedefleyen uygulamalar geliştirme hakkında daha fazla bilgi için [Geliştirme Kılavuzu'na](../development-guide.md)bakın.

## <a name="related-articles"></a>İlgili makaleler:

| Başlık | Açıklama |
| ----- |------------ |
| [Genel bakış](overview.md) | .NET Framework'u hedefleyen uygulamalar oluşturan geliştiriciler için ayrıntılı bilgiler sağlar. |
| [Yükleme kılavuzu](../install/index.md) | .NET Framework'ün yüklenmesi hakkında bilgi sağlar. |  
| [.NET Framework ve Out-of-Band Bültenleri](the-net-framework-and-out-of-band-releases.md) | .NET Framework out-of-band sürümlerini ve bunları uygulamanızda nasıl kullanacağınızı açıklar. |
| [Sistem Gereksinimleri](system-requirements.md) | .NET Framework'ün çalıştırılamıiçin donanım ve yazılım gereksinimlerini listeler. |
| [.NET Core ve Açık Kaynak](net-core-and-open-source.md) | .NET Framework ile ilgili olarak .NET Core'u ve açık kaynak kodlu .NET Core projelerine nasıl erişilir' i açıklar. |
| [.NET Çekirdek dokümantasyonu](../../core/index.md) | .NET Core için kavramsal ve API başvuru belgelerini sağlar. |
| [.NET Standard](../../standard/net-standard.md) | Tutarlı bir API kümesinin birden çok platformda kullanılabildiğini garanti etmek için tek tek .NET uygulamalarının desteklediği bir sürüm olan .NET Standard'ı tartışır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework kılavuzu](../index.yml)
- [Yenilikler](../whats-new/index.md)
- [.NET API tarayıcısı](../../../api/index.md)
- [Geliştirme rehberi](../development-guide.md)
