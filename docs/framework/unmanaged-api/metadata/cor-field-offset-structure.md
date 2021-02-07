---
description: 'Daha fazla bilgi edinin: COR_FIELD_OFFSET yapısı'
title: COR_FIELD_OFFSET Yapısı
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 7976e79a5484fa467d7ac887a4e1a7fa324abf69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678646"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="604d3-103">COR_FIELD_OFFSET Yapısı</span><span class="sxs-lookup"><span data-stu-id="604d3-103">COR_FIELD_OFFSET Structure</span></span>

<span data-ttu-id="604d3-104">Belirtilen alanın bir sınıf içindeki sapmasını depolar.</span><span class="sxs-lookup"><span data-stu-id="604d3-104">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="604d3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="604d3-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="604d3-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="604d3-106">Members</span></span>  
  
|<span data-ttu-id="604d3-107">Üye</span><span class="sxs-lookup"><span data-stu-id="604d3-107">Member</span></span>|<span data-ttu-id="604d3-108">Description</span><span class="sxs-lookup"><span data-stu-id="604d3-108">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="604d3-109">`mdFieldDef`Alanı temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="604d3-109">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="604d3-110">Alanın sınıfının içindeki boşluğu.</span><span class="sxs-lookup"><span data-stu-id="604d3-110">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="604d3-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="604d3-111">Remarks</span></span>  

 <span data-ttu-id="604d3-112">[IMetaDataImport:: GetClassLayout](imetadataimport-getclasslayout-method.md) ve [ımetadatayayma:: SetClassLayout](imetadataemit-setclasslayout-method.md) metotları türünde bir parametre alır `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="604d3-112">[IMetaDataImport::GetClassLayout](imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="604d3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="604d3-113">Requirements</span></span>  

 <span data-ttu-id="604d3-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="604d3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="604d3-115">**Üst bilgi:** CorHdr. h, CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="604d3-115">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="604d3-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="604d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604d3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="604d3-117">See also</span></span>

- [<span data-ttu-id="604d3-118">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="604d3-118">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="604d3-119">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="604d3-119">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="604d3-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="604d3-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
