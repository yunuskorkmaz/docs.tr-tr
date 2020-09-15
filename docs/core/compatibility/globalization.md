---
title: Genelleştirme son değişiklikleri
description: .NET Core 'da Genelleştirme 'deki son değişiklikleri listeler.
ms.date: 04/07/2020
ms.openlocfilehash: 93990d89204df1b2d7498e1d748378fae05598c3
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065077"
---
# <a name="globalization-breaking-changes"></a>Genelleştirme son değişiklikleri

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [Bazı Latin-1 karakterleri için Unicode kategorisi değişti](#unicode-category-changed-for-some-latin-1-characters) | 5.0 |
| [Genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır](#globalization-apis-use-icu-libraries-on-windows) | 5.0 |
| [StringInfo ve TextElementEnumerator artık UAX29 uyumlu](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | 5.0 |
| ["C" yerel ayarı, sabit yerel ayara eşlenir](#c-locale-maps-to-the-invariant-locale) | 3.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [unicode-categories-for-latin1-chars](../../../includes/core-changes/globalization/5.0/unicode-categories-for-latin1-chars.md)]

***

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
