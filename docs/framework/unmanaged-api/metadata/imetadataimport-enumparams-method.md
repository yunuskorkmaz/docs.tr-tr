---
title: IMetaDataImport::EnumParams Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b848c30e824d45f6f619cfdb3d00a2d3cdc4573e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448719"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="1ecc6-102">IMetaDataImport::EnumParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ecc6-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="1ecc6-103">Belirtilen MethodDef belirteç tarafından başvurulan yönteminin parametreleri temsil eden ParamDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ecc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ecc6-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ecc6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ecc6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1ecc6-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1ecc6-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="1ecc6-108">[in] Numaralandırma parametrelerle yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="1ecc6-109">[out] ParamDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1ecc6-110">[in] En büyük boyutunu `rParams` dizi.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="1ecc6-111">[out] Döndürülen ParamDef belirteçleri sayısı `rParams`.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ecc6-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1ecc6-112">Return Value</span></span>  
  
|<span data-ttu-id="1ecc6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ecc6-113">HRESULT</span></span>|<span data-ttu-id="1ecc6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ecc6-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1ecc6-115">`EnumParams` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1ecc6-116">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="1ecc6-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ecc6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ecc6-118">Requirements</span></span>  
 <span data-ttu-id="1ecc6-119">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ecc6-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ecc6-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ecc6-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ecc6-121">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1ecc6-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ecc6-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ecc6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ecc6-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-123">See Also</span></span>  
 [<span data-ttu-id="1ecc6-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ecc6-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1ecc6-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ecc6-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
