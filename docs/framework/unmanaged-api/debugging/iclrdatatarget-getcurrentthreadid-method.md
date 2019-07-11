---
title: ICLRDataTarget::GetCurrentThreadID Metodu
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45a409bda8861701e68d3ea1a956a4c35ce88ddd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738786"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="9d2ee-102">ICLRDataTarget::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="9d2ee-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="9d2ee-103">Geçerli iş parçacığı için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="9d2ee-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d2ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d2ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d2ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d2ee-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="9d2ee-106">[out] Hedef işlem için geçerli iş parçacığının işletim sistem tanımlayıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d2ee-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d2ee-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d2ee-107">Remarks</span></span>  
 <span data-ttu-id="9d2ee-108">Hedef işlem, geçerli iş parçacığının ise `GetCurrentThreadID` yöntemi başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d2ee-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d2ee-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d2ee-109">Requirements</span></span>  
 <span data-ttu-id="9d2ee-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d2ee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d2ee-111">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="9d2ee-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9d2ee-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d2ee-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d2ee-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d2ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2ee-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d2ee-114">See also</span></span>

- [<span data-ttu-id="9d2ee-115">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d2ee-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
