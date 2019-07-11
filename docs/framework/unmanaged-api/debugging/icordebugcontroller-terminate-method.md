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
ms.openlocfilehash: 06c91a813a80af5cf09914ca134ac9935ed787c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750065"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="2b466-102">ICorDebugController::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b466-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="2b466-103">Belirtilen çıkış kodu ile işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="2b466-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b466-104">Bu yöntem Win32 için bir sarmalayıcı olan `TerminateProcess` işlevi.</span><span class="sxs-lookup"><span data-stu-id="2b466-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="2b466-105">Bu nedenle, `Terminate` aynı çıkış kodunu kullanır biçimi Win32 `TerminateProcess` işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b466-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b466-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b466-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b466-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b466-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="2b466-108">[in] Çıkış kodu sayısal bir değer.</span><span class="sxs-lookup"><span data-stu-id="2b466-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="2b466-109">Geçerli bir sayısal değerler Winbase.h içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2b466-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b466-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b466-110">Remarks</span></span>  
 <span data-ttu-id="2b466-111">İşlemin ne zaman durdurulursa `Terminate` olan adlı işlemi kullanarak devam [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi hata ayıklayıcı sonlandırma onayı alması [ Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) veya [Icordebugmanagedcallback::exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="2b466-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b466-112">Bu yöntem, bir uygulama etki alanına göre uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="2b466-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="2b466-113">Diğer bir deyişle, bu anda uygulanmadı <xref:System.AppDomain> düzeyi.</span><span class="sxs-lookup"><span data-stu-id="2b466-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b466-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b466-114">Requirements</span></span>  
 <span data-ttu-id="2b466-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b466-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b466-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b466-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b466-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b466-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b466-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b466-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b466-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b466-119">See also</span></span>
