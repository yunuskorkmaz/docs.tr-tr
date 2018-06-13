---
title: COR_TYPEID Yapısı
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d4e07fb3d0988838fde662f4bb7d4719cc2d50f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408346"
---
# <a name="cortypeid-structure"></a><span data-ttu-id="58c90-102">COR_TYPEID Yapısı</span><span class="sxs-lookup"><span data-stu-id="58c90-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="58c90-103">Tür tanımlayıcısı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="58c90-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c90-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58c90-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="58c90-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="58c90-105">Members</span></span>  
  
|<span data-ttu-id="58c90-106">Üye</span><span class="sxs-lookup"><span data-stu-id="58c90-106">Member</span></span>|<span data-ttu-id="58c90-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58c90-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="58c90-108">İlk belirteci.</span><span class="sxs-lookup"><span data-stu-id="58c90-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="58c90-109">İkinci belirteci.</span><span class="sxs-lookup"><span data-stu-id="58c90-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58c90-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58c90-110">Remarks</span></span>  
 <span data-ttu-id="58c90-111">`COR_TYPEID` Yapısı çeşitli atık olarak toplanmış olacak nesneleri hakkında bilgi sağlayan hata ayıklama yöntemler tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="58c90-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="58c90-112">Bunun ardından bağımsız değişken olarak bu öğe hakkında ek bilgiler sağlayan diğer hata ayıklama yöntemlerine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="58c90-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="58c90-113">Örneğin, numaralandırma tarafından bir [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) nesnesi, tek tek alabilir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığında ayrı ayrı nesneleri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="58c90-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="58c90-114">Ardından geçirebilirsiniz `COR_TYPEID` değeri `COR_HEAPOBJECT.type` alanı [Icordebugprocess5::gettypefortypeıd](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) nesne türü bilgilerini sağlayan bir Icordebugtype nesne alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58c90-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="58c90-115">A `COR_TYPEID` nesne donuk olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="58c90-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="58c90-116">Tek tek alanların erişilen veya değil.</span><span class="sxs-lookup"><span data-stu-id="58c90-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="58c90-117">Bunun tek olarak sağlanan bir tanımlayıcı olarak kullanılır bir `out` yöntem çağrısı ve o can parametresinde sırayla, ek bilgi sağlamak için diğer yöntemleri için geçirilen.</span><span class="sxs-lookup"><span data-stu-id="58c90-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58c90-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58c90-118">Requirements</span></span>  
 <span data-ttu-id="58c90-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58c90-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58c90-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58c90-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58c90-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58c90-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58c90-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58c90-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c90-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58c90-123">See Also</span></span>  
 [<span data-ttu-id="58c90-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="58c90-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="58c90-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="58c90-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
