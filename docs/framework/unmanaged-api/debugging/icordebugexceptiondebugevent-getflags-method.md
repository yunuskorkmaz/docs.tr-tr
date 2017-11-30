---
title: "ICorDebugExceptionDebugEvent::GetFlags yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33534a65f7a58981abd3df324b5fe005a06669d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="f96b5-102">ICorDebugExceptionDebugEvent::GetFlags yöntemi</span><span class="sxs-lookup"><span data-stu-id="f96b5-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="f96b5-103">Özel durum geçirilebilir olup olmadığını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="f96b5-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f96b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f96b5-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f96b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f96b5-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="f96b5-106">[out] Bir işaretçi bir [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel geçirilebilir olup olmadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="f96b5-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f96b5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f96b5-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f96b5-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f96b5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f96b5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f96b5-109">Requirements</span></span>  
 <span data-ttu-id="f96b5-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f96b5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f96b5-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f96b5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f96b5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f96b5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f96b5-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f96b5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f96b5-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f96b5-114">See Also</span></span>  
 [<span data-ttu-id="f96b5-115">Icordebugexceptiondebugevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="f96b5-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="f96b5-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f96b5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
