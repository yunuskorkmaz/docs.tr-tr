---
title: IMetaDataImport::GetTypeDefProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3e7f2c2fe602ef3464766b62ef12e8f83767bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="4686e-102">IMetaDataImport::GetTypeDefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="4686e-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="4686e-103">Meta veri bilgilerini döndürür <xref:System.Type> belirtilen TypeDef belirteç tarafından temsil edilen.</span><span class="sxs-lookup"><span data-stu-id="4686e-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4686e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4686e-104">Syntax</span></span>  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4686e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4686e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4686e-106">[in] Meta veriler için dönüş türü temsil eder TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="4686e-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="4686e-107">[out] Tür adını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="4686e-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="4686e-108">[in] Geniş karakter cinsinden boyutu `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="4686e-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="4686e-109">[out] Döndürülen geniş karakter sayısını `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="4686e-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="4686e-110">[out] Tür tanımı değiştirme bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4686e-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="4686e-111">Bu değer gelen bir bit maskesi olan [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="4686e-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="4686e-112">[out] İstenen türün temel türünü temsil eden bir TypeDef veya TypeRef meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="4686e-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4686e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4686e-113">Requirements</span></span>  
 <span data-ttu-id="4686e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4686e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4686e-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4686e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4686e-116">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4686e-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4686e-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4686e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4686e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4686e-118">See Also</span></span>  
 [<span data-ttu-id="4686e-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4686e-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4686e-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4686e-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
