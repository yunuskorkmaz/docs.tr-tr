---
title: Charsets ve düzenleme - .NET
description: Farklı değerleri öğrenin CharSet .NET yerel kodu verilerinize nasıl sürekliliğe devreder değiştirebilirsiniz.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 0b9ea8498b56e6d14770cf57e7e82b9992b1ee50
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299884"
---
# <a name="charsets-and-marshalling"></a>Charsets ve taşıma

Yol `char` değerleri `string` nesneleri ve `System.Text.StringBuilder` nesnelerin sıraya değerine bağlıdır `CharSet` P/Invoke ya da yapı üzerinde alan. Ayarlayabileceğiniz `CharSet` ayarlayarak P/Invoke'nın <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> P/Invoke bildirirken alan. Ayarlanacak `CharSet` bir yapısı için <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> , struct bildiriminde alan. Bu öznitelik alanları ayarlı değil, belirlemek için dil derleyicisi kadar olur `CharSet` kullanılacak. C#ve VB <xref:System.Runtime.InteropServices.CharSet.Ansi> varsayılan karakter kümesi.

Aşağıdaki tablo her bir karakter kümesi arasındaki eşlemeyi gösterir ve bir karakter veya dize ile bu charset sıraya olduğunda nasıl gösterilir:

| CharSet | Windows            | UNIX                                   | Mono UNIX üzerinde        |
|---------|--------------------|----------------------------------------|---------------------|
| Ansi    | `char` (ANSI)      | `char` (ANSI MacOS, Linux üzerinde UTF-8) | `char` (UTF-8)      |
| Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16)                    | `char16_t` (UTF-16) |
| Otomatik    | `wchar_t` (UTF-16) | `char16_t` (UTF-16)                    | `char` (UTF-8)      |

Hangi gösterimi, charset alınırken, yerel gösterimine bekliyor bildiğinizden emin olun.
