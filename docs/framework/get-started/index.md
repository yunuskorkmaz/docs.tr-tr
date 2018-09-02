---
title: .NET Framework ile çalışmaya başlama
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aef77e6f2ec572ec0969166770aaf617cc933d67
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387779"
---
# <a name="get-started-with-the-net-framework"></a>.NET Framework ile çalışmaya başlama

.NET Framework, .NET Framework'ü hedefleyen uygulamaları yöneten bir çalışma zamanı yürütme ortamıdır. Bu, bellek yönetimi ve diğer sistem hizmetlerini ve sağlam yararlanmak programcılar sağlayan kapsamlı bir sınıf kitaplığı, sağlayan ortak dil çalışma zamanı, uygulama geliştirmenin bütün önemli alanları için güvenilir kod oluşur.

> [!NOTE] 
> .NET Framework, yalnızca Windows sistemlerinde kullanılabilir. Kullanabileceğiniz [.NET Core](../../core/index.md) uygulamaları Windows, MacOS ve Linux üzerinde çalıştırılacak. 

<a name="Introducing"></a>
## <a name="what-is-the-net-framework"></a>.NET Framework nedir?

.NET Framework, hizmetleri, çalışan uygulamalarına çeşitli sağlayan Windows için bir yönetilen yürütme ortamıdır. İki ana bileşenden oluşur: uygulamalar ve kitaplığı sınanmış, .NET Framework sınıf kitaplığı, çalışan işleyen yürütme motoru ortak dil çalışma zamanı (CLR), geliştiricilerin kendi uygulamalardan arayabileceğiniz yeniden kullanılabilir bir kod. .NET Framework uygulamalarını çalıştırmak için sağladığı hizmetler şunları içerir:

- Bellek yönetimi. Birçok programlama dilinde, programcılar ayırma ve bellek serbest bırakma ve nesne kullanım ömrü işlemesinden sorumludur. .NET Framework uygulamalarında CLR, uygulama adına bu hizmetleri sağlar.

- Ortak tür sistemi. Geleneksel programlama dillerinde, temel türler diller arası birlikte çalışabilirlik karmaşıklaştırır derleyici tarafından tanımlanır. .NET Framework'teki temel türler .NET Framework tür sistemi tarafından tanımlanır ve .NET Framework'ü hedefleyen tüm diller için ortaktır.

- Kapsamlı bir sınıf kitaplığı. Muazzam miktarlardaki ortak düşük düzeydeki programlama işlemlerini işlemek için kod yazmak zorunda kalmak yerine programcılar .NET Framework Sınıf Kitaplığı'ndan bir tür ve üyelerin erişilebilir kitaplığını kullanın.

- Geliştirme çerçeveleri ve teknolojileri. .NET Framework, ASP.NET web uygulamaları için ADO.NET veri erişimi için Windows Communication Foundation Hizmet odaklı uygulamalar ve Masaüstü uygulamaları için Windows Presentation Foundation Windows gibi uygulama geliştirmenin belirli alanlarına kitaplıkları içerir.

- Diller arası çalışabilirlik. .NET Framework'ü hedefleyen dil derleyicileri, ortak Ara dil (hangi sırayla, ortak dil çalışma zamanı tarafından çalışma zamanında derlenmiş CIL), adlandırılmış bir ara kod üretir. Bu özellik sayesinde tek bir dilde yazılan yordamlar diğer diller ve kendi tercih edilen dillerde uygulamalar oluşturmaya odaklanın programcıları için erişilebilir.

- Sürüm uyumluluğu. Nadir istisnalar ile .NET Framework'ün belirli bir sürümü kullanılarak geliştirilen uygulamalar, sonraki bir sürümü üzerinde hiçbir değişikliğe gerek olmadan çalıştırın.

