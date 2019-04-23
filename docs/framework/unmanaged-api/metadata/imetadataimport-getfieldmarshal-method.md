---
title: IMetaDataImport::GetFieldMarshal Yöntemi
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
ms.openlocfilehash: 35e780c330d0184d40bd99f34c3454f83075c1e0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139288"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="1d0a6-102">IMetaDataImport::GetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d0a6-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="1d0a6-103">Belirtilen alan metaveri belirteci tarafından temsil edilen alan yerel, yönetilmeyen tür için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="1d0a6-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d0a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d0a6-104">Syntax</span></span>  
  
```  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d0a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d0a6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1d0a6-106">[in] Birlikte çalışma hazırlama hakkında bilgi alın alanını temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="1d0a6-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="1d0a6-107">[out] Yerel alanın türünü meta veri imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1d0a6-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="1d0a6-108">[out] Bayt cinsinden boyutu `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="1d0a6-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d0a6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d0a6-109">Requirements</span></span>  
 <span data-ttu-id="1d0a6-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d0a6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d0a6-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1d0a6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d0a6-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1d0a6-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1d0a6-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d0a6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d0a6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d0a6-114">See also</span></span>

- [<span data-ttu-id="1d0a6-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d0a6-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1d0a6-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d0a6-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
