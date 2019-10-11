---
ms.openlocfilehash: f9ae32c44e5648eb74d7eab9fa5aa6cc2f17b9a1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237487"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>"C" yerel ayarı, sabit yerel ayara eşlenir

.NET Core 2,2 ve önceki sürümleri, "C" yerel ayarını en_US_POSIX yerel ayarıyla eşleyen varsayılan ıCU davranışına bağımlıdır. Büyük/küçük harfe duyarsız dize karşılaştırmaları desteklemediğinden en_US_POSIX yerel ayarının istenmeyen harmanlama davranışı vardır. Bazı Linux dağıtımları varsayılan yerel ayar olarak "C" yerel ayarını ayarlamadığı için, kullanıcılar beklenmeyen davranışlarla karşılaşıyor. 

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 ile başlayarak, "C" yerel ayar eşlemesi en_US_POSIX yerine sabit yerel ayarı kullanacak şekilde değiştirilmiştir. Sabit eşleme için "C" yerel ayarı Windows 'a tutarlılık için de uygulanır.

En_US_POSIX, büyük/küçük harfe duyarsız sıralama/arama dizesi işlemlerini desteklemediğinden, "C" öğesini en_US_POSIX kültürüne eşleme, müşteri karmaşıklığına neden oldu. "C" yerel ayarı bazı Linux dışı bir yerel ayar olarak kullanıldığından, müşteriler bu işletim sistemlerinde bu istenmeyen davranışla karşılaşmıştır. 

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

### <a name="recommended-action"></a>Önerilen eylem

Bu değişikliğin farkından daha fazla hiçbir şey yok. Bu değişiklik yalnızca "C" yerel ayar eşlemesini kullanan uygulamaları etkiler.

### <a name="category"></a>Kategori

Genelleştirme 

### <a name="affected-apis"></a>Etkilenen API’ler

Tüm harmanlama ve kültür API 'Leri bu değişiklikten etkilenir.

<!--

-->
