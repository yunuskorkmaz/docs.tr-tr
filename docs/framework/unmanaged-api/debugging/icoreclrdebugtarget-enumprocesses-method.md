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
ms.openlocfilehash: 6484832e8e737b9a0d0b3eaf3ede4078729f7a4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178435"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="3bd51-102">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3bd51-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="3bd51-103">Uzak bir bilgisayarda çalışan işlemleri sayısalhale eder.</span><span class="sxs-lookup"><span data-stu-id="3bd51-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bd51-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bd51-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bd51-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3bd51-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="3bd51-106">[çıkış] Döndürülen işlem `ppProcs`sayısı.</span><span class="sxs-lookup"><span data-stu-id="3bd51-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="3bd51-107">Bu değer 0 (sıfır) olabilir.</span><span class="sxs-lookup"><span data-stu-id="3bd51-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="3bd51-108">[çıkış] Uzak bilgisayarda çalışan işlemleri temsil eden bir dizi [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="3bd51-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3bd51-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3bd51-109">Return Value</span></span>  
 <span data-ttu-id="3bd51-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3bd51-110">S_OK</span></span>  
 <span data-ttu-id="3bd51-111">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="3bd51-111">Success.</span></span>  
  
 <span data-ttu-id="3bd51-112">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="3bd51-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="3bd51-113">`ppProcs`'ye yeterli bellek ayrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="3bd51-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="3bd51-114">E_FAIL (veya diğer E_ iade kodları)</span><span class="sxs-lookup"><span data-stu-id="3bd51-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="3bd51-115">Diğer başarısızlıklar.</span><span class="sxs-lookup"><span data-stu-id="3bd51-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bd51-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bd51-116">Remarks</span></span>  
 <span data-ttu-id="3bd51-117">Bu yöntemle ayrılan belleği serbest etmek için [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) yöntemini arayın.</span><span class="sxs-lookup"><span data-stu-id="3bd51-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bd51-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bd51-118">Requirements</span></span>  
 <span data-ttu-id="3bd51-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bd51-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bd51-120">**Üstbilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="3bd51-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="3bd51-121">**Kütüphane:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="3bd51-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="3bd51-122">**.NET Çerçeve Sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="3bd51-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bd51-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bd51-123">See also</span></span>

- [<span data-ttu-id="3bd51-124">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bd51-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
