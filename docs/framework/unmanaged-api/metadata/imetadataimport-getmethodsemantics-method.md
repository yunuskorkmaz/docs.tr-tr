---
description: ': IMetaDataImport:: Getmethodsemantik yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2b17e2ffaeef3a451850ce2cc9c4861d68df3a81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783865"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="ddb36-103">IMetaDataImport::GetMethodSemantics Metodu</span><span class="sxs-lookup"><span data-stu-id="ddb36-103">IMetaDataImport::GetMethodSemantics Method</span></span>

<span data-ttu-id="ddb36-104">Belirtilen MethodDef belirtecinin başvurduğu yöntem ile eşleştirilen özellik ve belirtilen EventProp belirteci tarafından başvurulan olay arasındaki ilişkiyi belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="ddb36-104">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb36-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddb36-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddb36-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ddb36-106">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="ddb36-107">'ndaki İçin anlamsal rol bilgilerini almak üzere yöntemini temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="ddb36-107">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="ddb36-108">'ndaki Yöntemin rolünün alınacağı eşleştirilmiş özelliği ve olayı temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="ddb36-108">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="ddb36-109">dışı İlişkili anlambilim bayraklarının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ddb36-109">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="ddb36-110">Bu değer [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) numaralandırmasındaki bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="ddb36-110">This value is a bitmask from the [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddb36-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ddb36-111">Remarks</span></span>  

 <span data-ttu-id="ddb36-112">[Imetadatayayma::D efineProperty](imetadataemit-defineproperty-method.md) yöntemi, yöntemin anlambilim bayraklarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ddb36-112">The [IMetaDataEmit::DefineProperty](imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb36-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddb36-113">Requirements</span></span>  

 <span data-ttu-id="ddb36-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddb36-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb36-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ddb36-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ddb36-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ddb36-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ddb36-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddb36-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb36-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddb36-118">See also</span></span>

- [<span data-ttu-id="ddb36-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddb36-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ddb36-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddb36-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
