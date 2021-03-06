---
title: 'Son değişiklik: CA2013: ReferenceEquals değerini değer türleriyle kullanma'
description: Kod Analizi kuralı CA2013 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: fc68d9a3af0d629dc39aba0091d32b1982d6f2c5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257773"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a>Uyarı CA2013: ReferenceEquals değerini değer türleriyle kullanmayın

.Net Code Analyzer Rule [CA2013](/visualstudio/code-quality/ca2013) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. <xref:System.Object.ReferenceEquals(System.Object,System.Object)>Bir veya daha fazla değer türünü eşitlik için karşılaştırmak üzere kullanılan herhangi bir kod için derleme uyarısı üretir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA2013](/visualstudio/code-quality/ca2013)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

Rule CA2013 <xref:System.Object.ReferenceEquals(System.Object,System.Object)> , eşitlik için bir veya daha fazla değer türünü karşılaştırmak için kullanılan örnekleri bulur. Bu şekilde eşitlik için değer türlerini karşılaştırma, değerler karşılaştırılmadan önce paketlendikleri için yanlış sonuçlara yol açabilir. <xref:System.Object.ReferenceEquals(System.Object,System.Object)>`false`karşılaştırılan değerler bir değer türünün aynı örneğini temsil ediyorsa bile döndürülür.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

- Kodu, gibi uygun bir eşitlik işleci kullanacak şekilde değiştirin `==` . Bu uyarıyı gizmemelisiniz.

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->
