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
ms.openlocfilehash: 1cfaf886d09d843f4dbf61af55a9388454b050ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957421"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="fe277-102">ICorDebugStringValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe277-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="fe277-103">Dize değerlerine uygulanan ICorDebugHeapValue öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fe277-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe277-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fe277-104">Methods</span></span>  
  
|<span data-ttu-id="fe277-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe277-105">Method</span></span>|<span data-ttu-id="fe277-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe277-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe277-107">GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe277-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="fe277-108">Bu `ICorDebugStringValue`tarafından başvurulan dizedeki karakter sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fe277-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="fe277-109">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe277-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="fe277-110">Bu `ICorDebugStringValue`tarafından başvurulan dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="fe277-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe277-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe277-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe277-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="fe277-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe277-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe277-113">Requirements</span></span>  
 <span data-ttu-id="fe277-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe277-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe277-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fe277-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe277-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe277-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe277-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe277-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe277-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe277-118">See also</span></span>

- [<span data-ttu-id="fe277-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe277-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
