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
ms.openlocfilehash: 35515d7c2b82ec2c42461406363964e0b60eb243
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785462"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="7b954-102">ICLRDataTarget::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="7b954-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="7b954-103">Geçerli iş parçacığının işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="7b954-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b954-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b954-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b954-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b954-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="7b954-106">dışı Hedef işlem için geçerli iş parçacığının işletim sistemi tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b954-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b954-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b954-107">Remarks</span></span>  
 <span data-ttu-id="7b954-108">Hedef işlem için geçerli bir iş parçacığı yoksa `GetCurrentThreadID` yöntemi başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b954-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b954-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b954-109">Requirements</span></span>  
 <span data-ttu-id="7b954-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b954-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b954-111">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="7b954-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7b954-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7b954-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b954-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b954-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b954-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b954-114">See also</span></span>

- [<span data-ttu-id="7b954-115">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b954-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
