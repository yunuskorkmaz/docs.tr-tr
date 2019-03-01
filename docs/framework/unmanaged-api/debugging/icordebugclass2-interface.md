---
title: ICorDebugClass2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46358a66d79030aeea42c75827f05cf07fa925ea
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967756"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="e95dd-102">ICorDebugClass2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95dd-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="e95dd-103">Genel bir sınıf veya türündeki bir yöntem parametresi olan bir sınıfı temsil eden <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="e95dd-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="e95dd-104">Bu arabirim genişletir [Icordebugclass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e95dd-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e95dd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e95dd-105">Methods</span></span>  
  
|<span data-ttu-id="e95dd-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e95dd-106">Method</span></span>|<span data-ttu-id="e95dd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e95dd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e95dd-108">GetParameterizedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e95dd-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="e95dd-109">Bu sınıf türü bildirimi alır.</span><span class="sxs-lookup"><span data-stu-id="e95dd-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="e95dd-110">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e95dd-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="e95dd-111">Bu sınıfın her yöntemi için yöntem kullanıcı tarafından tanımlanan kod olup olmadığını gösteren bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e95dd-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e95dd-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e95dd-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e95dd-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e95dd-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e95dd-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e95dd-114">Requirements</span></span>  
 <span data-ttu-id="e95dd-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e95dd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e95dd-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e95dd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e95dd-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e95dd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e95dd-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e95dd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95dd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e95dd-119">See also</span></span>
- [<span data-ttu-id="e95dd-120">Icordebugclass arabirimi</span><span class="sxs-lookup"><span data-stu-id="e95dd-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="e95dd-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e95dd-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
