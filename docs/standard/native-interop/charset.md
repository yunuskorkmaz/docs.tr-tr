---
title: Charsets ve Marshal-.NET
description: Farklı karakter kümesi, .NET 'in verilerinizi yerel koda nasıl bir şekilde kullandığını nasıl değiştirebileceğinizi öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 39566593aa38bacfa41b44a8af8cc2dfb294d766
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416115"
---
# <a name="charsets-and-marshaling"></a>Karakter kümesi ve hazırlama

`char`Değerlerin, `string` nesnelerin ve `System.Text.StringBuilder` nesnelerin nasıl sıralandığına göre, `CharSet` P/Invoke veya Structure üzerindeki alanın değerine göre değişir. P/Invoke `CharSet` 'nizi bildirirken alanı ayarlayarak p/Invoke kümesini ayarlayabilirsiniz <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> . `CharSet`Bir tür için ayarlamak için <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> sınıfınıza veya yapı bildirimindeki alanı ayarlayın. Bu öznitelik alanları ayarlanmamışsa, hangisinin kullanılacağını belirleyen dil derleyicisi vardır `CharSet` . C# ve Visual Basic <xref:System.Runtime.InteropServices.CharSet.Ansi> Varsayılan olarak karakter kümesini kullanır.

Aşağıdaki tabloda, her karakter kümesi ile bir karakter veya dizenin bu karakter kümesi ile sıralandığınızda nasıl temsil edildiği gösterilmektedir:

| `CharSet`deeri | Windows            | UNIX üzerinde .NET Core 2,2 ve önceki sürümleri | .NET Core 3,0 ve üzeri ve mono on Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| `Ansi`          | `char`(sistem varsayılan [Windows (ANSI) kod sayfası](/windows/win32/intl/code-pages))      | `char`(UTF-8)                    | `char`(UTF-8)                           |
| `Unicode`       | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char16_t`(UTF-16)                      |
| `Auto`          | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char`(UTF-8)                           |

Yerel gösteriminizi, karakter kümesini seçerken beklediği gösterimi öğrendiğinizden emin olun.
