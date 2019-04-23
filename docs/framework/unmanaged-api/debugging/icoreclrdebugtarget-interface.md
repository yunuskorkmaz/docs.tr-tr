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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2972b87b2d0136f182f8e8223988953e1896f2bd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183345"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="36f19-102">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36f19-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="36f19-103">Başvuru sayısı denetlemek, işlemleri numaralandırabilir ve bir uzak Macintosh Silverlight hedefine iliştirilmiş bir hata ayıklayıcı ile ilişkili belleği boşaltmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="36f19-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36f19-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="36f19-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="36f19-105">Methods</span></span>  
  
|<span data-ttu-id="36f19-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="36f19-106">Method</span></span>|<span data-ttu-id="36f19-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36f19-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36f19-108">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36f19-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="36f19-109">Uzak bir bilgisayarda çalışan işlemler numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="36f19-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="36f19-110">ICoreClrDebugTarget::EnumRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36f19-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="36f19-111">Uzak bir bilgisayarda belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="36f19-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="36f19-112">ICoreClrDebugTarget::FreeMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36f19-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="36f19-113">Bu sınıf numaralandırma yöntemleri tarafından ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="36f19-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36f19-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36f19-114">Remarks</span></span>  
 <span data-ttu-id="36f19-115">Bu işlevsellik şu anda yalnızca bir uzak Macintosh bilgisayarda çalışan bir Silverlight tabanlı uygulamanın hedef hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="36f19-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36f19-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36f19-116">Requirements</span></span>  
 <span data-ttu-id="36f19-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36f19-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36f19-118">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="36f19-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="36f19-119">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="36f19-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="36f19-120">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="36f19-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f19-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36f19-121">See also</span></span>

- [<span data-ttu-id="36f19-122">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36f19-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="36f19-123">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36f19-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="36f19-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="36f19-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
