---
title: ForwardTranslateAccelerator işlevi (WPF yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 4bb7e665bb836dc5f95b14f39179f1d4b9f8173d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080260"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="f0d86-102">ForwardTranslateAccelerator işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f0d86-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="f0d86-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="f0d86-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="f0d86-104">Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0d86-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d86-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0d86-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0d86-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0d86-106">Parameters</span></span>  
 <span data-ttu-id="f0d86-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="f0d86-107">pMsg</span></span>  
 <span data-ttu-id="f0d86-108">Bir ileti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f0d86-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="f0d86-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="f0d86-109">appUnhandled</span></span>  
 <span data-ttu-id="f0d86-110">`true` ne zaman uygulama giriş iletisini işlemek için bir fırsat verildi, ancak bunun işlediği değil; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="f0d86-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0d86-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0d86-111">Requirements</span></span>  
 <span data-ttu-id="f0d86-112">**Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0d86-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0d86-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="f0d86-113">**DLL:**</span></span>  
  
 <span data-ttu-id="f0d86-114">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="f0d86-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="f0d86-115">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="f0d86-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="f0d86-116">**.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d86-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d86-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0d86-117">See also</span></span>

- [<span data-ttu-id="f0d86-118">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f0d86-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
