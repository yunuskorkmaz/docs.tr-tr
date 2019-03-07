---
title: ICoreClrDebugTarget::EnumProcesses Yöntemi
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb7e64da5002f438198a8389d2d8385d7a4210a4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492718"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="3d729-102">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d729-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="3d729-103">Uzak bir bilgisayarda çalışan işlemler numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="3d729-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d729-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d729-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d729-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d729-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="3d729-106">[out] Döndürülen işlem sayısı `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="3d729-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="3d729-107">Bu değer, 0 (sıfır) olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d729-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="3d729-108">[out] Bir dizi [Coreclrdebugprocınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) uzak bilgisayarda çalışan işlemlere temsil eden yapılar.</span><span class="sxs-lookup"><span data-stu-id="3d729-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d729-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d729-109">Return Value</span></span>  
 <span data-ttu-id="3d729-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d729-110">S_OK</span></span>  
 <span data-ttu-id="3d729-111">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="3d729-111">Success.</span></span>  
  
 <span data-ttu-id="3d729-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3d729-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="3d729-113">Yeterli bellek ayrılamıyor `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="3d729-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="3d729-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="3d729-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="3d729-115">Diğer hatalar.</span><span class="sxs-lookup"><span data-stu-id="3d729-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d729-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d729-116">Remarks</span></span>  
 <span data-ttu-id="3d729-117">Bu yöntem tarafından ayrılmış olan belleği boşaltmak için çağrı [Icoreclrdebugtarget::freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3d729-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d729-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d729-118">Requirements</span></span>  
 <span data-ttu-id="3d729-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d729-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d729-120">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="3d729-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="3d729-121">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="3d729-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="3d729-122">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="3d729-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d729-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d729-123">See also</span></span>
- [<span data-ttu-id="3d729-124">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d729-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
