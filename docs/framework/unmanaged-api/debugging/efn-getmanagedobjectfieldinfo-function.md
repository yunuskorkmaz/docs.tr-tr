---
title: "_EFN_GetManagedObjectFieldInfo İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedObjectFieldInfo
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedObjectFieldInfo
helpviewer_keywords: _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3df09c9107b683381f21891a1001140c493a024
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="8403d-102">_EFN_GetManagedObjectFieldInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="8403d-102">_EFN_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="8403d-103">Uzaklık, bir alan ve alanın değerini, sağlanan nesne işaretçisi ve alan adını kullanarak bir nesne başından alır.</span><span class="sxs-lookup"><span data-stu-id="8403d-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8403d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8403d-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8403d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8403d-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="8403d-106">[in] Hata ayıklama istemci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8403d-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="8403d-107">[in] Bir yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8403d-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="8403d-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="8403d-108">szFieldName</span></span>  
 <span data-ttu-id="8403d-109">[in] Alan adı için bir yönetilen nesne işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8403d-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8403d-110">[out] Alan değeri.</span><span class="sxs-lookup"><span data-stu-id="8403d-110">[out] The field value.</span></span> <span data-ttu-id="8403d-111">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="8403d-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="8403d-112">[out] Uzaklık `objAddr` alanına.</span><span class="sxs-lookup"><span data-stu-id="8403d-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="8403d-113">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="8403d-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8403d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8403d-114">Remarks</span></span>  
 <span data-ttu-id="8403d-115">Uzaklığı 0 ise, uzaklık yazılır.</span><span class="sxs-lookup"><span data-stu-id="8403d-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="8403d-116">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlevi HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değeri ve 0x1000 hata kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8403d-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8403d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8403d-117">Requirements</span></span>  
 <span data-ttu-id="8403d-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8403d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8403d-119">**Başlık:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="8403d-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="8403d-120">**.NET framework sürümü:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8403d-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8403d-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8403d-121">See Also</span></span>  
 [<span data-ttu-id="8403d-122">Hata ayıklama genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="8403d-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
