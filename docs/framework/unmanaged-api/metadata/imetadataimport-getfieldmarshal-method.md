---
title: IMetaDataImport::GetFieldMarshal Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3bc90a17a0469cd716c1e3e990b5c0fb2ff8bf5a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647587"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="fb4c0-102">IMetaDataImport::GetFieldMarshal Metodu</span><span class="sxs-lookup"><span data-stu-id="fb4c0-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="fb4c0-103">Belirtilen alan metaveri belirteci tarafından temsil edilen alan yerel, yönetilmeyen tür için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="fb4c0-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb4c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb4c0-104">Syntax</span></span>  
  
```  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb4c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb4c0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="fb4c0-106">[in] Birlikte çalışma hazırlama hakkında bilgi alın alanını temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="fb4c0-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="fb4c0-107">[out] Yerel alanın türünü meta veri imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb4c0-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="fb4c0-108">[out] Bayt cinsinden boyutu `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="fb4c0-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb4c0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb4c0-109">Requirements</span></span>  
 <span data-ttu-id="fb4c0-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb4c0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb4c0-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fb4c0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb4c0-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fb4c0-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb4c0-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb4c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb4c0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb4c0-114">See also</span></span>
- [<span data-ttu-id="fb4c0-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb4c0-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fb4c0-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb4c0-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
