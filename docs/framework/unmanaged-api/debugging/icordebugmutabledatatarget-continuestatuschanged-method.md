---
title: ICorDebugMutableDataTarget::ContinueStatusChanged yöntemi
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f43e98530fcd6d11b7c76295a92d42baceddcd6e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764626"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="40c6c-102">ICorDebugMutableDataTarget::ContinueStatusChanged yöntemi</span><span class="sxs-lookup"><span data-stu-id="40c6c-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="40c6c-103">Belirtilen iş parçacığı üzerinde bekleyen hata ayıklama olayı için devamlılık durumu değişir.</span><span class="sxs-lookup"><span data-stu-id="40c6c-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40c6c-104">Syntax</span></span>  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c6c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40c6c-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="40c6c-106">İşletim sistemi tarafından tanımlanan iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="40c6c-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="40c6c-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) devamlılık durumu istenen yeni temsil eden değer.</span><span class="sxs-lookup"><span data-stu-id="40c6c-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40c6c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40c6c-108">Remarks</span></span>  
 <span data-ttu-id="40c6c-109">Hata ayıklayıcı çağrıları `ContinueStatusChanged` Icordebug yöntemi, çağırdığında yöntemi içinde normalde işlenecek yol potansiyel olarak farklı bir şekilde ele alınması için geçerli hata ayıklama olayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="40c6c-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="40c6c-110">Örneğin bekleyen bir özel durum ve hata ayıklayıcı özel durum iptal bir işlem istekleri (gibi [Icordebugılframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) veya `FuncEval`), bu API, özel durum olmasını istemek için kullanılır iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="40c6c-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c6c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40c6c-111">Requirements</span></span>  
 <span data-ttu-id="40c6c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40c6c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c6c-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40c6c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40c6c-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40c6c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40c6c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c6c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c6c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40c6c-116">See also</span></span>

- [<span data-ttu-id="40c6c-117">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40c6c-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="40c6c-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40c6c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
