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
ms.openlocfilehash: cd6c5726b9a938d04cf4eb018ec9851c81d9c745
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697070"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="9eb79-102">ICorDebugStringValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9eb79-102">ICorDebugStringValue Interface</span></span>

<span data-ttu-id="9eb79-103">Dize değerlerine uygulanan ICorDebugHeapValue öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9eb79-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9eb79-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9eb79-104">Methods</span></span>  
  
|<span data-ttu-id="9eb79-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9eb79-105">Method</span></span>|<span data-ttu-id="9eb79-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9eb79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9eb79-107">GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9eb79-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="9eb79-108">Bu tarafından başvurulan dizedeki karakter sayısını alır `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="9eb79-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="9eb79-109">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9eb79-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="9eb79-110">Bu tarafından başvurulan dizeyi alır `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="9eb79-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eb79-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9eb79-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9eb79-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="9eb79-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eb79-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9eb79-113">Requirements</span></span>  

 <span data-ttu-id="9eb79-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eb79-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eb79-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9eb79-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eb79-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9eb79-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eb79-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eb79-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb79-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9eb79-118">See also</span></span>

- [<span data-ttu-id="9eb79-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9eb79-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
