---
title: SYSLIB0012 uyarısı
description: Derleme zamanı uyarı SYSLIB0012 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2ed93b6eefbaa861faca319f0cc9bf19ac741f3b
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333326"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a>SYSLIB0012: Assembly. CodeBase ve Assembly. kaçış Edcodebase artık kullanılmıyor

Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Kod içinde kullanmak, `SYSLIB0012` derleme zamanında uyarı oluşturur.

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

Geçici çözüm

Bunun yerine <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> kullanın.
