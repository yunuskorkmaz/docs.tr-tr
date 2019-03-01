---
title: ICorDebugStringValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cff85a77b113440c2274910cae8ef93419d1bc1b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965364"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="cf31d-102">ICorDebugStringValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf31d-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="cf31d-103">Dize değerlerine uygulanan Icordebugheapvalue öğesinin.</span><span class="sxs-lookup"><span data-stu-id="cf31d-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf31d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cf31d-104">Methods</span></span>  
  
|<span data-ttu-id="cf31d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cf31d-105">Method</span></span>|<span data-ttu-id="cf31d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf31d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf31d-107">GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf31d-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="cf31d-108">Bu tarafından başvurulan dizedeki karakter sayısını alır `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="cf31d-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="cf31d-109">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf31d-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="cf31d-110">Bu tarafından başvurulan dize alır `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="cf31d-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf31d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf31d-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf31d-112">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cf31d-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf31d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf31d-113">Requirements</span></span>  
 <span data-ttu-id="cf31d-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf31d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf31d-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf31d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf31d-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf31d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf31d-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf31d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf31d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf31d-118">See also</span></span>
- [<span data-ttu-id="cf31d-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cf31d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
