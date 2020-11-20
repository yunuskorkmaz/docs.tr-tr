---
title: .NET sürümleri, düzeltme ekleri ve destek
description: .NET 5 (.NET Core dahil) ve sonraki sürümleri için sürümler, düzeltme ekleri ve destek hakkında bilgi edinin.
ms.date: 10/07/2020
ms.topic: overview
ms.author: tdykstra
author: tdykstra
ms.openlocfilehash: 896b88cbf1f7f31d2d26d69ec7d219da6b27ceff
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982295"
---
# <a name="releases-and-support-for-net-core-and-net-5"></a>.NET Core ve .NET 5 için yayınlar ve destek

Microsoft, .NET 5,0 (ve .NET Core) ve sonraki sürümler için büyük yayınlar, ikincil yayınlar ve bakım güncelleştirmeleri (düzeltme ekleri) ile birlikte gelir. Bu makalede sürüm türleri, bakım güncelleştirmeleri, SDK Özellik bantları, destek süreleri ve destek seçenekleri açıklanmaktadır.

## <a name="release-types"></a>Sürüm türleri

Her yayının türü hakkındaki bilgiler, *büyük. Minor. Patch* biçimindeki sürüm numarası olarak kodlanır.

Örnek:

* .NET Core 3,0 ve NET 5,0 ana sürümlerdir.
* .NET Core 3,1, .NET Core 3,0 ana sürümünden sonraki ilk küçük sürümdür.
* .NET Core 3.1.7, .NET Core 3,1 için yedinci düzeltme ekinde bulunur.

### <a name="major-releases"></a>Ana yayınlar

Başlıca yayınlar yeni özellikler, yeni ortak API yüzey alanı ve hata düzeltmeleri içerir. .NET Core 3,0 ve .NET 5,0 örnekleri bulunur.  Değişikliklerin doğası gereği, bu sürümlerin büyük değişiklikler olması beklenir. Ana yayınlar önceki ana sürümleriyle yan yana yüklenir.

### <a name="minor-releases"></a>Küçük yayınlar

İkincil yayınlar Ayrıca yeni özellikler, genel API yüzey alanı ve hata düzeltmeleri içerir ve aynı zamanda değişikliklere neden olabilir. .NET Core 2,1 ve .NET Core 3,1 örnekleri bulunur. Bu ve ana yayınlar arasındaki fark, değişikliklerin büyüklüğünününü daha küçüktür. .NET Core 3,0 ' den 3,1 ' e yükseltme yapan bir uygulamanın ileri git 'e daha küçük bir sıçramadır. İkincil yayınlar önceki küçük sürümlerde yan yana yüklenir.

### <a name="servicing-updates"></a>Bakım güncelleştirmeleri

Bakım güncelleştirmeleri (düzeltme ekleri) neredeyse her ay sevk edin ve bu güncelleştirmeler hem güvenlik hem de güvenlik dışı hata düzeltmelerini taşır. Örneğin, .NET Core 3.1.8, .NET Core 3,1 için sekizinci güncelleştirmedir. Bu güncelleştirmeler güvenlik düzeltmelerini içerdiklerinde, her zaman ayın ikinci Salı günü olan "Düzeltme Eki Salı" sayfasında yayımlanır. Bakım güncelleştirmelerinin uyumluluğu sürdürmesine yönelik olması beklenmektedir. .NET Core 3,1 ile başlayarak, bakım güncelleştirmeleri önceki güncelleştirmeyi kaldırana yükseltmelerdir. Örneğin, 3,1 için en son bakım güncelleştirmesi başarıyla yüklendikten sonra önceki 3,1 güncelleştirmesini kaldırır.

### <a name="feature-bands-sdk-only"></a>Özellik bantları (yalnızca SDK)

.NET SDK için sürüm oluşturma, .NET çalışma zamanından biraz farklı şekilde çalışır. Yeni Visual Studio sürümleriyle uyum sağlamak için, .NET SDK güncelleştirmeleri bazen yeni özellikleri veya MSBuild ve NuGet gibi bileşenlerin yeni sürümlerini içerir. Bu yeni özellikler veya bileşenler, önceki SDK güncelleştirmelerinde aynı ana veya ikincil sürüm için sevk edilen sürümlerle uyumsuz olabilir.

.NET SDK, bu tür güncelleştirmeleri ayırt etmek için özellik bantları kavramını kullanır. Örneğin, ilk .NET Core 3,1 SDK 'Sı 3.1.100 idi. Bu sürüm, 3.1.1 xx  *özellik bandına* karşılık gelir. Özellik bantları, sürüm numarasının üçüncü bölümündeki yüzlerce grupta tanımlanmıştır. Örneğin, 3.1.101 ve 3.1.201, 3.1.101 ve 3.1.199 aynı özellik bandında olduğu sürece iki farklı özellik bantındaki sürümleridir. .NET Core SDK 3.1.101 yüklendiğinde, varsa .NET Core SDK 3.1.100 makineden kaldırılır. Aynı makineye .NET Core SDK 3.1.200 yüklendiğinde, .NET Core SDK 3.1.101 kaldırılmaz.