- Yan yana yürütme. .NET Framework sürüm çakışmaları birden çok sürümünü aynı bilgisayarda ortak dil çalışma zamanı sağlayarak yardımcı olur. Bu uygulamalar birden çok sürümünü bulunabilir ve uygulama ile oluşturulan .NET Framework sürümünde çalıştırabileceğiniz anlamına gelir. Yan yana yürütme, .NET Framework sürüm grupları 1.0/1.1, 2.0/3.0/3.5 ve 4/4.5.x/4.6.x/4.7.x uygulanır.

- Çoklu sürüm desteği. Hedefleyerek [.NET Standard](~/docs/standard/net-standard.md), geliştiricilerin üzerinde standart'ın bu sürümü tarafından desteklenen birden çok .NET Framework platformunda çalışan sınıf kitaplıkları oluşturun. Örneğin, .NET Standard 2.0 hedefleyen kitaplıklar, .NET Framework 4.6.1, .NET Core 2.0 ve UWP 10.0.16299 hedefleyen uygulamalar tarafından kullanılabilir. 

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Kullanıcılar için .NET Framework

.NET Framework uygulamaları geliştirme yoktur, ancak bunları kullanmak, .NET Framework veya işleyişi hakkında belirli bilgilere sahip gerekmez. Çoğunlukla, .NET Framework kullanıcılara tamamen saydamdır.

Windows işletim sistemi kullanıyorsanız, .NET Framework bilgisayarınızda zaten yüklü. Ayrıca, .NET Framework gerektiren bir uygulama yüklerseniz uygulamanın kurulum programı bilgisayarınıza .NET Framework'ün belirli bir sürümünü yükleyebilirsiniz. Bazı durumlarda, .NET Framework'ü yüklemek isteyen bir iletişim kutusu görebilirsiniz. Yalnızca bu iletişim kutusu göründüğünde ve bilgisayarınızın Internet erişimi varsa uygulama çalıştırmayı denediyseniz, eksik sürümü .NET Framework'ün yüklemenize olanak sağlayan bir Web sayfasına gidebilirsiniz. Daha fazla bilgi için [Yükleme Kılavuzu](../install/index.md).

Genel olarak, bilgisayarınızda yüklü .NET Framework sürümlerini kaldırmanız gerekir. Bunun iki nedeni vardır:

- Kullandığınız uygulama .NET Framework'ün belirli bir sürüme bağlı olduğu durumlarda, uygulama o sürüm kaldırılırsa kesilmesine neden olabilir.

- .NET Framework'ün bazı sürümleri, önceki sürümlerin yerinde güncelleştirmelerdir. Örneğin, [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] sürüm 2.0 bir yerinde güncelleştirmedir ve 4.7.2 .NET Framework sürüm 4 4.7.1 aracılığıyla için bir yerinde güncelleştirmedir. Daha fazla bilgi için [.NET Framework sürümleri ve bağımlılıkları](../../../docs/framework/migration-guide/versions-and-dependencies.md).

Windows 8 öncesi Windows sürümlerinde .NET Framework'ü seçerseniz, her zaman kullanın **programlar ve Özellikler** kaldırmak için Denetim Masası'ndan. Hiçbir zaman bir .NET Framework sürümünü el ile kaldırın. Windows 8 ve üzeri, .NET Framework, işletim sisteminin bir bileşeni olan ve bağımsız olarak kaldırılamaz.

.NET Framework'ün birden çok sürümü aynı anda tek bir bilgisayarda bulunabilir unutmayın. Başka bir deyişle, sonraki bir sürümünü yüklemek için önceki sürümlerini kaldırmanız gerekmez.

<a name="ForDevelopers"></a> 
## <a name="the-net-framework-for-developers"></a>Geliştiriciler için .NET Framework

Bir geliştiriciyseniz, uygulamalarınızı oluşturmak için .NET Framework'ü destekleyen herhangi bir programlama dilini seçin. .NET Framework dil bağımsızlığı ve birlikte çalışabilirliği sağladığından, diğer .NET Framework uygulamaları ve bileşenleri ile bunların geliştirilen diline bakılmaksızın ile etkileşim kurun.

