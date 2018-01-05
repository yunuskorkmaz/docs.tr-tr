---
title: "COR_TYPE_LAYOUT Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPE_LAYOUT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPE_LAYOUT
helpviewer_keywords: COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 250d78dd9983b75fa7e1b3cfd99215160fbc2b1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="fa1b3-102">COR_TYPE_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="fa1b3-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="fa1b3-103">Bir nesnenin bellekte Düzen hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa1b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa1b3-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="fa1b3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fa1b3-105">Members</span></span>  
  
|<span data-ttu-id="fa1b3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fa1b3-106">Member</span></span>|<span data-ttu-id="fa1b3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa1b3-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="fa1b3-108">Bu tür için üst tür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="fa1b3-109">Bu NULL tür kimliği olacaktır (token1 = 0, token2 = 0) için türü kimliği karşılık geliyorsa <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="fa1b3-110">Bu tür bir nesne temel boyutu.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-110">The base size of an object of this type.</span></span> <span data-ttu-id="fa1b3-111">Bu değişken olmayan boyutlu nesneler için toplam boyutudur.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="fa1b3-112">Bu tür nesneler dahil alanları sayısı.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="fa1b3-113">Bu tür Kutulu, nesnenin alanlarının başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="fa1b3-114">Bu alan yalnızca ilkel ve yapıları gibi değer türleri için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="fa1b3-115">Bu tür ait olduğu CorElementType.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa1b3-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa1b3-116">Remarks</span></span>  
 <span data-ttu-id="fa1b3-117">Varsa `numFields` , sıfırdan büyük çağırabilirsiniz [Icordebugprocess5::gettypefields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) bu tür alanları hakkında bilgi edinmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="fa1b3-118">Varsa `type` olan `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, veya `ELEMENT_TYPE_SZARRAY`, bu tür nesneler boyutunu değişkendir ve geçirebilirsiniz [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) için yapı [Icordebugprocess5::getarraylayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa1b3-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa1b3-119">Requirements</span></span>  
 <span data-ttu-id="fa1b3-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa1b3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa1b3-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa1b3-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa1b3-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa1b3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa1b3-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa1b3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1b3-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa1b3-124">See Also</span></span>  
 [<span data-ttu-id="fa1b3-125">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="fa1b3-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="fa1b3-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fa1b3-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
