---
ms.openlocfilehash: 49041ce906ab0bb8b9482b79c44302465c4ca788
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702266"
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

Geliştiricinin bölümünde herhangi bir eylem gerekmez. Ancak, NLS genelleştirme API 'Lerini kullanmaya devam etmek istiyorsanız, bu davranışa dönmek için bir [çalışma zamanı anahtarı](../../../../docs/core/run-time-config/globalization.md#nls) ayarlayabilirsiniz.

#### <a name="category"></a>Kategori

Genelleştirme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- Ad alanındaki çoğu tür <xref:System.Globalization?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Span%601`
- `T:System.String`
- `N:System.Globalization`

-->
