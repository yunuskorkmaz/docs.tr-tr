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
ms.openlocfilehash: 0c1b18f24fd30b5f6d5e85633fc0c25839aba6df
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396414"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="1657e-102">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1657e-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="1657e-103">Uzak bir bilgisayarda çalışan işlemi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1657e-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1657e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1657e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1657e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1657e-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="1657e-106">dışı İçinde döndürülen işlem sayısı `ppProcs` .</span><span class="sxs-lookup"><span data-stu-id="1657e-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="1657e-107">Bu değer 0 (sıfır) olabilir.</span><span class="sxs-lookup"><span data-stu-id="1657e-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="1657e-108">dışı Uzak bilgisayarda çalışan süreçler temsil eden bir [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="1657e-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1657e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1657e-109">Return Value</span></span>  
 <span data-ttu-id="1657e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1657e-110">S_OK</span></span>  
 <span data-ttu-id="1657e-111">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="1657e-111">Success.</span></span>  
  
 <span data-ttu-id="1657e-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1657e-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="1657e-113">İçin yeterli bellek ayrılamıyor `ppProcs` .</span><span class="sxs-lookup"><span data-stu-id="1657e-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="1657e-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="1657e-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="1657e-115">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="1657e-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1657e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1657e-116">Remarks</span></span>  
 <span data-ttu-id="1657e-117">Bu yöntem tarafından ayrılan belleği boşaltmak için, [ıreclrdebugtarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="1657e-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1657e-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1657e-118">Requirements</span></span>  
 <span data-ttu-id="1657e-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1657e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1657e-120">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="1657e-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="1657e-121">**Kitaplık:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="1657e-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="1657e-122">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="1657e-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1657e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1657e-123">See also</span></span>

- [<span data-ttu-id="1657e-124">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1657e-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
