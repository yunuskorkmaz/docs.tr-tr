---
title: Birlikte çalışma son değişiklikleri
description: .NET Core ve .NET 5,0 ve üzeri sürümlerde birlikte çalışma içindeki son değişiklikleri listeler.
ms.date: 06/23/2020
ms.openlocfilehash: a38fb1837e565be33f8ae1119480c8f1ae848ab0
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438054"
---
# <a name="interop-breaking-changes"></a><span data-ttu-id="a32de-103">Birlikte çalışma son değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a32de-103">Interop breaking changes</span></span>

<span data-ttu-id="a32de-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="a32de-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="a32de-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="a32de-105">Breaking change</span></span> | <span data-ttu-id="a32de-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a32de-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="a32de-107">Bir arabirime RCW atama `InterfaceIsIInspectable` PlatformNotSupportedException oluşturur</span><span class="sxs-lookup"><span data-stu-id="a32de-107">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | <span data-ttu-id="a32de-108">5.0</span><span class="sxs-lookup"><span data-stu-id="a32de-108">5.0</span></span> |
| [<span data-ttu-id="a32de-109">Windows dışı platformlarda bir/W soneki yoklama yok</span><span class="sxs-lookup"><span data-stu-id="a32de-109">No A/W suffix probing on non-Windows platforms</span></span>](#no-aw-suffix-probing-on-non-windows-platforms) | <span data-ttu-id="a32de-110">5.0</span><span class="sxs-lookup"><span data-stu-id="a32de-110">5.0</span></span> |
| [<span data-ttu-id="a32de-111">WinRT için yerleşik destek .NET 'ten kaldırılmıştır</span><span class="sxs-lookup"><span data-stu-id="a32de-111">Built-in support for WinRT is removed from .NET</span></span>](#built-in-support-for-winrt-is-removed-from-net) | <span data-ttu-id="a32de-112">5.0</span><span class="sxs-lookup"><span data-stu-id="a32de-112">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="a32de-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="a32de-113">.NET 5.0</span></span>

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