### <a name="runtime-roll-forward-and-compatibility"></a>Çalışma zamanı alma-iletme ve uyumluluk

Büyük ve küçük güncelleştirmeler önceki sürümlerle yan yana yüklenir. Belirli bir *ana. ikincil* sürümü hedeflemek için oluşturulmuş bir uygulama, daha yeni bir sürüm yüklü olsa bile bu hedeflenen çalışma zamanını kullanmaya devam eder. Uygulama, bu davranışı kabul etmediğiniz takdirde çalışma zamanının daha yeni bir *ana.* alt sürümünü kullanmak üzere otomatik olarak geri almaz. .NET Core 3,0 hedeflemesi için oluşturulan bir uygulama, .NET Core 3,1 ' de otomatik olarak çalışmaya başlamaz. Üretime dağıtım yapmadan önce uygulamayı ve test etmeyi daha yeni bir büyük veya küçük çalışma zamanı sürümüne karşı yeniden oluşturmayı öneririz. Daha fazla bilgi için bkz. [çerçeveye bağımlı uygulamalar ileri](versions/selection.md#framework-dependent-apps-roll-forward) ve [kendine dahil edilen dağıtım çalışma zamanı ileri](deploying/runtime-patch-selection.md).

Bakım güncelleştirmeleri, büyük ve küçük sürümlerden farklı olarak değerlendirilir. .NET Core 3,1 hedeflemesi için oluşturulmuş bir uygulama varsayılan olarak 3.1.0 çalışma zamanında çalışır. Hizmet güncelleştirme yüklendiğinde, daha yeni bir 3.1.1 çalışma zamanı kullanmak için otomatik olarak ileriye kaydedilir. Bu davranış varsayılandır çünkü güvenlik düzeltmelerinin, gerekli başka bir eylem olmadan yüklendikleri anda kullanılmasını istiyoruz. Bu varsayılan ileri alma davranışından vazgeçebilirsiniz.

## <a name="net-core-and-net-5-version-lifecycles"></a>.NET Core ve .NET 5 sürüm yaşam döngüsü

.NET Core, .NET 5 ve sonraki sürümler .NET Framework sürümleri için kullanılan [sabit yaşam döngüsü](/lifecycle/policies/fixed) yerine [modern yaşam döngüsünü](/lifecycle/policies/modern) benimseyin. Sabit ömürleri olan ürünler, 5 yıl temel destek ve 5 yıllık uzatılmış destek gibi uzun bir destek süresi sağlar. Temel destek güvenlik ve güvenlik dışı düzeltmeleri içerir, ancak genişletilmiş destek yalnızca güvenlik düzeltmeleri sağlar. Modern yaşam döngüsünü benimseyen ürünlerin daha kısa destek süreleri ve daha sık sürümler içeren daha fazla hizmet benzeri destek modeli vardır.

### <a name="release-tracks"></a>Yayın izleri

Yayınlar için iki destek parçası vardır:

* *Geçerli* yayınlar

  Bu sürümler, sonraki büyük veya küçük sürümden sonra 3 ay sonra desteklenir.

  Örnek:

  * .NET Core 3,0 Eylül 2019 ' de gönderilmiştir ve sonrasında .NET Core 3,1, Aralık 2019 ' de gelir.
  * .NET Core 3,0 desteği, 2020 Mart 'ta, 3,1 gönderildikten sonra 3 ay sonra sona erdi.

* *Uzun süreli destek* (LTS) yayınları

  Bu sürümler, en az 3 yıl veya sonraki LTS sürümünün bu tarih daha sonra sevk edildikten 1 yıl sonra desteklenir.

  Örnek:

  * .NET Core 2,1 Mayıs 2018 ' de yayımlanmıştır ve 2018 Ağustos ayında bir LTS sürümü kabul edildi.
  * .NET Core 3,1, sonraki LTS sürümündedir ve 2019 Aralık 'ta yayımlanmıştır.
  * Ağustos 2021 (3 yıl), Aralık 2020 ' den daha sonra (3,1 sürümünden sonraki bir yılda), .NET Core 2,1, Ağustos 2021 aracılığıyla desteklenir.

LTS ve Current arasında alternatif yayınlar, bu nedenle daha önceki bir sürümün daha yeni bir sürümden daha uzun bir süre desteklenmesi mümkündür. Örneğin, .NET Core 2,1, 2021 destek içeren bir LTS sürümüdür. 3,0 sürümü daha sonra bir yıldan fazla sevk edildi ancak 2019 Aralık 'ta daha önce destek kalmadı.

