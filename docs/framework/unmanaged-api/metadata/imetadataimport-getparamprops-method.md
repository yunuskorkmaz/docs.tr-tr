---
title: IMetaDataImport::GetParamProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9d2c74adecdfb0201f9f0c08998feba674f9e0f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778931"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="7f961-102">IMetaDataImport::GetParamProps Metodu</span><span class="sxs-lookup"><span data-stu-id="7f961-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="7f961-103">Meta veri değerleri tarafından belirtilen ParamDef başvurulan parametresi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="7f961-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f961-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f961-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="7f961-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f961-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7f961-106">[in] Meta verileri döndürmek için parametre temsil eden bir ParamDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="7f961-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="7f961-107">[out] Yönteminin parametresi alan temsil eden bir MethodDef belirteç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7f961-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="7f961-108">[out] Sıralı konumu parametresi yöntemi bağımsız değişken listesi.</span><span class="sxs-lookup"><span data-stu-id="7f961-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="7f961-109">[out] Parametrenin adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="7f961-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7f961-110">[in] Geniş karakter cinsinden istenen boyuta `szName`.</span><span class="sxs-lookup"><span data-stu-id="7f961-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="7f961-111">[out] Geniş karakter cinsinden döndürülen boyutu `szName`.</span><span class="sxs-lookup"><span data-stu-id="7f961-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="7f961-112">[out] Parametresi ile ilişkili herhangi bir öznitelik bayrağı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7f961-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="7f961-113">Bu, bir bit maskesi, `CorParamAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="7f961-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="7f961-114">[out] Parametre belirten bir bayrak için bir işaretçi bir <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="7f961-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="7f961-115">[out] Parametresi tarafından döndürülen bir sabit dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7f961-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="7f961-116">[out] Boyutu `ppValue` geniş karakterler ya da sıfır `ppValue` bir dize tutmaz.</span><span class="sxs-lookup"><span data-stu-id="7f961-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f961-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f961-117">Remarks</span></span>

<span data-ttu-id="7f961-118">Sıralı değerleri `pulSequence` parametreleri için 1 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="7f961-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="7f961-119">Dönüş değeri bir sıra numarası 0 sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7f961-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f961-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f961-120">Requirements</span></span>  
 <span data-ttu-id="7f961-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f961-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f961-122">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7f961-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f961-123">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7f961-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f961-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f961-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f961-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f961-125">See also</span></span>

- [<span data-ttu-id="7f961-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f961-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7f961-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f961-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
