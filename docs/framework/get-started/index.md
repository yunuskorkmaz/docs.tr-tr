---
title: .NET Framework kullanmaya başlayın
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: cb56097d49b194234031aba3ee9811b961ae6c64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107718"
---
# <a name="get-started-with-the-net-framework"></a>.NET Framework kullanmaya başlayın

.NET Framework, .NET Framework hedef uygulamaları yöneten bir çalışma zamanı yürütme ortamıdır. Bu, bellek yönetimi ve diğer sistem hizmetleri sağlayan ortak dil çalışma zamanından ve programcıların uygulama geliştirmenin tüm önemli alanlarında güçlü, güvenilir koddan yararlanmasını sağlayan kapsamlı bir sınıf kitaplığı içerir.

> [!NOTE] 
> .NET Framework yalnızca Windows sistemlerinde kullanılabilir. Windows, MacOS ve Linux 'ta uygulama çalıştırmak için [.NET Core](../../core/index.md) ' u kullanabilirsiniz. 

## <a name="Introducing"></a>.NET Framework nedir?

.NET Framework, çalışan uygulamalarına çeşitli hizmetler sağlayan Windows için yönetilen bir yürütme ortamıdır. İki ana bileşenden oluşur: çalışan uygulamaları işleyen yürütme altyapısı olan ortak dil çalışma zamanı (CLR) ve geliştiricilerin kendi uygulamalarından çağırabileceği, test edilmiş ve yeniden kullanılabilir bir kitaplık sağlayan .NET Framework sınıf kitaplığı. .NET Framework uygulamaları çalıştırmak için sağladığı hizmetler şunlardır:

- Bellek yönetimi. Birçok programlama dilinde, programcılar bellek ayırmayı ve serbest bırakmayı ve nesne ömrünü işlemeyi sorumludur. .NET Framework uygulamalarda, CLR bu Hizmetleri uygulama adına sağlar.

- Ortak bir tür sistemi. Geleneksel programlama dillerinde temel türler derleyici tarafından tanımlanır, bu da çapraz dil birlikte çalışabilirliği karmaşıklaştırır. .NET Framework, temel türler .NET Framework tür sistemi tarafından tanımlanır ve .NET Framework hedefleyen tüm diller için ortaktır.

- Kapsamlı bir sınıf kitaplığı. Programcılar, sık kullanılan alt düzey programlama işlemlerini işlemek için çok miktarda kod yazmak yerine, .NET Framework sınıf kitaplığından bir tür ve üyeleri olan kolay erişilebilir bir kitaplık kullanır.

- Geliştirme çerçeveleri ve teknolojileri. .NET Framework, Web uygulamaları için ASP.NET, veri erişimi için ADO.NET, hizmet odaklı uygulamalar için Windows Communication Foundation ve Windows Masaüstü uygulamaları için Windows Presentation Foundation gibi belirli uygulama geliştirme alanlarının kitaplıklarını içerir.

- Dil birlikte çalışabilirliği. .NET Framework hedefleyen dil derleyicileri ortak ara dil (CıL) adlı bir ara kod yayarak ortak dil çalışma zamanı ile çalışma zamanında derlenir. Bu özellik ile, bir dilde yazılan yordamların diğer diller tarafından erişilebilir olması ve programcılar tercih ettiğiniz dillerde uygulama oluşturmaya odaklanmaktadır.

- Sürüm uyumluluğu. Nadir özel durumlar sayesinde, .NET Framework belirli bir sürümü kullanılarak geliştirilen uygulamalar, daha sonraki bir sürümde değişiklik yapılmadan çalışır.

- Yan yana yürütme. .NET Framework, aynı bilgisayarda ortak dil çalışma zamanının birden çok sürümünün var olmasına izin vererek sürüm çakışmalarını çözmeye yardımcı olur. Bu, birden çok uygulama sürümünün ve bir uygulamanın oluşturulduğu .NET Framework sürümünde çalışabileceği anlamına gelir. Yan yana yürütme, 1.0/1.1, 2.0/3.0/3.5 ve 4/4.5. x/4.6. x/4.7. x/4.8 sürüm grupları .NET Framework için geçerlidir.

- Çoklu sürüm desteği. [.NET Standard](../../standard/net-standard.md)hedefleyerek, geliştiriciler standart bu sürümü tarafından desteklenen birden çok .NET Framework platformda çalışan sınıf kitaplıkları oluşturur. Örneğin, 2,0 .NET Standard hedefleyen kitaplıklar .NET Framework 4.6.1, .NET Core 2,0 ve UWP 10.0.16299 ' yi hedefleyen uygulamalar tarafından kullanılabilir. 

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Kullanıcılar için .NET Framework

.NET Framework uygulamalar geliştirmezseniz ancak bunları kullanıyorsanız, .NET Framework veya işlemi hakkında belirli bilgilere sahip olmanız gerekmez. Çoğu bölüm için .NET Framework kullanıcılara tamamen saydamdır.

Windows işletim sistemi kullanıyorsanız, .NET Framework bilgisayarınızda zaten yüklü olabilir. Ayrıca, .NET Framework gerektiren bir uygulama yüklerseniz, uygulamanın kurulum programı bilgisayarınıza .NET Framework belirli bir sürümünü kurabilir. Bazı durumlarda, .NET Framework yüklemenizi isteyen bir iletişim kutusu görebilirsiniz. Bu iletişim kutusu göründüğünde bir uygulamayı çalıştırmaya çalıştıysanız ve bilgisayarınızda Internet erişimi varsa, .NET Framework eksik sürümünü yüklemenize izin veren bir Web sayfasına gidebilirsiniz. Daha fazla bilgi için bkz. [Yükleme Kılavuzu](../install/index.md).

