---
title: DotNet command - .NET Core CLI Temizle
description: Dotnet Temizle komutu, geçerli dizin temizler.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 9e68781fe00590f3c8d429631a3f72d525d29fa9
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697037"
---
# <a name="dotnet-clean"></a>DotNet Temizle

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet clean` -Proje çıktı temizler.

## <a name="synopsis"></a>Özet

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet clean` Komutu önceki yapı çıktı temizler. Olarak uygulanan bir [MSBuild hedef](/visualstudio/msbuild/msbuild-targets), bu komutu çalıştırdığınızda proje değerlendirilir. Yalnızca derleme sırasında oluşturulan çıkışları temizlenir. Her iki ara (*obj*) ve son çıktı (*bin*) klasörleri temizlendi.

## <a name="arguments"></a>Arguments

`PROJECT`

Temizlemek için MSBuild proje. MSBuild proje dosyası belirtilmezse, geçerli çalışma dizini ile biten bir dosya uzantısına sahip bir dosya için arar *proj* ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug` şeklindedir. Bu seçeneği yalnızca olan yapı süre boyunca belirtilmişse temizlenirken gerekli.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) derleme zamanında belirtildi. Framework tanımlanmalıdır [proje dosyası](csproj.md). Framework'te derleme zamanında belirtilmişse framework temizlenirken belirtmeniz gerekir.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-o|--output <OUTPUT_DIRECTORY>`

Dizin oluşturma çıkışları yer alır. Belirtin `-f|--framework <FRAMEWORK>` geçiş çıktı dizini ile proje yapılandırıldığında framework belirtilmişse.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Belirtilen çalışma zamanının çıkış klasörü siler. Bu kullanılır olduğunda bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen düzeyleri q [uiet], [en az sıfır] m, n [ormal], [kincil] d ve tanı [nostic] ' dir.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug` şeklindedir. Bu seçeneği yalnızca olan yapı süre boyunca belirtilmişse temizlenirken gerekli.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) derleme zamanında belirtildi. Framework tanımlanmalıdır [proje dosyası](csproj.md). Framework'te derleme zamanında belirtilmişse framework temizlenirken belirtmeniz gerekir.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-o|--output <OUTPUT_DIRECTORY>`

Dizin oluşturma çıkışları yer alır. Belirtin `-f|--framework <FRAMEWORK>` geçiş çıktı dizini ile proje yapılandırıldığında framework belirtilmişse.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen düzeyleri q [uiet], [en az sıfır] m, n [ormal], [kincil] d ve tanı [nostic] ' dir.

---

## <a name="examples"></a>Örnekler

Projenin varsayılan derlemeyi temizleme:

`dotnet clean`

Yayın yapılandırma kullanılarak oluşturulmuştur bir projeyi temizleyin:

`dotnet clean --configuration Release`
