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
ms.openlocfilehash: 0cc79c0a93fa4f05b8c793a8b7fb0b9b3f031b1a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791963"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="dfab9-102">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfab9-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="dfab9-103">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="dfab9-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfab9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfab9-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="dfab9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dfab9-105">Methods</span></span>  
  
|<span data-ttu-id="dfab9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dfab9-106">Method</span></span>|<span data-ttu-id="dfab9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfab9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfab9-108">ICorDebugRemote::CreateProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfab9-108">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="dfab9-109">Yönetilen hata ayıklama için uzak makinede bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dfab9-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="dfab9-110">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfab9-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="dfab9-111">Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="dfab9-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfab9-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfab9-112">Remarks</span></span>  
 <span data-ttu-id="dfab9-113">Şu anda bu işlev yalnızca uzak bir Macintosh makinesinde çalışan Silverlight tabanlı bir uygulama hedefinde hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dfab9-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfab9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfab9-114">Requirements</span></span>  
 <span data-ttu-id="dfab9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfab9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfab9-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dfab9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfab9-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dfab9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfab9-118">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="dfab9-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfab9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfab9-119">See also</span></span>

- [<span data-ttu-id="dfab9-120">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfab9-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="dfab9-121">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfab9-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="dfab9-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dfab9-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
