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
ms.openlocfilehash: 8c4a5c8efc87940b7df0bfd532beaa67931a8c81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442124"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="1b59d-102">COR_FIELD_OFFSET Yapısı</span><span class="sxs-lookup"><span data-stu-id="1b59d-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="1b59d-103">Belirtilen alanın bir sınıf içinde uzaklık depolar.</span><span class="sxs-lookup"><span data-stu-id="1b59d-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b59d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b59d-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="1b59d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1b59d-105">Members</span></span>  
  
|<span data-ttu-id="1b59d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1b59d-106">Member</span></span>|<span data-ttu-id="1b59d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b59d-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="1b59d-108">Bir `mdFieldDef` alanını temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="1b59d-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="1b59d-109">Alan kendi sınıfı içinde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="1b59d-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b59d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b59d-110">Remarks</span></span>  
 <span data-ttu-id="1b59d-111">[Imetadataımport::getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) ve [Imetadataemit::setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) yöntemlerini ele türünde bir parametre `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="1b59d-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b59d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b59d-112">Requirements</span></span>  
 <span data-ttu-id="1b59d-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b59d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b59d-114">**Başlık:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1b59d-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="1b59d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b59d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b59d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b59d-116">See Also</span></span>  
 [<span data-ttu-id="1b59d-117">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="1b59d-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="1b59d-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b59d-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="1b59d-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b59d-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
