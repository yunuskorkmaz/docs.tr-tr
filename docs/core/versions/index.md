---
title: .NET Core çalışma zamanı ve SDK 'nın sürümü oluşturma
description: Bu makale, .NET Core SDK ve çalışma zamanının nasıl sürümlendirilemez (anlamsal sürüm oluşturma ile benzerdir).
ms.date: 07/26/2018
ms.openlocfilehash: c85a2112b439768068663688947960ac814de824
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777325"
---
# <a name="overview-of-how-net-core-is-versioned"></a>.NET Core 'un sürümü oluşturma konusuna genel bakış

.NET Core, .NET Core çalışma zamanına ve uygulama geliştirmek için ihtiyacınız olan araçları içeren .NET Core SDK anlamına gelir. .NET Core SDK 'Ları .NET Core çalışma zamanının önceki bir sürümüyle çalışmak üzere tasarlanmıştır. Bu makalede çalışma zamanı ve SDK sürüm stratejisi açıklanmaktadır. .NET Standard için sürüm numaraları açıklaması, [.NET Standard](../../standard/net-standard.md#net-implementation-support)tanıtma makalesinde bulunabilir.

.NET Core çalışma zamanı ve .NET Core SDK yeni özellikleri farklı bir hızda ekleyin. genel olarak, .NET Core SDK güncelleştirilmiş araçları .NET Core çalışma zamanından daha hızlı bir şekilde, üretimde kullandığınız çalışma zamanını değiştirenden daha hızlı sağlar.

## <a name="versioning-details"></a>Sürüm oluşturma ayrıntıları

