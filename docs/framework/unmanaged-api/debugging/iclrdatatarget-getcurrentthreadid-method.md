---
title: ICLRDataTarget::GetCurrentThreadID Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetCurrentThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3820a3f32834f02b60fb33448bcaf8febdc15ce6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="fc49a-102">ICLRDataTarget::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="fc49a-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="fc49a-103">Geçerli iş parçacığı için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="fc49a-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc49a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc49a-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc49a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc49a-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="fc49a-106">[out] Hedef işlem için geçerli iş parçacığının işletim sistemi tanımlayıcısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fc49a-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc49a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc49a-107">Remarks</span></span>  
 <span data-ttu-id="fc49a-108">Hedef işlem için geçerli hiçbir iş parçacığı ise `GetCurrentThreadID` yöntemi başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc49a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc49a-109">Requirements</span></span>  
 <span data-ttu-id="fc49a-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc49a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc49a-111">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="fc49a-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fc49a-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc49a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc49a-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc49a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc49a-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc49a-114">See Also</span></span>  
 [<span data-ttu-id="fc49a-115">Iclrdatatarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc49a-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
