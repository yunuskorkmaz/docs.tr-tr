---
title: IGCHost::SetGCStartupLimits Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 3b0c11ac9d827bd252018172e2337df653054a7b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805209"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="1e251-102">IGCHost::SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e251-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="1e251-103">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1e251-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1e251-104">4,5 .NET Framework başlayarak, segment boyutunu ve en fazla nesil 0 boyutunu `DWORD` [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak daha büyük değerlere ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e251-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e251-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1e251-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e251-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e251-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="1e251-107">'ndaki Çöp toplama sistemi tarafından kullanılan segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="1e251-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="1e251-108">'ndaki 0 üretimi için en büyük boyut.</span><span class="sxs-lookup"><span data-stu-id="1e251-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e251-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e251-109">Remarks</span></span>  
 <span data-ttu-id="1e251-110">`SetGCStartupLimits`Yöntemi yalnızca bir kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e251-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="1e251-111">Bu değerler daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1e251-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e251-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e251-112">Requirements</span></span>  
 <span data-ttu-id="1e251-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e251-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e251-114">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="1e251-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1e251-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1e251-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e251-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e251-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e251-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e251-117">See also</span></span>

- [<span data-ttu-id="1e251-118">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e251-118">IGCHost Interface</span></span>](igchost-interface.md)
