---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135638"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a>Bozuk durum özel durumlarını işleme desteklenmiyor

.NET Core 'da bozuk işlem durumu özel durumlarını işleme desteklenmiyor.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, bozuk işlem durumu özel durumları, örneğin, C# ' de bir [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) ifadesiyle kullanılarak, yönetilen kod özel durum işleyicileri tarafından yakalanıp Işlenebiliyor.

.NET Core 1,0 ' den başlayarak, bozuk işlem durumu özel durumları yönetilen kod tarafından işlenemiyor. Ortak dil çalışma zamanı, yönetilen koda bozuk işlem durumu özel durumları teslim etmez.

#### <a name="version-introduced"></a>Sunulan sürüm

1.0

#### <a name="recommended-action"></a>Önerilen eylem

Bunun yerine, bunlara neden olan durumları ele alarak bozuk işlem durumu özel durumlarını işleme gereksinimini önleyin. Bozuk işlem durumu özel durumlarını işlemek kesinlikle gerekliyse, özel durum işleyicisini C veya C++ koduna yazın.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [Legacyboztedstateexceptionspolicy öğesi](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
