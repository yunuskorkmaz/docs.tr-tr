---
ms.openlocfilehash: 74c3d3247912dcd638a9379d54e682967c5e400b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302729"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a>Genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır

.NET 5,0 ve sonraki sürümleri, Windows 10 Mayıs 2019 güncelleştirme veya sonrasında çalışırken Genelleştirme işlevselliği için [Unicode (ıCU)](http://site.icu-project.org/home) kitaplıklarını kullanır.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce .NET kitaplıkları, Genelleştirme işlevselliği için [ulusal dil desteği (NLS)](/windows/win32/intl/national-language-support) API 'lerini kullandı. Örneğin, NLS işlevleri, tarih ve saat biçimi desenleri gibi kültür verilerini almak, dizeleri karşılaştırmak ve uygun kültür içinde dize büyük harfleri gerçekleştirmek için kullanılmıştır.

.NET 5,0 ' den itibaren, bir uygulama Windows 10 Mayıs 2019 veya sonraki sürümlerde çalışıyorsa, .NET kitaplıkları [ICU](http://site.icu-project.org/home) genelleştirme API 'lerini kullanır. Windows 10 Mayıs 2019 güncelleştirmesi ve sonraki sürümleri ıCU yerel kitaplığıyla birlikte sevk. .NET çalışma zamanı ıCU 'yi yükleye, bunun yerine NLS kullanır.

Bu değişiklik iki nedenden dolayı sunulmuştur:

- Uygulamalar Linux, macOS ve Windows dahil olmak üzere platformlar genelinde aynı Genelleştirme davranışına sahiptir.
- Uygulamalar, özel ıCU kitaplıklarını kullanarak Genelleştirme davranışını denetleyebilir.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0 Preview 4

#### <a name="recommended-action"></a>Önerilen eylem

Geliştiricinin bölümünde herhangi bir eylem gerekmez. Ancak, NLS genelleştirme API 'Lerini kullanmaya devam etmek istiyorsanız, bu davranışa dönmek için bir [çalışma zamanı anahtarı](../../../../docs/core/run-time-config/globalization.md#nls) ayarlayabilirsiniz. Kullanılabilir anahtarlar hakkında daha fazla bilgi için bkz. [.NET Genelleştirme ve ıCU](/dotnet/standard/globalization-localization/globalization-icu) makalesi.

#### <a name="category"></a>Kategori

Genelleştirme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- Ad alanındaki çoğu tür <xref:System.Globalization?displayProperty=fullName>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
