---
title: ForwardTranslateAccelerator Fonksiyonu - WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186625"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="fb545-102">ForwardTranslateAccelerator Fonksiyonu (WPF Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fb545-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="fb545-103">Bu API, Windows Sunu Temeli (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="fb545-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="fb545-104">Windows Yönetimi için Windows Sunu Temeli (WPF) altyapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb545-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb545-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb545-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb545-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb545-106">Parameters</span></span>  
 <span data-ttu-id="fb545-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="fb545-107">pMsg</span></span>  
 <span data-ttu-id="fb545-108">İleti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb545-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="fb545-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="fb545-109">appUnhandled</span></span>  
 <span data-ttu-id="fb545-110">`true`uygulamaya giriş iletisini işlemek için zaten bir şans verildiğinde, ancak uygulama ele alınmadığında; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="fb545-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb545-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb545-111">Requirements</span></span>  
 <span data-ttu-id="fb545-112">**Platformlar:** Bkz. [.NET Çerçeve Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb545-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb545-113">**Dll:**</span><span class="sxs-lookup"><span data-stu-id="fb545-113">**DLL:**</span></span>  
  
 <span data-ttu-id="fb545-114">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="fb545-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="fb545-115">.NET Framework 4 ve sonraki olarak: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="fb545-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="fb545-116">**.NET Çerçeve Sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb545-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb545-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb545-117">See also</span></span>

- [<span data-ttu-id="fb545-118">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fb545-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
