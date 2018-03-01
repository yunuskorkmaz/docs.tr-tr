---
title: "_EFN_GetManagedObjectName İşlevi"
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
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c29aa82143c34a229cee0a5b000657c9add22bd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="5eefb-102">_EFN_GetManagedObjectName İşlevi</span><span class="sxs-lookup"><span data-stu-id="5eefb-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="5eefb-103">Sağlanan yönetilen nesne işaretçisi kullanılarak bir türün adını alır.</span><span class="sxs-lookup"><span data-stu-id="5eefb-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eefb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5eefb-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5eefb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5eefb-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="5eefb-106">[in] Hata ayıklama istemci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5eefb-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="5eefb-107">[in] Bir yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5eefb-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="5eefb-108">szName</span><span class="sxs-lookup"><span data-stu-id="5eefb-108">szName</span></span>  
 <span data-ttu-id="5eefb-109">[out] Türünün adı.</span><span class="sxs-lookup"><span data-stu-id="5eefb-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="5eefb-110">[out] Karakter dizesi arabellekte kullanılabilir sayısı.</span><span class="sxs-lookup"><span data-stu-id="5eefb-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5eefb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5eefb-111">Remarks</span></span>  
 <span data-ttu-id="5eefb-112">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlevi HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değeri ve 0x1000 hata kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5eefb-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eefb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5eefb-113">Requirements</span></span>  
 <span data-ttu-id="5eefb-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5eefb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5eefb-115">**Başlık:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="5eefb-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="5eefb-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5eefb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eefb-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5eefb-117">See Also</span></span>  
 [<span data-ttu-id="5eefb-118">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5eefb-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
