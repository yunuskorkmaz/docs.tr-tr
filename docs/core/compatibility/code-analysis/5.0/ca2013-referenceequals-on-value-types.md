---
title: 'Son değişiklik: CA2013: ReferenceEquals değerini değer türleriyle kullanma'
description: Kod Analizi kuralı CA2013 'nin etkinleştirilmesi nedeniyle .NET 5,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: ca2b845427eff547b996b577394c6859e30f50bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761329"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a>Uyarı CA2013: ReferenceEquals değerini değer türleriyle kullanmayın

.Net Code Analyzer Rule [CA2013](/visualstudio/code-quality/ca2013) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. <xref:System.Object.ReferenceEquals(System.Object,System.Object)>Bir veya daha fazla değer türünü eşitlik için karşılaştırmak üzere kullanılan herhangi bir kod için derleme uyarısı üretir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA2013](/visualstudio/code-quality/ca2013)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

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
