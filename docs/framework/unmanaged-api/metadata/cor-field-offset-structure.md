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
ms.openlocfilehash: 820c99de1bdb108a24203a3438b1709ca54490b7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078128"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="95fd3-102">COR_FIELD_OFFSET Yapısı</span><span class="sxs-lookup"><span data-stu-id="95fd3-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="95fd3-103">Belirtilen alanın bir sınıf içinde bir uzaklık depolar.</span><span class="sxs-lookup"><span data-stu-id="95fd3-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95fd3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95fd3-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="95fd3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="95fd3-105">Members</span></span>  
  
|<span data-ttu-id="95fd3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="95fd3-106">Member</span></span>|<span data-ttu-id="95fd3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95fd3-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="95fd3-108">Bir `mdFieldDef` alanını temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="95fd3-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="95fd3-109">Alan sınıfıyla içinde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="95fd3-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95fd3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95fd3-110">Remarks</span></span>  
 <span data-ttu-id="95fd3-111">[Imetadataımport::getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) ve [Imetadataemit::setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) yöntemleri türünde bir parametre alır `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="95fd3-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95fd3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95fd3-112">Requirements</span></span>  
 <span data-ttu-id="95fd3-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95fd3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95fd3-114">**Üst bilgi:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="95fd3-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="95fd3-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95fd3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fd3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95fd3-116">See also</span></span>

- [<span data-ttu-id="95fd3-117">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="95fd3-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="95fd3-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95fd3-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="95fd3-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95fd3-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
