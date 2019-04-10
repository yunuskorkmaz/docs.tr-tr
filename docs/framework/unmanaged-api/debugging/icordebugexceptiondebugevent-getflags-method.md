---
title: ICorDebugExceptionDebugEvent::GetFlags yöntemi
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af4c7feb7076eeac6089a3255c7832c17a43469b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208845"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="356d3-102">ICorDebugExceptionDebugEvent::GetFlags yöntemi</span><span class="sxs-lookup"><span data-stu-id="356d3-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="356d3-103">Özel durum geçirilebilir olup olmadığını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="356d3-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="356d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="356d3-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="356d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="356d3-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="356d3-106">[out] Bir işaretçi bir [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum geçirilebilir olup olmadığını gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="356d3-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="356d3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="356d3-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="356d3-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="356d3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="356d3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="356d3-109">Requirements</span></span>  
 <span data-ttu-id="356d3-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="356d3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="356d3-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="356d3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="356d3-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="356d3-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="356d3-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="356d3-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="356d3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="356d3-114">See also</span></span>

- [<span data-ttu-id="356d3-115">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="356d3-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="356d3-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="356d3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
