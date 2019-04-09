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
ms.openlocfilehash: 11748d3ad99c4050045cce3786eec5604c02ac0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197808"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="ab643-102">IMetaDataImport::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="ab643-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="ab643-103">Belirtilen tür tanımı tarafından başvurulan sınıfın düzen bilgilerini belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="ab643-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab643-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab643-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ab643-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab643-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ab643-106">[in] Döndürülecek düzeni ile sınıf için TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="ab643-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="ab643-107">[out] 1, 2, 4, 8 veya 16, sınıf paketi boyutunu temsil eden değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="ab643-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="ab643-108">[out] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="ab643-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ab643-109">[in] En büyük boyutunu `rFieldOffset` dizisi.</span><span class="sxs-lookup"><span data-stu-id="ab643-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="ab643-110">[out] Döndürülen öğe sayısını `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="ab643-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="ab643-111">[out] Tarafından temsil edilen sınıf bayt cinsinden boyut `td`.</span><span class="sxs-lookup"><span data-stu-id="ab643-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab643-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab643-112">Requirements</span></span>  
 <span data-ttu-id="ab643-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab643-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab643-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ab643-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab643-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ab643-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ab643-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ab643-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab643-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab643-117">See also</span></span>

- [<span data-ttu-id="ab643-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab643-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ab643-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab643-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
