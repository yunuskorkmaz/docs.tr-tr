---
title: IMetaDataImport::GetMethodSemantics Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f8921c4f6a676c9647d4e8907a22f0d68b0b359
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="981d0-102">IMetaDataImport::GetMethodSemantics Metodu</span><span class="sxs-lookup"><span data-stu-id="981d0-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="981d0-103">Belirtilen MethodDef belirteç ve eşleştirilmiş özelliği tarafından başvurulan ve belirtilen EventProp tarafından başvurulan olay arasındaki ilişkiyi gösteren bayrak belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="981d0-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="981d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="981d0-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="981d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="981d0-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="981d0-106">[in] Anlam rol bilgilerini almak için yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="981d0-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="981d0-107">[in] Eşleştirilmiş özelliğe ve olaya yöntemin rol almak istediğiniz için temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="981d0-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="981d0-108">[out] İlişkili semantiği bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="981d0-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="981d0-109">Bu değer gelen bir bit maskesi olan [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="981d0-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="981d0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="981d0-110">Remarks</span></span>  
 <span data-ttu-id="981d0-111">[Imetadataemit::defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) yöntemi, bir yöntemin semantiği bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="981d0-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="981d0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="981d0-112">Requirements</span></span>  
 <span data-ttu-id="981d0-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="981d0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="981d0-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="981d0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="981d0-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="981d0-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="981d0-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="981d0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981d0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="981d0-117">See Also</span></span>  
 [<span data-ttu-id="981d0-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="981d0-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="981d0-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="981d0-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
