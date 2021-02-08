---
description: 'Daha fazla bilgi edinin: COR_TYPE_LAYOUT yapısı'
title: COR_TYPE_LAYOUT Yapısı
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
ms.openlocfilehash: 07bed0c526aae38cb380b57da505a3f02bdf4aae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801771"
---
# <a name="cor_type_layout-structure"></a><span data-ttu-id="7a705-103">COR_TYPE_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="7a705-103">COR_TYPE_LAYOUT Structure</span></span>

<span data-ttu-id="7a705-104">Bellekteki bir nesnenin düzeni hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a705-104">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a705-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a705-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="7a705-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7a705-106">Members</span></span>  
  
|<span data-ttu-id="7a705-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7a705-107">Member</span></span>|<span data-ttu-id="7a705-108">Description</span><span class="sxs-lookup"><span data-stu-id="7a705-108">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="7a705-109">Bu türe üst türün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7a705-109">The identifier of the parent type to this type.</span></span> <span data-ttu-id="7a705-110">Bu, tür kimliği öğesine karşılık geliyorsa, NULL tür kimliği (token1 = 0, token2 = 0) olacaktır <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7a705-110">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="7a705-111">Bu türdeki bir nesnenin temel boyutu.</span><span class="sxs-lookup"><span data-stu-id="7a705-111">The base size of an object of this type.</span></span> <span data-ttu-id="7a705-112">Bu, değişken olmayan ölçekli nesnelerin toplam boyutudur.</span><span class="sxs-lookup"><span data-stu-id="7a705-112">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="7a705-113">Bu türün nesnelerine dahil edilen alan sayısı.</span><span class="sxs-lookup"><span data-stu-id="7a705-113">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="7a705-114">Bu tür paketlenise, bir nesne alanlarının başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="7a705-114">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="7a705-115">Bu alan, yalnızca temel öğeler ve yapılar gibi değer türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7a705-115">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="7a705-116">Bu türün ait olduğu CorElementType.</span><span class="sxs-lookup"><span data-stu-id="7a705-116">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a705-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a705-117">Remarks</span></span>  

 <span data-ttu-id="7a705-118">`numFields`Sıfırdan büyükse, bu türdeki alanlarla ilgili bilgi almak Için [ICorDebugProcess5:: GetTypeFields](icordebugprocess5-gettypefields-method.md) metodunu çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a705-118">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="7a705-119">`type` `ELEMENT_TYPE_STRING` , Veya ise, `ELEMENT_TYPE_ARRAY` `ELEMENT_TYPE_SZARRAY` Bu türün nesnelerinin boyutu değişkendir ve [COR_TYPEID](cor-typeid-structure.md) yapısını [ICorDebugProcess5:: GetArrayLayout](icordebugprocess5-getarraylayout-method.md) metoduna geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a705-119">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a705-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a705-120">Requirements</span></span>  

 <span data-ttu-id="7a705-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a705-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a705-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7a705-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a705-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7a705-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a705-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a705-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a705-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a705-125">See also</span></span>

- [<span data-ttu-id="7a705-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="7a705-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="7a705-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7a705-127">Debugging</span></span>](index.md)
