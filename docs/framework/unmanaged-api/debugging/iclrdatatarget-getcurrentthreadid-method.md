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
ms.openlocfilehash: 3a355822710394e9351f10be78dea283e2e9907c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703597"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="a5e03-102">ICLRDataTarget::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="a5e03-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>

<span data-ttu-id="a5e03-103">Geçerli iş parçacığının işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="a5e03-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5e03-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a5e03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5e03-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5e03-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="a5e03-106">dışı Hedef işlem için geçerli iş parçacığının işletim sistemi tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5e03-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5e03-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5e03-107">Remarks</span></span>  

 <span data-ttu-id="a5e03-108">Hedef işlem için geçerli bir iş parçacığı yoksa `GetCurrentThreadID` Yöntem başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="a5e03-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5e03-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5e03-109">Requirements</span></span>  

 <span data-ttu-id="a5e03-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5e03-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e03-111">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="a5e03-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a5e03-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a5e03-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5e03-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e03-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e03-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5e03-114">See also</span></span>

- [<span data-ttu-id="a5e03-115">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5e03-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
