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
ms.openlocfilehash: 51104516008ffee0694c72733cb5f82b5ba6d8cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609463"
---
# <a name="cortypeid-structure"></a><span data-ttu-id="2cae0-102">COR_TYPEID Yapısı</span><span class="sxs-lookup"><span data-stu-id="2cae0-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="2cae0-103">Tür tanımlayıcısını içerir.</span><span class="sxs-lookup"><span data-stu-id="2cae0-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cae0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cae0-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="2cae0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2cae0-105">Members</span></span>  
  
|<span data-ttu-id="2cae0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2cae0-106">Member</span></span>|<span data-ttu-id="2cae0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cae0-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="2cae0-108">İlk belirteç.</span><span class="sxs-lookup"><span data-stu-id="2cae0-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="2cae0-109">İkinci belirteç.</span><span class="sxs-lookup"><span data-stu-id="2cae0-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cae0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cae0-110">Remarks</span></span>  
 <span data-ttu-id="2cae0-111">`COR_TYPEID` Yapısı, bir dizi atık olarak toplanmış olacak nesneleri hakkında bilgi sağlayan hata ayıklama yöntemi tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2cae0-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="2cae0-112">Bunu ardından bağımsız değişken olarak bu öğe hakkında ek bilgiler sağlayan diğer hata ayıklama yöntemleri geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2cae0-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="2cae0-113">Örneğin, numaralandırma tarafından bir [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) nesnesi, tek tek alabilirsiniz [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığındaki ayrı nesneleri temsil eden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2cae0-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="2cae0-114">Ardından geçirebilirsiniz `COR_TYPEID` değerini `COR_HEAPOBJECT.type` alanı [Icordebugprocess5::gettypefortypeıd](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) nesne türü bilgilerini sağlayan Icordebugtype nesne almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2cae0-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="2cae0-115">A `COR_TYPEID` nesne katı olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2cae0-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="2cae0-116">Tek tek alanları erişilen veya değil.</span><span class="sxs-lookup"><span data-stu-id="2cae0-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="2cae0-117">Bunun tek olarak sağlanan bir tanımlayıcı olarak kullanılır bir `out` parametresinde bir yöntem çağrısının ve bu can sırayla geçirilecek ek bilgi sağlamak için diğer yöntemler.</span><span class="sxs-lookup"><span data-stu-id="2cae0-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cae0-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2cae0-118">Requirements</span></span>  
 <span data-ttu-id="2cae0-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cae0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cae0-120">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cae0-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cae0-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cae0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cae0-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cae0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cae0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cae0-123">See also</span></span>

- [<span data-ttu-id="2cae0-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="2cae0-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="2cae0-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2cae0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
