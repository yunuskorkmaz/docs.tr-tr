---
title: "_CorImageUnloading İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f0c105e84d34e83320d6c7d159a94ba4148b302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corimageunloading-function"></a><span data-ttu-id="8463e-102">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="8463e-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="8463e-103">Yönetilen modül görüntüleri kaldırılır, yükleyici size bildirir.</span><span class="sxs-lookup"><span data-stu-id="8463e-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="8463e-104">Bu işlev uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="8463e-104">This function is not implemented.</span></span> <span data-ttu-id="8463e-105">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="8463e-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8463e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8463e-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8463e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8463e-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="8463e-108">[in] Başlangıç konumu kaldırmak için görüntünün bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8463e-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8463e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8463e-109">Requirements</span></span>  
 <span data-ttu-id="8463e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8463e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8463e-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8463e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8463e-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8463e-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8463e-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8463e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8463e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8463e-114">See Also</span></span>  
 [<span data-ttu-id="8463e-115">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8463e-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
