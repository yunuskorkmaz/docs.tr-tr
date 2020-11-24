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
ms.openlocfilehash: 093f49508e8e96a4003f1aab8eed59e2fd196ba9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679279"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="faa4e-102">ICoreClrDebugTarget::EnumRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="faa4e-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>

<span data-ttu-id="faa4e-103">Uzak bir bilgisayarda çalışan belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="faa4e-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa4e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="faa4e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="faa4e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="faa4e-105">Parameters</span></span>  

 `dwInternalProcessID`  
 <span data-ttu-id="faa4e-106">'ndaki Çalışma zamanlarını numaralandırmak istediğiniz işlemin iç işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="faa4e-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="faa4e-107">Bu `m_dwInternalID` , karşılık gelen [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)olacaktır.</span><span class="sxs-lookup"><span data-stu-id="faa4e-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="faa4e-108">dışı İçinde döndürülen çalışma zamanlarının sayısı `ppRuntimes` .</span><span class="sxs-lookup"><span data-stu-id="faa4e-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="faa4e-109">Bu değer 0 (sıfır) olabilir.</span><span class="sxs-lookup"><span data-stu-id="faa4e-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="faa4e-110">dışı Uzak hedef işlemde yüklü olan çalışma zamanlarını temsil eden [CoreCLR[gruntimeınfo](coreclrdebugruntimeinfo-structure.md) yapıtlarından oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="faa4e-110">[out] An array of [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faa4e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="faa4e-111">Return Value</span></span>  

 <span data-ttu-id="faa4e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="faa4e-112">S_OK</span></span>  
 <span data-ttu-id="faa4e-113">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="faa4e-113">Success.</span></span>  
  
 <span data-ttu-id="faa4e-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="faa4e-114">S_FALSE</span></span>  
 <span data-ttu-id="faa4e-115">`dwInternalProcessID` , büyük olasılıkla işlem sonlandırıldığı için, bilgisayar üzerinde çalışan herhangi bir işlemle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="faa4e-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="faa4e-116">`pcRuntimes` ve `ppRuntimes` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="faa4e-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="faa4e-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="faa4e-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="faa4e-118">İçin yeterli bellek ayrılamıyor `ppRuntimes` .</span><span class="sxs-lookup"><span data-stu-id="faa4e-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="faa4e-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="faa4e-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="faa4e-120">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="faa4e-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faa4e-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="faa4e-121">Remarks</span></span>  

 <span data-ttu-id="faa4e-122">Bu yöntem tarafından ayrılan belleği boşaltmak için, [ıreclrdebugtarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="faa4e-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faa4e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="faa4e-123">Requirements</span></span>  

 <span data-ttu-id="faa4e-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa4e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa4e-125">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="faa4e-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="faa4e-126">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="faa4e-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="faa4e-127">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="faa4e-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa4e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faa4e-128">See also</span></span>

- [<span data-ttu-id="faa4e-129">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="faa4e-129">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
