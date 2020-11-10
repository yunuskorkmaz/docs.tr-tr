---
title: SYSLIB0009 uyarısı
description: Derleme zamanı uyarı SYSLIB0009 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 47b4f595a54800370da90f61d838c665df8b6091
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439982"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a><span data-ttu-id="132c4-103">SYSLIB0009: AuthenticationManager kimlik doğrulama ve ön kimlik doğrulama yöntemlerinin desteklenmediği</span><span class="sxs-lookup"><span data-stu-id="132c4-103">SYSLIB0009: The AuthenticationManager Authenticate and PreAuthenticate methods are not supported</span></span>

<span data-ttu-id="132c4-104">Aşağıdaki API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="132c4-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="132c4-105">Bu API 'lerin kullanımı, `SYSLIB0009` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="132c4-105">Use of these APIs generates warning `SYSLIB0009` at compile time.</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a><span data-ttu-id="132c4-106">Uyarıyı gösterme</span><span class="sxs-lookup"><span data-stu-id="132c4-106">Suppress the warning</span></span>

<span data-ttu-id="132c4-107">Kodunuzu değiştirememek için, bir `#pragma` yönerge veya proje ayarı aracılığıyla uyarıyı gizleyebilirsiniz `<NoWarn>` .</span><span class="sxs-lookup"><span data-stu-id="132c4-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="132c4-108">Örnekler için bkz. [uyarıları gösterme](syslib-obsoletions.md#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="132c4-108">For examples, see [Suppress warnings](syslib-obsoletions.md#suppress-warnings).</span></span>
