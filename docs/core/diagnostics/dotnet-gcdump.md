---
title: DotNet-gcdump-.NET Core
description: DotNet-gcdump komut satırı aracını yükleme ve kullanma.
ms.date: 07/26/2020
ms.openlocfilehash: 10e4c7e9e3a1df5d0eb58e68d38c0af091aeedc1
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88575685"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a>Yığın Analizi Aracı (DotNet-gcdump)

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,1 SDK ve sonraki sürümleri

## <a name="install-dotnet-gcdump"></a>DotNet-gcdump 'i yükler

NuGet paketinin en son sürümünü yüklemek için `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a>Özeti

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a>Açıklama

`dotnet-gcdump`Genel araç, canlı .net IŞLEMLERININ GC (çöp toplayıcısı) dökümlerini toplamanın bir yoludur. Windows üzerinde ETW için platformlar arası bir alternatif olan EventPipe teknolojisini kullanır. GC dökümleri, hedef işlemde bir GC tetikleyerek, özel olayları açıp, nesne kökleri grafiğini Olay akışından yeniden oluşturarak oluşturulur. Bu, işlem çalışırken en az ek yük ile GC dökümlerinin toplanmasını sağlar. Bu dökümler birkaç senaryo için yararlıdır:

- Yığın üzerindeki nesne sayısını zaman içinde birkaç noktada karşılaştırma.
- Nesnelerin kökleri çözümleniyor ("Bu tür için hala bir başvuru var?" gibi sorulara yanıt verme).
- Yığındaki nesnelerin sayılarıyla ilgili genel istatistikleri toplama.

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a>DotNet-gcdump öğesinden yakalanan GC dökümünü görüntüleme

Windows 'da, `.gcdump` dosyalar, analiz veya Visual Studio 'Da [PerfView](https://github.com/microsoft/perfview) ' de görüntülenebilir. Şu anda Windows dışı platformlarda ' ı açma yöntemi yoktur `.gcdump` .

`.gcdump`Bir karşılaştırma deneyimi almak için birden çok s toplayabilir ve bunları Visual Studio 'da eşzamanlı olarak açabilirsiniz.

## <a name="options"></a>Seçenekler

- **`--version`**

  `dotnet-gcdump`Yardımcı programın sürümünü görüntüler.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## `dotnet-gcdump collect`

Şu anda çalışan bir işlemden bir GC dökümü toplar.

### <a name="synopsis"></a>Özeti

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut satırı yardımını gösterir.

- **`-p|--process-id <pid>`**

  GC dökümünü toplanacak işlem kimliği.

- **`-o|--output <gcdump-file-path>`**

  Toplanan GC dökümlerinin yazılması gereken yol. Varsayılan olarak olur *. \\ YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*.

- **`-v|--verbose`**

  GC dökümünü toplarken günlüğü çıkış.

- **`-t|--timeout <timeout>`**

  Bu çok saniyeden daha uzun sürerse GC dökümünü toplama hakkında bilgi verin. Varsayılan değer 30’dur.

- **`-n|--name <name>`**

  GC dökümünü toplanacak işlemin adı.

## `dotnet-gcdump ps`

GC dökümlerinin toplanabilecek DotNet süreçlerini listeler.

### <a name="synopsis"></a>Özeti

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

Önceden oluşturulmuş bir GC dökümünden veya çalışan bir işlemden rapor oluşturun ve öğesine yazın `stdout` .

### <a name="synopsis"></a>Özeti

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut satırı yardımını gösterir.

- **`-p|--process-id <pid>`**

  GC dökümünü toplanacak işlem kimliği.

- **`-t|--report-type <HeapStat>`**

  Oluşturulacak raporun türü. Kullanılabilir seçenekler: heapstat (varsayılan).

## <a name="troubleshoot"></a>Sorun giderme

- Gcdump içinde tür bilgisi yok.

   .NET Core 3,1 ' den önce, EventPipe ile çağrıldığında gcdumps arasında bir tür önbelleğinin temizlenmediği bir sorun oluştu. Bu, ikinci ve sonraki gcdumps için gönderilmemiş tür bilgilerinin belirlenmesi için gereken olaylara neden oldu. Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.

- COM ve statik türler GC dökümünde değildir.

   .NET Core 3,1-preview2 öncesinde, GC dökümü EventPipe aracılığıyla çağrıldığında statik ve COM türlerinin gönderilmediği bir sorun oluştu. Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.
