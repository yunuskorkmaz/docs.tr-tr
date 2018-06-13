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
ms.openlocfilehash: 837b2142e200e224fe32c2c673be0f317633452a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445364"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="a6a18-102">IMetaDataImport::GetFieldMarshal Metodu</span><span class="sxs-lookup"><span data-stu-id="a6a18-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="a6a18-103">Belirtilen alan meta veri simgesi tarafından temsil edilen alan yerel, yönetilmeyen türü için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="a6a18-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6a18-104">Syntax</span></span>  
  
```  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6a18-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6a18-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a6a18-106">[in] Birlikte çalışma sıralama bilgilerini almak için alanını temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="a6a18-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="a6a18-107">[out] Alanın yerel tür meta verileri imzasını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6a18-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="a6a18-108">[out] Bayt cinsinden boyutu `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="a6a18-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6a18-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6a18-109">Requirements</span></span>  
 <span data-ttu-id="a6a18-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6a18-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6a18-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a6a18-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6a18-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a6a18-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6a18-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a18-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a18-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6a18-114">See Also</span></span>  
 [<span data-ttu-id="a6a18-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6a18-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a6a18-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6a18-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
