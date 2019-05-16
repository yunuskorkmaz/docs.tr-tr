---
title: Global.JSON genel bakış
description: .NET Core SDK'sı sürümü, .NET Core CLI komutlarını çalıştırırken ayarlanacak global.json dosyasını kullanmayı öğrenin.
ms.date: 12/03/2018
ms.custom: updateeachrelease, seodec18
ms.openlocfilehash: a3d90e39401ece8d106d89a7533b7c1e1e4433cd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632393"
---
# <a name="globaljson-overview"></a>Global.JSON genel bakış

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

*Global.json* dosyası hangi .NET Core SDK'sı sürümü, .NET Core CLI komutlarını çalıştırmanız kullanıldığında tanımlamanıza izin verir. .NET Core SDK'yı seçerek projenizin hedeflediği çalışma zamanı belirtmelerini bağımsızdır. .NET Core SDK'sı sürümü, .NET Core CLI araçları hangi sürümlerinin kullanıldığını belirtir. Genel olarak, Araçlar, dolayısıyla en son sürümünü kullanmak istediğiniz *global.json* dosyası gereklidir.

Bunun yerine çalışma zamanı belirtme hakkında daha fazla bilgi için bkz. [hedef çerçeveyi](../../standard/frameworks.md).

.NET core SDK'sı arayan bir *global.json* dosyasında (Bu proje dizinine aynı olmak zorunda olmayan) geçerli çalışma dizinine veya onun üst dizinlerin biri.

## <a name="globaljson-schema"></a>Global.JSON şeması

### <a name="sdk"></a>SDK'sı

Tür: Nesne

Seçmek için .NET Core SDK'sı hakkında bilgileri belirtir.

#### <a name="version"></a>sürüm

Tür: Dize

.NET Core SDK'sını kullanmaya sürümü.

Unutmayın, bu alan:

- Değil Glob desteğine sahip, diğer bir deyişle, tam sürüm numarası belirtilmiş olması gerekir.
- Sürüm aralıklarını desteklemiyor.

Aşağıdaki örnek, içeriğini gösterir. bir *global.json* dosyası:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>Global.JSON ve .NET Core CLI

Hangi sürümlerinin bir ayarlamak için kullanılabilir olduğunu öğrenmek yararlıdır *global.json* dosya. Desteklenen kullanılabilir SDK'lar tam listesini bulabilirsiniz [.NET indirir](https://www.microsoft.com/net/download/all) site. .NET Core 2.1 SDK ile başlayarak, hangi SDK sürümlerinin makinenizde zaten yüklü olduğunu doğrulamak için aşağıdaki komutu çalıştırabilirsiniz:

```console
dotnet --list-sdks
```

Makinenizde ek .NET Core SDK'sı sürümünü birden yüklemek için şurayı ziyaret edin [.NET indirir](https://www.microsoft.com/net/download/all) site.

Yeni bir oluşturabilirsiniz *global.json* yürüterek geçerli dizin dosyası [yeni dotnet](dotnet-new.md) komutu, aşağıdaki örneğe benzer:

