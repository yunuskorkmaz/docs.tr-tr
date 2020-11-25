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
ms.openlocfilehash: cc01a417c3246ad2554c506f21e37a3cbbdeb991
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733197"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="4930f-102">IMetaDataImport::GetMethodSemantics Metodu</span><span class="sxs-lookup"><span data-stu-id="4930f-102">IMetaDataImport::GetMethodSemantics Method</span></span>

<span data-ttu-id="4930f-103">Belirtilen MethodDef belirtecinin başvurduğu yöntem ile eşleştirilen özellik ve belirtilen EventProp belirteci tarafından başvurulan olay arasındaki ilişkiyi belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="4930f-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4930f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4930f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4930f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4930f-105">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="4930f-106">'ndaki İçin anlamsal rol bilgilerini almak üzere yöntemini temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="4930f-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="4930f-107">'ndaki Yöntemin rolünün alınacağı eşleştirilmiş özelliği ve olayı temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="4930f-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="4930f-108">dışı İlişkili anlambilim bayraklarının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4930f-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="4930f-109">Bu değer [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) numaralandırmasındaki bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="4930f-109">This value is a bitmask from the [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4930f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4930f-110">Remarks</span></span>  

 <span data-ttu-id="4930f-111">[Imetadatayayma::D efineProperty](imetadataemit-defineproperty-method.md) yöntemi, yöntemin anlambilim bayraklarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4930f-111">The [IMetaDataEmit::DefineProperty](imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4930f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4930f-112">Requirements</span></span>  

 <span data-ttu-id="4930f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4930f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4930f-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4930f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4930f-115">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4930f-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4930f-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4930f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4930f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4930f-117">See also</span></span>

- [<span data-ttu-id="4930f-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4930f-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4930f-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4930f-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
