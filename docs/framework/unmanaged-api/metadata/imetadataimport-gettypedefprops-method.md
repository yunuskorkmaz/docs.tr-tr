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
ms.openlocfilehash: 1025ffde2bd066c81c4c562c0dd86e829fc2aef3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="cd101-102">IMetaDataImport::GetTypeDefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="cd101-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="cd101-103">Meta veri bilgilerini döndürür <xref:System.Type> belirtilen TypeDef belirteç tarafından temsil edilen.</span><span class="sxs-lookup"><span data-stu-id="cd101-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd101-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd101-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="cd101-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd101-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="cd101-106">[in] Meta veriler için dönüş türü temsil eder TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="cd101-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="cd101-107">[out] Tür adını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="cd101-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="cd101-108">[in] Geniş karakter cinsinden boyutu `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="cd101-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="cd101-109">[out] Döndürülen geniş karakter sayısını `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="cd101-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="cd101-110">[out] Tür tanımı değiştirme bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cd101-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="cd101-111">Bu değer gelen bir bit maskesi olan [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="cd101-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="cd101-112">[out] İstenen türün temel türünü temsil eden bir TypeDef veya TypeRef meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="cd101-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd101-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd101-113">Requirements</span></span>  
 <span data-ttu-id="cd101-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd101-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd101-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd101-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd101-116">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cd101-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd101-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd101-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd101-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd101-118">See Also</span></span>  
 [<span data-ttu-id="cd101-119">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd101-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cd101-120">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd101-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
