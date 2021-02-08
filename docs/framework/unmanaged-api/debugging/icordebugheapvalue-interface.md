---
description: 'Bu konuda daha fazla bilgi edinin: ICorDebugHeapValue Arabirimi'
title: ICorDebugHeapValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: 7c65cbce530f0d1f00d8610031fb604a0118ee29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803691"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="773f2-103">ICorDebugHeapValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="773f2-103">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="773f2-104">Ortak dil çalışma zamanı (CLR) atık toplayıcısı tarafından toplanan bir nesneyi temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="773f2-104">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="773f2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="773f2-105">Methods</span></span>  
  
|<span data-ttu-id="773f2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="773f2-106">Method</span></span>|<span data-ttu-id="773f2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="773f2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="773f2-108">CreateRelocBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="773f2-108">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="773f2-109">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="773f2-109">Not implemented.</span></span>|  
|[<span data-ttu-id="773f2-110">IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="773f2-110">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="773f2-111">Tarafından temsil edilen nesnenin geçerli olup olmadığını `ICorDebugHeapValue` veya çöp toplayıcı tarafından geri kazanıldığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="773f2-111">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="773f2-112">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="773f2-112">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="773f2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="773f2-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="773f2-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="773f2-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="773f2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="773f2-115">Requirements</span></span>  

 <span data-ttu-id="773f2-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="773f2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="773f2-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="773f2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="773f2-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="773f2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="773f2-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="773f2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="773f2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="773f2-120">See also</span></span>

- [<span data-ttu-id="773f2-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="773f2-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