Bakım güncelleştirmeleri aylık olarak ve güvenlik ve güvenlik dışı (güvenilirlik, uyumluluk ve kararlılık) düzeltmeleri içerir. Bakım güncelleştirmeleri, sonraki bakım güncelleştirmesi yayımlanıncaya kadar desteklenir. Bakım güncelleştirmelerinde çalışma zamanı iletme davranışı vardır. Diğer bir deyişle, uygulamalar varsayılan olarak en son yüklenen çalışma zamanı hizmet güncelleştirmesi üzerinde çalışır.

## <a name="how-to-choose-a-release"></a>Yayın seçme

Bir hizmet oluşturuyorsanız ve bunu düzenli olarak güncelleştirmeye devam ediyorsanız, .NET 5,0 gibi geçerli bir yayın, .NET 'in sunabileceği en son özelliklerle güncel kalmak için en iyi seçenektir.

Tüketicilere dağıtılacak bir istemci uygulaması oluşturuyorsanız, kararlılık en son özelliklere erişimle daha fazla önemli olabilir. Tüketici uygulamanın bir sonraki sürümüne yükseltebilmesi için uygulamanızın belirli bir süre için desteklenmesi gerekebilir. Bu durumda, .NET Core 3,1 gibi bir LTS sürümü doğru seçenek olabilir.

### <a name="servicing-updates"></a>Bakım güncelleştirmeleri

Bir sonraki bakım güncelleştirmesi yayımlanıncaya kadar .NET hizmet güncelleştirmeleri desteklenir. Yayın temposunda aylık.

Uygulamalarınızın güvenli ve desteklenen bir durumda olduğundan emin olmak için düzenli olarak bakım güncelleştirmeleri yüklemeniz gerekir. Örneğin, .NET Core 3,1 için en son bakım güncelleştirmesi 3.1.8 ve 3.1.9 gönderdiğimiz takdirde, 3.1.8 artık en son. 3,1 için desteklenen bakım düzeyi 3.1.9.

Her bir birincil ve ikincil sürüm için en son bakım güncelleştirmeleri hakkında bilgi için bkz. [.net İndirmeleri sayfası](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="end-of-support"></a>Destek sonu

Destek sonu, Microsoft 'un bir ürün sürümü için düzeltme, güncelleştirme veya teknik yardım sağlamaz. Bu tarihten önce, desteklenen bir sürümü kullanmaya taşıntığınızdan emin olun. Destek dışı olan sürümler artık uygulamalarınızı ve verilerinizi koruyan güvenlik güncelleştirmeleri almaz.

## <a name="supported-operating-systems"></a>Desteklenen işletim sistemleri

.NET 5 (ve .NET Core) ve sonraki sürümler, bir dizi işletim sisteminde çalıştırılabilir. Bu işletim sistemlerinin her biri, sponsor kuruluş tarafından tanımlanan bir yaşam döngüsüne sahiptir (örneğin, Microsoft, Red hat veya Apple). Bu yaşam döngüsü zamanlamalarını, işletim sistemi sürümleri için destek ekleme ve kaldırma sırasında dikkate alır.

Bir işletim sistemi sürümü destek dışında kaldığında, bu sürümü test etmeyi ve bu sürüm için destek sağlamayı durdurduk. Destek almak için kullanıcıların desteklenen bir işletim sistemi sürümüne ilerlememeniz gerekir.

Daha fazla bilgi için bkz. [.net OS yaşam döngüsü ilkesi](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md).

## <a name="get-support"></a>Destek alma

Microsoft yardımlı destek ve topluluk desteği arasında seçim yapabilirsiniz.

### <a name="microsoft-support"></a>Microsoft desteği

Yardımlı destek için [Microsoft desteği Professional ile iletişim kurun](https://support.microsoft.com/supportforbusiness/productselection/?sapid=4fd4947b-15ea-ce01-080f-97f2ca3c76e8).

Destek için uygun olması için desteklenen bir bakım düzeyinde (en son kullanılabilir bakım güncelleştirmesi) olmanız gerekir. Bir sistem 3,1 çalıştırıyorsa ve 3.1.8 bakım güncelleştirmesi yayımlanmışsa, 3.1.8 'nin ilk adım olarak yüklenmesi gerekir.

### <a name="community-support"></a>Topluluk desteği

Topluluk desteği için [topluluk sayfasına](https://dotnet.microsoft.com/platform/community)bakın.

## <a name="see-also"></a>Ayrıca bkz.

.NET Core 'un her sürümü ve .NET 5 için desteklenen tarih aralıkları dahil daha fazla bilgi için bkz. [destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).
