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
ms.openlocfilehash: 98a58c5e686a0650fa62752f6d1d50706d58e8d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698667"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="7b224-102">COR_FIELD_OFFSET Yapısı</span><span class="sxs-lookup"><span data-stu-id="7b224-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="7b224-103">Belirtilen alanın bir sınıf içinde bir uzaklık depolar.</span><span class="sxs-lookup"><span data-stu-id="7b224-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b224-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b224-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="7b224-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7b224-105">Members</span></span>  
  
|<span data-ttu-id="7b224-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7b224-106">Member</span></span>|<span data-ttu-id="7b224-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b224-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="7b224-108">Bir `mdFieldDef` alanını temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="7b224-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="7b224-109">Alan sınıfıyla içinde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="7b224-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b224-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b224-110">Remarks</span></span>  
 <span data-ttu-id="7b224-111">[Imetadataımport::getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) ve [Imetadataemit::setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) yöntemleri türünde bir parametre alır `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="7b224-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b224-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b224-112">Requirements</span></span>  
 <span data-ttu-id="7b224-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b224-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b224-114">**Üst bilgi:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7b224-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="7b224-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b224-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b224-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b224-116">See also</span></span>
- [<span data-ttu-id="7b224-117">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="7b224-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="7b224-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b224-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7b224-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b224-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
