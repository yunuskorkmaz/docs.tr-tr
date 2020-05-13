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
ms.openlocfilehash: 5537a48fd085ce98de855fa1ec0913e2637e58e0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376189"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="caba9-102">ICorDebugStringValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="caba9-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="caba9-103">Dize değerlerine uygulanan ICorDebugHeapValue öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="caba9-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="caba9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="caba9-104">Methods</span></span>  
  
|<span data-ttu-id="caba9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="caba9-105">Method</span></span>|<span data-ttu-id="caba9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="caba9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="caba9-107">GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="caba9-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="caba9-108">Bu tarafından başvurulan dizedeki karakter sayısını alır `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="caba9-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="caba9-109">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="caba9-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="caba9-110">Bu tarafından başvurulan dizeyi alır `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="caba9-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caba9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="caba9-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="caba9-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="caba9-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caba9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="caba9-113">Requirements</span></span>  
 <span data-ttu-id="caba9-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caba9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caba9-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="caba9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="caba9-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="caba9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caba9-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caba9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caba9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="caba9-118">See also</span></span>

- [<span data-ttu-id="caba9-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="caba9-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
