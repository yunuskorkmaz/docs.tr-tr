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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8642c165c29f9ca63535a0efbb9dbb58d4660a49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160400"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="d97cd-102">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="d97cd-102">CoInitializeCor Function</span></span>
<span data-ttu-id="d97cd-103">`CoInitializeCor` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d97cd-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d97cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d97cd-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d97cd-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d97cd-105">Remarks</span></span>  
 <span data-ttu-id="d97cd-106">Ortak dil çalışma zamanı'nı başlatmak için ya da kullanmak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="d97cd-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d97cd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d97cd-107">Requirements</span></span>  
 <span data-ttu-id="d97cd-108">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d97cd-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97cd-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d97cd-109">See also</span></span>

- [<span data-ttu-id="d97cd-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d97cd-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
