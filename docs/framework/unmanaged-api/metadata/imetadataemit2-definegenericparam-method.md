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
ms.openlocfilehash: 3898b095809e2b84f71aba2036f4d7a294dfdf6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444658"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="d8272-102">IMetaDataEmit2::DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8272-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="d8272-103">Genel tür parametresi için bir tanım oluşturur ve bu genel tür parametresine bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="d8272-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8272-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8272-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="d8272-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8272-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d8272-106">'ndaki Genel parametre tanımlanacak yöntemi veya oluşturucuyu temsil eden bir `mdTypeDef` veya `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="d8272-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="d8272-107">'ndaki Genel parametrenin dizini.</span><span class="sxs-lookup"><span data-stu-id="d8272-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="d8272-108">'ndaki Genel parametrenin türünü açıklayan [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="d8272-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="d8272-109">'ndaki Parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="d8272-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="d8272-110">'ndaki Bu parametre gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d8272-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="d8272-111">'ndaki Tür kısıtlamaları sıfır ile sonlandırılmış dizi.</span><span class="sxs-lookup"><span data-stu-id="d8272-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="d8272-112">Dizi üyeleri bir `mdTypeDef`, `mdTypeRef`veya `mdTypeSpec` meta veri belirteci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8272-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="d8272-113">dışı Genel parametreyi temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="d8272-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8272-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8272-114">Requirements</span></span>  
 <span data-ttu-id="d8272-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8272-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8272-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d8272-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8272-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d8272-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8272-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8272-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8272-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8272-119">See also</span></span>

- [<span data-ttu-id="d8272-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8272-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="d8272-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8272-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
