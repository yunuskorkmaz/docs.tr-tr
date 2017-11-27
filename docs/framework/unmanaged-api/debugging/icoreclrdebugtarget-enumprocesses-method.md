---
title: "ICoreClrDebugTarget::EnumProcesses Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumProcesses
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abdbf506505e9a49103a93ca2dc92bd805cfd509
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="7ceb9-102">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ceb9-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="7ceb9-103">Bir uzak bilgisayarda çalışan işlemler numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ceb9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ceb9-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ceb9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ceb9-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="7ceb9-106">[out] Döndürülen işlemlerin sayısı `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="7ceb9-107">Bu değer, 0 (sıfır) olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="7ceb9-108">[out] Bir dizi [Coreclrdebugprocınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) uzak bilgisayarda çalışan işlemler temsil eden yapılar.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ceb9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7ceb9-109">Return Value</span></span>  
 <span data-ttu-id="7ceb9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ceb9-110">S_OK</span></span>  
 <span data-ttu-id="7ceb9-111">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-111">Success.</span></span>  
  
 <span data-ttu-id="7ceb9-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7ceb9-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="7ceb9-113">İçin yeterli bellek ayrılamıyor `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="7ceb9-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="7ceb9-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7ceb9-115">Diğer hataları.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ceb9-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ceb9-116">Remarks</span></span>  
 <span data-ttu-id="7ceb9-117">Bu yöntem tarafından ayrılan belleği boşaltmak için çağrı [Icoreclrdebugtarget::freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ceb9-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ceb9-118">Requirements</span></span>  
 <span data-ttu-id="7ceb9-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ceb9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ceb9-120">**Başlık:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="7ceb9-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7ceb9-121">**Kitaplığı:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="7ceb9-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7ceb9-122">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7ceb9-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ceb9-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-123">See Also</span></span>  
 [<span data-ttu-id="7ceb9-124">Icoreclrdebugtarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ceb9-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
