---
title: Charsets ve düzenleme - .NET
description: Farklı değerleri öğrenin CharSet .NET yerel kodu verilerinize nasıl sürekliliğe devreder değiştirebilirsiniz.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2ff6c485906db481cb5236f83e885ba9fd46450b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416235"
---
# <a name="charsets-and-marshalling"></a>Charsets ve taşıma

Yol `char` değerleri `string` nesneleri ve `System.Text.StringBuilder` nesnelerin sıraya değerine bağlıdır `CharSet` P/Invoke ya da yapı üzerinde alan. Ayarlayabileceğiniz `CharSet` ayarlayarak P/Invoke'nın <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> P/Invoke bildirirken alan. Ayarlanacak `CharSet` bir yapısı için <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> , struct bildiriminde alan. Bu öznitelik alanları ayarlı değil, belirlemek için dil derleyicisi kadar olur `CharSet` kullanılacak. C#kullanan <xref:System.Runtime.InteropServices.CharSet.Ansi> varsayılan karakter kümesi.

Aşağıdaki tablo her bir karakter kümesi arasındaki eşlemeyi gösterir ve bir karakter veya dize ile bu charset sıraya olduğunda nasıl gösterilir:

| CharSet | Windows | UNIX | Mono UNIX üzerinde |
|---------|---------|-------|-------|
| Ansi    | `char` (ANSI)  | `char` (ANSI MacOS, Linux üzerinde UTF-8) | `char` (UTF-8) |
| Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char16_t` (UTF-16) |
| Otomatik | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char` (UTF-8) |

Hangi gösterimi, charset alınırken, yerel gösterimine bekliyor bildiğinizden emin olun.
