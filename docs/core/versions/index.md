---
title: .NET çalışma zamanı ve SDK 'nın sürümü oluşturma
description: Bu makalede, .NET SDK ve çalışma zamanının nasıl sürümleneceği (anlamsal sürüm oluşturma ile benzerdir) açıklanmaktadır.
ms.date: 12/07/2020
ms.openlocfilehash: 2fbc2775f31b4eab1c9883282c58accd9bb2b9f5
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633630"
---
# <a name="overview-of-how-net-is-versioned"></a>.NET sürümünün sürümü oluşturma konusuna genel bakış

[.NET çalışma zamanı ve .NET SDK](../introduction.md#sdk-and-runtimes) , farklı sıklıklara yeni özellikler ekler. Genel olarak, SDK çalışma zamanından daha sık güncelleştirilir. Bu makalede çalışma zamanı ve SDK sürüm numaraları açıklanmaktadır.

## <a name="versioning-details"></a>Sürüm oluşturma ayrıntıları

.NET çalışma zamanının, büyük/küçük ve düzeltme eki uygulama, [semantik sürümü oluşturma](#semantic-versioning)sonrasında sürüm oluşturma yaklaşımını vardır.

.NET SDK, anlamsal sürüm oluşturmayı takip etmez. .NET SDK 'nın daha hızlı ve sürüm numaralarının her ikisi de hizalı çalışma zamanına ve SDK 'nın kendi alt ve düzeltme eki yayınlarına iletişim kurması gerekir.

.NET SDK sürüm numarasının ilk iki konumu ile yayınlanan .NET çalışma zamanı sürümüne kilitlidir. SDK 'nın her sürümü bu çalışma zamanına veya daha düşük bir sürüme yönelik uygulamalar oluşturabilir.

SDK sürüm numarasının üçüncü konumu hem küçük hem de yayama numarasını iletişim kurar. İkincil sürüm 100 ile çarpılır. Son iki basamak, düzeltme eki numarasını temsil eder. İkincil sürüm 1, düzeltme eki sürüm 2 102 olarak temsil edilir. Örneğin, bir çalışma zamanı ve SDK sürüm numarası sırası aşağıda verilmiştir:

| Değiştir                | .NET Çalışma Zamanı      | .NET SDK ( \* )     |
|-----------------------|-------------------|-------------------|
| İlk yayın       | 2.2.0             | 2.2.100           |
| SDK Düzeltme Eki             | 2.2.0             | 2.2.101           |
| Çalışma zamanı ve SDK Düzeltme Eki | 2.2.1             | 2.2.102           |
| SDK özelliği değişikliği    | 2.2.1             | 2.2.200           |

LARıNı

- SDK 'nın, bir çalışma zamanı özelliği güncelleştirmesinden önce 10 Özellik Güncelleştirmesi varsa, sürüm numaraları 2.2.1000 gibi sayılarla 1000 serisine, 2.2.900 ' u takip eden özellik yayını olarak da. Bu durumun gerçekleşmesi beklenmez.
- 99 düzeltme eki sürümleri, özellik sürümü olmadan gerçekleşmez. Bir sürüm bu numaraya yaklaşırsa, bir özellik yayını zorlar.

[DotNet/Designs](https://github.com/dotnet/designs/pull/29) deposundaki ilk teklife daha fazla ayrıntı görebilirsiniz.

## <a name="semantic-versioning"></a>Anlamsal sürüm oluşturma

.NET *çalışma zamanı* kabaca, değişim kullanımını benimseme ve değişiklik türünü anlatmak için sürüm numarasının çeşitli kısımlarını kullanarak, daha önce [anlamsal sürüm oluşturma (semver)](https://semver.org/)kullanır `MAJOR.MINOR.PATCH` .

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

İsteğe bağlı `PRERELEASE` ve `BUILDNUMBER` parçalar, Desteklenen sürümlerin hiçbir parçası değildir ve yalnızca gecelik derlemeler, kaynak hedeflerden yerel yapılar ve desteklenmeyen önizleme sürümleri üzerinde bulunur.

### <a name="understand-runtime-version-number-changes"></a>Çalışma zamanı sürüm numarası değişikliklerini anlama

`MAJOR` Şu durumlarda artırılır:

- Üründe önemli değişiklikler veya yeni bir ürün yönü meydana gelir.
- Son değişiklikler alındı. Son değişiklikleri kabul etmek için yüksek bir çubuk vardır.
- Eski sürüm artık desteklenmiyor.
- Mevcut bağımlılığın daha yeni bir `MAJOR` sürümü benimsemiştir.

`MINOR` Şu durumlarda artırılır:

- Ortak API yüzey alanı eklendi.
- Yeni bir davranış eklenmiştir.
- Mevcut bağımlılığın daha yeni bir `MINOR` sürümü benimsemiştir.
- Yeni bir bağımlılık ortaya çıkarılmıştır.

`PATCH` Şu durumlarda artırılır:

- Hata düzeltmeleri yapılır.
- Daha yeni bir platform için destek eklenmiştir.
- Mevcut bağımlılığın daha yeni bir `PATCH` sürümü benimsemiştir.
- Diğer herhangi bir değişiklik, önceki durumlardan birine uymuyor.

Birden çok değişiklik olduğunda, tek tek değişikliklerden etkilenen en üst öğe artırılır ve aşağıdakiler sıfıra sıfırlanır. Örneğin, ne zaman `MAJOR` artırılır `MINOR` ve `PATCH` sıfıra sıfırlanır. Ne zaman `MINOR` artırılır, `PATCH` `MAJOR` dokunulmadan sola sıfırlanır.

## <a name="version-numbers-in-file-names"></a>Dosya adlarındaki sürüm numaraları

.NET için indirilen dosyalar sürümü (örneğin,) taşır `dotnet-sdk-2.1.300-win10-x64.exe` .

### <a name="preview-versions"></a>Önizleme sürümleri

Önizleme sürümlerinin `-preview[number]-([build]|"final")` sürüm numarasına eklenmiş olması gerekir. Örneğin, `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Hizmet sürümleri

Bir sürüm kapatıldıktan sonra, yayın dalları genellikle günlük derlemeler üretmeden ve bunun yerine bakım yapıları üretmede başlatılır. Hizmet sürümlerinin bir `-servicing-[number]` sürümüne eklenmiş olması gerekir. Örneğin, `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>.NET Standard sürümleriyle ilişki

.NET Standard bir .NET başvuru derlemesinden oluşur. Her platforma özel birden çok uygulama vardır. Başvuru derlemesi, belirli bir .NET Standard sürümünün parçası olan .NET API 'lerinin tanımını içerir. Her uygulama, belirli bir platformda .NET Standard sözleşmesini yerine getirir.

.NET Standard Reference derlemesi bir `MAJOR.MINOR` sürüm oluşturma düzeni kullanır. `PATCH` düzey, yalnızca bir API belirtimi (uygulama olmadan) kullanıma sunduğundan ve tanıma göre API üzerinde yapılan herhangi bir değişiklik, özellik kümesindeki bir değişikliği ve bu nedenle yeni bir sürümü temsil ettiğinden .NET Standard için kullanışlı değildir `MINOR` .

Her platformdaki uygulamalar, genellikle platform sürümünün bir parçası olarak ve bu nedenle bu platformda .NET Standard kullanan programcılara yönelik olarak güncelleştirilemeyebilir.

Daha fazla bilgi için bkz. [.NET Standard](../../standard/net-standard.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](../../standard/frameworks.md)
- [.NET dağıtım paketleme](../distribution-packaging.md)
- [.NET destek yaşam döngüsü olgu sayfası](https://dotnet.microsoft.com/platform/support/policy)
- [.NET için Docker görüntüleri](https://hub.docker.com/_/microsoft-dotnet/)
