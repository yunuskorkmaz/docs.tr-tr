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
ms.openlocfilehash: 4f6dbe8c17bd6a91078b87a87c1055fbf4977a88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132305"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="c4e11-102">COR_TYPEID Yapısı</span><span class="sxs-lookup"><span data-stu-id="c4e11-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="c4e11-103">Bir tür tanımlayıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="c4e11-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e11-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4e11-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="c4e11-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c4e11-105">Members</span></span>  
  
|<span data-ttu-id="c4e11-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c4e11-106">Member</span></span>|<span data-ttu-id="c4e11-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4e11-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="c4e11-108">İlk belirteç.</span><span class="sxs-lookup"><span data-stu-id="c4e11-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="c4e11-109">İkinci belirteç.</span><span class="sxs-lookup"><span data-stu-id="c4e11-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4e11-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4e11-110">Remarks</span></span>  
 <span data-ttu-id="c4e11-111">`COR_TYPEID` yapısı, atık olarak toplanabilecek nesneler hakkında bilgi sağlayan bir dizi hata ayıklama yöntemi tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c4e11-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="c4e11-112">Daha sonra, bu öğe hakkında ek bilgiler sağlayan diğer hata ayıklama yöntemlerine bir bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c4e11-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="c4e11-113">Örneğin, bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) nesnesini numaralandırarak, yönetilen yığında tek tek nesneleri temsil eden tek tek [cor_heapobject](cor-heapobject-structure.md) nesnelerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4e11-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="c4e11-114">Ardından, nesne hakkında tür bilgisi sağlayan ICorDebugType nesnesini almak için `COR_HEAPOBJECT.type` alanından `COR_TYPEID` değerini [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4e11-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="c4e11-115">`COR_TYPEID` nesnenin donuk olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4e11-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="c4e11-116">Bireysel alanlarına erişilmemelidir veya bunların kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4e11-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="c4e11-117">Tek kullanımı, yöntem çağrısında bir `out` parametresi olarak sağlanmış olan ve daha sonra ek bilgi sağlamak için diğer yöntemlere geçirilebilecek bir tanımlayıcı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4e11-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4e11-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4e11-118">Requirements</span></span>  
 <span data-ttu-id="c4e11-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4e11-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4e11-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4e11-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4e11-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4e11-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4e11-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4e11-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e11-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4e11-123">See also</span></span>

- [<span data-ttu-id="c4e11-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="c4e11-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="c4e11-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c4e11-125">Debugging</span></span>](index.md)
