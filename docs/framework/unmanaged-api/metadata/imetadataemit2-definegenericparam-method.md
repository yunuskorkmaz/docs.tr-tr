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
ms.openlocfilehash: 1868d13a9dbb73dbdf64e49c395bdbff02ce89d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177448"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="74835-102">IMetaDataEmit2::DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74835-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="74835-103">Genel bir tür parametresi için bir tanım oluşturur ve bu genel tür parametreiçin bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="74835-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74835-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74835-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="74835-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74835-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="74835-106">[içinde] Genel `mdTypeDef` `mdMethodDef` bir parametreyi tanımlamak için yöntemi veya oluşturucuyu temsil eden bir veya belirteç.</span><span class="sxs-lookup"><span data-stu-id="74835-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="74835-107">[içinde] Genel parametrenin dizini.</span><span class="sxs-lookup"><span data-stu-id="74835-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="74835-108">[içinde] Genel parametrenin türünü açıklayan [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) numaralandırmadeğeri.</span><span class="sxs-lookup"><span data-stu-id="74835-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="74835-109">[içinde] Parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="74835-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="74835-110">[içinde] Bu parametre gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="74835-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="74835-111">[içinde] Sıfır sonlandırılmış tür kısıtlamaları dizisi.</span><span class="sxs-lookup"><span data-stu-id="74835-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="74835-112">Dizi üyeleri bir `mdTypeDef` `mdTypeRef`, `mdTypeSpec` veya meta veri belirteci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74835-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="74835-113">[çıkış] Genel parametreyi temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="74835-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74835-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74835-114">Requirements</span></span>  
 <span data-ttu-id="74835-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74835-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74835-116">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74835-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74835-117">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="74835-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74835-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74835-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74835-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74835-119">See also</span></span>

- [<span data-ttu-id="74835-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74835-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="74835-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74835-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
