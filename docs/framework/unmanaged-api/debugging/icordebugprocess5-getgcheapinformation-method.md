---
title: ICorDebugProcess5::GetGCHeapInformation Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetGCHeapInformation
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70e9e3ab6c7332e492b7146e52e0265653803bf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="48610-102">ICorDebugProcess5::GetGCHeapInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="48610-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="48610-103">Şu anda numaralandırılabilir olup olmadığını atık toplama yığın hakkında genel bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="48610-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48610-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48610-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48610-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48610-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="48610-106">[out] Bir işaretçi bir [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) değeri atık toplama yığın hakkında genel bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="48610-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48610-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48610-107">Remarks</span></span>  
 <span data-ttu-id="48610-108">`ICorDebugProcess5::GetGCHeapInformation` Öbek numaralandırma önce yöntemi çağrılmalıdır veya çöp toplama işleminde yapıları emin olmak için tek tek yığın bölgeler şu anda geçerli.</span><span class="sxs-lookup"><span data-stu-id="48610-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="48610-109">Bir koleksiyonu işlemi devam ederken atık toplama yığın gitti olamaz.</span><span class="sxs-lookup"><span data-stu-id="48610-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="48610-110">Aksi takdirde, numaralandırma geçersiz atık toplama yapıları yakalama.</span><span class="sxs-lookup"><span data-stu-id="48610-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48610-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48610-111">Requirements</span></span>  
 <span data-ttu-id="48610-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48610-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48610-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48610-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48610-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48610-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48610-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48610-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48610-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48610-116">See Also</span></span>  
 [<span data-ttu-id="48610-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48610-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="48610-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="48610-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
