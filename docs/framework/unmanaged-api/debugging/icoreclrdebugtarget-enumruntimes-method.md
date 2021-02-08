---
description: 'Şu konuda daha fazla bilgi edinin: ıvreclrdebugtarget:: Enumbir yöntemi'
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
ms.openlocfilehash: 675747106b2acec2e8be3fcdf15831958bea7c7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794630"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="fc400-103">ICoreClrDebugTarget::EnumRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc400-103">ICoreClrDebugTarget::EnumRuntimes Method</span></span>

<span data-ttu-id="fc400-104">Uzak bir bilgisayarda çalışan belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="fc400-104">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc400-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc400-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc400-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc400-106">Parameters</span></span>  

 `dwInternalProcessID`  
 <span data-ttu-id="fc400-107">'ndaki Çalışma zamanlarını numaralandırmak istediğiniz işlemin iç işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fc400-107">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="fc400-108">Bu `m_dwInternalID` , karşılık gelen [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fc400-108">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="fc400-109">dışı İçinde döndürülen çalışma zamanlarının sayısı `ppRuntimes` .</span><span class="sxs-lookup"><span data-stu-id="fc400-109">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="fc400-110">Bu değer 0 (sıfır) olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc400-110">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="fc400-111">dışı Uzak hedef işlemde yüklü olan çalışma zamanlarını temsil eden [CoreCLR[gruntimeınfo](coreclrdebugruntimeinfo-structure.md) yapıtlarından oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="fc400-111">[out] An array of [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc400-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fc400-112">Return Value</span></span>  

 <span data-ttu-id="fc400-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc400-113">S_OK</span></span>  
 <span data-ttu-id="fc400-114">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="fc400-114">Success.</span></span>  
  
 <span data-ttu-id="fc400-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fc400-115">S_FALSE</span></span>  
 <span data-ttu-id="fc400-116">`dwInternalProcessID` , büyük olasılıkla işlem sonlandırıldığı için, bilgisayar üzerinde çalışan herhangi bir işlemle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="fc400-116">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="fc400-117">`pcRuntimes` ve `ppRuntimes` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fc400-117">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="fc400-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fc400-118">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="fc400-119">İçin yeterli bellek ayrılamıyor `ppRuntimes` .</span><span class="sxs-lookup"><span data-stu-id="fc400-119">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="fc400-120">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="fc400-120">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fc400-121">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="fc400-121">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc400-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc400-122">Remarks</span></span>  

 <span data-ttu-id="fc400-123">Bu yöntem tarafından ayrılan belleği boşaltmak için, [ıreclrdebugtarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="fc400-123">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc400-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc400-124">Requirements</span></span>  

 <span data-ttu-id="fc400-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc400-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc400-126">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="fc400-126">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="fc400-127">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="fc400-127">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="fc400-128">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="fc400-128">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc400-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc400-129">See also</span></span>

- [<span data-ttu-id="fc400-130">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc400-130">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
