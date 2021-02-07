---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugProcess8:: EnableExceptionCallbacksOutsideOfMyCode Yöntemi'
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: a85c9d62e5fb62fe620f0901509afa5a03504d4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691282"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="64b6c-103">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64b6c-103">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>

<span data-ttu-id="64b6c-104">[.NET Framework 4,6 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="64b6c-104">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="64b6c-105">Belirli [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) özel durum geri çağırmaları türlerini etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="64b6c-105">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b6c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64b6c-106">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64b6c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64b6c-107">Parameters</span></span>  

 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="64b6c-108">'ndaki</span><span class="sxs-lookup"><span data-stu-id="64b6c-108">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64b6c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64b6c-109">Remarks</span></span>  

 <span data-ttu-id="64b6c-110">Öğesinin değeri `enableExceptionsOutsideOfJMC` `false` :</span><span class="sxs-lookup"><span data-stu-id="64b6c-110">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="64b6c-111">DEBUG_EXCEPTION_FIRST_CHANCE bir özel durum, hata ayıklayıcıya geri çağırmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="64b6c-111">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="64b6c-112">Özel durum Kullanıcı koduna hiçbir şekilde (bir özel durum kaynağından bir özel durum işleyicisine yönelik yol olarak işaretlenen hiçbir yöntem içermez), bir DEBUG_EXCEPTION_CATCH_HANDLER_FOUND özel durum hata ayıklayıcıya geri çağırmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="64b6c-112">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="64b6c-113">Varsayılan değeri `enableExceptionsOutsideOfJMC` `true` .</span><span class="sxs-lookup"><span data-stu-id="64b6c-113">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64b6c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64b6c-114">Requirements</span></span>  

 <span data-ttu-id="64b6c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64b6c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64b6c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="64b6c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64b6c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="64b6c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64b6c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64b6c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b6c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64b6c-119">See also</span></span>

- [<span data-ttu-id="64b6c-120">ICorDebugProcess8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64b6c-120">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="64b6c-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64b6c-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
