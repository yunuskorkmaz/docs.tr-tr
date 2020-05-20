---
ms.openlocfilehash: c0551fa086644497c631cd9b6d7058398ff9ccfa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702320"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>"C" yerel ayarı, sabit yerel ayara eşlenir

.NET Core 2,2 ve önceki sürümleri, "C" yerel ayarını en_US_POSIX yerel ayarıyla eşleyen varsayılan ıCU davranışına bağımlıdır. Büyük/küçük harfe duyarsız dize karşılaştırmaları desteklemediğinden en_US_POSIX yerel ayarı istenmeyen harmanlama davranışına sahiptir. Bazı Linux dağıtımları varsayılan yerel ayar olarak "C" yerel ayarını ayarlamadığı için, kullanıcılar beklenmeyen davranışlarla karşılaşıyor.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 ile başlayarak, "C" yerel ayar eşlemesi en_US_POSIX yerine sabit yerel ayarı kullanacak şekilde değiştirilmiştir. Sabit eşleme için "C" yerel ayarı Windows 'a tutarlılık için de uygulanır.

"C" öğesini en_US_POSIX kültür ile eşleme, müşteri karışıklığına neden oldu, çünkü en_US_POSIX büyük/küçük harfe duyarsız sıralama/arama dizesi işlemlerini desteklemez "C" yerel ayarı bazı Linux dışı bir yerel ayar olarak kullanıldığından, müşteriler bu işletim sistemlerinde bu istenmeyen davranışla karşılaşmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişikliğin farkından daha fazla hiçbir şey yok. Bu değişiklik yalnızca "C" yerel ayar eşlemesini kullanan uygulamaları etkiler.

#### <a name="category"></a>Kategori

Genelleştirme

#### <a name="affected-apis"></a>Etkilenen API’ler

Tüm harmanlama ve kültür API 'Leri bu değişiklikten etkilenir.

<!--

#### Affected APIs

-->
