---
title: global.json’a genel bakış
description: .NET Core CLI komutlarını çalıştırırken .NET Core SDK sürümünü ayarlamak için Global. json dosyasını nasıl kullanacağınızı öğrenin.
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 5078bc03056c23bccf02e027441de72c69072c7d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202024"
---
# <a name="globaljson-overview"></a>global.json’a genel bakış

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri

*Global. JSON* dosyası, .NET Core CLI komutlarını çalıştırdığınızda hangi .NET Core SDK sürümünün kullanıldığını tanımlamanızı sağlar. .NET Core SDK seçilmesi, projenizin hedeflediği çalışma zamanını belirtmekten bağımsızdır. .NET Core SDK sürümü .NET Core CLI hangi sürümlerinin kullanıldığını gösterir.

Genel olarak, SDK araçlarının en son sürümünü kullanmak istiyorsunuz, bu nedenle *Global. JSON* dosyası gerekli değildir. Bazı Gelişmiş senaryolarda, SDK araçlarının sürümünü denetlemek isteyebilirsiniz ve bu makalede bunun nasıl yapılacağı açıklanır.

Bunun yerine çalışma zamanının belirtilmesi hakkında daha fazla bilgi için bkz. [hedef çerçeveler](../../standard/frameworks.md).

.NET Core SDK geçerli çalışma dizininde (proje diziniyle aynı olmayan) veya üst dizinlerinden biri olan *Global. JSON* dosyasını arar.

## <a name="globaljson-schema"></a>Global. JSON şeması

### <a name="sdk"></a>sdk

Türüyle`object`

Seçilecek .NET Core SDK hakkındaki bilgileri belirtir.

#### <a name="version"></a>sürüm

- Türüyle`string`

- Şu tarihten itibaren kullanılabilir: .NET Core 1,0 SDK.

Kullanılacak .NET Core SDK sürümü.

Bu alan:

- Joker karakter desteği yoktur, yani tam sürüm numarası belirtilmelidir.
- Sürüm aralıklarını desteklemez.

#### <a name="allowprerelease"></a>Allowönsürümü

- Türüyle`boolean`

- Şu tarihten itibaren kullanılabilir: .NET Core 3,0 SDK.

SDK Çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümlerini düşünmesinin gerekip gerekmediğini belirtir.

Bu değeri açıkça ayarlamazsanız, varsayılan değer Visual Studio 'dan çalıştırıp çalıştırdığınıza bağlıdır:

- Visual Studio 'da **değilseniz** varsayılan değer olur `true` .
- Visual Studio 'da çalışıyorsanız, istenen ön sürüm durumunu kullanır. Diğer bir deyişle, Visual Studio 'nun önizleme sürümünü kullanıyorsanız veya .NET Core SDK seçeneğinin ( **Araçlar** **Use previews of the .NET Core SDK**  >  **Seçenekler**  >  **ortamı**  >  **Önizleme özellikleri**altında) kullanım önizlemelerini ayarlarsanız, varsayılan değer olur `true` ; Aksi takdirde, `false` .

#### <a name="rollforward"></a>Ileri alınmaya

- Türüyle`string`

- Şu tarihten itibaren kullanılabilir: .NET Core 3,0 SDK.

