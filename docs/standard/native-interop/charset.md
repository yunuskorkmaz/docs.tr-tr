---
title: Charsets ve sıralama - .NET
description: Farklı değerleri öğrenin CharSet .NET yerel kodu verilerinize nasıl sürekliliğe devreder değiştirebilirsiniz.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: c50c58ad639b1efb29c13e5124fe3c32e8af96fc
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063333"
---
# <a name="charsets-and-marshaling"></a>Charsets ve hazırlama

Yol `char` değerleri `string` nesneleri ve `System.Text.StringBuilder` nesneleri sıralanmış değerine bağlıdır `CharSet` P/Invoke ya da yapı üzerinde alan. Ayarlayabileceğiniz `CharSet` ayarlayarak P/Invoke'nın <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> P/Invoke bildirirken alan. Ayarlanacak `CharSet` bir yapısı için <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> , struct bildiriminde alan. Bu öznitelik alanları ayarlı değil, belirlemek için dil derleyicisi kadar olur `CharSet` kullanılacak. C#ve VB <xref:System.Runtime.InteropServices.CharSet.Ansi> varsayılan karakter kümesi.

Aşağıdaki tablo her bir karakter kümesi arasındaki eşlemeyi gösterir ve bir karakter veya dize ile bu charset sıralandığı zaman nasıl gösterilir:

| `CharSet` Değer | Windows            | .NET core 2.2 ve daha önce on UNIX | .NET core 3.0 ve sonraki ve UNIX üzerinde Mono |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (ANSI)      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Otomatik            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Hangi gösterimi, charset alınırken, yerel gösterimine bekliyor bildiğinizden emin olun.
