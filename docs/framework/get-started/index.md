---
title: .NET Framework kullanmaya başlayın
description: Uygulamaları yöneten bir çalışma zamanı yürütme ortamı olan .NET ' i kullanmaya başlayın. Ortak dil çalışma zamanı (CLR) ve kapsamlı bir sınıf kitaplığı içerir.
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: b6ad74d2984443a3b8345c2261996e7ab30acdff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621658"
---
# <a name="get-started-with-net-framework"></a>.NET Framework kullanmaya başlayın

.NET Framework, .NET Framework hedef uygulamaları yöneten bir çalışma zamanı yürütme ortamıdır. Bu, bellek yönetimi ve diğer sistem hizmetleri sağlayan ortak dil çalışma zamanından ve programcıların uygulama geliştirmenin tüm önemli alanlarında güçlü, güvenilir koddan yararlanmasını sağlayan kapsamlı bir sınıf kitaplığı içerir.

> [!NOTE]
> .NET Framework yalnızca Windows sistemlerinde kullanılabilir. Windows, MacOS ve Linux 'ta uygulama geliştirmek ve çalıştırmak için [.NET Core](../../core/index.yml) ' u kullanabilirsiniz.

## <a name="what-is-net-framework"></a>.NET Framework nedir?

.NET Framework, çalışan uygulamalarına çeşitli hizmetler sağlayan, Windows için yönetilen bir yürütme ortamıdır. İki ana bileşenden oluşur: çalışan uygulamaları işleyen yürütme altyapısı olan ortak dil çalışma zamanı (CLR) ve geliştiricilerin kendi uygulamalarından çağırabileceği, test edilmiş ve yeniden kullanılabilir bir kitaplık sağlayan .NET Framework sınıf kitaplığı. .NET Framework çalışan uygulamalar için sağlanan hizmetler şunları içerir:

- Bellek yönetimi. Birçok programlama dilinde, programcılar bellek ayırmayı ve serbest bırakmayı ve nesne ömrünü işlemeyi sorumludur. .NET Framework uygulamalarda, CLR bu Hizmetleri uygulama adına sağlar.

- Ortak bir tür sistemi. Geleneksel programlama dillerinde temel türler derleyici tarafından tanımlanır, bu da çapraz dil birlikte çalışabilirliği karmaşıklaştırır. .NET Framework, temel türler .NET Framework tür sistemi tarafından tanımlanır ve .NET Framework hedeflenen tüm dillerde ortaktır.

- Kapsamlı bir sınıf kitaplığı. Programcılar, sık kullanılan alt düzey programlama işlemlerini işlemek için çok miktarda kod yazmak yerine, .NET Framework sınıf kitaplığından bir tür ve üyeleri olan kolay erişilebilir bir kitaplık kullanır.

- Geliştirme çerçeveleri ve teknolojileri. .NET Framework, Web uygulamaları için ASP.NET, veri erişimi için ADO.NET, hizmet odaklı uygulamalar için Windows Communication Foundation ve Windows Masaüstü uygulamaları için Windows Presentation Foundation gibi belirli uygulama geliştirme alanlarının kitaplıklarını içerir.

- Dil birlikte çalışabilirliği. .NET Framework hedef olan dil derleyicileri, ortak ara dil (CıL) adlı bir ara kod yayarak ortak dil çalışma zamanı ile çalışma zamanında derlenir. Bu özellik ile, bir dilde yazılan yordamların diğer diller tarafından erişilebilir olması ve programcılar tercih ettiğiniz dillerde uygulama oluşturmaya odaklanmaktadır.

- Sürüm uyumluluğu. Nadir özel durumlar sayesinde, belirli bir .NET Framework sürümü kullanılarak geliştirilen uygulamalar, daha sonraki bir sürümde değişiklik yapılmadan çalışır.

