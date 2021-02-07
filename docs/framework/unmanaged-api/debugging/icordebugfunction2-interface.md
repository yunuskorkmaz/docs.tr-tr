---
description: 'Daha fazla bilgi edinin: ICorDebugFunction2 Interface'
title: ICorDebugFunction2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: e5297d46acb9b174537363fc185fa2d540d55a75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692205"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="856b7-103">ICorDebugFunction2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="856b7-103">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="856b7-104">Kullanıcı dışı kodu atlayan Yalnızca kendi kodum adım adım hata ayıklama desteği sağlamak için ICorDebugFunction arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="856b7-104">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="856b7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="856b7-105">Methods</span></span>  
  
|<span data-ttu-id="856b7-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="856b7-106">Method</span></span>|<span data-ttu-id="856b7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="856b7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="856b7-108">EnumerateNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="856b7-108">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="856b7-109">(Henüz uygulanmadı.) Bu ICorDebugFunction2 nesnesinin başvurduğu işlevdeki yerel kod deyimlerini içeren bir ICorDebugCodeEnum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="856b7-109">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="856b7-110">GetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="856b7-110">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="856b7-111">Bu işlevin Kullanıcı kodu olarak işaretlenip işaretlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="856b7-111">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="856b7-112">GetVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="856b7-112">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="856b7-113">Bu işlevin Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="856b7-113">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="856b7-114">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="856b7-114">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="856b7-115">Bu işlevi Yalnızca kendi kodum Adımlama için işaretler.</span><span class="sxs-lookup"><span data-stu-id="856b7-115">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="856b7-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="856b7-116">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="856b7-117">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="856b7-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="856b7-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="856b7-118">Requirements</span></span>  

 <span data-ttu-id="856b7-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="856b7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="856b7-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="856b7-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="856b7-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="856b7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="856b7-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="856b7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856b7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="856b7-123">See also</span></span>

- [<span data-ttu-id="856b7-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="856b7-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
