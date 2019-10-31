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
ms.openlocfilehash: cb2ab28824d209dd1eed627600e30e9ddb0d7c7a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125719"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="b87a7-102">ICorDebugClass2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b87a7-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="b87a7-103">Bir genel sınıfı veya <xref:System.Type>türünde bir yöntem parametresi olan bir sınıfı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b87a7-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="b87a7-104">Bu arabirim [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)'ı genişletir.</span><span class="sxs-lookup"><span data-stu-id="b87a7-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b87a7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b87a7-105">Methods</span></span>  
  
|<span data-ttu-id="b87a7-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b87a7-106">Method</span></span>|<span data-ttu-id="b87a7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b87a7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b87a7-108">GetParameterizedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b87a7-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="b87a7-109">Bu sınıf için tür bildirimini alır.</span><span class="sxs-lookup"><span data-stu-id="b87a7-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="b87a7-110">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b87a7-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="b87a7-111">Bu sınıfın her bir yöntemi için, yöntemin Kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b87a7-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b87a7-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b87a7-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b87a7-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="b87a7-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b87a7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b87a7-114">Requirements</span></span>  
 <span data-ttu-id="b87a7-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b87a7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b87a7-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b87a7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b87a7-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b87a7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b87a7-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b87a7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b87a7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b87a7-119">See also</span></span>

- [<span data-ttu-id="b87a7-120">ICorDebugClass arabirimi</span><span class="sxs-lookup"><span data-stu-id="b87a7-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="b87a7-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b87a7-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
