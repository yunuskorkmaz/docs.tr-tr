---
title: "SaveToHistory işlevi (WPF yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af5294aad43b28bc590dd84466e133553f0ee47b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="feba7-102">SaveToHistory işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="feba7-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="feba7-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="feba7-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="feba7-104">Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="feba7-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feba7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="feba7-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="feba7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="feba7-106">Parameters</span></span>  
 <span data-ttu-id="feba7-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="feba7-107">pHistoryStream</span></span>  
 <span data-ttu-id="feba7-108">Geçmiş akışı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="feba7-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feba7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feba7-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feba7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feba7-110">Requirements</span></span>  
 <span data-ttu-id="feba7-111">**Platformlar:** bkz [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feba7-111">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feba7-112">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="feba7-112">**DLL:**</span></span>  
  
 <span data-ttu-id="feba7-113">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="feba7-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="feba7-114">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="feba7-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="feba7-115">**.NET framework sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feba7-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feba7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="feba7-116">See Also</span></span>  
 [<span data-ttu-id="feba7-117">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="feba7-117">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
