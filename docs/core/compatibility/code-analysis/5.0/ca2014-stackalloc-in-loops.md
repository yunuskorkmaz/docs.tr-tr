---
title: 'Son değişiklik: CA2014: Döngülerde stackalloc kullanmayın'
description: Kod Analizi kuralı CA2014 'nin etkinleştirilmesi nedeniyle .NET 5,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: 7ad6203c0edd930bbbe43cdb8df0413cba833d8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761326"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a>Uyarı CA2014: Döngülerde stackalloc kullanmayın

.Net Code Analyzer Rule [CA2014](/visualstudio/code-quality/ca2014) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. Bir döngü içinde [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) ifadesinin kullanıldığı herhangi bir C# kodu için derleme uyarısı oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA2014](/visualstudio/code-quality/ca2014)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

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
