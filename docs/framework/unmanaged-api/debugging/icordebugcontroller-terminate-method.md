---
title: ICorDebugController::Terminate Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: fb8cfb2d1c5902ecd0d5858ef21ba48b65b12506
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125329"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="2f1f9-102">ICorDebugController::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f1f9-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="2f1f9-103">Belirtilen çıkış koduyla işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="2f1f9-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f1f9-104">Bu yöntem, Win32 `TerminateProcess` işlevi için bir sarmalayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2f1f9-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="2f1f9-105">Bu nedenle `Terminate`, Win32 `TerminateProcess` işlevi tarafından kullanılan aynı şekilde çıkış kodunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f1f9-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f1f9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f1f9-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f1f9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f1f9-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="2f1f9-108">'ndaki Çıkış kodu olan sayısal bir değer.</span><span class="sxs-lookup"><span data-stu-id="2f1f9-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="2f1f9-109">Geçerli sayısal değerler Winbase. h içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2f1f9-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f1f9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f1f9-110">Remarks</span></span>  
 <span data-ttu-id="2f1f9-111">`Terminate` çağrıldığında işlem durdurulmuşsa, hata ayıklayıcının ICorDebugManagedCallback aracılığıyla sonlandırmanın onayını alabilmesi için [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi kullanılarak devam edilmelidir [:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) veya [ICorDebugManagedCallback:: Exbir ppdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="2f1f9-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f1f9-112">Bu yöntem bir uygulama etki alanı tarafından uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="2f1f9-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="2f1f9-113">Diğer bir deyişle, <xref:System.AppDomain> düzeyinde uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="2f1f9-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f1f9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f1f9-114">Requirements</span></span>  
 <span data-ttu-id="2f1f9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f1f9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f1f9-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f1f9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f1f9-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2f1f9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f1f9-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f1f9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f1f9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f1f9-119">See also</span></span>