- Yan yana yürütme. .NET Framework, aynı bilgisayarda ortak dil çalışma zamanının birden çok sürümünün var olmasına izin vererek sürüm çakışmalarını çözmeye yardımcı olur. Bu, birden çok uygulama sürümünün ve bir uygulamanın oluşturulduğu .NET Framework sürümünde çalışabileceği anlamına gelir. Yan yana yürütme, 1.0/1.1, 2.0/3.0/3.5 ve 4/4.5. x/4.6. x/4.7. x/4.8 sürüm grupları .NET Framework için geçerlidir.

- Çoklu sürüm desteği. [.NET Standard](../../standard/net-standard.md)hedefleyerek, geliştiriciler standart bu sürümü tarafından desteklenen birden çok .NET Framework platformda çalışan sınıf kitaplıkları oluşturur. Örneğin, .NET Standard 2,0 ' i hedefleyen kitaplıklar .NET Framework 4.6.1, .NET Core 2,0 ve UWP 10.0.16299 ' i hedefleyen uygulamalar tarafından kullanılabilir.

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Kullanıcılar için .NET Framework

.NET Framework uygulamalar geliştirmezseniz ancak bunları kullanıyorsanız, .NET Framework veya işlemi ile ilgili belirli bilgilere sahip olmanız gerekmez. Çoğu bölüm için Framework kullanıcılara tamamen saydamdır.

Windows işletim sistemi kullanıyorsanız, .NET Framework bilgisayarınızda zaten yüklü olabilir. Ayrıca, .NET Framework gerektiren bir uygulama yüklerseniz, uygulamanın kurulum programı bilgisayarınıza Framework 'ün belirli bir sürümünü yükleyebilirsiniz. Bazı durumlarda .NET Framework yüklemenizi isteyen bir iletişim kutusu görebilirsiniz. Bu iletişim kutusu göründüğünde bir uygulamayı çalıştırmaya çalıştıysanız ve bilgisayarınızda internet erişimi varsa, eksik .NET Framework sürümünü yüklemenize izin veren bir Web sayfasına gidebilirsiniz. Daha fazla bilgi için bkz. [Yükleme Kılavuzu](../install/index.md).

Genel olarak, bilgisayarınızda yüklü olan .NET Framework sürümlerini kaldırmamanız gerekir. Bunun iki nedeni vardır:

- Kullandığınız bir uygulama belirli bir .NET Framework sürümüne bağımlıysa, söz konusu sürüm kaldırılırsa bu uygulama kesintiye uğramayabilir.

- Bazı .NET Framework sürümleri, önceki sürümlere yönelik yerinde güncelleştirmelerdir. Örneğin .NET Framework 3,5, sürüm 2,0 ' ye yönelik bir yerinde güncelleştirmedir ve .NET Framework 4,8, 4 ile 4.7.2 arası sürümlere bir yerinde güncelleştirmedir. Daha fazla bilgi için bkz. [.NET Framework sürümler ve bağımlılıklar](../migration-guide/versions-and-dependencies.md).

Windows 8 ' den önceki Windows sürümlerinde, .NET Framework kaldırmayı seçerseniz, kaldırmak için Denetim Masası 'Ndaki **Programlar ve Özellikler** ' i her zaman kullanın. .NET Framework bir sürümünü el ile kaldırmayın. Windows 8 ve üzeri sürümlerde, .NET Framework bir işletim sistemi bileşenidir ve bağımsız olarak kaldırılamaz.

.NET Framework birden çok sürümü aynı anda tek bir bilgisayarda bulunabilir. Bu, daha sonraki bir sürümü yüklemek için önceki sürümleri kaldırmanız gerekmediği anlamına gelir.

## <a name="net-framework-for-developers"></a>Geliştiriciler için .NET Framework

Geliştiriciyseniz, uygulamalarınızı oluşturmak için .NET Framework destekleyen herhangi bir programlama dilini seçin. .NET Framework, Dil bağımsızlığı ve birlikte çalışabilirliği sağladığından, geliştirildiği dilden bağımsız olarak diğer .NET Framework uygulamalarıyla ve bileşenleriyle etkileşime geçebilirsiniz.

