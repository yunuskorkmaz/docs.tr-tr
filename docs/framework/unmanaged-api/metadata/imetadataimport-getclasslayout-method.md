---
title: IMetaDataImport::GetClassLayout Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a93b3e8dde88d87479921efad44236725be6e080
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="67884-102">IMetaDataImport::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="67884-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="67884-103">Belirtilen TypeDef tarafından başvurulan sınıfı için düzen bilgilerini belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="67884-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67884-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67884-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="67884-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67884-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="67884-106">[in] Döndürülecek düzeni sınıfı için TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="67884-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="67884-107">[out] 1, 2, 4, 8 veya 16, paket boyutu sınıftan temsil eden değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="67884-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="67884-108">[out] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="67884-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="67884-109">[in] En büyük boyutunu `rFieldOffset` dizi.</span><span class="sxs-lookup"><span data-stu-id="67884-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="67884-110">[out] Döndürülen öğe sayısını `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="67884-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="67884-111">[out] Tarafından temsil edilen sınıfının bayt boyutunda `td`.</span><span class="sxs-lookup"><span data-stu-id="67884-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67884-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67884-112">Requirements</span></span>  
 <span data-ttu-id="67884-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67884-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67884-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="67884-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67884-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="67884-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67884-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67884-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67884-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67884-117">See Also</span></span>  
 [<span data-ttu-id="67884-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67884-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="67884-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67884-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
