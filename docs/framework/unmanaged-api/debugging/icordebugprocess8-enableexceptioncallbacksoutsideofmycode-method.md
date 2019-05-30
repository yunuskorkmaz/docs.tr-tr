---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52a58f75ca7abd1bd1f871bcf4637bfd7eb7bdcd
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300538"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="c6996-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6996-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="c6996-103">[.NET Framework 4.6 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="c6996-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="c6996-104">Etkinleştirir veya belirli türlerdeki devre dışı bırakır [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalarını.</span><span class="sxs-lookup"><span data-stu-id="c6996-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6996-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6996-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6996-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6996-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="c6996-107">[in]</span><span class="sxs-lookup"><span data-stu-id="c6996-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6996-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6996-108">Remarks</span></span>  
 <span data-ttu-id="c6996-109">Varsa değerini `enableExceptionsOutsideOfJMC` olduğu `false`:</span><span class="sxs-lookup"><span data-stu-id="c6996-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="c6996-110">DEBUG_EXCEPTION_FIRST_CHANCE özel durumu bir geri çağırma içinde hata ayıklayıcıya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="c6996-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="c6996-111">Varsa özel durumun hiç kullanıcı kodu çıkışları DEBUG_EXCEPTION_CATCH_HANDLER_FOUND özel durum geri aramada hata ayıklayıcıyı oluşturmayacaktır (diğer bir deyişle, bir özel durum işleyicisi bir özel durum kaynaktan yolunu JustMyCode ya da JMC işaretlenmiş bir yöntemi yok).</span><span class="sxs-lookup"><span data-stu-id="c6996-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="c6996-112">Varsayılan değer olan `enableExceptionsOutsideOfJMC` olduğu `true`.</span><span class="sxs-lookup"><span data-stu-id="c6996-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6996-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6996-113">Requirements</span></span>  
 <span data-ttu-id="c6996-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6996-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6996-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6996-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6996-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6996-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6996-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6996-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6996-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6996-118">See also</span></span>

- [<span data-ttu-id="c6996-119">ICorDebugProcess8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6996-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="c6996-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c6996-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
