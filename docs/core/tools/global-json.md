---
title: global.json’a genel bakış
description: .NET Core CLI komutlarını çalıştırırken .NET Core SDK sürümünü ayarlamak için Global. json dosyasını nasıl kullanacağınızı öğrenin.
ms.date: 12/03/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 4da703266e98b209cdd031f4ea856b4d7c83930c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714167"
---
# <a name="globaljson-overview"></a>global.json’a genel bakış

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

*Global. JSON* dosyası, .NET Core CLI komutlarını çalıştırdığınızda hangi .NET Core SDK sürümünün kullanıldığını tanımlamanızı sağlar. .NET Core SDK seçilmesi, projenizin hedeflediği çalışma zamanını belirtmekten bağımsızdır. .NET Core SDK sürümü .NET Core CLI araçlarının hangi sürümlerinin kullanıldığını gösterir. Genel olarak, araçların en son sürümünü kullanmak istersiniz, bu yüzden *Global. JSON* dosyası gerekli değildir.

Bunun yerine çalışma zamanının belirtilmesi hakkında daha fazla bilgi için bkz. [hedef çerçeveler](../../standard/frameworks.md).

.NET Core SDK geçerli çalışma dizininde (proje diziniyle aynı olmayan) veya üst dizinlerinden biri olan *Global. JSON* dosyasını arar.

## <a name="globaljson-schema"></a>Global. JSON şeması

### <a name="sdk"></a>sdk

Tür: nesne

Seçilecek .NET Core SDK hakkındaki bilgileri belirtir.

#### <a name="version"></a>sürümü

Türü: Dize

Kullanılacak .NET Core SDK sürümü.

Bu alanın şu şekilde olduğunu unutmayın:

- Glob desteği yoktur, yani tam sürüm numarası belirtilmelidir.
- Sürüm aralıklarını desteklemez.

Aşağıdaki örnek, bir *Global. JSON* dosyasının içeriğini gösterir:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>Global. JSON ve .NET Core CLI

*Global. JSON* dosyasında bir tane ayarlamak için hangi sürümlerin kullanılabildiğini bilmek yararlı olur. Desteklenen kullanılabilir SDK 'ların tam listesini [.NET Core](https://dotnet.microsoft.com/download/dotnet-core) ' u indirin sayfasından bulabilirsiniz. .NET Core 2,1 SDK ile başlayarak, makinenizde zaten yüklü olan SDK sürümlerini doğrulamak için aşağıdaki komutu çalıştırabilirsiniz:

```dotnetcli
dotnet --list-sdks
```

