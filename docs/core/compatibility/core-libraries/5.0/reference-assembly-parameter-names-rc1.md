---
title: "Son değişiklik: RC2 'de parametre adları değişti"
description: Bazı başvuru derleme parametresi adlarının, .NET 5,0 ' nin önizleme ve sürüm adayı sürümlerinden değiştiği çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 554a4fa9e08fdb504f380465496d7e7e9df85814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761502"
---
# <a name="parameter-names-changed-in-rc2"></a>RC2 'de parametre adları değiştirildi

Bazı başvuru derleme parametresi adları, uygulama derlemelerindeki parametre adlarıyla eşleşecek şekilde değiştirilmiştir.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET 5,0 Önizleme ve RC sürümlerinde, bazı [Başvuru derleme](../../../../standard/assembly/reference-assemblies.md) parametresi adları, uygulama derlemesinde karşılık gelen parametrelere farklıdır. Bu, adlandırılmış bağımsız değişkenler ve yansıma kullanılırken soruna neden olabilir.

.NET 5,0 RC2 'de, bu eşleşmeyen parametre adları, başvuru derlemelerinde, uygulama derlemelerindeki karşılık gelen parametre adlarıyla tam olarak eşleşecek şekilde güncelleştirildi.

Aşağıdaki tabloda, değiştirilen API 'Ler ve parametre adları gösterilmektedir.

| API | Eski parametre adı | Yeni parametre adı |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

## <a name="reason-for-change"></a>Değişiklik nedeni

Parametre adları tutarlılık için değiştirilmiştir ve adlandırılmış bağımsız değişkenler ve yansıma kullanılırken hatalardan kaçınmak için.

## <a name="version-introduced"></a>Sunulan sürüm

5,0 RC2

## <a name="recommended-action"></a>Önerilen eylem

Bir parametre adı değişikliği nedeniyle bir derleyici hatasıyla karşılaşırsanız parametre adını uygun şekilde güncelleştirin.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
