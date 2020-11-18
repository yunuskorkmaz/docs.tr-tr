---
title: DotNet-gcdump Tanılama aracı-.NET CLı
description: .NET EventPipe kullanarak canlı .NET işlemlerinin GC (çöp toplayıcısı) dökümlerini toplamak için DotNet-gcdump CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 59de1845ada9e5bdd0b24bf4312517283324ce94
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826046"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a>Yığın Analizi Aracı (DotNet-gcdump)

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,1 SDK ve sonraki sürümleri

## <a name="install"></a>Yükleme

İndirmek ve yüklemek için iki yol vardır `dotnet-gcdump` :

- **DotNet genel aracı:**

  NuGet paketinin en son sürümünü yüklemek için `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- **Doğrudan indirme:**

  Platformunuzla eşleşen araç yürütülebilirini indirin:

  | İşletim Sistemi  | Platform |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [ARM](https://aka.ms/dotnet-gcdump/win-arm) \| [ARM-x64](https://aka.ms/dotnet-gcdump/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-gcdump/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [ARM](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64) |

## <a name="synopsis"></a>Özeti

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a>Açıklama

`dotnet-gcdump`Genel araç, [eventpipe](./eventpipe.md)kullanarak canlı .net Işlemlerinin GC (çöp toplayıcısı) dökümlerini toplar. GC dökümleri, hedef işlemde bir GC tetikleyerek, özel olayları açıp, nesne kökleri grafiğini Olay akışından yeniden oluşturarak oluşturulur. Bu işlem, işlem çalışırken ve en az ek yük ile GC dökümlerinin toplanmasını sağlar. Bu dökümler birkaç senaryo için yararlıdır:

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

  GC dökümünü toplanacak işlem KIMLIĞI.

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

  GC dökümünü toplanacak işlem KIMLIĞI.

- **`-t|--report-type <HeapStat>`**

  Oluşturulacak raporun türü. Kullanılabilir seçenekler: heapstat (varsayılan).

## <a name="troubleshoot"></a>Sorun giderme

- Gcdump içinde tür bilgisi yok.

   .NET Core 3,1 ' den önce, EventPipe ile çağrıldığında gcdumps arasında bir tür önbelleğinin temizlenmediği bir sorun oluştu. Bu, ikinci ve sonraki gcdumps için gönderilmemiş tür bilgilerinin belirlenmesi için gereken olaylara neden oldu. Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.

- COM ve statik türler GC dökümünde değildir.

   .NET Core 3,1-preview2 öncesinde, GC dökümü EventPipe aracılığıyla çağrıldığında statik ve COM türlerinin gönderilmediği bir sorun oluştu. Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.