Bir SDK sürümü seçerken kullanılacak geri alma ilkesi, belirli bir SDK sürümü eksik olduğunda geri dönüş olarak veya daha yüksek bir sürümü kullanmak için bir yönerge olarak. Bir [Sürüm](#version) `rollForward` , olarak ayarlamadıkça bir değer ile belirtilmelidir `latestMajor` .

Kullanılabilir ilkeleri ve bunların davranışlarını anlamak için şu biçimdeki SDK sürümü için aşağıdaki tanımları göz önünde bulundurun `x.y.znn` :

- `x`ana sürümdür.
- `y`, ikincil sürümdür.
- `z`, özellik bantdır.
- `nn`Düzeltme Eki sürümüdür.

Aşağıdaki tabloda anahtar için olası değerler gösterilmektedir `rollForward` :

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

### <a name="msbuild-sdks"></a>MSBuild-SDK 'lar

Türüyle`object`

Proje SDK sürümünü her bir proje yerine tek bir yerde denetlemenize olanak tanır. Daha fazla bilgi için bkz. [Proje SDK 'Ları nasıl çözümlenir](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, ön sürüm sürümlerinin nasıl kullanılacağını gösterir:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

Aşağıdaki örnek, belirtilen sürümden daha büyük veya eşit olan en yüksek sürümü nasıl kullanacağınızı gösterir. Gösterilen JSON, 2.2.200 ' den önceki SDK sürümlerine izin vermez ve 3.0.xxx ve 3.1.xxx dahil olmak üzere 2.2.200 veya sonraki bir sürüme izin verir.

```json
{
  "sdk": {
    "version": "2.2.200",
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

Aşağıdaki örnek, belirli bir büyük ve küçük sürümünün yüklü olduğu en son özellik bandı ve düzeltme eki sürümünü nasıl kullanacağınızı gösterir. Gösterilen JSON, 3.1.102 ' den önceki SDK sürümlerine izin vermez ve 3.1.102 ya da 3.1.103 veya 3.1.200 gibi daha sonraki 3.1.xxx sürümlerini sağlar.

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

Aşağıdaki örnek, belirli bir sürümün yüklü olduğu en yüksek düzeltme eki sürümünü nasıl kullanacağınızı gösterir. Gösterilen JSON, 3.1.102 ' den önceki SDK sürümlerine izin vermez ve 3.1.102 ya da 3.1.103 veya 3.1.199 gibi sonraki 3.1.1 xx sürümüne izin verir.

```json
{
  "sdk": {
    "version": "3.1.102",
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
> Eşleşen kurallar `dotnet.exe` , tüm yüklü .net çekirdeği yüklü çalışma zamanları genelinde ortak olan giriş noktasına tabidir. .NET Core çalışma zamanının en son yüklü sürümü için eşleşen kurallar, yan yana birden çok çalışma zamanı yüklendiğinde kullanılır.

## <a name="net-core-3x"></a>[.NET Core 3. x](#tab/netcore3x)

.NET Core 3,0 ile başlayarak, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:

- Global. *JSON* dosyası bulunamazsa veya *Global. JSON* bir SDK sürümü ya da bir değer belirtmezse `allowPrerelease` , en yüksek yüklü SDK sürümü kullanılır (ayarına eşdeğerdir `rollForward` `latestMajor` ). Ön sürüm SDK sürümlerinin kabul edilip edilmediği, nasıl `dotnet` çağrıldığına bağlıdır.
  - Visual Studio 'da **değilseniz** , ön sürüm sürümleri göz önünde bulundurulmaz.
  - Visual Studio 'da çalışıyorsanız, istenen ön sürüm durumunu kullanır. Diğer bir deyişle, Visual Studio 'nun önizleme sürümünü kullanıyorsanız veya .NET Core SDK seçeneğinin ( **Araçlar** **Use previews of the .NET Core SDK**  >  **Seçenekler**  >  **ortamı**  >  **Önizleme özellikleri**altında) kullanım önizlemelerini ayarlarsanız, ön sürüm sürümlerinin kabul edilmesi gerekir; Aksi takdirde yalnızca yayın sürümleri kabul edilir.
- Bir SDK sürümü belirtmeyen ancak bir değer belirttiğinde bir *Global. JSON* dosyası bulunursa `allowPrerelease` , en yüksek yüklü SDK sürümü kullanılır (ayarına eşdeğerdir `rollForward` `latestMajor` ). En son SDK sürümünün yayınlanıp yayınlanamayacağını veya ön sürümün değerine bağlı olup olmadığı `allowPrerelease` . `true`ön sürüm sürümlerinin kabul edileceğini belirtir; `false`yalnızca yayın sürümlerinin kabul edileceğini gösterir.
- Bir *Global. JSON* dosyası bulunursa ve bir SDK sürümü belirtiyorsa:

  - `rollFoward`Değer ayarlanmamışsa, `latestPatch` varsayılan ilke olarak kullanır `rollForward` . Aksi takdirde, her bir değeri ve bunların davranışını [rollforward](#rollforward) bölümünde denetleyin.
  - Ön sürüm sürümlerinin göz önünde bulundurulmayacağı ve `allowPrerelease` ayarlanmadı ayarı, [Allowbir ön sürümü](#allowprerelease) bölümünde açıklanmıştır.

## <a name="net-core-2x"></a>[.NET Core 2. x](#tab/netcore2x)

.NET Core 2. x SDK 'da, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:

- *Global. JSON* dosyası bulunmazsa veya *geneldir. JSON* bir SDK sürümü belirtmez, en son yüklenen SDK sürümü kullanılır. En son SDK sürümü yayın veya ön sürüm olabilir; en yüksek sürüm numarası kazanır.
- *Global. JSON* bir SDK sürümü belirtirseniz:
  - Makinede belirtilen SDK sürümü bulunursa, bu tam sürüm kullanılır.
  - Makinede belirtilen SDK sürümü bulunamazsa, bu sürümün en son yüklenen SDK **düzeltme eki sürümü** kullanılır. En son yüklenen SDK **düzeltme eki sürümü** sürüm veya ön sürüm olabilir; en yüksek sürüm numarası kazanır. .NET Core 2,1 ve üzeri sürümlerde, belirtilen **Düzeltme Eki sürümünden** düşük olan **yama sürümleri** SDK seçiminde yok sayılır.
  - Belirtilen SDK sürümü ve uygun bir SDK **yaması sürümü** bulunamazsa hata oluşur.

SDK sürümü aşağıdaki bölümlerden oluşur:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

.NET Core SDK **özellik sürümü** , `x` `xyz` SDK sürümleri 2.1.100 ve üzeri için () sayının son parçasında () ilk basamak () ile temsil edilir. Genel olarak, .NET Core SDK .NET Core 'dan daha hızlı bir yayın döngüsüne sahiptir.

**Düzeltme eki sürümü** , `yz` `xyz` SDK sürümleri 2.1.100 ve üzeri için () sayısının son bölümünde son iki basamak () tarafından tanımlanır. Örneğin, `2.1.300` SDK sürümü olarak belirtirseniz, SDK seçimi için en fazla bulur `2.1.399` ancak `2.1.400` için bir düzeltme eki sürümü kabul edilmez `2.1.300` .

Aracılığıyla .NET Core SDK `2.1.100` sürümler `2.1.201` sürüm numarası şemaları arasındaki geçiş sırasında yayımlanmıştır ve gösterimi doğru şekilde işlemez `xyz` . Bu sürümleri *Global. JSON* dosyasında belirtirseniz, belirtilen sürümlerin hedef makinelerde olduğundan emin olmanız önerilir.

---

## <a name="troubleshoot-build-warnings"></a>Derleme uyarıları sorunlarını giderme

* Aşağıdaki uyarı, projenizin .NET Core SDK ön sürümü kullanılarak derlendiğini gösterir:

  > .NET Core SDK bir önizleme sürümü ile çalışıyorsunuz. SDK sürümünü geçerli projedeki Global. JSON dosyası aracılığıyla tanımlayabilirsiniz. Daha fazlası <https://go.microsoft.com/fwlink/?linkid=869452> :

  .NET Core SDK sürümlerde yüksek kaliteli bir geçmiş ve taahhüt vardır. Ancak, bir ön sürüm sürümü kullanmak istemiyorsanız, .NET Core 3,0 SDK ile kullanabileceğiniz farklı stratejileri veya [allowbir ön](#allowprerelease) sürümü bölümünde daha sonraki bir sürümü kontrol edin. .NET Core 3,0 veya daha yüksek bir çalışma zamanı veya SDK yüklü olmayan makinelerde, bir *Global. JSON* dosyası oluşturmanız ve kullanmak istediğiniz tam sürümü belirtmeniz gerekir.

* Aşağıdaki uyarı, projenizin .NET Core 2,1 SDK ve sonraki sürümlerle uyumlu olmayan 1,0 veya 1,1 EF Core hedeflediği anlamına gelir:

  > ' {StartupProject} ' başlangıç projesi Framework 'ü hedefliyor. NETCoreApp ' sürümü ' {targetFrameworkVersion} '. Entity Framework Core .NET komut satırı araçlarının bu sürümü yalnızca sürüm 2,0 veya üstünü destekler. Araçların eski sürümlerini kullanma hakkında daha fazla bilgi için bkz <https://go.microsoft.com/fwlink/?linkid=871254> ..

  .NET Core 2,1 SDK (sürüm 2.1.300) ile başlayarak, `dotnet ef` komut SDK 'ya dahil edilir. Projenizi derlemek için, makinenizde .NET Core 2,0 SDK 'sını (sürüm 2.1.201) veya daha önceki bir sürümü yükleyip *Global. JSON* dosyasını kullanarak istenen SDK sürümünü tanımlayın. Komutu hakkında daha fazla bilgi için `dotnet ef` bkz. [.NET komut satırı araçlarını EF Core](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Ayrıca bkz.

- [Proje SDK 'Ları nasıl çözümlenir](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
