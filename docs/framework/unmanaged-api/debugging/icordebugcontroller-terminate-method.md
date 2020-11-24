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
ms.openlocfilehash: 460aeeca9d62ce91a11a24d774c8e681ed4f00ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679812"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="e3522-102">ICorDebugController::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3522-102">ICorDebugController::Terminate Method</span></span>

<span data-ttu-id="e3522-103">Belirtilen çıkış koduyla işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e3522-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3522-104">Bu yöntem, Win32 işlevi için bir sarmalayıcıdır `TerminateProcess` .</span><span class="sxs-lookup"><span data-stu-id="e3522-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="e3522-105">Bu nedenle, `Terminate` çıkış kodunu Win32 `TerminateProcess` işlevinin kullandığı şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="e3522-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3522-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e3522-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3522-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3522-107">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="e3522-108">'ndaki Çıkış kodu olan sayısal bir değer.</span><span class="sxs-lookup"><span data-stu-id="e3522-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="e3522-109">Geçerli sayısal değerler Winbase. h içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e3522-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3522-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3522-110">Remarks</span></span>  

 <span data-ttu-id="e3522-111">İşlem `Terminate` çağrıldığında, hata ayıklayıcının [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) veya [ICorDebugManagedCallback:: exetppdomain](icordebugmanagedcallback-exitappdomain-method.md) geri çağırması aracılığıyla sonlandırma onayını alabilmesi için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) yöntemi kullanılarak işlem devam edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e3522-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3522-112">Bu yöntem bir uygulama etki alanı tarafından uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="e3522-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="e3522-113">Diğer bir deyişle, <xref:System.AppDomain> düzeyinde uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="e3522-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3522-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3522-114">Requirements</span></span>  

 <span data-ttu-id="e3522-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3522-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3522-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e3522-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3522-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e3522-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3522-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3522-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3522-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3522-119">See also</span></span>
