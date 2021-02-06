---
description: ': Imetadatayayma:: SetFieldMarshal yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataEmit::SetFieldMarshal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: 4694487479b0249e875abfd9ecd963a5dc404d46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658054"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="98730-103">IMetaDataEmit::SetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98730-103">IMetaDataEmit::SetFieldMarshal Method</span></span>

<span data-ttu-id="98730-104">Belirtilen belirteç tarafından başvurulan alan, yöntem döndürme veya yöntem parametresi için PInvoke sıralama bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98730-104">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98730-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98730-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98730-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98730-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="98730-107">'ndaki Hedef veri öğesi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="98730-107">[in] The token for target data item.</span></span> <span data-ttu-id="98730-108">Bu bir ya da `mdFieldDef` bir `mdParamDef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="98730-108">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="98730-109">'ndaki Yönetilmeyen tür için imza.</span><span class="sxs-lookup"><span data-stu-id="98730-109">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="98730-110">'ndaki İçindeki bayt sayısı `pvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="98730-110">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98730-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98730-111">Requirements</span></span>  

 <span data-ttu-id="98730-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98730-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98730-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="98730-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98730-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="98730-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98730-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98730-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98730-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98730-116">See also</span></span>

- [<span data-ttu-id="98730-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98730-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="98730-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98730-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
