---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568243"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry artık tutarsız giriş boyutları ile arşivleri işler

Zip arşivleri, hem sıkıştırılmış boyutu hem de sıkıştırılmamış boyutu merkez dizini ve yerel üstbilgide listeler.  Giriş verilerinin kendisi de boyutunu gösterir.  .NET Core 2.2 ve önceki sürümlerinde, bu değerler tutarlılık açısından hiçbir zaman denetlenmedi. .NET Core 3.0 ile başlayarak, şimdi vardır.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 2.2 ve <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> önceki sürümlerinde, yerel üstbilgi zip dosyasının merkezi üstbilgiyle aynı fikirde olmasa bile başarılı olur. Veri, uzunluğu merkezi dizinde/yerel üstbilgide listelenen sıkıştırılmamış dosya boyutunu aşsa bile, sıkıştırılmış akışın sonuna kadar sıkıştırılır.

.NET Core 3.0 ile <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> başlayarak, yöntem yerel üstbilgi ve merkezi üstbilginin bir girişin sıkıştırılmış ve sıkıştırılmamış boyutları üzerinde anlaştığını denetler.  Bunu yapmazlarsa, yöntem, arşivin yerel üstbilgi ve/veya zip dosyasının merkezi diziniyle aynı fikirde olmayan veri tanımlayıcı listesi boyutları varsa bir <xref:System.IO.InvalidDataException> hata yapar. Bir giriş okurken, sıkıştırılmış veriler üstbilgide listelenen sıkıştırılmamış dosya boyutuna kesilir.

Bu değişiklik, bir verinin <xref:System.IO.Compression.ZipArchiveEntry> boyutunu doğru bir şekilde temsil etmesini ve yalnızca bu miktarda verinin okunmasını sağlamak için yapılmıştır.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Bu sorunları sergileyen herhangi bir zip arşivini yeniden paketleyin.

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