```console
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a>Eşleştirme kuralları

> [!NOTE]
> Eşleştirme kuralları, .NET Core çalışma zamanı bir parçası olduğu apphost tarafından yönetilir.
> Konak en son sürümünü, birden çok çalışma zamanları yüklü yan yana olduğunda kullanılır.

.NET Core 2.0 ile başlayarak, SDK'yı kullanmak için hangi sürümünün belirlerken aşağıdaki kurallar geçerlidir:

- Hayır ise *global.json* dosya bulunduğunda veya *global.json* bir SDK sürümü belirtmeyen en son yüklenen SDK sürüm kullanılır. En son SDK sürümü, yayın veya yayın öncesi-en yüksek sürüm numarası WINS olabilir.
- Varsa *global.json* SDK sürümü belirtin:
  - Belirtilen SDK sürümü makinede bulunursa o tam sürümü kullanılır.
  - Belirtilen SDK sürümü makinede bulunamazsa, en son SDK'sı yüklü **düzeltme eki sürümü** olan sürümü kullanılır. SDK'sı yüklü en son sürüm **düzeltme eki sürümü** yayın veya yayın öncesi-en yüksek sürüm numarası WINS olabilir. .NET Core 2.1 ve üzeri **düzeltme eki sürümleri** tutardan **düzeltme eki sürümü** belirtilen SDK seçiminde göz ardı edilir.
  - Varsa belirtilen SDK sürümü ve uygun bir SDK **düzeltme eki sürümü** bulunamıyor, hata oluşur.

SDK sürümü, şu anda aşağıdaki bölümlerden oluşur:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Özellik yayın** .NET Core SDK'ın ilk basamak tarafından temsil edilen (`x`) numarasının son bölümünde (`xyz`) 2.1.100 SDK sürümleri ve üzeri. Genel olarak, .NET Core SDK'sı, .NET Core daha hızlı sürüm döngüsü vardır.

**Düzeltme eki sürümü** son iki basamak tarafından tanımlanan (`yz`) numarasının son bölümünde (`xyz`) 2.1.100 SDK sürümleri ve üzeri. Örneğin, belirttiğiniz `2.1.300` SDK sürümü kadar SDK seçimi bulur `2.1.399` ancak `2.1.400` için bir düzeltme eki sürümü kabul değil `2.1.300`.

.NET core SDK sürümleri `2.1.100` aracılığıyla `2.1.201` sürüm numarası düzeni arasında geçiş sırasında yayımlanan ve doğru bir şekilde işlemez `xyz` gösterimi. Bu sürümlerde belirtirseniz önerilir *global.json* dosyası belirtilen sürümlerde hedef makinelerde olduğundan emin olun.

.NET Core SDK'sı ile bir sürüm ve tam eşleşme belirtilmişse 1.x bulunamadı, en son yüklenen SDK sürüm kullanıldı. En son SDK sürümü, yayın veya yayın öncesi-en yüksek sürüm numarası WINS olabilir.

## <a name="troubleshooting-build-warnings"></a>Sorun giderme derleme uyarıları

> [!WARNING]
> .NET Core SDK'sını bir önizleme sürümü ile çalışıyor. Geçerli projede SDK sürümü bir global.json dosyasını aracılığıyla tanımlayabilirsiniz. Daha fazla bilgi için <https://go.microsoft.com/fwlink/?linkid=869452>

Bu uyarı, projeniz .NET Core SDK'sı, bir önizleme sürümünü kullanarak açıklandığı şekilde derleniyor olduğunu gösterir. [kurallarına](#matching-rules) bölümü. .NET core SDK'sı sürümü geçmişi ve yüksek kaliteli olma taahhüdü bulunuyor. Ancak, bir önizleme sürümünü kullanmak istemiyorsanız, ekleme bir *global.json* proje hiyerarşisi yapısı kullanın ve hangi SDK sürümünü belirtmek üzere dosyaya `dotnet --list-sdks` sürümü, makinenizde yüklü olduğundan emin olmak için. Yeni bir sürümü yayımlandığında yeni sürümü kullanmak için ya da kaldırma *global.json* dosya ya da daha yeni sürümünü kullanacak şekilde güncelleştirin.

> [!WARNING]
> Başlangıç projesi '{startupProject}' hedef framework '. NETCoreApp' sürümü '{targetFrameworkVersion}'. Entity Framework Core ve .NET komut satırı araçları bu sürümü yalnızca sürüm 2.0 veya üstü destekler. Araçlar'ın eski sürümlerini kullanma hakkında daha fazla bilgi için bkz. <https://go.microsoft.com/fwlink/?linkid=871254>

.NET Core 2.1 SDK (sürüm 2.1.300) ile başlayan `dotnet ef` komutu birlikte gelen SDK. Bu uyarı, projenizi EF Core 1.0 veya 1.1, .NET Core 2.1 SDK ve sonraki sürümler ile uyumlu değil hedefleyen olduğunu gösterir. Projenizi derlemek için .NET Core 2.0 SDK'sını (sürüm 2.1.201) yükleyin ve makinenizde önceki ve istenen SDK sürümüyle tanımlamak *global.json* dosya. Hakkında daha fazla bilgi için `dotnet ef` komutu, bkz: [EF Core .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Ayrıca bkz.

- [Proje SDK'ları nasıl çözümlenir](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
