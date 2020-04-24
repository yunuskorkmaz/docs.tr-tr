---
title: .NET Çekirdek Çalışma Süresi ve SDK nasıl sürülür?
description: Bu makalede, .NET Core SDK ve Runtime'ın nasıl sürülme şekli (anlamsal sürüme benzer) öğretilir.
ms.date: 07/26/2018
ms.openlocfilehash: f166a6dfc1c9127eb629365efd628855489a60cb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644390"
---
# <a name="overview-of-how-net-core-is-versioned"></a>.NET Core'un nasıl sürümlendirilene genel bakış

.NET Core, .NET Core Runtime ve .NET Core SDK'yı ifade eder ve uygulamaları geliştirmek için ihtiyacınız olan araçları içerir. .NET Core SDK'lar ,NET Core Runtime'ın önceki tüm sürümüyle çalışacak şekilde tasarlanmıştır. Bu makalede çalışma zamanı ve SDK sürüm stratejisi açıklanmaktadır. .NET Standard için sürüm numaralarının açıklamasını [.NET Standard'ı](../../standard/net-standard.md#net-implementation-support)tanıtan makalede bulabilirsiniz.

.NET Core Runtime ve .NET Core SDK farklı bir hızda yeni özellikler ekler - genel olarak .NET Core SDK, üretimde kullandığınız çalışma süresini değiştiren .NET Core Runtime'dan daha hızlı güncelleştirilmiş araçlar sağlar.

## <a name="versioning-details"></a>Sürüm ayrıntıları

".NET Core 2.1" .NET Core Runtime sürüm numarasını ifade eder. .NET Core [Runtime, anlamsal sürümden](#semantic-versioning)sonra sürümleme için büyük/minör/yama yaklaşımına sahiptir.

.NET Core SDK anlamsal sürüm izlemez. .NET Core SDK daha hızlı sürümler ve sürümleri hem hizalanmış çalışma süresi hem de SDK'nın kendi küçük ve yama sürümlerini iletmelidir. .NET Core SDK sürümünün ilk iki pozisyonu ,NET Core Runtime ile birlikte yayımlanır. SDK'nın her sürümü bu çalışma süresi veya daha düşük sürüm için uygulamalar oluşturabilir.

SDK sürüm numarasının üçüncü konumu hem küçük hem de yama numarasını ileter. Küçük sürüm 100 ile çarpılır. Küçük sürüm 1, yama sürüm 2 102 olarak temsil edilecektir. Son iki basamak yama numarasını temsil eder. Örneğin, .NET Core 2.2 sürümü aşağıdaki tablo gibi sürümler oluşturabilir:

| Değiştir                | .NET Core Runtime | .NET Çekirdek SDK (\*) |
|-----------------------|-------------------|-------------------|
| İlk yayın       | 2.2.0             | 2.2.100           |
| SDK Yama             | 2.2.0             | 2.2.101           |
| Çalışma Süresi ve SDK Yama | 2.2.1             | 2.2.102           |
| SDK Özellik değişikliği    | 2.2.1             | 2.2.200           |

(\*) Bu grafik, 2.2 .NET Çekirdek Çalışma Süresini örnek olarak kullanır, çünkü tarihi bir eser .NET Core 2.1'in ilk SDK'sı 2.1.300 anlamına gelir. Daha fazla bilgi için [.NET Core sürüm seçimine](selection.md)bakın.

Notlar:

- SDK'da çalışma zamanı özellik güncelleştirmesinden önce 10 özellik güncelleştirmesi varsa, sürüm numaraları 2.2.900'den sonraki özellik sürümü olarak 2.2.1000 gibi sayılarla 1000 serisine dönüşür. Bu durumun gerçekleşmesi beklenmiyor.
- Bir özellik sürümü olmadan 99 yama bültenleri oluşmaz. Bir sürüm bu sayıya yaklaşırsa, bir özellik yayımı zorlar.

İlk teklifte daha fazla ayrıntıyı [dotnet/tasarım](https://github.com/dotnet/designs/pull/29) deposunda görebilirsiniz.

## <a name="semantic-versioning"></a>Anlamsal sürüm

.NET Çekirdek *Çalışma süresi* kabaca [Anlamsal Sürüm (SemVer)](https://semver.org/)yapışır , `MAJOR.MINOR.PATCH` sürüm kullanımını benimseyen, değişim derecesini ve türünü tanımlamak için sürüm numarasının çeşitli bölümlerini kullanarak.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

İsteğe `PRERELEASE` `BUILDNUMBER` bağlı ve parçalar hiçbir zaman desteklenen sürümlerin bir parçası değildir ve yalnızca gecelik yapılarda, kaynak hedeflerinden yerel yapılarda ve desteklenmeyen önizleme sürümlerinde bulunur.

### <a name="understand-runtime-version-number-changes"></a>Çalışma zamanı sürüm numarası değişikliklerini anlama

`MAJOR`zaman artımlı:

- Üründe veya yeni bir ürün yönünde önemli değişiklikler meydana gelir.
- Son dakika değişiklikleri yapıldı. Değişiklikleri kırmayı kabul etmek için yüksek bir çıta var.
- Eski sürüm artık desteklenmeyecek.
- Varolan `MAJOR` bir bağımlılığın daha yeni bir sürümü benimsenmiştir.

`MINOR`zaman artımlı:

- Genel API yüzey alanı eklenir.
- Yeni bir davranış eklenir.
- Varolan `MINOR` bir bağımlılığın daha yeni bir sürümü benimsenmiştir.
- Yeni bir bağımlılık tanıtıldı.

`PATCH`zaman artımlı:

- Hata düzeltmeleri yapılır.
- Daha yeni bir platform desteği eklendi.
- Varolan `PATCH` bir bağımlılığın daha yeni bir sürümü benimsenmiştir.
- Başka bir değişiklik önceki durumlardan birine uymuyor.

Birden çok değişiklik olduğunda, tek tek değişikliklerden etkilenen en yüksek öğe artımlanır ve aşağıdakiler sıfırlanır. Örneğin, ne `MAJOR` zaman artımlı `MINOR` `PATCH` ve sıfırlanır. Ne `MINOR` zaman artış gösterilir, `PATCH` sıfırlanır ise `MAJOR` dokunulmaz bırakılır.

## <a name="version-numbers-in-file-names"></a>Dosya adlarında sürüm numaraları

.NET Core için indirilen dosyalar, örneğin sürümü `dotnet-sdk-2.1.300-win10-x64.exe`taşır.

### <a name="preview-versions"></a>Önizleme sürümleri

Önizleme sürümleri `-preview[number]-([build]|"final")` nin sürümüne eklenen bir sürüm vardır. Örneğin, `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Servis sürümleri

Bir sürüm söndükten sonra, sürüm dalları genellikle günlük yapılar üretmeyi durdurur ve bunun yerine servis yapılarını üretmeye başlar. Servis sürümleri, `-servicing-[number]` sürüme eklenebilir. Örneğin, `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>.NET Standart sürümleriyle ilişki

.NET Standart bir .NET referans derlemeoluşur. Her platforma özgü birden çok uygulama vardır. Başvuru derlemesi, belirli bir .NET Standart sürümünün parçası olan .NET API'lerinin tanımını içerir. Her uygulama, belirli bir platformdaki .NET Standart sözleşmesini yerine getirin. .NET Standardı ile ilgili makalede [.NET Standard](../../standard/net-standard.md) hakkında daha fazla bilgi edinebilirsiniz.

.NET Standart başvuru derlemesi bir `MAJOR.MINOR` sürüm şeması kullanır. `PATCH`düzey .NET Standard için kullanışlı değildir, çünkü yalnızca bir API belirtimini (uygulama yok) ortaya çıkarır ve tanım olarak API'deki herhangi bir değişiklik özellik kümesinde bir değişikliği ve dolayısıyla yeni `MINOR` bir sürümü temsil eder.

Her platformdaki uygulamalar genellikle platform sürümükapsamında güncellenebilir ve bu nedenle bu platformda .NET Standard'ı kullanan programcılar tarafından belirgin olmayabilir.

.NET Core'un her sürümü .NET Standard'ın bir sürümünü uygular. .NET Standard'ın bir sürümünün uygulanması, .NET Standard'ın önceki sürümleri için destek anlamına gelir. .NET Standart ve .NET Core sürümü bağımsız olarak. .NET Core 2.0'ın .NET Standard 2.0'ı uygulaması bir tesadüftür. .NET Core 2.1 de .NET Standart 2.0 uygular. .NET Core, .NET Standard'ın gelecekteki sürümlerini kullanılabilir olduklarında destekleyecektir.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | 1,6'ya kadar     |
| 2,0       | 2,0'a kadar     |
| 2.1       | 2,0'a kadar     |
| 2,2       | 2,0'a kadar     |
| 3,0       | 2,1'e kadar     |

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](../../standard/frameworks.md)
- [.NET Core dağıtımı paketleme](../distribution-packaging.md)
- [.NET Çekirdek Destek Yaşam Döngüsü Bilgi Formu](https://dotnet.microsoft.com/platform/support/policy)
- [.NET Core 2+ Sürüm Bağlama](https://github.com/dotnet/designs/issues/3)
- [.NET Core için Docker görüntüleri](https://hub.docker.com/_/microsoft-dotnet-core/)
