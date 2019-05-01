---
title: Charsets ve düzenleme - .NET
description: Farklı değerleri öğrenin CharSet .NET yerel kodu verilerinize nasıl sürekliliğe devreder değiştirebilirsiniz.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: f436bbbf435df07d242f9bf295b0264c4cfd5b3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973582"
---
# <a name="charsets-and-marshalling"></a>Charsets ve taşıma

Yol `char` değerleri `string` nesneleri ve `System.Text.StringBuilder` nesnelerin sıraya değerine bağlıdır `CharSet` P/Invoke ya da yapı üzerinde alan. Ayarlayabileceğiniz `CharSet` ayarlayarak P/Invoke'nın <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> P/Invoke bildirirken alan. Ayarlanacak `CharSet` bir yapısı için <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> , struct bildiriminde alan. Bu öznitelik alanları ayarlı değil, belirlemek için dil derleyicisi kadar olur `CharSet` kullanılacak. C#ve VB <xref:System.Runtime.InteropServices.CharSet.Ansi> varsayılan karakter kümesi.

Aşağıdaki tablo her bir karakter kümesi arasındaki eşlemeyi gösterir ve bir karakter veya dize ile bu charset sıraya olduğunda nasıl gösterilir:

| CharSet | Windows            | .NET Core 2.2 ve daha önce UNIX | Mono ve .NET Core 3.0 ve sonraki sürümlerde UNIX |
|---------|--------------------|-----------------------------|------------------------------------------|
| Ansi    | `char` (ANSI)      | `char` (UTF-8)              | `char` (UTF-8)                           |
| Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16)         | `char16_t` (UTF-16)                      |
| Otomatik    | `wchar_t` (UTF-16) | `char16_t` (UTF-16)         | `char` (UTF-8)                           |

Hangi gösterimi, charset alınırken, yerel gösterimine bekliyor bildiğinizden emin olun.
