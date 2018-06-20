---
title: ICorDebugMutableDataTarget::ContinueStatusChanged yöntemi
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d2560aa484c6965047b2fdaf2c539b8ab675bc8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207709"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="abde7-102">ICorDebugMutableDataTarget::ContinueStatusChanged yöntemi</span><span class="sxs-lookup"><span data-stu-id="abde7-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="abde7-103">Belirtilen iş parçacığı üzerinde bekleyen hata ayıklama olayı devamlılık durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="abde7-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abde7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abde7-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abde7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abde7-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="abde7-106">İşletim sistemi tarafından tanımlanan iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="abde7-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="abde7-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) yeni temsil eden değer istenen devamlılık durumu.</span><span class="sxs-lookup"><span data-stu-id="abde7-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abde7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abde7-108">Remarks</span></span>  
 <span data-ttu-id="abde7-109">Hata ayıklayıcı çağrıları `ContinueStatusChanged` Icordebug yöntemi, çağırdığında yöntemi içinde normalde işlenecek şekilde potansiyel olarak farklı şekilde ele alınması için geçerli hata ayıklama olayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="abde7-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="abde7-110">Örneğin, bekleyen bir istisna vardır ve özel durum iptal bir işlem hata ayıklayıcı isterse (gibi [Icordebugılframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) veya `FuncEval`), bu API, özel durum olmasını istemek için kullanılır iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="abde7-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abde7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abde7-111">Requirements</span></span>  
 <span data-ttu-id="abde7-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abde7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abde7-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abde7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abde7-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abde7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abde7-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abde7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abde7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="abde7-116">See Also</span></span>  
 [<span data-ttu-id="abde7-117">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abde7-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="abde7-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="abde7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
