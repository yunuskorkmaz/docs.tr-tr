---
description: 'Daha fazla bilgi edinin: COR_TYPEID yapısı'
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
ms.openlocfilehash: fe246d544697275ffc4ea3ab6ed21c0f33863881
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712221"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="0262d-103">COR_TYPEID Yapısı</span><span class="sxs-lookup"><span data-stu-id="0262d-103">COR_TYPEID Structure</span></span>

<span data-ttu-id="0262d-104">Bir tür tanımlayıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="0262d-104">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0262d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0262d-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="0262d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0262d-106">Members</span></span>  
  
|<span data-ttu-id="0262d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0262d-107">Member</span></span>|<span data-ttu-id="0262d-108">Description</span><span class="sxs-lookup"><span data-stu-id="0262d-108">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="0262d-109">İlk belirteç.</span><span class="sxs-lookup"><span data-stu-id="0262d-109">The first token.</span></span>|  
|`token2`|<span data-ttu-id="0262d-110">İkinci belirteç.</span><span class="sxs-lookup"><span data-stu-id="0262d-110">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0262d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0262d-111">Remarks</span></span>  

 <span data-ttu-id="0262d-112">`COR_TYPEID`Yapı, atık toplanacak nesneler hakkında bilgi sağlayan bir dizi hata ayıklama yöntemi tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0262d-112">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="0262d-113">Daha sonra, bu öğe hakkında ek bilgiler sağlayan diğer hata ayıklama yöntemlerine bir bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0262d-113">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="0262d-114">Örneğin, bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) nesnesini numaralandırarak, yönetilen yığında tek tek nesneleri temsil eden bağımsız [cor_heapobject](cor-heapobject-structure.md) nesneleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0262d-114">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="0262d-115">Ardından, `COR_TYPEID` `COR_HEAPOBJECT.type` nesne hakkında tür bilgisi sağlayan ICorDebugType nesnesini almak için alanından değeri [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0262d-115">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="0262d-116">Bir `COR_TYPEID` nesnenin donuk olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0262d-116">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="0262d-117">Bireysel alanlarına erişilmemelidir veya bunların kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0262d-117">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="0262d-118">Tek kullanımı, yöntem çağrısında bir parametre olarak verilen ve daha sonra `out` ek bilgi sağlamak için diğer yöntemlere geçirilebilecek bir tanımlayıcı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0262d-118">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0262d-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0262d-119">Requirements</span></span>  

 <span data-ttu-id="0262d-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0262d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0262d-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0262d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0262d-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0262d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0262d-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0262d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0262d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0262d-124">See also</span></span>

- [<span data-ttu-id="0262d-125">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="0262d-125">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0262d-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0262d-126">Debugging</span></span>](index.md)
