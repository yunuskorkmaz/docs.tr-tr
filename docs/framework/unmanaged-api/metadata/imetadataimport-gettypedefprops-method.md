---
title: IMetaDataImport::GetTypeDefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a482c7a06efe888408206f2de569e0a8739b85b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777513"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="cd622-102">IMetaDataImport::GetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd622-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="cd622-103">Meta veri bilgilerini döndürür <xref:System.Type> belirtilen TypeDef belirteci tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="cd622-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd622-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd622-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="cd622-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd622-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="cd622-106">[in] TypeDef belirteç meta verileri için dönüş türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cd622-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="cd622-107">[out] Tür adı içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="cd622-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="cd622-108">[in] Geniş karakter cinsinden boyutu `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="cd622-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="cd622-109">[out] Döndürülen geniş karakter sayısını `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="cd622-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="cd622-110">[out] Tür tanımını değiştiren bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cd622-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="cd622-111">Gelen bir bit maskesi değerdir [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="cd622-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="cd622-112">[out] İstenen türün temel türünü temsil eden bir tür tanımı veya TypeRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="cd622-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd622-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd622-113">Requirements</span></span>  
 <span data-ttu-id="cd622-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd622-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd622-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="cd622-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd622-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cd622-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd622-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd622-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd622-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd622-118">See also</span></span>

- [<span data-ttu-id="cd622-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd622-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cd622-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd622-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
