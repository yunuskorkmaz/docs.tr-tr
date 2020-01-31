---
title: ForwardTranslateAccelerator Işlevi-WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747041"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="69ba8-102">ForwardTranslateAccelerator Işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="69ba8-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="69ba8-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="69ba8-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="69ba8-104">Windows yönetimi için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69ba8-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69ba8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69ba8-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="69ba8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69ba8-106">Parameters</span></span>  
 <span data-ttu-id="69ba8-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="69ba8-107">pMsg</span></span>  
 <span data-ttu-id="69ba8-108">İleti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="69ba8-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="69ba8-109">Appişlenmemiş</span><span class="sxs-lookup"><span data-stu-id="69ba8-109">appUnhandled</span></span>  
 <span data-ttu-id="69ba8-110">uygulamaya giriş iletisini işleme şansı verildiğinde, ancak işlenmeyen `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="69ba8-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69ba8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69ba8-111">Requirements</span></span>  
 <span data-ttu-id="69ba8-112">**Platformlar:** Bkz. [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69ba8-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69ba8-113">**DOSYASıNı**</span><span class="sxs-lookup"><span data-stu-id="69ba8-113">**DLL:**</span></span>  
  
 <span data-ttu-id="69ba8-114">.NET Framework 3,0 ve 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="69ba8-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="69ba8-115">.NET Framework 4 ve üzeri: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="69ba8-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="69ba8-116">**.NET Framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69ba8-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69ba8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69ba8-117">See also</span></span>

- [<span data-ttu-id="69ba8-118">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="69ba8-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
