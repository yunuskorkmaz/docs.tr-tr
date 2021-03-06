---
title: "Son değişiklik: CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama<T>"
description: Kod Analizi kuralı CA2015 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: 4333cec7657657f7e9ba864bcb9979609ad379e0
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257745"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a>Uyarı CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama\<T>

.Net Code Analyzer Rule [CA2015](/visualstudio/code-quality/ca2015) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. Sonlandırıcıyı tanımlayan herhangi bir tür için derleme uyarısı oluşturur <xref:System.Buffers.MemoryManager%601> .

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA2015](/visualstudio/code-quality/ca2015)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

Bir Sonlandırıcı tanımlatan türetilen kural CA2015 Flags türleri <xref:System.Buffers.MemoryManager%601> . ' Dan türetilen bir türe Sonlandırıcı eklemek <xref:System.Buffers.MemoryManager%601> , büyük olasılıkla bir hatanın göstergesidir. Bir içinde elde edilen yerel bir kaynağın <xref:System.Span%601> temizlenmesinin yanı da hala tarafından kullanılıyor olması önerilir <xref:System.Span%601> .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

- Sonlandırıcı tanımını kaldırın. Daha fazla bilgi için bkz. [CA2015](/visualstudio/code-quality/ca2015).

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
