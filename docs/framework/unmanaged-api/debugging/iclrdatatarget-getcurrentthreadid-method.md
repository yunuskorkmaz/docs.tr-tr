---
description: ': ICLRDataTarget:: GetCurrentThreadID yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ae1ef00fd6afbecf741d1e4ed215c816dcf6af8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801364"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="6a2ba-103">ICLRDataTarget::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="6a2ba-103">ICLRDataTarget::GetCurrentThreadID Method</span></span>

<span data-ttu-id="6a2ba-104">Geçerli iş parçacığının işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="6a2ba-104">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a2ba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a2ba-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a2ba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a2ba-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="6a2ba-107">dışı Hedef işlem için geçerli iş parçacığının işletim sistemi tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6a2ba-107">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a2ba-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a2ba-108">Remarks</span></span>  

 <span data-ttu-id="6a2ba-109">Hedef işlem için geçerli bir iş parçacığı yoksa `GetCurrentThreadID` Yöntem başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a2ba-109">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a2ba-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a2ba-110">Requirements</span></span>  

 <span data-ttu-id="6a2ba-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a2ba-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a2ba-112">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="6a2ba-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6a2ba-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6a2ba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a2ba-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a2ba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a2ba-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a2ba-115">See also</span></span>

- [<span data-ttu-id="6a2ba-116">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a2ba-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
