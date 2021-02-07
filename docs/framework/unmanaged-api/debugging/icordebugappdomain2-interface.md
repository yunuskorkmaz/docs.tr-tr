---
description: 'Daha fazla bilgi edinin: ICorDebugAppDomain2 Interface'
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
ms.openlocfilehash: 2f2fcc4166a0c825abaa04392f9905d17e286803
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754195"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="410f1-103">ICorDebugAppDomain2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="410f1-103">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="410f1-104">Diziler, işaretçiler, işlev işaretçileri ve başvuru türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="410f1-104">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="410f1-105">Bu arabirim, ICorDebugAppDomain arabiriminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="410f1-105">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="410f1-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="410f1-106">Methods</span></span>  
  
|<span data-ttu-id="410f1-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="410f1-107">Method</span></span>|<span data-ttu-id="410f1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="410f1-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="410f1-109">GetArrayOrPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="410f1-109">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="410f1-110">Belirtilen türde bir diziyi veya belirtilen türe bir işaretçi ya da başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="410f1-110">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="410f1-111">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="410f1-111">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="410f1-112">Belirli bir imzaya sahip bir işleve yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="410f1-112">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="410f1-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="410f1-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="410f1-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="410f1-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="410f1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="410f1-115">Requirements</span></span>  

 <span data-ttu-id="410f1-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="410f1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410f1-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="410f1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="410f1-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="410f1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="410f1-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="410f1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410f1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="410f1-120">See also</span></span>

- [<span data-ttu-id="410f1-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="410f1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
