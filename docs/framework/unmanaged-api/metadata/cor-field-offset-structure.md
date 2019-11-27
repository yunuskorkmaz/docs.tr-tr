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
ms.openlocfilehash: 646952d5cd55b74081a0ba6171a6eee6b0138512
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443969"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="0e266-102">COR_FIELD_OFFSET Yapısı</span><span class="sxs-lookup"><span data-stu-id="0e266-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="0e266-103">Belirtilen alanın bir sınıf içindeki sapmasını depolar.</span><span class="sxs-lookup"><span data-stu-id="0e266-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e266-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e266-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="0e266-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="0e266-105">Members</span></span>  
  
|<span data-ttu-id="0e266-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="0e266-106">Member</span></span>|<span data-ttu-id="0e266-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e266-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="0e266-108">Alanı temsil eden bir `mdFieldDef` meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0e266-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="0e266-109">Alanın sınıfının içindeki boşluğu.</span><span class="sxs-lookup"><span data-stu-id="0e266-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e266-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e266-110">Remarks</span></span>  
 <span data-ttu-id="0e266-111">[IMetaDataImport:: GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) ve [ımetadatayayma:: setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) metotları `COR_FIELD_OFFSET`türünde bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="0e266-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e266-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e266-112">Requirements</span></span>  
 <span data-ttu-id="0e266-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e266-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e266-114">**Üst bilgi:** CorHdr. h, CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="0e266-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="0e266-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e266-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e266-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e266-116">See also</span></span>

- [<span data-ttu-id="0e266-117">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="0e266-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="0e266-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e266-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0e266-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e266-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
