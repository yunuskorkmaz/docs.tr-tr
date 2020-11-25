---
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
ms.openlocfilehash: 1a8ab5aa5909af60089d5e4cc8092e15bc75e8cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724188"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="6e79e-102">COR_FIELD_OFFSET Yapısı</span><span class="sxs-lookup"><span data-stu-id="6e79e-102">COR_FIELD_OFFSET Structure</span></span>

<span data-ttu-id="6e79e-103">Belirtilen alanın bir sınıf içindeki sapmasını depolar.</span><span class="sxs-lookup"><span data-stu-id="6e79e-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e79e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e79e-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="6e79e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6e79e-105">Members</span></span>  
  
|<span data-ttu-id="6e79e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6e79e-106">Member</span></span>|<span data-ttu-id="6e79e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e79e-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="6e79e-108">`mdFieldDef`Alanı temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6e79e-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="6e79e-109">Alanın sınıfının içindeki boşluğu.</span><span class="sxs-lookup"><span data-stu-id="6e79e-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e79e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e79e-110">Remarks</span></span>  

 <span data-ttu-id="6e79e-111">[IMetaDataImport:: GetClassLayout](imetadataimport-getclasslayout-method.md) ve [ımetadatayayma:: SetClassLayout](imetadataemit-setclasslayout-method.md) metotları türünde bir parametre alır `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="6e79e-111">[IMetaDataImport::GetClassLayout](imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e79e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e79e-112">Requirements</span></span>  

 <span data-ttu-id="6e79e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e79e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e79e-114">**Üst bilgi:** CorHdr. h, CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="6e79e-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="6e79e-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e79e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e79e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e79e-116">See also</span></span>

- [<span data-ttu-id="6e79e-117">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="6e79e-117">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="6e79e-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e79e-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6e79e-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e79e-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
