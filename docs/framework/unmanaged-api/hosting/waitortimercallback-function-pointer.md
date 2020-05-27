---
title: WAITORTIMERCALLBACK İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: ee5dd611888ec52e360ef45fab4c01e9c5b2d6bb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009460"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="5fd8c-102">WAITORTIMERCALLBACK İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="5fd8c-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="5fd8c-103">Ana bilgisayarı bir bekleme tutamacının ( <xref:System.Threading.WaitHandle> ) sinyal ettiğini veya zaman aşımına uğradığını bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="5fd8c-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="5fd8c-104">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5fd8c-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fd8c-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5fd8c-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fd8c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5fd8c-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="5fd8c-107">'ndaki Ana bilgisayar tarafından tanımlanan bilgileri içeren bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5fd8c-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="5fd8c-108">[in] `true` bekleme işlemi zaman aşımına uğradı veya sinyal edildiyse `false` .</span><span class="sxs-lookup"><span data-stu-id="5fd8c-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fd8c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fd8c-109">Remarks</span></span>  
 <span data-ttu-id="5fd8c-110">`WAITORTIMERCALLBACK`Noktaların bir geri çağırma işlevi olduğu ve barındırma uygulamasının yazarı tarafından uygulanması gereken işlev.</span><span class="sxs-lookup"><span data-stu-id="5fd8c-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fd8c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fd8c-111">Requirements</span></span>  
 <span data-ttu-id="5fd8c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fd8c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fd8c-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5fd8c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5fd8c-114">**Kitaplık:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="5fd8c-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="5fd8c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fd8c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fd8c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fd8c-116">See also</span></span>

- [<span data-ttu-id="5fd8c-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5fd8c-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
