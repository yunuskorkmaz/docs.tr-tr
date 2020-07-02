---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620694"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="74822-101">WinForm 'ın Checkforoverflowyetersizliği özelliği artık System. Drawing için doğru</span><span class="sxs-lookup"><span data-stu-id="74822-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="74822-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="74822-102">Details</span></span>

<span data-ttu-id="74822-103">System.Drawing.dll derlemesinin Checkforoverflowyetersizliği özelliği true olarak ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="74822-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="74822-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="74822-104">Suggestion</span></span>

<span data-ttu-id="74822-105">Daha önce taşmalar oluştuğunda, sonuç sessizce kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="74822-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="74822-106">Şimdi bir <xref:System.OverflowException?displayProperty=fullName> özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="74822-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="74822-107">Name</span><span class="sxs-lookup"><span data-stu-id="74822-107">Name</span></span>    | <span data-ttu-id="74822-108">Değer</span><span class="sxs-lookup"><span data-stu-id="74822-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="74822-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="74822-109">Scope</span></span>   |<span data-ttu-id="74822-110">Edge</span><span class="sxs-lookup"><span data-stu-id="74822-110">Edge</span></span>|
|<span data-ttu-id="74822-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="74822-111">Version</span></span>|<span data-ttu-id="74822-112">4,5</span><span class="sxs-lookup"><span data-stu-id="74822-112">4.5</span></span>|
|<span data-ttu-id="74822-113">Tür</span><span class="sxs-lookup"><span data-stu-id="74822-113">Type</span></span>|<span data-ttu-id="74822-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="74822-114">Runtime</span></span>|