.NET Framework uygulamaları veya bileşenleri geliştirmek için aşağıdakileri yapın:

1. İşletim sisteminizde önceden yüklü değilse, uygulamanızın hedeflenecek .NET Framework sürümünü yüklemelisiniz. En son üretim sürümü .NET Framework 4,8 ' dir. Windows 10 Mayıs 2019 güncelleştirmesine önceden yüklenmiştir ve Windows işletim sisteminin önceki sürümlerinde indirilebilir. .NET Framework sistem gereksinimleri için bkz. [sistem gereksinimleri](system-requirements.md). .NET Framework diğer sürümlerini yükleme hakkında bilgi için bkz. [Yükleme Kılavuzu](../install/guide-for-developers.md). Ek .NET Framework paketleri bant dışında serbest bırakılır, bu da normal veya zamanlanmış herhangi bir yayın döngüsünün dışında, sıralı olarak yayımlandıkları anlamına gelir. Bu paketler hakkında daha fazla bilgi için bkz. [.NET Framework ve bant dışı yayınlar](the-net-framework-and-out-of-band-releases.md).

2. Uygulamalarınızı geliştirmek için kullanmayı düşündüğünüz .NET Framework sürümünün desteklediği dili veya dilleri seçin. [Visual Basic](../../visual-basic/index.yml), [C#](../../csharp/index.yml), [F #](../../fsharp/index.yml)ve Microsoft 'tan [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) dahil olmak üzere çeşitli diller mevcuttur. ( [Ortak dil altyapısı (CLI) belirtimine](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)bağlı .NET Framework uygulamalar geliştirmenize olanak tanıyan bir programlama dilidir.)

3. Uygulamalarınızı oluşturmak ve seçtiğiniz programlama dilini veya dillerini desteklemek için kullanmak üzere geliştirme ortamını seçin. .NET Framework uygulamalar için Microsoft tümleşik geliştirme ortamı (IDE), [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Çeşitli sürümlerde kullanılabilir.

.NET Framework hedefleyen uygulamalar geliştirme hakkında daha fazla bilgi için bkz. [geliştirme Kılavuzu](../development-guide.md).

## <a name="related-articles"></a>İlgili makaleler:

| Başlık | Açıklama |
| ----- |------------ |
| [Genel Bakış](overview.md) | .NET Framework hedefleyen uygulamalar oluşturan geliştiriciler için ayrıntılı bilgiler sağlar. |
| [Yükleme kılavuzu](../install/index.md) | .NET Framework yükleme hakkında bilgi sağlar. |  
| [.NET Framework ve bant dışı yayınlar](the-net-framework-and-out-of-band-releases.md) | Bant dışı yayınları .NET Framework ve bunları uygulamanızda nasıl kullanacağınızı açıklar. |
| [Sistem Gereksinimleri](system-requirements.md) | .NET Framework çalıştırmak için donanım ve yazılım gereksinimlerini listeler. |
| [.NET Core ve Açık Kaynak](net-core-and-open-source.md) | .NET Framework ve açık kaynaklı .NET Core projelerine nasıl erişebileceğiniz ile ilgili olarak .NET Core açıklanır. |
| [.NET Core belgeleri](../../core/index.yml) | .NET Core için kavramsal ve API başvuru belgelerini sağlar. |
| [.NET Standard](../../standard/net-standard.md) | Ayrı ayrı .NET uygulamalarının birden çok platformda kullanılabilir olduğunu garantilemek için tek tek .NET uygulamalarının desteklediği bir sürümlenmiş belirtim .NET Standard açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework kılavuzu](../index.yml)
- [Yenilikler](../whats-new/index.md)
- [.NET API tarayıcısı](../../../api/index.md)
- [Geliştirme kılavuzu](../development-guide.md)
