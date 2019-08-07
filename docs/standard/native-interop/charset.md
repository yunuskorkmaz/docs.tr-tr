---
title: Charsets ve Marshal-.NET
description: Farklı karakter kümesi, .NET 'in verilerinizi yerel koda nasıl bir şekilde kullandığını nasıl değiştirebileceğinizi öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: cac71c5d09514dfe1244d16224944e05826edfa9
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817846"
---
# <a name="charsets-and-marshaling"></a>Karakter kümesi ve hazırlama

Değerlerin, `char` `string` nesnelerin `CharSet` ve `System.Text.StringBuilder` nesnelerin nasıl sıralandığına göre, P/Invoke veya Structure üzerindeki alanın değerine göre değişir. P/Invoke 'nizi `CharSet` bildirirken <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alanı ayarlayarak p/Invoke kümesini ayarlayabilirsiniz. Bir yapıyı ayarlamak `CharSet` için yapı bildirimindeki <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> alanı ayarlayın. Bu öznitelik alanları ayarlanmamışsa, hangisinin `CharSet` kullanılacağını belirleyen dil derleyicisi vardır. C#ve vb varsayılan olarak <xref:System.Runtime.InteropServices.CharSet.Ansi> karakter kümesini kullanır.

Aşağıdaki tabloda, her karakter kümesi ile bir karakter veya dizenin bu karakter kümesi ile sıralandığınızda nasıl temsil edildiği gösterilmektedir:

| `CharSet`deeri | Windows            | UNIX üzerinde .NET Core 2,2 ve önceki sürümleri | .NET Core 3,0 ve üzeri ve mono on Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char`(sistem varsayılan [Windows (ANSI) kod sayfası](/windows/win32/intl/code-pages))      | `char`(UTF-8)                    | `char`(UTF-8)                           |
| Unicode         | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char16_t`(UTF-16)                      |
| Otomatik            | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char`(UTF-8)                           |

Yerel gösteriminizi, karakter kümesini seçerken beklediği gösterimi öğrendiğinizden emin olun.
