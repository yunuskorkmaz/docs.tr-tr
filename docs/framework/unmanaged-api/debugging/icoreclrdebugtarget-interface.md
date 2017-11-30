---
title: ICoreClrDebugTarget Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e13355078727a55c950bed795d3b01b6c7d52564
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="87f23-102">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87f23-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="87f23-103">Başvuru sayıları denetlemek, işlemleri numaralandıran ve bir uzak Macintosh Silverlight hedefe bağlı bir hata ayıklayıcısı ile ilişkili belleği serbest yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="87f23-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f23-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87f23-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="87f23-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="87f23-105">Methods</span></span>  
  
|<span data-ttu-id="87f23-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="87f23-106">Method</span></span>|<span data-ttu-id="87f23-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87f23-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87f23-108">Icoreclrdebugtarget::enumprocesses yöntemi</span><span class="sxs-lookup"><span data-stu-id="87f23-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="87f23-109">Bir uzak bilgisayarda çalışan işlemler numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="87f23-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="87f23-110">Icoreclrdebugtarget::enumruntimes yöntemi</span><span class="sxs-lookup"><span data-stu-id="87f23-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="87f23-111">Ortak dil çalışma zamanları (CLRs), uzak bir bilgisayarda belirtilen işlemde numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="87f23-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="87f23-112">Icoreclrdebugtarget::freememory yöntemi</span><span class="sxs-lookup"><span data-stu-id="87f23-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="87f23-113">Bu sınıf numaralandırma yöntemleri tarafından ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="87f23-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87f23-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87f23-114">Remarks</span></span>  
 <span data-ttu-id="87f23-115">Şu anda bu işlevsellik yalnızca bir uzak Macintosh bilgisayarda çalışan Silverlight tabanlı uygulamaya hedef hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="87f23-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f23-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87f23-116">Requirements</span></span>  
 <span data-ttu-id="87f23-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87f23-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87f23-118">**Başlık:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="87f23-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="87f23-119">**Kitaplığı:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="87f23-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="87f23-120">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="87f23-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f23-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87f23-121">See Also</span></span>  
 [<span data-ttu-id="87f23-122">Icordebugremotetarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="87f23-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="87f23-123">Icordebug arabirimi</span><span class="sxs-lookup"><span data-stu-id="87f23-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="87f23-124">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="87f23-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
