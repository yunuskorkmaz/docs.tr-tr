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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afb31646d21ec7e15f79601f5fe83ea6ce44fa90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134686"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="b6fb4-102">ICoreClrDebugTarget::EnumRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6fb4-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="b6fb4-103">Uzak bir bilgisayarda çalışan belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6fb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6fb4-104">Syntax</span></span>  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6fb4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6fb4-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="b6fb4-106">[in] Çalışma zamanları numaralandırmak kullanmak istediğiniz işlemi iç işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="b6fb4-107">Bu `m_dwInternalID` öğelerinden karşılık gelen [Coreclrdebugprocınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="b6fb4-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="b6fb4-108">[out] Döndürülen çalışma zamanları sayısını `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="b6fb4-109">Bu değer, 0 (sıfır) olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="b6fb4-110">[out] Bir dizi [Coreclrdebugruntimeınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) çalışma zamanları temsil eden yapılar uzak hedef işleminde yüklendi.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6fb4-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6fb4-111">Return Value</span></span>  
 <span data-ttu-id="b6fb4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6fb4-112">S_OK</span></span>  
 <span data-ttu-id="b6fb4-113">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-113">Success.</span></span>  
  
 <span data-ttu-id="b6fb4-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b6fb4-114">S_FALSE</span></span>  
 <span data-ttu-id="b6fb4-115">`dwInternalProcessID` işlemin sonlandırıldığından, bilgisayarda çalışan herhangi bir işlem büyük olasılıkla eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="b6fb4-116">`pcRuntimes` ve `ppRuntimes` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="b6fb4-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b6fb4-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b6fb4-118">Yeterli bellek ayrılamıyor `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="b6fb4-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="b6fb4-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b6fb4-120">Diğer hatalar.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6fb4-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6fb4-121">Remarks</span></span>  
 <span data-ttu-id="b6fb4-122">Bu yöntem tarafından ayrılmış olan belleği boşaltmak için çağrı [Icoreclrdebugtarget::freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6fb4-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6fb4-123">Requirements</span></span>  
 <span data-ttu-id="b6fb4-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6fb4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6fb4-125">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="b6fb4-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b6fb4-126">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b6fb4-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b6fb4-127">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b6fb4-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6fb4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-128">See also</span></span>

- [<span data-ttu-id="b6fb4-129">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6fb4-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
