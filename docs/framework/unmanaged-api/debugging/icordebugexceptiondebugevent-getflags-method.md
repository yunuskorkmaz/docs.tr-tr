---
title: ICorDebugExceptionDebugEvent::GetFlags yöntemi
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 739b2412d6b75df0921f778c95cc2fe65fef9b79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636046"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="43abc-102">ICorDebugExceptionDebugEvent::GetFlags yöntemi</span><span class="sxs-lookup"><span data-stu-id="43abc-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="43abc-103">Özel durum geçirilebilir olup olmadığını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="43abc-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43abc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43abc-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43abc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43abc-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="43abc-106">[out] Bir işaretçi bir [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum geçirilebilir olup olmadığını gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="43abc-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43abc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43abc-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43abc-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="43abc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43abc-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43abc-109">Requirements</span></span>  
 <span data-ttu-id="43abc-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43abc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43abc-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43abc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43abc-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43abc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43abc-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43abc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43abc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43abc-114">See also</span></span>
- [<span data-ttu-id="43abc-115">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43abc-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="43abc-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="43abc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
