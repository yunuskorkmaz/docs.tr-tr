---
title: Genelleştirme son değişiklikleri
description: .NET Core 'da Genelleştirme 'deki son değişiklikleri listeler.
ms.date: 04/07/2020
ms.openlocfilehash: 0c3367cb3515c6f473f53be6062b54f2e836b8c5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702318"
---
# <a name="globalization-breaking-changes"></a><span data-ttu-id="3fde7-103">Genelleştirme son değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3fde7-103">Globalization breaking changes</span></span>

<span data-ttu-id="3fde7-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="3fde7-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="3fde7-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="3fde7-105">Breaking change</span></span> | <span data-ttu-id="3fde7-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3fde7-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="3fde7-107">Genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır</span><span class="sxs-lookup"><span data-stu-id="3fde7-107">Globalization APIs use ICU libraries on Windows</span></span>](#globalization-apis-use-icu-libraries-on-windows) | <span data-ttu-id="3fde7-108">5.0</span><span class="sxs-lookup"><span data-stu-id="3fde7-108">5.0</span></span> |
| [<span data-ttu-id="3fde7-109">StringInfo ve TextElementEnumerator artık UAX29 uyumlu</span><span class="sxs-lookup"><span data-stu-id="3fde7-109">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | <span data-ttu-id="3fde7-110">5.0</span><span class="sxs-lookup"><span data-stu-id="3fde7-110">5.0</span></span> |
| [<span data-ttu-id="3fde7-111">"C" yerel ayarı, sabit yerel ayara eşlenir</span><span class="sxs-lookup"><span data-stu-id="3fde7-111">"C" locale maps to the invariant locale</span></span>](#c-locale-maps-to-the-invariant-locale) | <span data-ttu-id="3fde7-112">3.0</span><span class="sxs-lookup"><span data-stu-id="3fde7-112">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="3fde7-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="3fde7-113">.NET 5.0</span></span>

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="3fde7-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3fde7-114">.NET Core 3.0</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
