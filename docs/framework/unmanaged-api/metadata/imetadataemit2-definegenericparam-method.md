---
description: 'Hakkında daha fazla bilgi edinin: IMetaDataEmit2::D efineGenericParam yöntemi'
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
ms.openlocfilehash: 813661adca162f47a864b19c9754b49072bb4c7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745794"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="b8acb-103">IMetaDataEmit2::DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8acb-103">IMetaDataEmit2::DefineGenericParam Method</span></span>

<span data-ttu-id="b8acb-104">Genel tür parametresi için bir tanım oluşturur ve bu genel tür parametresine bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="b8acb-104">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8acb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8acb-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b8acb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8acb-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="b8acb-107">'ndaki `mdTypeDef` `mdMethodDef` Genel parametre tanımlamak için yöntemi veya oluşturucuyu temsil eden bir veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="b8acb-107">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="b8acb-108">'ndaki Genel parametrenin dizini.</span><span class="sxs-lookup"><span data-stu-id="b8acb-108">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="b8acb-109">'ndaki Genel parametrenin türünü açıklayan [CorGenericParamAttr](corgenericparamattr-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="b8acb-109">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="b8acb-110">'ndaki Parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="b8acb-110">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="b8acb-111">'ndaki Bu parametre gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b8acb-111">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="b8acb-112">'ndaki Tür kısıtlamaları sıfır ile sonlandırılmış dizi.</span><span class="sxs-lookup"><span data-stu-id="b8acb-112">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="b8acb-113">Dizi üyeleri bir `mdTypeDef` , `mdTypeRef` veya `mdTypeSpec` meta veri belirteci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8acb-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="b8acb-114">dışı Genel parametreyi temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="b8acb-114">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8acb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8acb-115">Requirements</span></span>  

 <span data-ttu-id="b8acb-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8acb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8acb-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b8acb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8acb-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b8acb-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8acb-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8acb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8acb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8acb-120">See also</span></span>

- [<span data-ttu-id="b8acb-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8acb-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="b8acb-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8acb-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
