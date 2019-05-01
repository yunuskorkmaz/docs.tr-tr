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
ms.openlocfilehash: 6709b14ce8e7bc131f9feb7a277fb41851ee4352
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994272"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="f7c53-102">ICorDebugStringValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7c53-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="f7c53-103">Dize değerlerine uygulanan Icordebugheapvalue öğesinin.</span><span class="sxs-lookup"><span data-stu-id="f7c53-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7c53-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f7c53-104">Methods</span></span>  
  
|<span data-ttu-id="f7c53-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f7c53-105">Method</span></span>|<span data-ttu-id="f7c53-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7c53-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7c53-107">GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7c53-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="f7c53-108">Bu tarafından başvurulan dizedeki karakter sayısını alır `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="f7c53-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="f7c53-109">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7c53-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="f7c53-110">Bu tarafından başvurulan dize alır `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="f7c53-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7c53-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7c53-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7c53-112">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f7c53-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7c53-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7c53-113">Requirements</span></span>  
 <span data-ttu-id="f7c53-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7c53-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c53-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7c53-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7c53-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7c53-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7c53-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c53-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c53-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7c53-118">See also</span></span>

- [<span data-ttu-id="f7c53-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f7c53-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
