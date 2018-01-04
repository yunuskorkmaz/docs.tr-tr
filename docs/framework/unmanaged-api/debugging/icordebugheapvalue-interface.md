---
title: Icordebugheapvalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue
helpviewer_keywords: ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2ab132b73369526204f8fd811e1567b07b4a9b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue-interface1"></a><span data-ttu-id="704f8-102">Icordebugheapvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="704f8-102">ICorDebugHeapValue Interface1</span></span>
<span data-ttu-id="704f8-103">"Ortak dil çalışma zamanı (CLR) atık toplayıcısı tarafından toplanan nesneyi temsil eden Icordebugvalue" sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="704f8-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="704f8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="704f8-104">Methods</span></span>  
  
|<span data-ttu-id="704f8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="704f8-105">Method</span></span>|<span data-ttu-id="704f8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="704f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="704f8-107">CreateRelocBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="704f8-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="704f8-108">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="704f8-108">Not implemented.</span></span>|  
|[<span data-ttu-id="704f8-109">IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="704f8-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="704f8-110">Nesne bu tarafından temsil edilen olup olmadığını belirten bir değer alır `ICorDebugHeapValue` geçerli değil ya da atık toplayıcısı tarafından iadesi.</span><span class="sxs-lookup"><span data-stu-id="704f8-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="704f8-111">Bu yöntem .NET Framework sürüm 2.0 kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="704f8-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="704f8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="704f8-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="704f8-113">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="704f8-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="704f8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="704f8-114">Requirements</span></span>  
 <span data-ttu-id="704f8-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="704f8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="704f8-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="704f8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="704f8-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="704f8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="704f8-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="704f8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704f8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="704f8-119">See Also</span></span>  
    
    
    
 [<span data-ttu-id="704f8-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="704f8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
