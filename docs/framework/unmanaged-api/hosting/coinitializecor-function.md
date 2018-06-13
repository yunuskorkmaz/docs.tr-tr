---
title: CoInitializeCor İşlevi
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
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
ms.openlocfilehash: 91315e8af0cc46a3450a7515b885988cffe34927
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429994"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="21750-102">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="21750-102">CoInitializeCor Function</span></span>
<span data-ttu-id="21750-103">`CoInitializeCor` Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="21750-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21750-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21750-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="21750-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21750-105">Remarks</span></span>  
 <span data-ttu-id="21750-106">Ortak dil çalışma zamanı başlatmak için kullanın ya da [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="21750-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21750-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21750-107">Requirements</span></span>  
 <span data-ttu-id="21750-108">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="21750-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21750-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21750-109">See Also</span></span>  
 [<span data-ttu-id="21750-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="21750-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
