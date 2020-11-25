---
title: CoInitializeCor İşlevi
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: 9d077d5c5a414568b5643cad0171e101d7bb06f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731715"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="e3e8e-102">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="e3e8e-102">CoInitializeCor Function</span></span>

<span data-ttu-id="e3e8e-103">`CoInitializeCor` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e3e8e-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e8e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3e8e-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="e3e8e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3e8e-105">Remarks</span></span>  

 <span data-ttu-id="e3e8e-106">Ortak dil çalışma zamanını başlatmak için [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="e3e8e-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3e8e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3e8e-107">Requirements</span></span>  

 <span data-ttu-id="e3e8e-108">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e3e8e-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e8e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3e8e-109">See also</span></span>

- [<span data-ttu-id="e3e8e-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e3e8e-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
