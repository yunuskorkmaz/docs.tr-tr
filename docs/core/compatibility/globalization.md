---
title: Genelleştirme son değişiklikleri
description: .NET Core 'da Genelleştirme 'deki son değişiklikleri listeler.
ms.date: 04/07/2020
ms.openlocfilehash: 93990d89204df1b2d7498e1d748378fae05598c3
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065077"
---
# <a name="globalization-breaking-changes"></a><span data-ttu-id="7d1bf-103">Genelleştirme son değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="7d1bf-103">Globalization breaking changes</span></span>

<span data-ttu-id="7d1bf-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="7d1bf-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="7d1bf-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="7d1bf-105">Breaking change</span></span> | <span data-ttu-id="7d1bf-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7d1bf-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="7d1bf-107">Bazı Latin-1 karakterleri için Unicode kategorisi değişti</span><span class="sxs-lookup"><span data-stu-id="7d1bf-107">Unicode category changed for some Latin-1 characters</span></span>](#unicode-category-changed-for-some-latin-1-characters) | <span data-ttu-id="7d1bf-108">5.0</span><span class="sxs-lookup"><span data-stu-id="7d1bf-108">5.0</span></span> |
| [<span data-ttu-id="7d1bf-109">Genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır</span><span class="sxs-lookup"><span data-stu-id="7d1bf-109">Globalization APIs use ICU libraries on Windows</span></span>](#globalization-apis-use-icu-libraries-on-windows) | <span data-ttu-id="7d1bf-110">5.0</span><span class="sxs-lookup"><span data-stu-id="7d1bf-110">5.0</span></span> |
| [<span data-ttu-id="7d1bf-111">StringInfo ve TextElementEnumerator artık UAX29 uyumlu</span><span class="sxs-lookup"><span data-stu-id="7d1bf-111">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | <span data-ttu-id="7d1bf-112">5.0</span><span class="sxs-lookup"><span data-stu-id="7d1bf-112">5.0</span></span> |
| [<span data-ttu-id="7d1bf-113">"C" yerel ayarı, sabit yerel ayara eşlenir</span><span class="sxs-lookup"><span data-stu-id="7d1bf-113">"C" locale maps to the invariant locale</span></span>](#c-locale-maps-to-the-invariant-locale) | <span data-ttu-id="7d1bf-114">3.0</span><span class="sxs-lookup"><span data-stu-id="7d1bf-114">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="7d1bf-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7d1bf-115">.NET 5.0</span></span>

[!INCLUDE [unicode-categories-for-latin1-chars](../../../includes/core-changes/globalization/5.0/unicode-categories-for-latin1-chars.md)]

***

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="7d1bf-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d1bf-116">.NET Core 3.0</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
