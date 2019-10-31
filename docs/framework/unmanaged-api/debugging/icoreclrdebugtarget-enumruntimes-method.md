---
title: ICoreClrDebugTarget::EnumRuntimes Yöntemi
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
ms.openlocfilehash: 2579bed9ae432a2b9460c421c6ee5bdc40d1e149
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121832"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="934dd-102">ICoreClrDebugTarget::EnumRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="934dd-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="934dd-103">Uzak bir bilgisayarda çalışan belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="934dd-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="934dd-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="934dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="934dd-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="934dd-106">'ndaki Çalışma zamanlarını numaralandırmak istediğiniz işlemin iç işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="934dd-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="934dd-107">Bu, karşılık gelen [coreclrdebugprocınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)`m_dwInternalID` olacaktır.</span><span class="sxs-lookup"><span data-stu-id="934dd-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="934dd-108">dışı `ppRuntimes`döndürülen çalışma zamanlarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="934dd-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="934dd-109">Bu değer 0 (sıfır) olabilir.</span><span class="sxs-lookup"><span data-stu-id="934dd-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="934dd-110">dışı Uzak hedef işlemde yüklü olan çalışma zamanlarını temsil eden [CoreCLR[gruntimeınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) yapıtlarından oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="934dd-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="934dd-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="934dd-111">Return Value</span></span>  
 <span data-ttu-id="934dd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="934dd-112">S_OK</span></span>  
 <span data-ttu-id="934dd-113">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="934dd-113">Success.</span></span>  
  
 <span data-ttu-id="934dd-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="934dd-114">S_FALSE</span></span>  
 <span data-ttu-id="934dd-115">`dwInternalProcessID`, büyük olasılıkla işlem sonlandırıldığı için, bilgisayar üzerinde çalışan herhangi bir işlemle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="934dd-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="934dd-116">`pcRuntimes` ve `ppRuntimes` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="934dd-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="934dd-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="934dd-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="934dd-118">`ppRuntimes`için yeterli bellek ayrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="934dd-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="934dd-119">E_FAıL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="934dd-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="934dd-120">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="934dd-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="934dd-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="934dd-121">Remarks</span></span>  
 <span data-ttu-id="934dd-122">Bu yöntem tarafından ayrılan belleği boşaltmak için, [ıreclrdebugtarget:: FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="934dd-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934dd-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="934dd-123">Requirements</span></span>  
 <span data-ttu-id="934dd-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934dd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934dd-125">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="934dd-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="934dd-126">**Kitaplık:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="934dd-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="934dd-127">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="934dd-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934dd-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="934dd-128">See also</span></span>

- [<span data-ttu-id="934dd-129">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="934dd-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
