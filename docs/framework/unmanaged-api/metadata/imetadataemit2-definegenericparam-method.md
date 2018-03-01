---
title: "IMetaDataEmit2::DefineGenericParam Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 598c616ca91b73d9cb184d9e431e75d00d3f9850
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="561e4-102">IMetaDataEmit2::DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="561e4-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="561e4-103">Genel tür parametresi için bir tanım oluşturur ve o genel tür parametresi için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="561e4-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="561e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="561e4-104">Syntax</span></span>  
  
```  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="561e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="561e4-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="561e4-106">[in] Bir `mdTypeDef` veya `mdMethodDef` yöntemi veya genel bir parametreye tanımlanacağı Oluşturucusu temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="561e4-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="561e4-107">[in] Genel parametresini dizini.</span><span class="sxs-lookup"><span data-stu-id="561e4-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="561e4-108">[in] Değerini [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) türünü genel parametresi için açıklayan numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="561e4-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="561e4-109">[in] Parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="561e4-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="561e4-110">[in] Bu parametre, gelecekteki genişletilebilirliği için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="561e4-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="561e4-111">[in] Tür kısıtlamaları sıfır sonlandırılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="561e4-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="561e4-112">Dizi üyeleri olmalıdır bir `mdTypeDef`, `mdTypeRef`, veya `mdTypeSpec` meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="561e4-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="561e4-113">[out] Genel parametresini temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="561e4-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="561e4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="561e4-114">Requirements</span></span>  
 <span data-ttu-id="561e4-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="561e4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="561e4-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="561e4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="561e4-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="561e4-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="561e4-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="561e4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="561e4-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="561e4-119">See Also</span></span>  
 [<span data-ttu-id="561e4-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="561e4-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="561e4-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="561e4-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
