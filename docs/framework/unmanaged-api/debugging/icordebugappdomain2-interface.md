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
ms.openlocfilehash: 1643d91f373ff233540026440ee21aa4c146f3e3
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895128"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="6fa6c-102">ICorDebugAppDomain2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6fa6c-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="6fa6c-103">Diziler, işaretçiler, işlev işaretçileri ve başvuru türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fa6c-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="6fa6c-104">Bu arabirim, ICorDebugAppDomain arabiriminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa6c-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6fa6c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6fa6c-105">Methods</span></span>  
  
|<span data-ttu-id="6fa6c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6fa6c-106">Method</span></span>|<span data-ttu-id="6fa6c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fa6c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6fa6c-108">GetArrayOrPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6fa6c-108">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="6fa6c-109">Belirtilen türde bir diziyi veya belirtilen türe bir işaretçi ya da başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="6fa6c-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="6fa6c-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="6fa6c-110">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="6fa6c-111">Belirli bir imzaya sahip bir işleve yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6fa6c-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fa6c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6fa6c-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fa6c-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6fa6c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fa6c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6fa6c-114">Requirements</span></span>  
 <span data-ttu-id="6fa6c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fa6c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fa6c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6fa6c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fa6c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6fa6c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fa6c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fa6c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa6c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fa6c-119">See also</span></span>

- [<span data-ttu-id="6fa6c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6fa6c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
