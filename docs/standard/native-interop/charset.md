---
title: Charsets ve Marshal-.NET
description: Farklı karakter kümesi, .NET 'in verilerinizi yerel koda nasıl bir şekilde kullandığını nasıl değiştirebileceğinizi öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 301fa3d8bd379e76a0e751c3a20d0d8be37d9ac0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700918"
---
# <a name="charsets-and-marshaling"></a>Karakter kümesi ve hazırlama

@No__t-0 değerlerinin, `string` nesnelerinin ve `System.Text.StringBuilder` nesnelerinin sıralanma biçimi, P/Invoke ya da yapısındaki `CharSet` alanının değerine bağlıdır. P/Invoke 'nizi bildirirken <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alanını ayarlayarak P/Invoke 'ın `CharSet` ' yı ayarlayabilirsiniz. Bir tür için `CharSet` ' ı ayarlamak için, sınıfınıza veya yapı bildirimindeki <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> alanını ayarlayın. Bu öznitelik alanları ayarlanmamışsa, hangi `CharSet` ' ı kullanacağını belirleyen dil derleyicisi vardır. C#ve VB, varsayılan olarak <xref:System.Runtime.InteropServices.CharSet.Ansi> karakter kümesini kullanır.

Aşağıdaki tabloda, her karakter kümesi ile bir karakter veya dizenin bu karakter kümesi ile sıralandığınızda nasıl temsil edildiği gösterilmektedir:

| `CharSet` değeri | Windows            | UNIX üzerinde .NET Core 2,2 ve önceki sürümleri | .NET Core 3,0 ve üzeri ve mono on Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (sistem varsayılan [Windows (ANSI) kod sayfası](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Otomatik            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Yerel gösteriminizi, karakter kümesini seçerken beklediği gösterimi öğrendiğinizden emin olun.
