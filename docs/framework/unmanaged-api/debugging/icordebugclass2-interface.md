---
description: 'Daha fazla bilgi edinin: ICorDebugClass2 Interface'
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
ms.openlocfilehash: 80aa8e59ccc774141e7fcea130d1fc6a38fa37da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711481"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="6eae0-103">ICorDebugClass2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6eae0-103">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="6eae0-104">Bir genel sınıfı veya türünde bir yöntem parametresi olan bir sınıfı temsil eder <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="6eae0-104">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="6eae0-105">Bu arabirim [ICorDebugClass](icordebugclass-interface.md)'ı genişletir.</span><span class="sxs-lookup"><span data-stu-id="6eae0-105">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6eae0-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6eae0-106">Methods</span></span>  
  
|<span data-ttu-id="6eae0-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6eae0-107">Method</span></span>|<span data-ttu-id="6eae0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6eae0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6eae0-109">GetParameterizedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6eae0-109">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="6eae0-110">Bu sınıf için tür bildirimini alır.</span><span class="sxs-lookup"><span data-stu-id="6eae0-110">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="6eae0-111">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6eae0-111">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="6eae0-112">Bu sınıfın her bir yöntemi için, yöntemin Kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6eae0-112">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6eae0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6eae0-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6eae0-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6eae0-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eae0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6eae0-115">Requirements</span></span>  

 <span data-ttu-id="6eae0-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eae0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eae0-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6eae0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6eae0-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6eae0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6eae0-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eae0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eae0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6eae0-120">See also</span></span>

- [<span data-ttu-id="6eae0-121">ICorDebugClass Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6eae0-121">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="6eae0-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6eae0-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