".NET Core 2,1", .NET Core çalışma zamanı sürüm numarasını ifade eder. .NET Core çalışma zamanının, sürüm oluşturma için [anlam sürümü oluşturma](#semantic-versioning)sonrasında büyük/küçük/küçük Patch yaklaşımı vardır.

.NET Core SDK anlam sürümü oluşturmayı takip etmez. .NET Core SDK daha hızlı ve sürümleri, hem hizalanmış çalışma zamanı hem de SDK 'nın kendi alt ve düzeltme eki sürümlerini iletmelidir. .NET Core SDK sürümünün ilk iki konumu, ile birlikte yayımlanan .NET Core çalışma zamanına kilitlidir. SDK 'nın her sürümü bu çalışma zamanına veya daha düşük bir sürüme yönelik uygulamalar oluşturabilir.

SDK sürüm numarasının üçüncü konumu hem küçük hem de yayama numarasını iletişim kurar. İkincil sürüm 100 ile çarpılır. İkincil sürüm 1, düzeltme eki sürüm 2 102 olarak temsil edilir. Son iki basamak, düzeltme eki numarasını temsil eder. Örneğin, .NET Core 2,2 sürümü aşağıdaki tablo gibi yayınlar oluşturabilir:

| Değişiklik                | .NET Core Runtime | .NET Core SDK (\*) |
|-----------------------|-------------------|-------------------|
| İlk yayın       | 2.2.0             | 2.2.100           |
| SDK Düzeltme Eki             | 2.2.0             | 2.2.101           |
| Çalışma zamanı ve SDK Düzeltme Eki | 2.2.1             | 2.2.102           |
| SDK özelliği değişikliği    | 2.2.1             | 2.2.200           |

(\*) Bu grafik, .NET Core 2,1 için ilk SDK 'nın 2.1.300 olduğu bir geçmiş yapıtı olduğu için örnek olarak 2,2 .NET Core çalışma zamanını kullanır. Daha fazla bilgi için bkz. [.NET Core sürüm seçimi](selection.md).

LARıNı

- SDK 'nın, bir çalışma zamanı özelliği güncelleştirmesinden önce 10 Özellik Güncelleştirmesi varsa, sürüm numaraları 2.2.1000 gibi sayılarla 1000 serisine, 2.2.900 ' u takip eden özellik yayını olarak da. Bu durumun gerçekleşmesi beklenmez.
- 99 düzeltme eki sürümleri, özellik sürümü olmadan gerçekleşmez. Bir sürüm bu numaraya yaklaşırsa, bir özellik yayını zorlar.

[DotNet/Designs](https://github.com/dotnet/designs/pull/29) deposundaki ilk teklife daha fazla ayrıntı görebilirsiniz.

## <a name="semantic-versioning"></a>Anlamsal sürüm oluşturma

.NET Core *çalışma zamanı* kabaca, `MAJOR.MINOR.PATCH` sürümünün kullanımını benimseerek, değişim derecesini ve türünü belirtmek için sürüm numarasının çeşitli kısımlarını kullanarak, kabaca sürüm oluşturma [(semver)](https://semver.org/)kullanır.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

İsteğe bağlı `PRERELEASE` ve `BUILDNUMBER` parçalar hiçbir şekilde desteklenen yayınların bir parçası değildir ve yalnızca gecelik derlemelerde, kaynak hedeflerden yerel derlemelerde ve desteklenmeyen önizleme sürümlerinde mevcuttur.

### <a name="understand-runtime-version-number-changes"></a>Çalışma zamanı sürüm numarası değişikliklerini anlama

`MAJOR` şu durumlarda artırılır:

- Üründe önemli değişiklikler veya yeni bir ürün yönü meydana gelir.
- Son değişiklikler alındı. Son değişiklikleri kabul etmek için yüksek bir çubuk vardır.
- Eski sürüm artık desteklenmiyor.
- Mevcut bir bağımlılığın daha yeni bir `MAJOR` sürümü benimsemiştir.

`MINOR` şu durumlarda artırılır:

- Ortak API yüzey alanı eklendi.
- Yeni bir davranış eklenmiştir.
- Mevcut bir bağımlılığın daha yeni bir `MINOR` sürümü benimsemiştir.
- Yeni bir bağımlılık ortaya çıkarılmıştır.

`PATCH` şu durumlarda artırılır:

- Hata düzeltmeleri yapılır.
- Daha yeni bir platform için destek eklenmiştir.
- Mevcut bir bağımlılığın daha yeni bir `PATCH` sürümü benimsemiştir.
- Diğer herhangi bir değişiklik, önceki durumlardan birine uymuyor.

Birden çok değişiklik olduğunda, tek tek değişikliklerden etkilenen en üst öğe artırılır ve aşağıdakiler sıfıra sıfırlanır. Örneğin `MAJOR` arttırılır `MINOR` ve `PATCH` sıfır olarak sıfırlanır. `MINOR` artırılabiliyorsa, `MAJOR` dokunulmadan sola `PATCH` sıfırlanır.

## <a name="version-numbers-in-file-names"></a>Dosya adlarındaki sürüm numaraları

.NET Core için indirilen dosyalar sürümü (örneğin, `dotnet-sdk-2.1.300-win10-x64.exe`) taşır.

### <a name="preview-versions"></a>Önizleme sürümleri

Önizleme sürümleri sürüme eklenmiş bir `-preview[number]-([build]|"final")` sahiptir. Örneğin: `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Hizmet sürümleri

Bir sürüm kapatıldıktan sonra, yayın dalları genellikle günlük derlemeler üretmeden ve bunun yerine bakım yapıları üretmede başlatılır. Hizmet sürümlerinin bir `-servicing-[number]` sürüme eklenmiş olması gerekir. Örneğin: `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>.NET Standard sürümleriyle ilişki

.NET Standard bir .NET başvuru derlemesinden oluşur. Her platforma özel birden çok uygulama vardır. Başvuru derlemesi, belirli bir .NET Standard sürümünün parçası olan .NET API 'lerinin tanımını içerir. Her uygulama, belirli bir platformda .NET Standard sözleşmesini yerine getirir. .NET Standard hakkında daha fazla bilgi edinmek için .NET kılavuzundaki [.NET Standard](../../standard/net-standard.md) makalesine bakın.

.NET Standard Reference derlemesi `MAJOR.MINOR` sürüm oluşturma düzeni kullanır. `PATCH` düzeyi, yalnızca bir API belirtimi (uygulama olmadan) kullanıma sunduğundan ve tanıma göre API üzerinde yapılan herhangi bir değişiklik, özellik kümesindeki bir değişikliği ve bu nedenle yeni bir `MINOR` sürümünü temsil ettiğinden .NET Standard için yararlı değildir.

Her platformdaki uygulamalar, genellikle platform sürümünün bir parçası olarak ve bu nedenle bu platformda .NET Standard kullanan programcılara yönelik olarak güncelleştirilemeyebilir.

.NET Core 'un her sürümü bir .NET Standard sürümünü uygular. Bir .NET Standard sürümünün uygulanması, önceki .NET Standard sürümleri için destek gerektirir. Bağımsız olarak .NET Standard ve .NET Core sürümü. .NET Core 2,0 .NET Standard 2,0 ' nin uyguladığı bir rastlantı. .NET Core 2,1 .NET Standard 2,0 ' i de uygular. .NET Core, kullanılabilir hale geldiğinde .NET Standard gelecek sürümlerini destekleyecektir.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | 1,6 kadar     |
| 2,0       | 2,0 kadar     |
| 2.1       | 2,0 kadar     |
| 2.2       | 2,0 kadar     |
| 3.0       | 2,1 kadar     |

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](../../standard/frameworks.md)
- [.NET Core dağıtımı paketleme](../build/distribution-packaging.md)
- [.NET Core destek yaşam döngüsü olgu sayfası](https://dotnet.microsoft.com/platform/support/policy)
- [.NET Core 2 + sürüm bağlama](https://github.com/dotnet/designs/issues/3)
- [.NET Core için Docker görüntüleri](https://hub.docker.com/_/microsoft-dotnet-core/)
