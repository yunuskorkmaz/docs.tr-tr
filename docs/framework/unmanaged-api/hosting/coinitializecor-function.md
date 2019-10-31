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
ms.openlocfilehash: e8d65e739504e01a7d11b37d1b34d7313b13a5e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138329"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="07297-102">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="07297-102">CoInitializeCor Function</span></span>
<span data-ttu-id="07297-103">`CoInitializeCor` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="07297-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07297-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07297-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="07297-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07297-105">Remarks</span></span>  
 <span data-ttu-id="07297-106">Ortak dil çalışma zamanını başlatmak için [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="07297-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07297-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07297-107">Requirements</span></span>  
 <span data-ttu-id="07297-108">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="07297-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07297-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07297-109">See also</span></span>

- [<span data-ttu-id="07297-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="07297-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
