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
ms.openlocfilehash: 188f98504fa73c4a85615a4e688bae02d966b9b6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616755"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="ee95c-102">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="ee95c-102">CoInitializeCor Function</span></span>
<span data-ttu-id="ee95c-103">`CoInitializeCor`artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ee95c-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee95c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ee95c-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="ee95c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee95c-105">Remarks</span></span>  
 <span data-ttu-id="ee95c-106">Ortak dil çalışma zamanını başlatmak için [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee95c-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee95c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee95c-107">Requirements</span></span>  
 <span data-ttu-id="ee95c-108">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ee95c-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee95c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee95c-109">See also</span></span>

- [<span data-ttu-id="ee95c-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ee95c-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
