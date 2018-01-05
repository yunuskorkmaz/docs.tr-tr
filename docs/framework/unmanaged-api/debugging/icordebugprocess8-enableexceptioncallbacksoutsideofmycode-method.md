---
title: "ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f13236c865f9a57d77ebf83ab48e010f06ef08e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="94e2a-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94e2a-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="94e2a-103">[Desteklenen [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] ve sonraki sürümlerinde]</span><span class="sxs-lookup"><span data-stu-id="94e2a-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="94e2a-104">Etkinleştirir ya da belirli türlerdeki devre dışı bırakır [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="94e2a-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94e2a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94e2a-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94e2a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94e2a-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="94e2a-107">[in]</span><span class="sxs-lookup"><span data-stu-id="94e2a-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94e2a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94e2a-108">Remarks</span></span>  
 <span data-ttu-id="94e2a-109">Varsa değerini `enableExceptionsOutsideOfJMC` olan `false`:</span><span class="sxs-lookup"><span data-stu-id="94e2a-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="94e2a-110">Bir DEBUG_EXCEPTION_FIRST_CHANCE özel çağırma işleminde hata ayıklayıcısı için yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="94e2a-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="94e2a-111">Özel durum hiç kullanıcı koda çıkışları DEBUG_EXCEPTION_CATCH_HANDLER_FOUND özel durum çağırma işleminde hata ayıklayıcıya neden olur değil (diğer bir deyişle, bir özel durum işleyici bir özel durum kaynaktan yoluna JustMyCode veya JMC olarak işaretlenmiş yöntemi yok).</span><span class="sxs-lookup"><span data-stu-id="94e2a-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="94e2a-112">Varsayılan değer olan `enableExceptionsOutsideOfJMC` olan `true`.</span><span class="sxs-lookup"><span data-stu-id="94e2a-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94e2a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94e2a-113">Requirements</span></span>  
 <span data-ttu-id="94e2a-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94e2a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94e2a-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94e2a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94e2a-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94e2a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94e2a-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94e2a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e2a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94e2a-118">See Also</span></span>  
 [<span data-ttu-id="94e2a-119">ICorDebugProcess8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94e2a-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [<span data-ttu-id="94e2a-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94e2a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
