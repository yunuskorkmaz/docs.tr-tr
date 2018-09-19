---
title: DotNet command - .NET Core CLI Temizle
description: Dotnet temiz komut geçerli dizinde temizler.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 5553e4b4423a2d824c05caf7114c47b5f1c20477
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45988341"
---
# <a name="dotnet-clean"></a>DotNet Temizle

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet clean` -Bir projenin çıkışı temizler.

## <a name="synopsis"></a>Özeti

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

`dotnet clean` Komut önceki yapı çıkışını temizler. Olarak uygulanan bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets), projenin komut çalıştırıldığında değerlendirilir. Yalnızca derleme sırasında oluşturulan çıkışları temizlenir. Her iki Orta (*obj*) ve son çıktı (*bin*) klasörler temizlendi.

## <a name="arguments"></a>Arguments

`PROJECT`

Temizlemek için MSBuild proje. Bir proje dosyası belirtilmezse, MSBuild ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir. Bu seçeneği yalnızca olan derleme zamanında belirtilmişse temizlenirken gerekli.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) oluşturma zamanında belirtildi. Framework tanımlanmalıdır [proje dosyası](csproj.md). Oluşturma zamanında framework belirtilmişse framework temizlenirken belirtmeniz gerekir.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-o|--output <OUTPUT_DIRECTORY>`

Dizini, derleme çıktılarını yerleştirilir. Belirtin `-f|--framework <FRAMEWORK>` çerçeve proje oluşturulduğunda belirttiyseniz çıkış dizini anahtarıyla geçin.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Belirtilen çalışma zamanı çıktı klasörünü siler. Bu, bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen düzeyleri q [uiet], m [en az sıfır], [ormal] n, d [ayrıntılı] ve tanı [tanısı] ' dir.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir. Bu seçeneği yalnızca olan derleme zamanında belirtilmişse temizlenirken gerekli.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) oluşturma zamanında belirtildi. Framework tanımlanmalıdır [proje dosyası](csproj.md). Oluşturma zamanında framework belirtilmişse framework temizlenirken belirtmeniz gerekir.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-o|--output <OUTPUT_DIRECTORY>`

Dizini, derleme çıktılarını yerleştirilir. Belirtin `-f|--framework <FRAMEWORK>` çerçeve proje oluşturulduğunda belirttiyseniz çıkış dizini anahtarıyla geçin.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen düzeyleri q [uiet], m [en az sıfır], [ormal] n, d [ayrıntılı] ve tanı [tanısı] ' dir.

---

## <a name="examples"></a>Örnekler

Projenin varsayılan derlemeyi temizleme:

`dotnet clean`

Yayın Yapılandırması kullanılarak oluşturulan bir projeyi Temizle:

`dotnet clean --configuration Release`
