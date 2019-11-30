---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568243"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor

ZIP arşivi, merkezi dizinde ve yerel üstbilgide Sıkıştırılmış boyut ve sıkıştırılmamış boyut listesini de listeler.  Giriş verilerinin kendisi de boyutunu gösterir.  .NET Core 2,2 ve önceki sürümlerinde, bu değerler hiçbir şekilde tutarlılık denetimi yapılmadı. .NET Core 3,0 ' den itibaren artık kullanıma sunulmuştur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerde <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>, yerel üst bilgi ZIP dosyasının orta üst bilgisiyle kabul etmese bile başarılı olur. Verilerin uzunluğu, merkezi Dizin/yerel üst bilgisinde listelenen sıkıştırılmamış dosya boyutunu aşsa bile, sıkıştırılan akışın sonuna ulaşılana kadar veriler açılır.

<xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> yöntemi, .NET Core 3,0 ile başlayarak, bir girdinin sıkıştırılmış ve sıkıştırılmamış boyutları üzerinde, yerel üst bilgi ve orta üst bilgi kullanımını kabul eder.  Aksi takdirde, arşiv 'in yerel üstbilgisi ve/veya ZIP dosyasının merkezi diziniyle kabul eterdikleri veri tanımlayıcısı listesi boyutları yoksa Yöntem bir <xref:System.IO.InvalidDataException> oluşturur. Bir girişi okurken, sıkıştırması açılmış veriler üst bilgide listelenen sıkıştırılmamış dosya boyutuna kesilir.

Bu değişiklik, bir <xref:System.IO.Compression.ZipArchiveEntry> verilerin boyutunu doğru bir şekilde temsil ettiğinden ve yalnızca o miktarda veri okunduğunuzdan emin olmak için yapılmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu sorunları gösteren herhangi bir ZIP arşivini yeniden paketleyin.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
