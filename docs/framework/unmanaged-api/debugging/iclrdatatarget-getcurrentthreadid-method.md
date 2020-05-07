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
ms.openlocfilehash: c75c55b64ff20728bc5695d0ddfe1b4f6deda4a6
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860642"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="cb2a4-102">ICLRDataTarget::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="cb2a4-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="cb2a4-103">Geçerli iş parçacığının işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="cb2a4-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb2a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb2a4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb2a4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb2a4-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="cb2a4-106">dışı Hedef işlem için geçerli iş parçacığının işletim sistemi tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb2a4-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb2a4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb2a4-107">Remarks</span></span>  
 <span data-ttu-id="cb2a4-108">Hedef işlem için geçerli bir iş parçacığı yoksa `GetCurrentThreadID` yöntem başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="cb2a4-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb2a4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb2a4-109">Requirements</span></span>  
 <span data-ttu-id="cb2a4-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb2a4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb2a4-111">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="cb2a4-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cb2a4-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cb2a4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb2a4-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb2a4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb2a4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb2a4-114">See also</span></span>

- [<span data-ttu-id="cb2a4-115">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb2a4-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
