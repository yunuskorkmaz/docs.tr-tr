---
title: ICorDebugAppDomain2 Arabirimi
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
ms.openlocfilehash: f20ae6977504f958b7bfa8e2f073b7db6e8b822b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731481"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="4db94-102">ICorDebugAppDomain2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4db94-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="4db94-103">Diziler, işaretçiler, işlev işaretçileri ve başvuru türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4db94-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="4db94-104">Bu arabirim, ICorDebugAppDomain arabiriminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="4db94-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4db94-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4db94-105">Methods</span></span>  
  
|<span data-ttu-id="4db94-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4db94-106">Method</span></span>|<span data-ttu-id="4db94-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4db94-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4db94-108">GetArrayOrPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4db94-108">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="4db94-109">Belirtilen türde bir diziyi veya belirtilen türe bir işaretçi ya da başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="4db94-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="4db94-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="4db94-110">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="4db94-111">Belirli bir imzaya sahip bir işleve yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="4db94-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4db94-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4db94-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4db94-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4db94-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4db94-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4db94-114">Requirements</span></span>  

 <span data-ttu-id="4db94-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4db94-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4db94-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4db94-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4db94-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4db94-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4db94-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4db94-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db94-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4db94-119">See also</span></span>

- [<span data-ttu-id="4db94-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4db94-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
