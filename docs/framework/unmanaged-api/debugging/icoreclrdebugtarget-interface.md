---
title: ICoreClrDebugTarget Arabirimi
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: 83afe121b6bf0de3c5542695e38b6605db7a8b6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121824"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="7c9f1-102">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c9f1-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="7c9f1-103">Başvuru sayılarını denetleyen, işlem numaralandırmakta olan ve uzak bir Macintosh Silverlight hedefine bağlı bir hata ayıklayıcı ile ilişkili belleği serbest alan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c9f1-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c9f1-104">Syntax</span></span>  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7c9f1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7c9f1-105">Methods</span></span>  
  
|<span data-ttu-id="7c9f1-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7c9f1-106">Method</span></span>|<span data-ttu-id="7c9f1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c9f1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c9f1-108">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c9f1-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="7c9f1-109">Uzak bir bilgisayarda çalışan işlemi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7c9f1-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="7c9f1-110">ICoreClrDebugTarget::EnumRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c9f1-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="7c9f1-111">Uzak bilgisayardaki belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7c9f1-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="7c9f1-112">ICoreClrDebugTarget::FreeMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c9f1-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="7c9f1-113">Bu sınıftaki sabit listesi yöntemleriyle ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="7c9f1-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c9f1-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c9f1-114">Remarks</span></span>  
 <span data-ttu-id="7c9f1-115">Şu anda bu işlev yalnızca uzak bir Macintosh bilgisayarda çalışan Silverlight tabanlı bir uygulama hedefinde hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7c9f1-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9f1-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c9f1-116">Requirements</span></span>  
 <span data-ttu-id="7c9f1-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9f1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9f1-118">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="7c9f1-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7c9f1-119">**Kitaplık:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="7c9f1-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7c9f1-120">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="7c9f1-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9f1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c9f1-121">See also</span></span>

- [<span data-ttu-id="7c9f1-122">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c9f1-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="7c9f1-123">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c9f1-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="7c9f1-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7c9f1-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
