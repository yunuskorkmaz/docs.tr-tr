---
description: 'Daha fazla bilgi edinin: WAITORTIMERCALLBACK Işlev Işaretçisi'
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
ms.openlocfilehash: 6fd9e7eab56e48086eefcb26fc48cbf5f45d4a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679062"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="59d05-103">WAITORTIMERCALLBACK İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="59d05-103">WAITORTIMERCALLBACK Function Pointer</span></span>

<span data-ttu-id="59d05-104">Ana bilgisayarı bir bekleme tutamacının ( <xref:System.Threading.WaitHandle> ) sinyal ettiğini veya zaman aşımına uğradığını bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="59d05-104">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="59d05-105">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="59d05-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d05-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59d05-106">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59d05-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59d05-107">Parameters</span></span>  

 `lpParameter`  
 <span data-ttu-id="59d05-108">'ndaki Ana bilgisayar tarafından tanımlanan bilgileri içeren bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="59d05-108">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="59d05-109">[in] `true` bekleme işlemi zaman aşımına uğradı veya sinyal edildiyse `false` .</span><span class="sxs-lookup"><span data-stu-id="59d05-109">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59d05-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59d05-110">Remarks</span></span>  

 <span data-ttu-id="59d05-111">`WAITORTIMERCALLBACK`Noktaların bir geri çağırma işlevi olduğu ve barındırma uygulamasının yazarı tarafından uygulanması gereken işlev.</span><span class="sxs-lookup"><span data-stu-id="59d05-111">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59d05-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59d05-112">Requirements</span></span>  

 <span data-ttu-id="59d05-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59d05-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59d05-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="59d05-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59d05-115">**Kitaplık:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="59d05-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="59d05-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59d05-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d05-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59d05-117">See also</span></span>

- [<span data-ttu-id="59d05-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="59d05-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
