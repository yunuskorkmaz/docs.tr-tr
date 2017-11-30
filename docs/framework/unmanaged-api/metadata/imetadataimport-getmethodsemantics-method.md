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
ms.openlocfilehash: f15aedb74fd7322031d213c5229f65d70f7cb771
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="c0602-102">IMetaDataImport::GetMethodSemantics Metodu</span><span class="sxs-lookup"><span data-stu-id="c0602-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="c0602-103">Belirtilen MethodDef belirteç ve eşleştirilmiş özelliği tarafından başvurulan ve belirtilen EventProp tarafından başvurulan olay arasındaki ilişkiyi gösteren bayrak belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="c0602-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0602-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0602-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0602-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0602-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="c0602-106">[in] Anlam rol bilgilerini almak için yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="c0602-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="c0602-107">[in] Eşleştirilmiş özelliğe ve olaya yöntemin rol almak istediğiniz için temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="c0602-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="c0602-108">[out] İlişkili semantiği bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c0602-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="c0602-109">Bu değer gelen bir bit maskesi olan [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="c0602-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0602-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0602-110">Remarks</span></span>  
 <span data-ttu-id="c0602-111">[Imetadataemit::defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) yöntemi, bir yöntemin semantiği bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c0602-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0602-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0602-112">Requirements</span></span>  
 <span data-ttu-id="c0602-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0602-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0602-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0602-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0602-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c0602-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0602-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0602-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0602-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0602-117">See Also</span></span>  
 [<span data-ttu-id="c0602-118">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0602-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c0602-119">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0602-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
