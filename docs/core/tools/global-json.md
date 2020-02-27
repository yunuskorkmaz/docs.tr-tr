---
title: global.json’a genel bakış
description: .NET Core CLI komutlarını çalıştırırken .NET Core SDK sürümünü ayarlamak için Global. json dosyasını nasıl kullanacağınızı öğrenin.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 70257566e1ff30f5c97212a5e0e3c308c27738b7
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626001"
---
# <a name="globaljson-overview"></a>global.json’a genel bakış

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri

*Global. JSON* dosyası, .NET Core CLI komutlarını çalıştırdığınızda hangi .NET Core SDK sürümünün kullanıldığını tanımlamanızı sağlar. .NET Core SDK seçilmesi, projenizin hedeflediği çalışma zamanını belirtmekten bağımsızdır. .NET Core SDK sürümü .NET Core CLI hangi sürümlerinin kullanıldığını gösterir.

Genel olarak, SDK araçlarının en son sürümünü kullanmak istiyorsunuz, bu nedenle *Global. JSON* dosyası gerekli değildir. Bazı Gelişmiş senaryolarda, SDK araçlarının sürümünü denetlemek isteyebilirsiniz ve bu makalede bunun nasıl yapılacağı açıklanır.

Bunun yerine çalışma zamanının belirtilmesi hakkında daha fazla bilgi için bkz. [hedef çerçeveler](../../standard/frameworks.md).

.NET Core SDK geçerli çalışma dizininde (proje diziniyle aynı olmayan) veya üst dizinlerinden biri olan *Global. JSON* dosyasını arar.

## <a name="globaljson-schema"></a>Global. JSON şeması

### <a name="sdk"></a>sdk

Tür: `object`

Seçilecek .NET Core SDK hakkındaki bilgileri belirtir.

#### <a name="version"></a>version

- Tür: `string`

- Şu tarihten itibaren kullanılabilir: .NET Core 1,0 SDK.

Kullanılacak .NET Core SDK sürümü.

Bu alan:

- Joker karakter desteği yoktur, yani tam sürüm numarası belirtilmelidir.
- Sürüm aralıklarını desteklemez.

#### <a name="allowprerelease"></a>Allowönsürümü

- Tür: `boolean`

- Şu tarihten itibaren kullanılabilir: .NET Core 3,0 SDK.

SDK Çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümlerini düşünmesinin gerekip gerekmediğini belirtir.

Bu değeri açıkça ayarlamazsanız, varsayılan değer Visual Studio 'dan çalıştırıp çalıştırdığınıza bağlıdır:

- Visual Studio 'da **değilseniz** , varsayılan değer `true`olur.
- Visual Studio 'da çalışıyorsanız, istenen ön sürüm durumunu kullanır. Diğer bir deyişle, Visual Studio 'nun bir önizleme sürümünü kullanıyorsanız veya .NET Core SDK seçeneğinin ( **araçlar** > **seçenekler** > **ortam** > **Önizleme özellikleri**) **kullanım önizlemelerini** ayarlarsanız, varsayılan değer `true`olur; Aksi takdirde, `false`.

#### <a name="rollforward"></a>Ileri alınmaya

- Tür: `string`

- Şu tarihten itibaren kullanılabilir: .NET Core 3,0 SDK.

