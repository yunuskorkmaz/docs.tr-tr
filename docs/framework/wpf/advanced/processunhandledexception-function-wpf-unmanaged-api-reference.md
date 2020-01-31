---
title: ProcessUnhandledException Işlevi-WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743926"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="86db7-102">ProcessUnhandledException Işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="86db7-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="86db7-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="86db7-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="86db7-104">Özel durum işleme için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86db7-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86db7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86db7-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="86db7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86db7-106">Parameters</span></span>  
 <span data-ttu-id="86db7-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="86db7-107">errorMsg</span></span>  
 <span data-ttu-id="86db7-108">Hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="86db7-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86db7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86db7-109">Requirements</span></span>  
 <span data-ttu-id="86db7-110">**Platformlar:** Bkz. [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86db7-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86db7-111">**DOSYASıNı**</span><span class="sxs-lookup"><span data-stu-id="86db7-111">**DLL:**</span></span>  
  
 <span data-ttu-id="86db7-112">.NET Framework 3,0 ve 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="86db7-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="86db7-113">.NET Framework 4 ve üzeri: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="86db7-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="86db7-114">**.NET Framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86db7-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86db7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86db7-115">See also</span></span>

- [<span data-ttu-id="86db7-116">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="86db7-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
