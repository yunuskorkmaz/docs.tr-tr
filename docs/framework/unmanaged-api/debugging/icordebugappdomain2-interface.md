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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63772c6642cc6f7f96a375beab4f7ef1b4884139
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959839"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="356e3-102">ICorDebugAppDomain2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="356e3-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="356e3-103">Diziler, işaretçiler, işlev işaretçileri ve başvuru türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="356e3-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="356e3-104">Bu arabirim, ICorDebugAppDomain arabiriminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="356e3-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="356e3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="356e3-105">Methods</span></span>  
  
|<span data-ttu-id="356e3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="356e3-106">Method</span></span>|<span data-ttu-id="356e3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="356e3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="356e3-108">GetArrayOrPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="356e3-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="356e3-109">Belirtilen türde bir diziyi veya belirtilen türe bir işaretçi ya da başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="356e3-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="356e3-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="356e3-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="356e3-111">Belirli bir imzaya sahip bir işleve yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="356e3-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="356e3-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="356e3-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="356e3-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="356e3-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="356e3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="356e3-114">Requirements</span></span>  
 <span data-ttu-id="356e3-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="356e3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="356e3-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="356e3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="356e3-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="356e3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="356e3-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="356e3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356e3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="356e3-119">See also</span></span>

- [<span data-ttu-id="356e3-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="356e3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
