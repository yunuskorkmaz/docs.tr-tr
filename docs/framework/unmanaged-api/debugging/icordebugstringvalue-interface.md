---
description: ': ICorDebugStringValue arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b4e762d8c0a62c1b76b59364e9d29c4b8d2386fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717337"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="4111d-103">ICorDebugStringValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4111d-103">ICorDebugStringValue Interface</span></span>

<span data-ttu-id="4111d-104">Dize değerlerine uygulanan ICorDebugHeapValue öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4111d-104">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4111d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4111d-105">Methods</span></span>  
  
|<span data-ttu-id="4111d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4111d-106">Method</span></span>|<span data-ttu-id="4111d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4111d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4111d-108">GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4111d-108">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="4111d-109">Bu tarafından başvurulan dizedeki karakter sayısını alır `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="4111d-109">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="4111d-110">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4111d-110">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="4111d-111">Bu tarafından başvurulan dizeyi alır `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="4111d-111">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4111d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4111d-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4111d-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4111d-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4111d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4111d-114">Requirements</span></span>  

 <span data-ttu-id="4111d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4111d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4111d-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4111d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4111d-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4111d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4111d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4111d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4111d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4111d-119">See also</span></span>

- [<span data-ttu-id="4111d-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4111d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
