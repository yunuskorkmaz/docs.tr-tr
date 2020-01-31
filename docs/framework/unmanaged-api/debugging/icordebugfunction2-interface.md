---
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
ms.openlocfilehash: 5364e39f7e0a9b6c9cd10cd8f17bab4a03a4b7af
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794475"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="feb38-102">ICorDebugFunction2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feb38-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="feb38-103">Kullanıcı dışı kodu atlayan Yalnızca kendi kodum adım adım hata ayıklama desteği sağlamak için ICorDebugFunction arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="feb38-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="feb38-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="feb38-104">Methods</span></span>  
  
|<span data-ttu-id="feb38-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="feb38-105">Method</span></span>|<span data-ttu-id="feb38-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feb38-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="feb38-107">EnumerateNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb38-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="feb38-108">(Henüz uygulanmadı.) Bu ICorDebugFunction2 nesnesinin başvurduğu işlevdeki yerel kod deyimlerini içeren bir ICorDebugCodeEnum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="feb38-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="feb38-109">GetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb38-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="feb38-110">Bu işlevin Kullanıcı kodu olarak işaretlenip işaretlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="feb38-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="feb38-111">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb38-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="feb38-112">Bu işlevin Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="feb38-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="feb38-113">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb38-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="feb38-114">Bu işlevi Yalnızca kendi kodum Adımlama için işaretler.</span><span class="sxs-lookup"><span data-stu-id="feb38-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feb38-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="feb38-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="feb38-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="feb38-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb38-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feb38-117">Requirements</span></span>  
 <span data-ttu-id="feb38-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feb38-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feb38-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="feb38-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="feb38-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="feb38-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="feb38-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feb38-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb38-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feb38-122">See also</span></span>

- [<span data-ttu-id="feb38-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="feb38-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
