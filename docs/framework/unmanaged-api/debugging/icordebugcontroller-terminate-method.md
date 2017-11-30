---
title: "ICorDebugController::Terminate Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Terminate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb3831e2640de8ad34299695b571cb4071974bd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="31bbf-102">ICorDebugController::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31bbf-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="31bbf-103">Belirtilen çıkış kodu ile işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="31bbf-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31bbf-104">Win32 için sarmalayıcı bu yöntemdir `TerminateProcess` işlevi.</span><span class="sxs-lookup"><span data-stu-id="31bbf-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="31bbf-105">Bu nedenle, `Terminate` aynı çıkış kodunu kullanır biçimi Win32 `TerminateProcess` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="31bbf-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31bbf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31bbf-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31bbf-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31bbf-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="31bbf-108">[in] Çıkış kodu sayısal bir değer.</span><span class="sxs-lookup"><span data-stu-id="31bbf-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="31bbf-109">Geçerli sayısal değerleri Winbase.h tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="31bbf-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31bbf-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31bbf-110">Remarks</span></span>  
 <span data-ttu-id="31bbf-111">İşlem zaman durdurulursa `Terminate` olduğu adlı işlemi kullanarak devam [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi hata ayıklayıcı sonlandırma onayı alması [ Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) veya [Icordebugmanagedcallback::exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="31bbf-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31bbf-112">Bu yöntem, bir uygulama etki alanı tarafından uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="31bbf-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="31bbf-113">Diğer bir deyişle, bu anda uygulanmadı <xref:System.AppDomain> düzeyi.</span><span class="sxs-lookup"><span data-stu-id="31bbf-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31bbf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31bbf-114">Requirements</span></span>  
 <span data-ttu-id="31bbf-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31bbf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31bbf-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31bbf-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31bbf-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31bbf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31bbf-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31bbf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31bbf-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31bbf-119">See Also</span></span>  
 
