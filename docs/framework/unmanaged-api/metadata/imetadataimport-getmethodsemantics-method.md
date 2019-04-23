---
title: IMetaDataImport::GetMethodSemantics Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ddbd8c6935f2c0275c132e30ea175c6f198fac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200096"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="44a1c-102">IMetaDataImport::GetMethodSemantics Metodu</span><span class="sxs-lookup"><span data-stu-id="44a1c-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="44a1c-103">Belirteç belirtilen MethodDef belirteç ve eşleştirilmiş özelliği tarafından başvurulan metot ve olay tarafından belirtilen EventProp başvurulan arasındaki ilişkiyi gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="44a1c-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a1c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44a1c-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44a1c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44a1c-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="44a1c-106">[in] Anlam rol bilgilerini almak için yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="44a1c-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="44a1c-107">[in] Eşleştirilmiş özellik ve yöntem rol alınacağı olay temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="44a1c-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="44a1c-108">[out] İlişkili bir semantik bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="44a1c-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="44a1c-109">Gelen bir bit maskesi değerdir [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="44a1c-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44a1c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44a1c-110">Remarks</span></span>  
 <span data-ttu-id="44a1c-111">[Imetadataemit::defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) yöntemi, bir yöntemin semantiği bayraklar ayarlar.</span><span class="sxs-lookup"><span data-stu-id="44a1c-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44a1c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44a1c-112">Requirements</span></span>  
 <span data-ttu-id="44a1c-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44a1c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44a1c-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="44a1c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44a1c-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="44a1c-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44a1c-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44a1c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a1c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44a1c-117">See also</span></span>

- [<span data-ttu-id="44a1c-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44a1c-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="44a1c-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44a1c-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