Bir SDK sürümü seçerken kullanılacak geri alma ilkesi, belirli bir SDK sürümü eksik olduğunda geri dönüş olarak veya daha yüksek bir sürümü kullanmak için bir yönerge olarak. Bir [Sürüm](#version) , `latestMajor`ayarmadığınız müddetçe `rollForward` değerle belirtilmelidir.

Kullanılabilir ilkeleri ve bunların davranışlarını anlamak için `x.y.znn`biçimdeki SDK sürümü için aşağıdaki tanımları göz önünde bulundurun:

- ana sürümdür `x`.
- `y`, ikincil sürümdür.
- `z`, özellik bantdır.
- `nn` düzeltme eki sürümüdür.

Aşağıdaki tabloda `rollForward` anahtarı için olası değerler gösterilmektedir:

| Değer         | Davranış |
| ------------- | ---------- |
| `patch`       | Belirtilen sürümü kullanır. <br> Bulunamazsa, en son düzeltme eki düzeyine doğru kaydeder. <br> Bulunamazsa, başarısız olur. <br><br> Bu değer, SDK 'nın önceki sürümlerindeki eski davranıştır. |
| `feature`     | Belirtilen ana, ikincil ve özellik bandı için en son düzeltme eki düzeyini kullanır. <br> Bulunamazsa, aynı birincil/ikincil içindeki bir sonraki yüksek Özellik bandına doğru kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır. <br> Bulunamazsa, başarısız olur. |
| `minor`       | Belirtilen ana, ikincil ve özellik bandı için en son düzeltme eki düzeyini kullanır. <br> Bulunamazsa, aynı birincil/alt sürüm içindeki bir sonraki daha yüksek Özellik bandına kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır. <br> Bulunamazsa, aynı ana sırada bir sonraki yüksek ve daha düşük Özellik bandına doğru kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır. <br> Bulunamazsa, başarısız olur. |
| `major`       | Belirtilen ana, ikincil ve özellik bandı için en son düzeltme eki düzeyini kullanır. <br> Bulunamazsa, aynı birincil/alt sürüm içindeki bir sonraki daha yüksek Özellik bandına kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır. <br> Bulunamazsa, aynı ana sırada bir sonraki yüksek ve daha düşük Özellik bandına doğru kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır. <br> Bulunamazsa, daha yüksek büyük, küçük ve özellik bandına ileri doğru kaydeder ve bu özellik bandı için en son düzeltme eki düzeyini kullanır. <br> Bulunamazsa, başarısız olur. |
| `latestPatch` | , İstenen ana, alt ve özellik bandı ile bir düzeltme eki düzeyi ve belirtilen değerden daha büyük veya eşit olan en son yüklenen düzeltme eki düzeyini kullanır. <br> Bulunamazsa, başarısız olur. |
| `latestFeature` | , Belirtilen değerden daha büyük veya eşit olan bir özellik bandı ile istenen büyük ve küçük ile eşleşen en yüksek yüklü Özellik bandı ve düzeltme eki düzeyini kullanır. <br> Bulunamazsa, başarısız olur. |
| `latestMinor` | , Belirtilen değerden daha büyük veya ona eşit olan, istenen ana ile eşleşen en yüksek alt, özellik bandı ve düzeltme eki düzeyini kullanır. <br> Bulunamazsa, başarısız olur. |
| `latestMajor` | , Belirtilen değerden büyük veya eşit olan en yüksek yüklü .NET Core SDK kullanır. <br> Bulunamazsa başarısız olur. |
| `disable`     | İleri doğru değil. Tam eşleşme gereklidir. |

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, ön sürüm sürümlerinin nasıl kullanılacağını gösterir:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

Aşağıdaki örnek, belirtilen sürümden daha büyük veya eşit olan en yüksek sürümü nasıl kullanacağınızı gösterir:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

Aşağıdaki örnek, belirtilen sürümün tam olarak nasıl kullanılacağını göstermektedir:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

Aşağıdaki örnek, belirli bir sürümün yüklü olduğu en yüksek düzeltme eki sürümünün (3.1.1 xx biçiminde) nasıl kullanılacağını gösterir:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>Global. JSON ve .NET Core CLI

*Global. JSON* dosyasında bir tane ayarlamak için MAKINENIZDE hangi SDK sürümlerinin yüklü olduğunu bilmemiz yararlı olur. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [.NET Core 'un zaten yüklü olduğunu denetleme](../install/how-to-detect-installed-versions.md#check-sdk-versions).

Makinenize ek .NET Core SDK sürümleri yüklemek için [.NET Core 'U indir](https://dotnet.microsoft.com/download/dotnet-core) sayfasını ziyaret edin.

Aşağıdaki örneğe benzer şekilde, [DotNet New](dotnet-new.md) komutunu yürüterek geçerli dizinde yeni bir *Global. JSON* dosyası oluşturabilirsiniz:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Eşleşen kurallar

> [!NOTE]
> Eşleşen kurallar, yüklü olan tüm .NET çekirdeği yüklü çalışma zamanları genelinde ortak olan `dotnet.exe` giriş noktasına tabidir. .NET Core çalışma zamanının en son yüklü sürümü için eşleşen kurallar, yan yana birden çok çalışma zamanı yüklendiğinde kullanılır.

## <a name="net-core-3x"></a>[.NET Core 3. x](#tab/netcore3x)

.NET Core 3,0 ile başlayarak, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:

- Global. *JSON* dosyası bulunmazsa veya *Global. JSON* bir SDK sürümü veya bir `allowPrerelease` değeri belirtmezse, en yüksek yüklü SDK sürümü kullanılır (`rollForward` ayarı `latestMajor`olarak eşdeğerdir). Ön sürüm SDK sürümlerinin kabul edilip edilmediği, `dotnet` nasıl çağrıldığına bağlıdır.
  - Visual Studio 'da **değilseniz** , ön sürüm sürümleri göz önünde bulundurulmaz.
  - Visual Studio 'da çalışıyorsanız, istenen ön sürüm durumunu kullanır. Diğer bir deyişle, Visual Studio 'nun önizleme sürümünü kullanıyorsanız veya .NET Core SDK seçeneğinin ( **araçlar** > **seçenekler** > **ortam** > **Önizleme özellikleri**) **kullanım önizlemelerini** ayarlarsanız, ön sürüm sürümleri göz önünde bulundurululur; Aksi takdirde, yalnızca yayın sürümleri kabul edilir.
- Bir SDK sürümü belirtmeyen, ancak bir `allowPrerelease` değerini belirten bir *Global. JSON* dosyası bulunursa, en yüksek yüklü SDK sürümü kullanılır (`latestMajor``rollForward` ayarlamaya eşdeğerdir). En son SDK sürümünün yayınlanıp yayınlanamayacağını veya ön sürümü `allowPrerelease`değerine bağlıdır. `true`, ön sürüm sürümlerinin kabul edileceğini belirtir; `false` yalnızca yayın sürümlerinin kabul edileceğini gösterir.
- Bir *Global. JSON* dosyası bulunursa ve bir SDK sürümü belirtiyorsa:

  - `rollFoward` değer ayarlanmamışsa, varsayılan `rollForward` ilkesi olarak `latestPatch` kullanır. Aksi takdirde, her bir değeri ve bunların davranışını [rollforward](#rollforward) bölümünde denetleyin.
  - Ön sürüm sürümlerinin dikkate alınıp alınmayacağını ve `allowPrerelease` ayarlanmamışsa, [Allowbir ön sürümü](#allowprerelease) bölümünde açıklanan varsayılan davranış nedir?

## <a name="net-core-2x"></a>[.NET Core 2. x](#tab/netcore2x)

.NET Core 2. x SDK 'da, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:

- *Global. JSON* dosyası bulunmazsa veya *geneldir. JSON* bir SDK sürümü belirtmez, en son yüklenen SDK sürümü kullanılır. En son SDK sürümü yayın veya ön sürüm olabilir; en yüksek sürüm numarası kazanır.
- *Global. JSON* bir SDK sürümü belirtirseniz:
  - Makinede belirtilen SDK sürümü bulunursa, bu tam sürüm kullanılır.
  - Makinede belirtilen SDK sürümü bulunamazsa, bu sürümün en son yüklenen SDK **düzeltme eki sürümü** kullanılır. En son yüklenen SDK **düzeltme eki sürümü** sürüm veya ön sürüm olabilir; en yüksek sürüm numarası kazanır. .NET Core 2,1 ve üzeri sürümlerde, belirtilen **Düzeltme Eki sürümünden** düşük olan **yama sürümleri** SDK seçiminde yok sayılır.
  - Belirtilen SDK sürümü ve uygun bir SDK **yaması sürümü** bulunamazsa hata oluşur.

SDK sürümü aşağıdaki bölümlerden oluşur:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

.NET Core SDK **özellik sürümü** , SDK sürümleri 2.1.100 ve üzeri için sayının (`xyz`) son parçasında ilk basamak (`x`) ile temsil edilir. Genel olarak, .NET Core SDK .NET Core 'dan daha hızlı bir yayın döngüsüne sahiptir.

**Düzeltme eki sürümü** , SDK sürümleri 2.1.100 ve üzeri için sayının (`xyz`) son bölümünde son iki basamak (`yz`) tarafından tanımlanır. Örneğin, SDK sürümü olarak `2.1.300` belirtirseniz, SDK seçimi en fazla `2.1.399` bulur ancak `2.1.400` `2.1.300`için bir düzeltme eki sürümü olarak kabul edilmez.

`2.1.201` aracılığıyla `2.1.100` .NET Core SDK sürümler sürüm numarası şemaları arasındaki geçiş sırasında yayımlanmıştır ve `xyz` gösterimini doğru şekilde işlemez. Bu sürümleri *Global. JSON* dosyasında belirtirseniz, belirtilen sürümlerin hedef makinelerde olduğundan emin olmanız önerilir.

---

## <a name="troubleshoot-build-warnings"></a>Derleme uyarıları sorunlarını giderme

* Aşağıdaki uyarı, projenizin .NET Core SDK ön sürümü kullanılarak derlendiğini gösterir:

  > .NET Core SDK bir önizleme sürümü ile çalışıyorsunuz. SDK sürümünü geçerli projedeki Global. JSON dosyası aracılığıyla tanımlayabilirsiniz. Daha fazla <https://go.microsoft.com/fwlink/?linkid=869452>.

  .NET Core SDK sürümlerde yüksek kaliteli bir geçmiş ve taahhüt vardır. Ancak, bir ön sürüm sürümü kullanmak istemiyorsanız, .NET Core 3,0 SDK ile kullanabileceğiniz farklı stratejileri veya [allowbir ön](#allowprerelease) sürümü bölümünde daha sonraki bir sürümü kontrol edin. .NET Core 3,0 veya daha yüksek bir çalışma zamanı veya SDK yüklü olmayan makinelerde, bir *Global. JSON* dosyası oluşturmanız ve kullanmak istediğiniz tam sürümü belirtmeniz gerekir.

* Aşağıdaki uyarı, projenizin .NET Core 2,1 SDK ve sonraki sürümlerle uyumlu olmayan 1,0 veya 1,1 EF Core hedeflediği anlamına gelir:

  > ' {StartupProject} ' başlangıç projesi Framework 'ü hedefliyor. NETCoreApp ' sürümü ' {targetFrameworkVersion} '. Entity Framework Core .NET komut satırı araçlarının bu sürümü yalnızca sürüm 2,0 veya üstünü destekler. Araçların eski sürümlerini kullanma hakkında daha fazla bilgi için bkz. <https://go.microsoft.com/fwlink/?linkid=871254>.

  .NET Core 2,1 SDK (sürüm 2.1.300) ile başlayarak, `dotnet ef` komutu SDK 'ya dahil edilir. Projenizi derlemek için, makinenizde .NET Core 2,0 SDK 'sını (sürüm 2.1.201) veya daha önceki bir sürümü yükleyip *Global. JSON* dosyasını kullanarak istenen SDK sürümünü tanımlayın. `dotnet ef` komutu hakkında daha fazla bilgi için bkz. [EF Core .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Ayrıca bkz.

- [Proje SDK 'Ları nasıl çözümlenir](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
