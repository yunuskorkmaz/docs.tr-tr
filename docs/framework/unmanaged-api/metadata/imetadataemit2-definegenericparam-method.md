---
title: IMetaDataEmit2::DefineGenericParam Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b54f5bb47135bcf56c91cd07b916c959e75b9fb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745333"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="26ed0-102">IMetaDataEmit2::DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ed0-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="26ed0-103">Genel tür parametresi için bir tanım oluşturur ve o genel tür parametresi için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="26ed0-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26ed0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26ed0-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="26ed0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26ed0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="26ed0-106">[in] Bir `mdTypeDef` veya `mdMethodDef` yöntem veya Oluşturucu genel parametre tanımlanacağı temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="26ed0-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="26ed0-107">[in] Genel parametre dizini.</span><span class="sxs-lookup"><span data-stu-id="26ed0-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="26ed0-108">[in] Değerini [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) türünü genel parametresi için açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="26ed0-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="26ed0-109">[in] Parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="26ed0-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="26ed0-110">[in] Bu parametre sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="26ed0-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="26ed0-111">[in] Tür kısıtlamaları Sıfırla sonlandırılmış dizisi.</span><span class="sxs-lookup"><span data-stu-id="26ed0-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="26ed0-112">Dizi üyeleri olmalıdır bir `mdTypeDef`, `mdTypeRef`, veya `mdTypeSpec` meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="26ed0-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="26ed0-113">[out] Genel parametre temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="26ed0-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26ed0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26ed0-114">Requirements</span></span>  
 <span data-ttu-id="26ed0-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26ed0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26ed0-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="26ed0-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26ed0-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="26ed0-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26ed0-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26ed0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ed0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26ed0-119">See also</span></span>
- [<span data-ttu-id="26ed0-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26ed0-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="26ed0-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26ed0-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
