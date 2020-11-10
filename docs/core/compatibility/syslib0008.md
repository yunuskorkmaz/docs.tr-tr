---
title: SYSLIB0008 uyarısı
description: Derleme zamanı uyarı SYSLIB0008 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 22ac5b4c5f57ec3f92585ee8d1f8cf278a15dbb0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440601"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a><span data-ttu-id="4fe39-103">SYSLIB0008: CreatePdbGenerator desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="4fe39-103">SYSLIB0008: CreatePdbGenerator is not supported</span></span>

<span data-ttu-id="4fe39-104"><xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>API, .net 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="4fe39-104">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API is marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="4fe39-105">Bu API 'nin kullanılması, `SYSLIB0008` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4fe39-105">Using this API generates warning `SYSLIB0008` at compile time.</span></span>

## <a name="suppress-the-warning"></a><span data-ttu-id="4fe39-106">Uyarıyı gösterme</span><span class="sxs-lookup"><span data-stu-id="4fe39-106">Suppress the warning</span></span>

<span data-ttu-id="4fe39-107">Kodunuzu değiştirememek için, bir `#pragma` yönerge veya proje ayarı aracılığıyla uyarıyı gizleyebilirsiniz `<NoWarn>` .</span><span class="sxs-lookup"><span data-stu-id="4fe39-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="4fe39-108">Örnekler için bkz. [uyarıları gösterme](syslib-obsoletions.md#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="4fe39-108">For examples, see [Suppress warnings](syslib-obsoletions.md#suppress-warnings).</span></span>
