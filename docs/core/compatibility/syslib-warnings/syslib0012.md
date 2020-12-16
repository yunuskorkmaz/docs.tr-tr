---
title: SYSLIB0012 uyarısı
description: Derleme zamanı uyarı SYSLIB0012 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 9b3fa94029efb2343e6dbbeb3ae36195f0956523
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596553"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a>SYSLIB0012: Assembly. CodeBase ve Assembly. kaçış Edcodebase artık kullanılmıyor

Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Kod içinde kullanmak, `SYSLIB0012` derleme zamanında uyarı oluşturur.

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a>Geçici Çözümler

Bunun yerine <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> kullanın.

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]
