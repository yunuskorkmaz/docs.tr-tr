---
title: SDK ve .NET Core çalışma zamanı nasıl belirlendiği
description: Bu makalede çalışma zamanı ve .NET Core SDK'sı sürümü (benzer anlamsal sürüm) şeklini öğretir.
author: bleroy
ms.date: 07/26/2018
ms.custom: seodec18
ms.openlocfilehash: 54b09a6b74b2cf213cea781dec95a413ac2ad059
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170723"
---
# <a name="overview-of-how-net-core-is-versioned"></a>.NET Core nasıl tutulan genel bakış

.NET core, .NET Core çalışma zamanı ve .NET Core uygulamaları geliştirmek için ihtiyacınız olan araçları içeren SDK, ifade eder. .NET core SDK'ları, .NET Core çalışma zamanı'nın önceki bir sürümüyle çalışacak şekilde tasarlanmıştır. Bu makalede, çalışma zamanını ve SDK sürüm stratejisi açıklanmaktadır. .NET Standard için sürüm numaraları açıklaması ile tanışın makalede bulunabilir [.NET Standard](../../standard/net-standard.md#net-implementation-support).

.NET Core çalışma zamanı ve .NET Core SDK'sı, farklı bir fiyat karşılığında yeni özellikler eklemek - genel araçları daha fazla .NET Core çalışma zamanı, üretimde kullandığınız çalışma zamanı değişiklikleri daha hızlı bir şekilde güncelleştirilmiş .NET Core SDK'sı sağlar. Ne yazık ki bu sorun son birkaç yılda birkaç sürüm stratejilerine sonuçlandı. Üzerinde makaledeki geçmişi hakkında bilgi edinebilirsiniz [.NET Core sürüm](version-history.md).

## <a name="versioning-details"></a>Sürüm oluşturma ayrıntıları

".NET Core 2.1".NET Core çalışma zamanı sürüm numarasını ifade eder. .NET Core çalışma zamanı izleyen sürüm oluşturma için büyük/küçük/düzeltme eki bir yaklaşım olan [semantic versioning](#semantic-versioning).

.NET Core SDK'sını semantic versioning izleyin değil. .NET Core SDK'sını daha hızlı serbest bırakır ve kendi sürümleri hem hizalanmış çalışma zamanını ve SDK'ın kendi küçük ve yayınlar düzeltme eki iletişim kurması gerekir. .NET Core çalışma zamanı ile yayımlanan ilk iki .NET Core SDK'sı sürüm konumlarını kilitlenir. Her bir SDK sürümü, bu çalışma zamanı veya herhangi bir alt sürümü için uygulamalar oluşturabilirsiniz.

SDK sürüm numarasının üçüncü konumu hem küçük iletişim kurar ve düzeltme numarası. Alt sürüm 100 ile çarpılır. İkincil sürüm 1, 2 düzeltme eki sürümü 102 olarak temsil edilir. Son iki basamak düzeltme numarasını temsil eder. Örneğin, .NET Core 2.2 sürümünü sürümleri aşağıdaki tabloda gibi oluşturabilirsiniz:

| Değiştir                | .NET core çalışma zamanı | .NET core SDK'sı (*) |
|-----------------------|-------------------|-------------------|
| İlk yayın       | 2.2.0             | 2.2.100           |
| SDK'sı düzeltme eki             | 2.2.0             | 2.2.101           |
| Çalışma zamanını ve SDK'sı düzeltme eki | 2.2.1             | 2.2.102           |
| SDK'sı özelliği değiştirme    | 2.2.1             | 2.2.200           |

(\*) Bu grafik gelecekteki 2.2 kullanan .NET Core çalışma zamanı örnek olarak bir geçmiş yapıt ilk SDK'sı için .NET Core 2.1 anlamına geldiğinden 2.1.300 olduğu. Daha fazla bilgi için [.NET Core sürümü oluşturma geçmişine](version-history.md).

NOTLAR:

* SDK'sı 10 özellik güncelleştirmeleri bir çalışma zamanı özelliği güncelleştirmeden önce sahip, sürüm numaraları 1000 dizi halinde 2.2.1000 gibi sayılarla 2.2.900 aşağıdaki özellik yayını sarabilirsiniz. Bu durum gerçekleşmesi beklenen değil.
* bir özellik yayını gerçekleşmeyeceğini olmadan 99 yayınlar eki. Bir yayın yaklaştığında bu sayı, bir özellik yayını zorlar.

İlk teklifinde daha fazla ayrıntı görebilirsiniz [dotnet/tasarımları](https://github.com/dotnet/designs/pull/29) depo.

## <a name="semantic-versioning"></a>Semantic versioning

.NET Core *çalışma zamanı* kabaca aynılarını [Semantic Versioning (SemVer)](https://semver.org/), kullanımını benimseyen `MAJOR.MINOR.PATCH` sürüm oluşturma, derece ve türünü tanımlamak için sürüm numarasını çeşitli bölümlerini kullanarak değiştirin.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

İsteğe bağlı `PRERELEASE` ve `BUILDNUMBER` bölümleri hiçbir zaman desteklenen sürümleri parçasıdır ve yalnızca gecelik derlemeler, kaynak hedefler, yerel yapılar üzerinde mevcut ve desteklenmeyen Önizleme sürümleri.

### <a name="understand-runtime-version-number-changes"></a>Çalışma zamanı sürümü numarası değişiklikleri anlama

`MAJOR` ne zaman artırılır:

* Ürün veya yeni bir ürün yönü önemli değişiklikler oluşur.
* Yeni değişiklikler alınmıştır. Bozucu değişiklikleri kabul etmek için yüksek Çubuğu yoktur.
* Eski bir sürümü artık desteklenmiyor.
* Daha yeni bir `MAJOR` mevcut bir bağımlılık sürümünü benimsenen.

`MINOR` ne zaman artırılır:

* Genel API yüzey alanı eklenir.
* Yeni bir davranış eklenir.
* Daha yeni bir `MINOR` mevcut bir bağımlılık sürümünü benimsenen.
* Yeni bir bağımlılık kullanıma sunulmuştur.

`PATCH` ne zaman artırılır:

* Hata düzeltmeleri yapılır.
* Daha yeni bir platform için destek eklendi.
* Daha yeni bir `PATCH` mevcut bir bağımlılık sürümünü benimsenen.
* Herhangi bir değişiklik önceki durumlarından biri sığmıyor.

Birden çok değişiklik olduğunda, tek tek değişikliklerden etkilenen en yüksek öğeden artırılır ve aşağıdaki sorguyu sıfırlanır. Örneğin, `MAJOR` artırılır, `MINOR` ve `PATCH` sıfırlanır. Zaman `MINOR` artırılır, `PATCH` sıfır while sıfırlama `MAJOR` dokunulmadan olduğu.

## <a name="version-numbers-in-file-names"></a>Dosya adları içinde sürüm numaraları

.NET Core taşıma için sürümünü, örneğin, indirilen dosyaları `dotnet-sdk-2.1.300-win10-x64.exe`.

### <a name="preview-versions"></a>Önizleme sürümleri

Önizleme sürümlerine sahip bir `-preview[number]-([build]|"final")` sürümüne eklenmiş. Örneğin: `2.0.0-preview1-final`

### <a name="servicing-versions"></a>Sürüm hizmet verme

Bir yayın, yayın dalları genellikle geçtikten sonra oluşturmayı durdur günlük oluşturur ve bunun yerine hizmet yapıları üretme başlatın. Bakım sürümlerde bir `-servicing-[number]` sürümüne eklenmiş. Örneğin: `2.0.1-servicing-006924`

## <a name="relationship-to-net-standard-versions"></a>İlişki .NET Standard sürümleri

.NET standart .NET başvuru bütünleştirilmiş kodu oluşur. Her platform için belirli çoklu uygulamaları vardır. Başvuru bütünleştirilmiş kodu belirli bir .NET Standard sürümünü parçası olan bir .NET API tanımını içerir. Her uygulama, belirli bir platformda .NET Standard sözleşme karşılar. .NET Standard hakkında daha fazla makaleyi edinebilirsiniz [.NET Standard](../../standard/net-standard.md) .NET Kılavuzu'nda.

.NET Standard başvurusu derleme kullandığı bir `MAJOR.MINOR` sürüm oluşturma düzeni. `PATCH` tanımına göre API herhangi bir değişiklik özellik kümesini ve bu nedenle yeni bir değişikliği temsil eder ve bir API Belirtimi (uygulaması) yalnızca gösterir çünkü düzeyi .NET Standard için kullanışlı değildir `MINOR` sürümü.

Her platformda uygulamaları, genellikle platform sürümü ve bu nedenle olmayan yetkisiz değiştirmeye karşı korumalı programcılar bu platformda .NET Standard kullanarak bir parçası olarak güncelleştirilebilir.

Her sürümünde .NET Core, .NET Standard'ın bir sürümünü uygular. .NET Standard'ın bir sürümünü uygulama, .NET Standard'ın önceki sürümleri için destek anlamına gelir. .NET standard ve .NET Core sürümünün bağımsız olarak. Bu, .NET Core 2.0 .NET Standard 2.0 uygulayan bir rastlantı olur. .NET core 2.1 ayrıca .NET Standard 2.0 uygular. .NET core, .NET Standard'ın gelecek sürümlerinde kullanıma sunuldukça destekleyecektir.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | en fazla 1.6     |
| 2,0       | 2.0     |
| 2.1       | 2.0     |

## <a name="see-also"></a>Ayrıca bkz.

* [Hedef çerçeveler](../../standard/frameworks.md)  
* [.NET Core dağıtımı paketleme](../build/distribution-packaging.md)  
* [.NET core destek yaşam döngüsü bilgi sayfası](https://www.microsoft.com/net/core/support)  
* [.NET core 2 + sürüm bağlama](https://github.com/dotnet/designs/issues/3)  
* [.NET Core için docker görüntüleri](https://hub.docker.com/r/microsoft/dotnet/)
