---
title: "_EFN_GetManagedObjectName İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedObjectName
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedObjectName
helpviewer_keywords: _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80e36f6c60c4c305cad9176cd7f185d8b6d2fdf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="59a5b-102">_EFN_GetManagedObjectName İşlevi</span><span class="sxs-lookup"><span data-stu-id="59a5b-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="59a5b-103">Sağlanan yönetilen nesne işaretçisi kullanılarak bir türün adını alır.</span><span class="sxs-lookup"><span data-stu-id="59a5b-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59a5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59a5b-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59a5b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59a5b-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="59a5b-106">[in] Hata ayıklama istemci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="59a5b-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="59a5b-107">[in] Bir yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="59a5b-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="59a5b-108">szName</span><span class="sxs-lookup"><span data-stu-id="59a5b-108">szName</span></span>  
 <span data-ttu-id="59a5b-109">[out] Türünün adı.</span><span class="sxs-lookup"><span data-stu-id="59a5b-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="59a5b-110">[out] Karakter dizesi arabellekte kullanılabilir sayısı.</span><span class="sxs-lookup"><span data-stu-id="59a5b-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59a5b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59a5b-111">Remarks</span></span>  
 <span data-ttu-id="59a5b-112">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlevi HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değeri ve 0x1000 hata kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="59a5b-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59a5b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59a5b-113">Requirements</span></span>  
 <span data-ttu-id="59a5b-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59a5b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59a5b-115">**Başlık:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="59a5b-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="59a5b-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59a5b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a5b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59a5b-117">See Also</span></span>  
 [<span data-ttu-id="59a5b-118">Hata ayıklama genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="59a5b-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
