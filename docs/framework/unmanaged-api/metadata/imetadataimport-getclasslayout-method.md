---
title: IMetaDataImport::GetClassLayout Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67447e90198ded258645ad7d9173eed37bb60915
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479421"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="eab8e-102">IMetaDataImport::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="eab8e-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="eab8e-103">Belirtilen tür tanımı tarafından başvurulan sınıfın düzen bilgilerini belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="eab8e-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab8e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eab8e-104">Syntax</span></span>  
  
```  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eab8e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eab8e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="eab8e-106">[in] Döndürülecek düzeni ile sınıf için TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="eab8e-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="eab8e-107">[out] 1, 2, 4, 8 veya 16, sınıf paketi boyutunu temsil eden değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="eab8e-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="eab8e-108">[out] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="eab8e-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="eab8e-109">[in] En büyük boyutunu `rFieldOffset` dizisi.</span><span class="sxs-lookup"><span data-stu-id="eab8e-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="eab8e-110">[out] Döndürülen öğe sayısını `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="eab8e-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="eab8e-111">[out] Tarafından temsil edilen sınıf bayt cinsinden boyut `td`.</span><span class="sxs-lookup"><span data-stu-id="eab8e-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab8e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eab8e-112">Requirements</span></span>  
 <span data-ttu-id="eab8e-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab8e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab8e-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="eab8e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eab8e-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="eab8e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eab8e-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab8e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab8e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eab8e-117">See also</span></span>
- [<span data-ttu-id="eab8e-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eab8e-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="eab8e-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eab8e-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
