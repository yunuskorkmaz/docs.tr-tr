---
title: LoadFromHistory işlevi (WPF yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: a4480d54390aea2771e2939b0a0825f6c49c3564
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766145"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="64d06-102">LoadFromHistory işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="64d06-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="64d06-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="64d06-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="64d06-104">Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64d06-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d06-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64d06-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d06-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64d06-106">Parameters</span></span>  
 <span data-ttu-id="64d06-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="64d06-107">pHistoryStream</span></span>  
 <span data-ttu-id="64d06-108">Geçmiş bilgileri akışı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64d06-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="64d06-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="64d06-109">pBindCtx</span></span>  
 <span data-ttu-id="64d06-110">Bir bağlama bağlamı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64d06-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d06-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64d06-111">Requirements</span></span>  
 <span data-ttu-id="64d06-112">**Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d06-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d06-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="64d06-113">**DLL:**</span></span>  
  
 <span data-ttu-id="64d06-114">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="64d06-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="64d06-115">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="64d06-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="64d06-116">**.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d06-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d06-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64d06-117">See also</span></span>

- [<span data-ttu-id="64d06-118">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="64d06-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
