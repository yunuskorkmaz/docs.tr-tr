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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee1c30809567097e67b6b1e40f5534429d748abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964363"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="35bd2-102">ICorDebugController::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35bd2-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="35bd2-103">Belirtilen çıkış koduyla işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="35bd2-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35bd2-104">Bu yöntem, Win32 `TerminateProcess` işlevi için bir sarmalayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="35bd2-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="35bd2-105">Bu nedenle `Terminate` , çıkış kodunu Win32 `TerminateProcess` işlevinin kullandığı şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="35bd2-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35bd2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35bd2-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35bd2-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35bd2-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="35bd2-108">'ndaki Çıkış kodu olan sayısal bir değer.</span><span class="sxs-lookup"><span data-stu-id="35bd2-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="35bd2-109">Geçerli sayısal değerler Winbase. h içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="35bd2-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35bd2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35bd2-110">Remarks</span></span>  
 <span data-ttu-id="35bd2-111">İşlem `Terminate` çağrıldığında, işlem hata ayıklayıcının ICorDebugManagedCallback aracılığıyla sonlandırmanın onayını alabilmesi için [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi kullanılarak devam edilmelidir [:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) veya [ICorDebugManagedCallback:: Exbir ppdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="35bd2-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35bd2-112">Bu yöntem bir uygulama etki alanı tarafından uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="35bd2-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="35bd2-113">Diğer bir deyişle, <xref:System.AppDomain> düzeyinde uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="35bd2-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35bd2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35bd2-114">Requirements</span></span>  
 <span data-ttu-id="35bd2-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35bd2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35bd2-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35bd2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35bd2-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="35bd2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35bd2-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35bd2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35bd2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35bd2-119">See also</span></span>
