---
title: ProcessUnhandledException işlevi (WPF yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 3a95e8e68361f060d843247f400043a79dc28889
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466875"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="1dc6d-102">ProcessUnhandledException işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1dc6d-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="1dc6d-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="1dc6d-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="1dc6d-104">Windows Presentation Foundation (WPF) altyapısı tarafından özel durum işleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1dc6d-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dc6d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dc6d-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dc6d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dc6d-106">Parameters</span></span>  
 <span data-ttu-id="1dc6d-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="1dc6d-107">errorMsg</span></span>  
 <span data-ttu-id="1dc6d-108">Hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="1dc6d-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dc6d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dc6d-109">Requirements</span></span>  
 <span data-ttu-id="1dc6d-110">**Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dc6d-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dc6d-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="1dc6d-111">**DLL:**</span></span>  
  
 <span data-ttu-id="1dc6d-112">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="1dc6d-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="1dc6d-113">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="1dc6d-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="1dc6d-114">**.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dc6d-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc6d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dc6d-115">See also</span></span>
- [<span data-ttu-id="1dc6d-116">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1dc6d-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
