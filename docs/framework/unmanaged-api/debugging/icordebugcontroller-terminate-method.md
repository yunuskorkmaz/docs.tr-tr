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
ms.openlocfilehash: 851a127c117b826c271dd021c41cfdb36045a1ff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783748"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="b684c-102">ICorDebugController::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b684c-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="b684c-103">Belirtilen çıkış koduyla işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="b684c-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b684c-104">Bu yöntem, Win32 `TerminateProcess` işlevi için bir sarmalayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="b684c-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="b684c-105">Bu nedenle `Terminate`, Win32 `TerminateProcess` işlevi tarafından kullanılan aynı şekilde çıkış kodunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="b684c-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b684c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b684c-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b684c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b684c-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="b684c-108">'ndaki Çıkış kodu olan sayısal bir değer.</span><span class="sxs-lookup"><span data-stu-id="b684c-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="b684c-109">Geçerli sayısal değerler Winbase. h içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b684c-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b684c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b684c-110">Remarks</span></span>  
 <span data-ttu-id="b684c-111">`Terminate` çağrıldığında işlem durdurulmuşsa, hata ayıklayıcının [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) veya [ICorDebugManagedCallback:: Exetppdomain](icordebugmanagedcallback-exitappdomain-method.md) geri çağırması aracılığıyla sonlandırmanın onayını alabilmesi Için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) yöntemi kullanılarak devam edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b684c-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b684c-112">Bu yöntem bir uygulama etki alanı tarafından uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="b684c-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="b684c-113">Diğer bir deyişle, <xref:System.AppDomain> düzeyinde uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="b684c-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b684c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b684c-114">Requirements</span></span>  
 <span data-ttu-id="b684c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b684c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b684c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b684c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b684c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b684c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b684c-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b684c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b684c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b684c-119">See also</span></span>
