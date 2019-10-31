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
ms.openlocfilehash: ccb5cda11a2466496a4b3981e8185cbb7130f66f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122903"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="665b2-102">ICLRDataTarget::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="665b2-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="665b2-103">Geçerli iş parçacığının işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="665b2-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="665b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="665b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="665b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="665b2-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="665b2-106">dışı Hedef işlem için geçerli iş parçacığının işletim sistemi tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="665b2-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="665b2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="665b2-107">Remarks</span></span>  
 <span data-ttu-id="665b2-108">Hedef işlem için geçerli bir iş parçacığı yoksa `GetCurrentThreadID` yöntemi başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="665b2-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="665b2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="665b2-109">Requirements</span></span>  
 <span data-ttu-id="665b2-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="665b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="665b2-111">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="665b2-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="665b2-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="665b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="665b2-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="665b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665b2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="665b2-114">See also</span></span>

- [<span data-ttu-id="665b2-115">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="665b2-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
