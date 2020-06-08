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
ms.openlocfilehash: e4401ea8a70e7ace8d8efc5e0a6d29f6db51b3df
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503821"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="95c51-102">IMetaDataEmit2::DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95c51-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="95c51-103">Genel tür parametresi için bir tanım oluşturur ve bu genel tür parametresine bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="95c51-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c51-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="95c51-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="95c51-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95c51-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="95c51-106">'ndaki `mdTypeDef` `mdMethodDef` Genel parametre tanımlamak için yöntemi veya oluşturucuyu temsil eden bir veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="95c51-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="95c51-107">'ndaki Genel parametrenin dizini.</span><span class="sxs-lookup"><span data-stu-id="95c51-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="95c51-108">'ndaki Genel parametrenin türünü açıklayan [CorGenericParamAttr](corgenericparamattr-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="95c51-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="95c51-109">'ndaki Parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="95c51-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="95c51-110">'ndaki Bu parametre gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="95c51-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="95c51-111">'ndaki Tür kısıtlamaları sıfır ile sonlandırılmış dizi.</span><span class="sxs-lookup"><span data-stu-id="95c51-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="95c51-112">Dizi üyeleri bir `mdTypeDef` , `mdTypeRef` veya `mdTypeSpec` meta veri belirteci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95c51-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="95c51-113">dışı Genel parametreyi temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="95c51-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c51-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95c51-114">Requirements</span></span>  
 <span data-ttu-id="95c51-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c51-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c51-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="95c51-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95c51-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="95c51-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95c51-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c51-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c51-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95c51-119">See also</span></span>

- [<span data-ttu-id="95c51-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95c51-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="95c51-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95c51-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
