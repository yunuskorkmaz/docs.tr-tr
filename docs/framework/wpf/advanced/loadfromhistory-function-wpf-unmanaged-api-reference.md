---
title: "LoadFromHistory işlevi (WPF yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: LoadFromHistory
api_location: PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6eca1c30664e381101b6e51c1347341432a042b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="7956f-102">LoadFromHistory işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7956f-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="7956f-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="7956f-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="7956f-104">Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7956f-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7956f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7956f-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7956f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7956f-106">Parameters</span></span>  
 <span data-ttu-id="7956f-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="7956f-107">pHistoryStream</span></span>  
 <span data-ttu-id="7956f-108">Bir işaretçi bir akışa geçmiş bilgileri.</span><span class="sxs-lookup"><span data-stu-id="7956f-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="7956f-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="7956f-109">pBindCtx</span></span>  
 <span data-ttu-id="7956f-110">Bir bağlama bağlamı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7956f-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7956f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7956f-111">Requirements</span></span>  
 <span data-ttu-id="7956f-112">**Platformlar:** bkz [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7956f-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7956f-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="7956f-113">**DLL:**</span></span>  
  
 <span data-ttu-id="7956f-114">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="7956f-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="7956f-115">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="7956f-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="7956f-116">**.NET framework sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7956f-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7956f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7956f-117">See Also</span></span>  
 [<span data-ttu-id="7956f-118">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7956f-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
