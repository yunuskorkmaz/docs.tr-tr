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
ms.openlocfilehash: 4f4908f5d03687fb415c91325941aaab148832dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447749"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="9121f-102">IMetaDataImport::GetMethodSemantics Metodu</span><span class="sxs-lookup"><span data-stu-id="9121f-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="9121f-103">Belirtilen MethodDef belirteç ve eşleştirilmiş özelliği tarafından başvurulan ve belirtilen EventProp tarafından başvurulan olay arasındaki ilişkiyi gösteren bayrak belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="9121f-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9121f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9121f-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9121f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9121f-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="9121f-106">[in] Anlam rol bilgilerini almak için yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="9121f-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="9121f-107">[in] Eşleştirilmiş özelliğe ve olaya yöntemin rol almak istediğiniz için temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="9121f-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="9121f-108">[out] İlişkili semantiği bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9121f-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="9121f-109">Bu değer gelen bir bit maskesi olan [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="9121f-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9121f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9121f-110">Remarks</span></span>  
 <span data-ttu-id="9121f-111">[Imetadataemit::defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) yöntemi, bir yöntemin semantiği bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9121f-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9121f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9121f-112">Requirements</span></span>  
 <span data-ttu-id="9121f-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9121f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9121f-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9121f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9121f-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9121f-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9121f-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9121f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9121f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9121f-117">See Also</span></span>  
 [<span data-ttu-id="9121f-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9121f-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9121f-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9121f-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
