---
title: ICorDebugRemote Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a50a799c625c647aa275994bc92738b8a4267eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782726"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="85fb2-102">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85fb2-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="85fb2-103">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="85fb2-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85fb2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85fb2-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="85fb2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="85fb2-105">Methods</span></span>  
  
|<span data-ttu-id="85fb2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="85fb2-106">Method</span></span>|<span data-ttu-id="85fb2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85fb2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85fb2-108">ICorDebugRemote::CreateProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85fb2-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="85fb2-109">Yönetilen hata ayıklama uzak makinede bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85fb2-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="85fb2-110">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85fb2-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="85fb2-111">Hata ayıklayıcısı altında uzak bir makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="85fb2-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85fb2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85fb2-112">Remarks</span></span>  
 <span data-ttu-id="85fb2-113">Bu işlevsellik şu anda yalnızca hata ayıklama uzak Macintosh makinede çalışan Silverlight tabanlı uygulamanın hedef desteklenir.</span><span class="sxs-lookup"><span data-stu-id="85fb2-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85fb2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85fb2-114">Requirements</span></span>  
 <span data-ttu-id="85fb2-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85fb2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85fb2-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85fb2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85fb2-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85fb2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85fb2-118">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="85fb2-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85fb2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85fb2-119">See also</span></span>

- [<span data-ttu-id="85fb2-120">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85fb2-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="85fb2-121">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85fb2-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="85fb2-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="85fb2-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
