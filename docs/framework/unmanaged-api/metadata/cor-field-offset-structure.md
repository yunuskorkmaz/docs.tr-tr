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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfbb22d231d16be7757ff5df26a5a010928af54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767055"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="f30ff-102">COR_FIELD_OFFSET Yapısı</span><span class="sxs-lookup"><span data-stu-id="f30ff-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="f30ff-103">Belirtilen alanın bir sınıf içinde bir uzaklık depolar.</span><span class="sxs-lookup"><span data-stu-id="f30ff-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f30ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f30ff-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="f30ff-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f30ff-105">Members</span></span>  
  
|<span data-ttu-id="f30ff-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f30ff-106">Member</span></span>|<span data-ttu-id="f30ff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f30ff-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="f30ff-108">Bir `mdFieldDef` alanını temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f30ff-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="f30ff-109">Alan sınıfıyla içinde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="f30ff-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f30ff-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f30ff-110">Remarks</span></span>  
 <span data-ttu-id="f30ff-111">[Imetadataımport::getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) ve [Imetadataemit::setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) yöntemleri türünde bir parametre alır `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="f30ff-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f30ff-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f30ff-112">Requirements</span></span>  
 <span data-ttu-id="f30ff-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f30ff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f30ff-114">**Üst bilgi:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f30ff-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="f30ff-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f30ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f30ff-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f30ff-116">See also</span></span>

- [<span data-ttu-id="f30ff-117">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="f30ff-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="f30ff-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f30ff-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f30ff-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f30ff-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
