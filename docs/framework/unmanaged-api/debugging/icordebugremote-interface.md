---
title: ICorDebugRemote Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cc34c3a1049a24a27fae4d13288efbd5a98a4dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="d3429-102">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3429-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="d3429-103">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3429-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3429-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3429-104">Syntax</span></span>  
  
```  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d3429-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3429-105">Methods</span></span>  
  
|<span data-ttu-id="d3429-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d3429-106">Method</span></span>|<span data-ttu-id="d3429-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3429-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3429-108">ICorDebugRemote::CreateProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3429-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="d3429-109">Yönetilen hata ayıklama için bir işlemi uzak makinede oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3429-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="d3429-110">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3429-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="d3429-111">Hata ayıklayıcı altında uzaktaki bir makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="d3429-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3429-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3429-112">Remarks</span></span>  
 <span data-ttu-id="d3429-113">Şu anda bu işlevsellik yalnızca bir uzak Macintosh makine üzerinde çalışan Silverlight tabanlı uygulamaya hedef hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d3429-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3429-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3429-114">Requirements</span></span>  
 <span data-ttu-id="d3429-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3429-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3429-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3429-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3429-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3429-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3429-118">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d3429-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3429-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3429-119">See Also</span></span>  
 [<span data-ttu-id="d3429-120">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3429-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="d3429-121">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3429-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="d3429-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3429-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
