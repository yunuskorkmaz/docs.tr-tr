---
title: 'Son değişiklik: CA2014: Döngülerde stackalloc kullanmayın'
description: Kod Analizi kuralı CA2014 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: ac17c8ee588576947e21618a55c0eea883aa37ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257784"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a>Uyarı CA2014: Döngülerde stackalloc kullanmayın

.Net Code Analyzer Rule [CA2014](/visualstudio/code-quality/ca2014) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. Bir döngü içinde [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) ifadesinin kullanıldığı herhangi bir C# kodu için derleme uyarısı oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA2014](/visualstudio/code-quality/ca2014)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

Rule CA2014, bir [stackalloc ifadesinin](../../../../csharp/language-reference/operators/stackalloc.md) bir döngü Içinde kullanıldığı C# kodunu arar. [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) , geçerli yığın çerçevesindeki belleği ayırır. Geçerli yöntem çağrısı döndürülünceye kadar bellek serbest bırakılana kadar, yığın taşlarına yol açabilir. Yığın taşması özel durumlarını yakalayamayacak, yığın taşması durumunda uygulama sonlandırılacak.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

- Döngüler içinde [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) kullanmaktan kaçının. Bellek bloğunu döngü dışında ayırın ve döngü içinde yeniden kullanın. Daha fazla bilgi için bkz. [CA2014](/visualstudio/code-quality/ca2014).

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
