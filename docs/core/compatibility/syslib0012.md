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
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="a2f59-103">SYSLIB0012: Assembly. CodeBase ve Assembly. kaçış Edcodebase artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="a2f59-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="a2f59-104">Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="a2f59-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="a2f59-105">Kod içinde kullanmak, `SYSLIB0012` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2f59-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="a2f59-106">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="a2f59-106">Workarounds</span></span>

<span data-ttu-id="a2f59-107">Bunun yerine <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2f59-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]
