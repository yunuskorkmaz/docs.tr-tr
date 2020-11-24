---
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
ms.openlocfilehash: d479416f5f1cb4042f9b3fc112e22b67e37d3f78
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672714"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="8a932-102">IMetaDataEmit::SetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a932-102">IMetaDataEmit::SetFieldMarshal Method</span></span>

<span data-ttu-id="8a932-103">Belirtilen belirteç tarafından başvurulan alan, yöntem döndürme veya yöntem parametresi için PInvoke sıralama bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8a932-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a932-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8a932-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a932-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a932-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="8a932-106">'ndaki Hedef veri öğesi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="8a932-106">[in] The token for target data item.</span></span> <span data-ttu-id="8a932-107">Bu bir ya da `mdFieldDef` bir `mdParamDef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="8a932-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="8a932-108">'ndaki Yönetilmeyen tür için imza.</span><span class="sxs-lookup"><span data-stu-id="8a932-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="8a932-109">'ndaki İçindeki bayt sayısı `pvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="8a932-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a932-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a932-110">Requirements</span></span>  

 <span data-ttu-id="8a932-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a932-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a932-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8a932-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a932-113">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8a932-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a932-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a932-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a932-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a932-115">See also</span></span>

- [<span data-ttu-id="8a932-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a932-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8a932-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a932-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
