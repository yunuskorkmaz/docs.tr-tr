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
ms.openlocfilehash: 91a19e5e15dddd446208dfa3b2c32826282067eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175401"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="a026b-102">IMetaDataImport::GetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a026b-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="a026b-103">Belirtilen alan meta veri belirteci tarafından temsil edilen alanın yerel, yönetilmeyen türüne bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="a026b-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a026b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a026b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a026b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a026b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a026b-106">[içinde] Interop mareşal bilgi almak için alanı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a026b-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="a026b-107">[çıkış] Alanın yerel türünün meta veri imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a026b-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="a026b-108">[çıkış] `ppvNativeType`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="a026b-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a026b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a026b-109">Requirements</span></span>  
 <span data-ttu-id="a026b-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a026b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a026b-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a026b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a026b-112">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="a026b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a026b-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a026b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a026b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a026b-114">See also</span></span>

- [<span data-ttu-id="a026b-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a026b-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a026b-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a026b-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