Genel olarak, bilgisayarınızda yüklü olan .NET Framework sürümlerini kaldırmamanız gerekir. Bunun iki nedeni vardır:

- Kullandığınız bir uygulama .NET Framework belirli bir sürümüne bağımlıysa, söz konusu sürüm kaldırılırsa bu uygulama kesintiye uğramayabilir.

- .NET Framework bazı sürümleri, önceki sürümlere yönelik yerinde güncelleştirmelerdir. Örneğin .NET Framework 3,5, sürüm 2,0 ' ye yönelik bir yerinde güncelleştirmedir ve .NET Framework 4,8, 4 ile 4.7.2 arası sürümlere yönelik bir yerinde güncelleştirmedir. Daha fazla bilgi için bkz. [.NET Framework sürümler ve bağımlılıklar](../migration-guide/versions-and-dependencies.md).

Windows 8 ' den önceki Windows sürümlerinde, .NET Framework kaldırmayı seçerseniz, kaldırmak için Denetim Masası 'Ndaki **Programlar ve Özellikler** ' i her zaman kullanın. .NET Framework sürümünü hiçbir şekilde el ile kaldırmayın. Windows 8 ve üzeri sürümlerde .NET Framework bir işletim sistemi bileşenidir ve bağımsız olarak kaldırılamaz.

.NET Framework birden çok sürümü aynı anda tek bir bilgisayarda birlikte bulunabilir. Bu, daha sonraki bir sürümü yüklemek için önceki sürümleri kaldırmanız gerekmediği anlamına gelir.

## <a name="ForDevelopers"></a>Geliştiriciler için .NET Framework

Geliştiriciyseniz, uygulamalarınızı oluşturmak için .NET Framework destekleyen herhangi bir programlama dilini seçin. .NET Framework dil bağımsızlığı ve birlikte çalışabilirliği sağladığından, geliştirildiği dilden bağımsız olarak diğer .NET Framework uygulamalarıyla ve bileşenleriyle etkileşime geçin.

.NET Framework uygulamaları veya bileşenleri geliştirmek için aşağıdakileri yapın:

1. İşletim sisteminizde önceden yüklü değilse, uygulamanızın hedefleyecek .NET Framework sürümünü yüklemelisiniz. En son üretim sürümü 4,8 .NET Framework. Windows 10 Mayıs 2019 güncelleştirmesine önceden yüklenmiştir ve Windows işletim sisteminin önceki sürümlerinde indirilebilir. .NET Framework sistem gereksinimleri için bkz. [sistem gereksinimleri](system-requirements.md). .NET Framework diğer sürümlerini yükleme hakkında bilgi için bkz. [Yükleme Kılavuzu](../install/guide-for-developers.md). Ek .NET Framework paketleri bant dışında serbest bırakılır, bu da normal veya zamanlanmış herhangi bir yayın döngüsünün dışında, sıralı olarak yayımlandıkları anlamına gelir. Bu paketler hakkında daha fazla bilgi için bkz. [.NET Framework ve bant dışı yayınlar](the-net-framework-and-out-of-band-releases.md).

2. Uygulamalarınızı geliştirmek için kullanmayı düşündüğünüz .NET Framework tarafından desteklenen dili veya dilleri seçin. Microsoft 'tan [Visual Basic](../../visual-basic/index.md), [C#](../../csharp/index.md), [F#](../../fsharp/index.md)ve [ C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) dahil olmak üzere çeşitli diller mevcuttur. (.NET Framework uygulamalar geliştirmenize olanak tanıyan bir programlama dili, [ortak dil altyapısı (CLI) belirtimine](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)uyar.)

3. Uygulamalarınızı oluşturmak ve seçtiğiniz programlama dilini veya dillerini desteklemek için kullanmak üzere geliştirme ortamını seçin. .NET Framework uygulamalar için Microsoft tümleşik geliştirme ortamı (IDE), [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Çeşitli sürümlerde kullanılabilir.

.NET Framework hedefleyen uygulamalar geliştirme hakkında daha fazla bilgi için bkz. [geliştirme Kılavuzu](../development-guide.md).

## <a name="related-articles"></a>İlgili makaleler

| Başlık | Açıklama |
| ----- |------------ |
| [Genel bakış](overview.md) | .NET Framework hedefleyen uygulamalar oluşturan geliştiriciler için ayrıntılı bilgiler sağlar. |
| [Yükleme kılavuzu](../install/index.md) | .NET Framework yükleme hakkında bilgi sağlar. |  
| [.NET Framework ve Bant Dışı Yayınlar](the-net-framework-and-out-of-band-releases.md) | Bant dışı yayınların .NET Framework ve bunları uygulamanızda nasıl kullanacağınızı açıklar. |
| [Sistem Gereksinimleri](system-requirements.md) | .NET Framework çalıştırmak için donanım ve yazılım gereksinimlerini listeler. |
| [.NET Core ve Açık Kaynak](net-core-and-open-source.md) | .NET Framework ile ilgili olarak .NET Core ve açık kaynaklı .NET Core projelerine nasıl erişebileceğinizi açıklar. |
| [.NET Core belgeleri](../../core/index.md) | .NET Core için kavramsal ve API başvuru belgelerini sağlar. |
| [.NET Standard](../../standard/net-standard.md) | Tek tek .NET uygulamalarının birden çok platformda kullanılabilir olan tutarlı bir API kümesinin olduğunu güvence altına almak için destekledikleri bir sürümlenmiş belirtim olan .NET Standard açıklanmaktadır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Kılavuzu](../index.md)
- [Yenilikler](../whats-new/index.md)
- [.NET API tarayıcısı](../../../api/index.md)
- [Geliştirme Kılavuzu](../development-guide.md)
