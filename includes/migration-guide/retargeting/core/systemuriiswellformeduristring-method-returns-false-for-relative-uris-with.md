---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617280"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>System. Uri. ıwellformeduristring yöntemi, ilk kesimde iki nokta üst üste karakteri olan göreli URI 'Ler için false döndürür

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' den başlayarak, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> göreli URI 'leri `:` ilk segmentlerinde ile, doğru biçimlendirilmemiş olarak değerlendirir. Bu, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> RFC3986 ile uyumlu hale getirilme .NET Framework 4,0 ' deki davranış değişikdir.

#### <a name="suggestion"></a>Öneri

Bu değişiklik (diğer birçok URI değişikliği gibi) yalnızca .NET Framework 4,5 (veya üzeri) hedefleyen uygulamaları etkiler. Eski davranışı kullanmaya devam etmek için uygulamayı 4,0 .NET Framework karşı hedefleyin. Alternatif olarak, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> `:` eski davranışı tercih ediyorsanız, doğrulama amacıyla kaldırmak isteyebileceğiniz karakterleri arayarak, URI 'yi tarayın.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
