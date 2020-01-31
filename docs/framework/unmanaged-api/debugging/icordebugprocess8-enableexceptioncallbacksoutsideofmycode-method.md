---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: 2c0da899b3f6f3c229c6f5e5b4cafe48fdc19742
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792165"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="682d2-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="682d2-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="682d2-103">[.NET Framework 4,6 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="682d2-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="682d2-104">Belirli [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) özel durum geri çağırmaları türlerini etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="682d2-104">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="682d2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="682d2-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="682d2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="682d2-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="682d2-107">'ndaki</span><span class="sxs-lookup"><span data-stu-id="682d2-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="682d2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="682d2-108">Remarks</span></span>  
 <span data-ttu-id="682d2-109">`enableExceptionsOutsideOfJMC` değeri `false`:</span><span class="sxs-lookup"><span data-stu-id="682d2-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="682d2-110">DEBUG_EXCEPTION_FIRST_CHANCE bir özel durum, hata ayıklayıcıya geri çağırmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="682d2-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="682d2-111">Özel durum Kullanıcı koduna hiçbir şekilde (bir özel durum kaynağından bir özel durum işleyicisine yönelik yol olarak işaretlenen hiçbir yöntem içermez), bir DEBUG_EXCEPTION_CATCH_HANDLER_FOUND özel durum hata ayıklayıcıya geri çağırmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="682d2-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="682d2-112">`enableExceptionsOutsideOfJMC` varsayılan değeri `true`.</span><span class="sxs-lookup"><span data-stu-id="682d2-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="682d2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="682d2-113">Requirements</span></span>  
 <span data-ttu-id="682d2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="682d2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="682d2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="682d2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="682d2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="682d2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="682d2-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="682d2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="682d2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="682d2-118">See also</span></span>

- [<span data-ttu-id="682d2-119">ICorDebugProcess8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="682d2-119">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="682d2-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="682d2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
