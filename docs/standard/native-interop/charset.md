---
title: Charsets ve Marshal-.NET
description: Farklı karakter kümesi, .NET 'in verilerinizi yerel koda nasıl bir şekilde kullandığını nasıl değiştirebileceğinizi öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 4be4bd5a968eb5c0d6959a0f378ee1223ed906ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706393"
---
# <a name="charsets-and-marshaling"></a>Karakter kümesi ve hazırlama

`char` değerleri, `string` nesneleri ve `System.Text.StringBuilder` nesnelerinin sıralanma biçimi, P/Invoke ya da yapısındaki `CharSet` alanının değerine bağlıdır. P/Invoke 'nizi bildirirken <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alanını ayarlayarak P/Invoke `CharSet` ayarlayabilirsiniz. Bir tür için `CharSet` ayarlamak için, sınıfınıza veya yapı bildirimindeki <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> alanını ayarlayın. Bu öznitelik alanları ayarlanmamışsa, hangi `CharSet` kullanacağınızı belirleyen dil derleyicisine kadar olur. C#Visual Basic <xref:System.Runtime.InteropServices.CharSet.Ansi> karakter kümesini varsayılan olarak kullanın.

Aşağıdaki tabloda, her karakter kümesi ile bir karakter veya dizenin bu karakter kümesi ile sıralandığınızda nasıl temsil edildiği gösterilmektedir:

| `CharSet` değeri | Windows            | UNIX üzerinde .NET Core 2,2 ve önceki sürümleri | .NET Core 3,0 ve üzeri ve mono on Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (sistem varsayılan [Windows (ANSI) kod sayfası](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Otomatik            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Yerel gösteriminizi, karakter kümesini seçerken beklediği gösterimi öğrendiğinizden emin olun.
