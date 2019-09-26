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
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273989"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="4e641-102">COR_TYPEID Yapısı</span><span class="sxs-lookup"><span data-stu-id="4e641-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="4e641-103">Bir tür tanımlayıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="4e641-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e641-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e641-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="4e641-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4e641-105">Members</span></span>  
  
|<span data-ttu-id="4e641-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4e641-106">Member</span></span>|<span data-ttu-id="4e641-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e641-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="4e641-108">İlk belirteç.</span><span class="sxs-lookup"><span data-stu-id="4e641-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="4e641-109">İkinci belirteç.</span><span class="sxs-lookup"><span data-stu-id="4e641-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e641-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e641-110">Remarks</span></span>  
 <span data-ttu-id="4e641-111">`COR_TYPEID` Yapı, atık toplanacak nesneler hakkında bilgi sağlayan bir dizi hata ayıklama yöntemi tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4e641-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="4e641-112">Daha sonra, bu öğe hakkında ek bilgiler sağlayan diğer hata ayıklama yöntemlerine bir bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4e641-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="4e641-113">Örneğin, bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) nesnesini numaralandırarak, yönetilen yığında tek tek nesneleri temsil eden tek tek [cor_heapobject](cor-heapobject-structure.md) nesnelerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e641-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="4e641-114">Ardından, nesne hakkında tür `COR_TYPEID` bilgisi sağlayan ICorDebugType nesnesini almak için `COR_HEAPOBJECT.type` alanından değeri [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e641-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="4e641-115">Bir `COR_TYPEID` nesnenin donuk olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4e641-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="4e641-116">Bireysel alanlarına erişilmemelidir veya bunların kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e641-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="4e641-117">Tek kullanımı, yöntem çağrısında bir `out` parametre olarak verilen ve daha sonra ek bilgi sağlamak için diğer yöntemlere geçirilebilecek bir tanımlayıcı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4e641-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e641-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e641-118">Requirements</span></span>  
 <span data-ttu-id="4e641-119">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e641-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e641-120">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4e641-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e641-121">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4e641-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e641-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e641-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e641-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e641-123">See also</span></span>

- [<span data-ttu-id="4e641-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="4e641-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="4e641-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4e641-125">Debugging</span></span>](index.md)
