---
title: Icordebugappdomain2 arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4549b0fe6379979a7b9bd6344d65ff465f33f17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506140"
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="f46a1-102">Icordebugappdomain2 arabirimi1</span><span class="sxs-lookup"><span data-stu-id="f46a1-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="f46a1-103">Diziler, işaretçiler, işlev işaretçileri ve başvuru türleri ile çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f46a1-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="f46a1-104">Bu arabirim, Icordebugappdomain arabiriminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="f46a1-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f46a1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f46a1-105">Methods</span></span>  
  
|<span data-ttu-id="f46a1-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f46a1-106">Method</span></span>|<span data-ttu-id="f46a1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f46a1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f46a1-108">GetArrayOrPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f46a1-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="f46a1-109">Belirtilen tür veya işaretçi veya başvuru belirtilen türe dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="f46a1-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="f46a1-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="f46a1-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="f46a1-111">Belirli bir imzaya sahip bir işlev için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f46a1-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f46a1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f46a1-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f46a1-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f46a1-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f46a1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f46a1-114">Requirements</span></span>  
 <span data-ttu-id="f46a1-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f46a1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f46a1-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f46a1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f46a1-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f46a1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f46a1-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f46a1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f46a1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f46a1-119">See also</span></span>
- [<span data-ttu-id="f46a1-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f46a1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
