---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567775"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Değişmez yerel ekiyle "C" yerel eşlemleri

.NET Core 2.2 ve önceki sürümler, "C" yerelsini en_US_POSIX yerel le eşleyen varsayılan Yoğun Bakım Davranışı'na bağlıdır. Büyük/küçük harf duyarsız dize karşılaştırmalarını desteklemediği için en_US_POSIX yerel alanı istenmeyen bir harmanlama davranışına sahiptir. Bazı Linux dağıtımları "C" yerel ayarını varsayılan yerel ayar olarak ayarladıklarından, kullanıcılar beklenmeyen davranışlar yaşıyordu.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 ile başlayarak, "C" yerel eşleme en_US_POSIX yerine Değişmez yerel eşlemi kullanmak üzere değiştirildi. Değişmez eşleme için "C" yerel eşleme tutarlılık için Windows'a da uygulanır.

"C"yi en_US_POSIX kültüre eşleme, en_US_POSIX hızlı servis talebi duyarsız sıralama/arama dize işlemlerini desteklemediği için müşteri karışıklığına neden oldu. "C" yerel alanı, Linux dağıtımlarının bazılarında varsayılan bir yerel alan olarak kullanıldığından, müşteriler bu işletim sistemlerinde bu istenmeyen davranışı yaşadılar.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

### <a name="recommended-action"></a>Önerilen eylem

Bu değişikliğin farkındalığından daha özel bir şey yok. Bu değişiklik yalnızca "C" yerel eşleme eşlemesi kullanan uygulamaları etkiler.

### <a name="category"></a>Kategori

Genelleştirme

### <a name="affected-apis"></a>Etkilenen API’ler

Tüm harmanlama ve kültür API'leri bu değişiklikden etkilenir.

<!--

-->
