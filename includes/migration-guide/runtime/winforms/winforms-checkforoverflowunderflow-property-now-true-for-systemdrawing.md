---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235847"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="71da4-101">WinForm'ın CheckForOverflowUnderflow özelliği için System.Drawing geçerlidir</span><span class="sxs-lookup"><span data-stu-id="71da4-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="71da4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="71da4-102">Details</span></span>|<span data-ttu-id="71da4-103">System.Drawing.dll derleme CheckForOverflowUnderflow özellik ayarlanmışsa true.</span><span class="sxs-lookup"><span data-stu-id="71da4-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="71da4-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="71da4-104">Suggestion</span></span>|<span data-ttu-id="71da4-105">Daha önce taşmalar oluştuğunda, sonuç sessizce kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="71da4-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="71da4-106">Artık bir <xref:System.OverflowException?displayProperty=name> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="71da4-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="71da4-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="71da4-107">Scope</span></span>|<span data-ttu-id="71da4-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="71da4-108">Edge</span></span>|
|<span data-ttu-id="71da4-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="71da4-109">Version</span></span>|<span data-ttu-id="71da4-110">4,5</span><span class="sxs-lookup"><span data-stu-id="71da4-110">4.5</span></span>|
|<span data-ttu-id="71da4-111">Tür</span><span class="sxs-lookup"><span data-stu-id="71da4-111">Type</span></span>|<span data-ttu-id="71da4-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="71da4-112">Runtime</span></span>|
