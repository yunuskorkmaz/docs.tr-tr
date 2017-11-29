---
title: IMetaDataImport::GetParamProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3f36282df52b316bfa32c50c3fa9f55f829aa04e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="3f371-102">IMetaDataImport::GetParamProps Metodu</span><span class="sxs-lookup"><span data-stu-id="3f371-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="3f371-103">Meta veri değerleri belirtilen ParamDef tarafından başvurulan parametresi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="3f371-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f371-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f371-104">Syntax</span></span>  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f371-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f371-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="3f371-106">[in] Meta verileri döndürmek için parametre temsil eden bir ParamDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="3f371-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="3f371-107">[out] Parametresi alan yöntemi temsil eden bir MethodDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f371-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="3f371-108">[out] Sıralı konumu parametresi yöntemi bağımsız değişken listesi.</span><span class="sxs-lookup"><span data-stu-id="3f371-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="3f371-109">[out] Parametrenin adını tutmak için arabellek.</span><span class="sxs-lookup"><span data-stu-id="3f371-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3f371-110">[in] Geniş karakterler istenen boyutta `szName`.</span><span class="sxs-lookup"><span data-stu-id="3f371-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="3f371-111">[out] Geniş karakterler döndürülen boyutu `szName`.</span><span class="sxs-lookup"><span data-stu-id="3f371-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="3f371-112">[out] Parametresi ile ilişkili herhangi bir öznitelik bayrağı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f371-112">[out] A pointer to any attribute flags associated with the parameter.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="3f371-113">[out] Parametre belirten bir bayrak için bir işaretçi bir <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="3f371-113">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3f371-114">[out] Parametresi tarafından döndürülen bir sabit dize için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f371-114">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="3f371-115">[out] Boyutunu `ppValue` geniş karakterler ya da sıfır `ppValue` bir dize tutmaz.</span><span class="sxs-lookup"><span data-stu-id="3f371-115">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f371-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f371-116">Requirements</span></span>  
 <span data-ttu-id="3f371-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f371-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f371-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f371-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f371-119">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3f371-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f371-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f371-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f371-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f371-121">See Also</span></span>  
 [<span data-ttu-id="3f371-122">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f371-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3f371-123">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f371-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
