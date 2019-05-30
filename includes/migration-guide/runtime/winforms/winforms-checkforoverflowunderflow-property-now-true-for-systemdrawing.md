---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379629"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="fff25-101">WinForm'ın CheckForOverflowUnderflow özelliği için System.Drawing geçerlidir</span><span class="sxs-lookup"><span data-stu-id="fff25-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fff25-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fff25-102">Details</span></span>|<span data-ttu-id="fff25-103">System.Drawing.dll derleme CheckForOverflowUnderflow özellik ayarlanmışsa true.</span><span class="sxs-lookup"><span data-stu-id="fff25-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="fff25-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="fff25-104">Suggestion</span></span>|<span data-ttu-id="fff25-105">Daha önce taşmalar oluştuğunda, sonuç sessizce kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="fff25-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="fff25-106">Artık bir <xref:System.OverflowException?displayProperty=name> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fff25-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="fff25-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="fff25-107">Scope</span></span>|<span data-ttu-id="fff25-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="fff25-108">Edge</span></span>|
|<span data-ttu-id="fff25-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fff25-109">Version</span></span>|<span data-ttu-id="fff25-110">4,5</span><span class="sxs-lookup"><span data-stu-id="fff25-110">4.5</span></span>|
|<span data-ttu-id="fff25-111">Tür</span><span class="sxs-lookup"><span data-stu-id="fff25-111">Type</span></span>|<span data-ttu-id="fff25-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="fff25-112">Runtime</span></span>|
