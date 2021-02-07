---
description: 'Şu konuda daha fazla bilgi edinin: ICoreClrDebugTarget:: EnumProcesses yöntemi'
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
ms.openlocfilehash: 73dc8a2b00f7a57879855158e6b871117d015f3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738045"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="dd51b-103">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd51b-103">ICoreClrDebugTarget::EnumProcesses Method</span></span>

<span data-ttu-id="dd51b-104">Uzak bir bilgisayarda çalışan işlemi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="dd51b-104">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd51b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd51b-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd51b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd51b-106">Parameters</span></span>  

 `pcProcs`  
 <span data-ttu-id="dd51b-107">dışı İçinde döndürülen işlem sayısı `ppProcs` .</span><span class="sxs-lookup"><span data-stu-id="dd51b-107">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="dd51b-108">Bu değer 0 (sıfır) olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd51b-108">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="dd51b-109">dışı Uzak bilgisayarda çalışan süreçler temsil eden bir [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="dd51b-109">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd51b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dd51b-110">Return Value</span></span>  

 <span data-ttu-id="dd51b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd51b-111">S_OK</span></span>  
 <span data-ttu-id="dd51b-112">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="dd51b-112">Success.</span></span>  
  
 <span data-ttu-id="dd51b-113">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="dd51b-113">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="dd51b-114">İçin yeterli bellek ayrılamıyor `ppProcs` .</span><span class="sxs-lookup"><span data-stu-id="dd51b-114">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="dd51b-115">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="dd51b-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="dd51b-116">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="dd51b-116">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd51b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd51b-117">Remarks</span></span>  

 <span data-ttu-id="dd51b-118">Bu yöntem tarafından ayrılan belleği boşaltmak için, [ıreclrdebugtarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="dd51b-118">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd51b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd51b-119">Requirements</span></span>  

 <span data-ttu-id="dd51b-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd51b-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd51b-121">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="dd51b-121">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="dd51b-122">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="dd51b-122">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="dd51b-123">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="dd51b-123">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd51b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd51b-124">See also</span></span>

- [<span data-ttu-id="dd51b-125">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd51b-125">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
