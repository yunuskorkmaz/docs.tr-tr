---
title: SYSLIB0012 uyarısı
description: Derleme zamanı uyarı SYSLIB0012 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dc139d5c5cb6d6a34d161147b350b3324d15117e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440588"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a>SYSLIB0012: Assembly. CodeBase ve Assembly. kaçış Edcodebase artık kullanılmıyor

Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Kod içinde kullanmak, `SYSLIB0012` derleme zamanında uyarı oluşturur.

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a>Geçici Çözümler

Bunun yerine <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> kullanın.

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]