Makinenize ek .NET Core SDK sürümleri yüklemek için [.NET Core 'U indir](https://dotnet.microsoft.com/download/dotnet-core) sayfasını ziyaret edin.

Aşağıdaki örneğe benzer şekilde, [DotNet New](dotnet-new.md) komutunu yürüterek geçerli dizinde yeni bir *Global. JSON* dosyası oluşturabilirsiniz:

```dotnetcli
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a>Eşleşen kurallar

> [!NOTE]
> Eşleşen kurallar, .NET Core çalışma zamanının bir parçası olan apphost tarafından yönetilir.
> Ana bilgisayarın en son sürümü, yan yana birden fazla çalışma zamanı yüklendiğinde kullanılır.

.NET Core 2,0 ile başlayarak, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:

- *Global. JSON* dosyası bulunmazsa veya *geneldir. JSON* bir SDK sürümü belirtmez, en son yüklenen SDK sürümü kullanılır. En son SDK sürümü yayın veya yayın öncesi olabilir. en yüksek sürüm numarası kazanır.
- *Global. JSON* bir SDK sürümü belirtirseniz:
  - Makinede belirtilen SDK sürümü bulunursa, bu tam sürüm kullanılır.
  - Makinede belirtilen SDK sürümü bulunamazsa, bu sürümün en son yüklenen SDK **düzeltme eki sürümü** kullanılır. En son yüklenen SDK **düzeltme eki sürümü** sürüm veya yayın öncesi olabilir. en yüksek sürüm numarası kazanır. .NET Core 2,1 ve üzeri sürümlerde, belirtilen **Düzeltme Eki sürümünden** düşük olan **yama sürümleri** SDK seçiminde yok sayılır.
  - Belirtilen SDK sürümü ve uygun bir SDK **yaması sürümü** bulunamazsa hata oluşur.

SDK sürümü şu anda aşağıdaki bölümlerden oluşur:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

.NET Core SDK **özellik sürümü** , SDK sürümleri 2.1.100 ve üzeri için sayının (`xyz`) son parçasında ilk basamak (`x`) ile temsil edilir. Genel olarak, .NET Core SDK .NET Core 'dan daha hızlı bir yayın döngüsüne sahiptir.

**Düzeltme eki sürümü** , SDK sürümleri 2.1.100 ve üzeri için sayının (`xyz`) son bölümünde son iki basamak (`yz`) tarafından tanımlanır. Örneğin, SDK sürümü olarak `2.1.300` belirtirseniz, SDK seçimi en fazla `2.1.399` bulur ancak `2.1.400` `2.1.300`için bir düzeltme eki sürümü olarak kabul edilmez.

`2.1.201` aracılığıyla `2.1.100` .NET Core SDK sürümler sürüm numarası şemaları arasındaki geçiş sırasında yayımlanmıştır ve `xyz` gösterimini doğru şekilde işlemez. Bu sürümleri *Global. JSON* dosyasında belirtirseniz, belirtilen sürümlerin hedef makinelerde olduğundan emin olmanız önerilir.

.NET Core SDK 1. x ile bir sürüm belirttiyseniz ve tam eşleşme bulunmazsa, en son yüklenen SDK sürümü kullanılmıştır. En son SDK sürümü yayın veya yayın öncesi olabilir. en yüksek sürüm numarası kazanır.

## <a name="troubleshooting-build-warnings"></a>Derleme uyarıları sorunlarını giderme

> [!WARNING]
> .NET Core SDK bir önizleme sürümü ile çalışıyorsunuz. SDK sürümünü geçerli projedeki Global. JSON dosyası aracılığıyla tanımlayabilirsiniz. Daha fazla <https://go.microsoft.com/fwlink/?linkid=869452>

Bu uyarı, projenizin, [eşleşen kurallar](#matching-rules) bölümünde açıklandığı gibi .NET Core SDK bir önizleme sürümü kullanılarak derlendiğini gösterir. .NET Core SDK sürümlerde yüksek kaliteli bir geçmiş ve taahhüt vardır. Ancak, bir önizleme sürümü kullanmak istemiyorsanız, hangi SDK sürümünün kullanılacağını belirtmek için proje hiyerarşisi yapısına bir *Global. JSON* dosyası ekleyin ve sürümün makinenizde yüklü olduğunu onaylamak için `dotnet --list-sdks` kullanın. Yeni bir sürüm yayınlandığında, yeni sürümü kullanmak için *Global. JSON* dosyasını kaldırın veya daha yeni sürümü kullanacak şekilde güncelleştirin.

> [!WARNING]
> ' {StartupProject} ' başlangıç projesi Framework 'ü hedefliyor. NETCoreApp ' sürümü ' {targetFrameworkVersion} '. Entity Framework Core .NET komut satırı araçlarının bu sürümü yalnızca sürüm 2,0 veya üstünü destekler. Araçların eski sürümlerini kullanma hakkında daha fazla bilgi için bkz. <https://go.microsoft.com/fwlink/?linkid=871254>

.NET Core 2,1 SDK (sürüm 2.1.300) ile başlayarak, `dotnet ef` komutu SDK 'ya dahil edilir. Bu uyarı, projenizin .NET Core 2,1 SDK ve sonraki sürümlerle uyumlu olmayan EF Core 1,0 veya 1,1 ' i hedeflediğini belirtir. Projenizi derlemek için, makinenizde .NET Core 2,0 SDK (sürüm 2.1.201) ve önceki bir sürümü yükleyip *Global. JSON* dosyasını kullanarak istenen SDK sürümünü tanımlayın. `dotnet ef` komutu hakkında daha fazla bilgi için bkz. [EF Core .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Ayrıca bkz.

- [Proje SDK 'Ları nasıl çözümlenir](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
