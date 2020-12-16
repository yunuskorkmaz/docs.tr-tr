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
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="0f37b-103">SYSLIB0012: Assembly. CodeBase ve Assembly. kaçış Edcodebase artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="0f37b-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="0f37b-104">Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="0f37b-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="0f37b-105">Kod içinde kullanmak, `SYSLIB0012` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f37b-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="0f37b-106">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="0f37b-106">Workarounds</span></span>

<span data-ttu-id="0f37b-107">Bunun yerine <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f37b-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]
