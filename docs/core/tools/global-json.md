---
title: global.json’a genel bakış
description: .NET Core CLI komutlarını çalıştırırken .NET Core SDK sürümünü ayarlamak için global.json dosyasını nasıl kullanacağınızı öğrenin.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 70257566e1ff30f5c97212a5e0e3c308c27738b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626001"
---
# <a name="globaljson-overview"></a>global.json’a genel bakış

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.0 SDK ve sonraki sürümler

*global.json* dosyası, .NET Core CLI komutlarını çalıştırdığınızda hangi .NET Core SDK sürümünün kullanıldığını tanımlamanızı sağlar. .NET Core SDK'yı seçmek, proje hedeflerinizi çalışma zamanı olarak belirtmekten bağımsızdır. .NET Core SDK sürümü .NET Core CLI'nin hangi sürümlerinin kullanıldığını gösterir.

Genel olarak, SDK araçlarının en son sürümünü kullanmak istiyorsunuz, bu nedenle *global.json* dosyası gerekmez. Bazı gelişmiş senaryolarda, SDK araçlarının sürümünü denetlemek isteyebilirsiniz ve bu makalede bunun nasıl yapılacağını açıklar.

Bunun yerine çalışma zamanı belirtme hakkında daha fazla bilgi için [Hedef çerçeveleri'ne](../../standard/frameworks.md)bakın.

.NET Core SDK, geçerli çalışma dizininde (proje dizini ile aynı olmayan) veya ana dizinde bir *global.json* dosyası arar.

## <a name="globaljson-schema"></a>global.json şema

### <a name="sdk"></a>sdk

Türü:`object`

Seçmek için .NET Core SDK hakkında bilgi belirtir.

#### <a name="version"></a>version

- Türü:`string`

- Şu andan itibaren kullanılabilir: .NET Core 1.0 SDK.

.NET Core SDK sürümü kullanmak.

Bu alan:

- Joker karakter desteği yok, yani tam sürüm numarası belirtilmelidir.
- Sürüm aralıklarını desteklemiyor.

#### <a name="allowprerelease"></a>izinPrerelease

- Türü:`boolean`

- Şu andan itibaren kullanılabilir: .NET Core 3.0 SDK.

SDK çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümleri ni göz önünde bulundurup göz önünde bulundurmaması gerektiğini gösterir.

Bu değeri açıkça ayarlamazsanız, varsayılan değer Visual Studio'dan çalışıp çalışmadığınıza bağlıdır:

- Visual Studio'da **değilseniz,** varsayılan değer `true`.
- Visual Studio'daysanız, istenen yayın öncesi durumu kullanır. Diğer bir zamanda, Visual Studio'nun Önizleme sürümünü kullanıyorsanız veya **.NET Core SDK seçeneğinin Kullanım önizlemelerini** **(Araç** >  `true`**Seçenekleri** > **Ortamı** > Önizleme**Özellikleri**altında) ayarlarsanız, varsayılan değer; aksi `false`takdirde, .

#### <a name="rollforward"></a>Rollforward

- Türü:`string`

- Şu andan itibaren kullanılabilir: .NET Core 3.0 SDK.

Bir SDK sürümünü seçerken kullanılacak roll-forward ilkesi, belirli bir SDK sürümü eksikolduğunda veya daha yüksek bir sürümü kullanma yönergesi olarak geri dönüş olarak. Bir [sürüm,](#version) `latestMajor`'ye `rollForward` ayarlıyorsanız, bir değerle belirtilmelidir.

Kullanılabilir ilkeleri ve davranışlarını anlamak için, biçimdeki `x.y.znn`bir SDK sürümü için aşağıdaki tanımları göz önünde bulundurun:

- `x`ana sürümüdür.
- `y`küçük versiyonudur.
- `z`özellik grubudur.
- `nn`yama sürümüdür.

Aşağıdaki `rollForward` tablo, anahtar için olası değerleri gösterir:

| Değer         | Davranış |
| ------------- | ---------- |
| `patch`       | Belirtilen sürümü kullanır. <br> Bulunamazsa, en son yama düzeyine doğru yuvarlanır. <br> Bulunmazsa, başarısız olur. <br><br> Bu değer, SDK'nın önceki sürümlerindeki eski davranıştır. |
| `feature`     | Belirtilen büyük, minör ve özellik bandı için en son yama düzeyini kullanır. <br> Bulunamazsa, aynı ana/minör içindeki bir sonraki yüksek özellik bandına doğru yuvarlanır ve bu özellik bandı için en son yama düzeyini kullanır. <br> Bulunmazsa, başarısız olur. |
| `minor`       | Belirtilen büyük, minör ve özellik bandı için en son yama düzeyini kullanır. <br> Bulunamazsa, aynı ana/küçük sürümdeki bir sonraki yüksek özellik bandına doğru ilerler ve bu özellik bandı için en son yama düzeyini kullanır. <br> Bulunamazsa, aynı ana daldaki bir sonraki yüksek minör ve özellik bandına doğru ilerler ve bu özellik bandı için en son yama düzeyini kullanır. <br> Bulunmazsa, başarısız olur. |
| `major`       | Belirtilen büyük, minör ve özellik bandı için en son yama düzeyini kullanır. <br> Bulunamazsa, aynı ana/küçük sürümdeki bir sonraki yüksek özellik bandına doğru ilerler ve bu özellik bandı için en son yama düzeyini kullanır. <br> Bulunamazsa, aynı ana daldaki bir sonraki yüksek minör ve özellik bandına doğru ilerler ve bu özellik bandı için en son yama düzeyini kullanır. <br> Bulunamazsa, bir sonraki yüksek büyük, minör ve özellik bandına doğru yuvarlanır ve bu özellik bandı için en son yama düzeyini kullanır. <br> Bulunmazsa, başarısız olur. |
| `latestPatch` | İstenen büyük, minör ve özellik bandını yama düzeyiyle eşleştiren ve belirtilen değerden daha büyük veya eşit olan en son yüklü yama düzeyini kullanır. <br> Bulunmazsa, başarısız olur. |
| `latestFeature` | İstenen büyük ve küçük bantla eşleşen en yüksek yüklü özellik bandını ve yama düzeyini, belirtilen değerden büyük veya eşit bir özellik bandıyla kullanır. <br> Bulunmazsa, başarısız olur. |
| `latestMinor` | İstenen büyük le eşleşen en yüksek yüklü küçük, özellik bandını ve yama düzeyini, belirtilen değerden büyük veya eşit olan bir küçükle eşleşir. <br> Bulunmazsa, başarısız olur. |
| `latestMajor` | En yüksek yüklü .NET Core SDK'yı, belirtilen değerden büyük veya eşit bir ana ile kullanır. <br> Bulunamazsa, başarısız olur. |
| `disable`     | İlerleme kaydetmiyor. Tam eşleşme gerekli. |

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, yayın öncesi sürümlerin nasıl kullanılmaydığını gösterir:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

Aşağıdaki örnek, belirtilen sürümden daha büyük veya eşit olan yüklü en yüksek sürümün nasıl kullanılacağını gösterir:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

Aşağıdaki örnekte, tam olarak belirtilen sürümün nasıl kullanılacağı gösterilmektedir:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

Aşağıdaki örnek, belirli bir sürümün yüklü en yüksek yama sürümünün nasıl kullanılacağını gösterir (formda, 3.1.1xx):

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json ve .NET Çekirdek CLI

*Global.json* dosyasında bir tane ayarlamak için makinenize hangi SDK sürümlerinin yüklenmiş olduğunu bilmek yararlı olur. Bunun nasıl yapılacılaştırılabildiği hakkında daha fazla bilgi için [,.NET Core'](../install/how-to-detect-installed-versions.md#check-sdk-versions)un zaten yüklü olduğundan düşünü

Makinenize ek .NET Core SDK sürümleri yüklemek için [İndir .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasını ziyaret edin.

Aşağıdaki örneğe benzer [şekilde dotnet yeni](dotnet-new.md) komutunu çalıştırarak geçerli dizinde yeni bir *global.json* dosyası oluşturabilirsiniz:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Eşleşen kurallar

> [!NOTE]
> Eşleşen kurallar, yüklü olan `dotnet.exe` tüm .NET Core yüklü çalışma zamanlarında yaygın olan giriş noktası tarafından yönetilir. .NET Core Runtime'ın en son yüklenen sürümünün eşleşen kuralları, yan yana yüklenen birden çok çalışma zamanı olduğunda kullanılır.

## <a name="net-core-3x"></a>[.NET Çekirdek 3.x](#tab/netcore3x)

.NET Core 3.0 ile başlayarak, SDK'nın hangi sürümünü kullanacağını belirlerken aşağıdaki kurallar geçerlidir:

- *Global.json* dosyası bulunmazsa veya *global.json* bir SDK sürümü veya `allowPrerelease` bir değer belirtmezse, en yüksek yüklü SDK sürümü kullanılır (ayar `rollForward` değeri). `latestMajor` Yayın öncesi SDK sürümlerinin nasıl `dotnet` çağrıldığına bağlıdır.
  - Visual Studio'da **değilseniz,** ön sürüm sürümleri dikkate alınır.
  - Visual Studio'daysanız, istenen yayın öncesi durumu kullanır. Diğer bir de, Visual Studio'nun Önizleme sürümünü kullanıyorsanız veya **.NET Core SDK seçeneğinin Kullanım önizlemelerini** **(Araç** > **Seçenekleri** > **Ortamı** > Önizleme**Özellikleri**altında) ayarlarsanız, ön sürüm sürümleri dikkate alınır; aksi takdirde, yalnızca sürüm sürümleri dikkate alınır.
- Bir *global.json* dosyası sdk sürümünü belirtmez ancak bir `allowPrerelease` değer belirtir bulunursa, en yüksek yüklü SDK sürümü `rollForward` `latestMajor`kullanılır (ayar eşdeğeri). En son SDK sürümünün serbest bırakılıp yayınlanamayacağı `allowPrerelease`veya yayın öncesi olup olmadığı, sönme nin değerine bağlıdır. `true`ön sürüm sürümlerinin dikkate alınagösterdiğini gösterir; `false` yalnızca sürüm sürümlerinin dikkate alındığını gösterir.
- *Global.json* dosyası bulunursa ve bir SDK sürümü belirtirse:

  - Değer `rollFoward` ayarlı değilse, `latestPatch` varsayılan `rollForward` ilke olarak kullanır. Aksi takdirde, [rollForward](#rollforward) bölümünde her değeri ve davranışlarını denetleyin.
  - Yayın öncesi sürüm sürümlerinin dikkate alınıp `allowPrerelease` alınmadığı ve ayarlanmadığında varsayılan davranışın ne olduğu [izin verilen Ön sürüm](#allowprerelease) bölümünde açıklanmıştır.

## <a name="net-core-2x"></a>[.NET Çekirdek 2.x](#tab/netcore2x)

.NET Core 2.x SDK'da, SDK'nın hangi sürümünü kullanacağı belirlenirken aşağıdaki kurallar geçerlidir:

- *Global.json* dosyası bulunmazsa veya *global.json* bir SDK sürümü belirtmezse, en son yüklenen SDK sürümü kullanılır. En son SDK sürümü serbest veya ön sürüm olabilir - en yüksek sürüm numarası kazanır.
- *global.json* bir SDK sürümü belirtmezse:
  - Belirtilen SDK sürümü makinede bulunursa, bu tam sürüm kullanılır.
  - Belirtilen SDK sürümü makinede bulunamazsa, bu sürümün en son yüklenen SDK **yama sürümü** kullanılır. En son yüklenen SDK **yama sürümü** serbest bırakılabilir veya ön sürüm olabilir - en yüksek sürüm numarası kazanır. .NET Core 2.1 ve üzeri sürümlerde, belirtilen **yama sürümünden** daha düşük **yama sürümleri** SDK seçiminde yoksayılır.
  - Belirtilen SDK sürümü ve uygun bir SDK **yama sürümü** bulunamazsa, bir hata atılır.

SDK sürümü aşağıdaki bölümlerden oluşur:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

.NET Core SDK'nın **özellik sürümü,** SDK`x`2.1.100 ve`xyz`üzeri sürümler için sayının son bölümündeki () ilk basamak ( ) ile temsil edilir. Genel olarak, .NET Core SDK.NET Core'dan daha hızlı bir sürüm döngüsüne sahiptir.

**Yama sürümü,** SDK sürümleri 2.1.100 ve üzeri için sayının son bölümündeki`yz`(`xyz`) son iki basamakla tanımlanır. Örneğin, SDK `2.1.300` sürümü olarak belirtirseniz, SDK seçimi `2.1.399` `2.1.400` kadar bulur ancak için `2.1.300`bir yama sürümü olarak kabul etmez .

.NET Core SDK sürümleri `2.1.100` sürüm `2.1.201` numarası düzenleri arasında geçiş sırasında yayımlandı `xyz` ve gösterimi doğru şekilde işlemez. Bu sürümleri *global.json* dosyasında belirtmenizi, belirtilen sürümlerin hedef makinelerde olduğundan emin olmamızı şiddetle öneririz.

---

## <a name="troubleshoot-build-warnings"></a>Yapı uyarılarını giderme

* Aşağıdaki uyarı, projenizin .NET Core SDK'nın ön sürüm sürümü kullanılarak derlenmiş olduğunu gösterir:

  > .NET Core SDK'nın önizleme sürümüyle çalışıyorsunuz. Geçerli projedeki global.json dosyası aracılığıyla SDK sürümünü tanımlayabilirsiniz. Daha <https://go.microsoft.com/fwlink/?linkid=869452>fazla .

  .NET Core SDK versiyonları yüksek kalitede bir geçmişe ve bağlılığa sahiptir. Ancak, bir ön sürüm sürümü kullanmak istemiyorsanız, [.NET](#allowprerelease) Core 3.0 SDK veya izin Önceki Sürüm bölümünde daha sonraki bir sürümü ile kullanabileceğiniz farklı stratejileri kontrol edin. .NET Core 3.0 veya daha yüksek Çalışma Süresi veya SDK yüklü hiç makineleri için, bir *global.json* dosyası oluşturmak ve kullanmak istediğiniz tam sürümünü belirtmeniz gerekir.

* Aşağıdaki uyarı, projenizin .NET Core 2.1 SDK ve sonraki sürümlerle uyumlu olmayan EF Core 1.0 veya 1.1'i hedeflediğini gösterir:

  > Başlangıç projesi '{startupProject}' hedefleri çerçevesi'. NETCoreApp' sürümü '{targetFrameworkVersion}'. Entity Framework Core .NET Komut satırı Araçları'nın bu sürümü yalnızca sürüm 2.0 veya daha yüksek destekler. Araçların eski sürümlerini kullanma hakkında <https://go.microsoft.com/fwlink/?linkid=871254>bilgi için bkz.

  .NET Core 2.1 SDK (sürüm 2.1.300) ile başlayan `dotnet ef` komut, SDK'ya dahil edilir. Projenizi derlemek için .NET Core 2.0 SDK (sürüm 2.1.201) veya daha önce makinenize yükleyin ve *global.json* dosyasını kullanarak istenen SDK sürümünü tanımlayın. `dotnet ef` Komut hakkında daha fazla bilgi [için, BKZ.](/ef/core/miscellaneous/cli/dotnet)

## <a name="see-also"></a>Ayrıca bkz.

- [Proje SDK'ları nasıl çözülür?](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
