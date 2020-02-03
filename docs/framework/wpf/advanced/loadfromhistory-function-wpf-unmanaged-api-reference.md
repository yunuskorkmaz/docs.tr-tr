---
title: LoadFromHistory Işlevi-WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727935"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="388ed-102">LoadFromHistory Işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="388ed-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="388ed-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="388ed-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="388ed-104">Windows yönetimi için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="388ed-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="388ed-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="388ed-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="388ed-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="388ed-106">Parameters</span></span>  
 <span data-ttu-id="388ed-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="388ed-107">pHistoryStream</span></span>  
 <span data-ttu-id="388ed-108">Geçmiş bilgileri akışına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="388ed-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="388ed-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="388ed-109">pBindCtx</span></span>  
 <span data-ttu-id="388ed-110">Bağlama bağlamına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="388ed-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="388ed-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="388ed-111">Requirements</span></span>  
 <span data-ttu-id="388ed-112">**Platformlar:** Bkz. [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="388ed-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="388ed-113">**DOSYASıNı**</span><span class="sxs-lookup"><span data-stu-id="388ed-113">**DLL:**</span></span>  
  
 <span data-ttu-id="388ed-114">.NET Framework 3,0 ve 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="388ed-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="388ed-115">.NET Framework 4 ve üzeri: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="388ed-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="388ed-116">**.NET Framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="388ed-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388ed-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="388ed-117">See also</span></span>

- [<span data-ttu-id="388ed-118">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="388ed-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