.NET Framework uygulamaları veya bileşenleri geliştirmek için aşağıdakileri yapın:

1. İşletim sisteminize göre önceden değil, uygulamanızı hedefleyen .NET Framework sürümünü yükleyin. En son üretim sürümü .NET, Windows önceden 4.7.2, altyapısıdır 10 Nisan 2018 güncelleştirmesi ve Windows işletim sisteminin önceki sürümlerinde indirilebilir. .NET Framework sistem gereksinimleri için bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md). .NET Framework'ın diğer sürümlerinin yüklenmesi hakkında daha fazla bilgi için bkz: [Yükleme Kılavuzu](../../../docs/framework/install/guide-for-developers.md). Ek .NET Framework paketleri, sıralı olarak dışında tüm normal veya zamanlanmış sürüm döngüsü yayımlandıktan, yani bant dışı bırakılır. Bu paketler hakkında daha fazla bilgi için bkz: [.NET Framework ve bant dışı yayınlar](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).

2. Uygulamalarınızı geliştirmek için kullanmak istediğiniz .NET Framework tarafından desteklenen diller ve dil seçin. Çok sayıda dil kullanılabilir dahil olmak üzere [Visual Basic](../../visual-basic/index.md), [C#](../../csharp/index.md), [F #](../../fsharp/index.md)ve C + +/ CLI Microsoft gelen. (Aynılarını .NET Framework için uygulamalar geliştirmenizi sağlayan bir programlama dili [ortak dil altyapısı (CLI) belirtimi](https://go.microsoft.com/fwlink/?LinkId=199862).)

3. Seçin ve yükleyin geliştirme ortamı, uygulamalarınızı ve, oluşturmak üzere kullanmak için seçtiğiniz programlama dilini veya dillerini destekler. .NET Framework uygulamaları için Microsoft tümleşik geliştirme ortamıdır (IDE) [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Sürümleri bir süre içinde kullanılabilir.

.NET Framework'ü hedefleyen uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [geliştirme Kılavuzu](../../../docs/framework/development-guide.md).

## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| ----- |------------ |
| [Genel bakış](../../../docs/framework/get-started/overview.md) | .NET Framework'ü hedefleyen uygulamalar oluşturan geliştiriciler için ayrıntılı bilgi sağlar. |
| [Yükleme kılavuzu](../../../docs/framework/install/index.md) | .NET Framework'ü yükleme hakkında bilgi sağlar. |  
| [.NET Framework ve Bant Dışı Yayınlar](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md) | .NET Framework bant dışı yayınlar ve bunları uygulamanızda nasıl kullanacağınızı açıklar. |
| [Sistem Gereksinimleri](../../../docs/framework/get-started/system-requirements.md) | .NET Framework çalıştırmak için donanım ve yazılım gereksinimleri listelenmiştir. |
| [.NET Core ve Açık Kaynak](../../../docs/framework/get-started/net-core-and-open-source.md) | .NET Core .NET Framework ve açık kaynak .NET Core projeleri erişim ile ilgili olarak açıklar. |
| [.NET core belgeleri](https://docs.microsoft.com/dotnet/) | Kavramsal sağlar ve .NET Core için API başvuru belgeleri. |
| [.NET Standard](~/docs/standard/net-standard.md) | Tutarlı bir API kümesi birden çok platformda kullanılabilir olduğunu garanti etmek için tek tek .NET uygulamaları destekleyen bir sürüm bilgisi belirtimi .NET Standard açıklanır.

## <a name="see-also"></a>Ayrıca bkz.

[.NET framework Kılavuzu](../../../docs/framework/index.md)   
[Yenilikler](../../../docs/framework/whats-new/index.md)   
[.NET API tarayıcısı](/dotnet/api/)   
[Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)
