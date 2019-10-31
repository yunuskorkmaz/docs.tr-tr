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
ms.openlocfilehash: d1d3a5eb6e0b24b40a35c13a99465dd3c7032a91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138951"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="40669-102">ICorDebugStringValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40669-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="40669-103">Dize değerlerine uygulanan ICorDebugHeapValue öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="40669-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40669-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="40669-104">Methods</span></span>  
  
|<span data-ttu-id="40669-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="40669-105">Method</span></span>|<span data-ttu-id="40669-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40669-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40669-107">GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40669-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="40669-108">Bu `ICorDebugStringValue`başvurduğu dizedeki karakter sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="40669-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="40669-109">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40669-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="40669-110">Bu `ICorDebugStringValue`başvurulan dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="40669-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40669-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40669-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40669-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="40669-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40669-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40669-113">Requirements</span></span>  
 <span data-ttu-id="40669-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40669-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40669-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40669-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40669-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="40669-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40669-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40669-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40669-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40669-118">See also</span></span>

- [<span data-ttu-id="40669-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40669-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
