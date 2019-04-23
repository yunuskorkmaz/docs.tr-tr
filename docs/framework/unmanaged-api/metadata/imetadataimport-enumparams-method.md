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
ms.openlocfilehash: 4ed5ddd74e61e63426871f659aa1c962d38fd534
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221407"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="5138f-102">IMetaDataImport::EnumParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5138f-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="5138f-103">Belirtilen MethodDef belirteci tarafından başvurulan yönteminin parametreleri temsil eden ParamDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="5138f-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5138f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5138f-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5138f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5138f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5138f-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5138f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5138f-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5138f-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="5138f-108">[in] Numaralandırılacak parametrelere sahip bir yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="5138f-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="5138f-109">[out] Dizi ParamDef simgeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5138f-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5138f-110">[in] En büyük boyutunu `rParams` dizisi.</span><span class="sxs-lookup"><span data-stu-id="5138f-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5138f-111">[out] Döndürülen ParamDef belirteçleri sayısı `rParams`.</span><span class="sxs-lookup"><span data-stu-id="5138f-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5138f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5138f-112">Return Value</span></span>  
  
|<span data-ttu-id="5138f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5138f-113">HRESULT</span></span>|<span data-ttu-id="5138f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5138f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5138f-115">`EnumParams` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5138f-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5138f-116">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="5138f-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="5138f-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="5138f-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5138f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5138f-118">Requirements</span></span>  
 <span data-ttu-id="5138f-119">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5138f-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5138f-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5138f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5138f-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="5138f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5138f-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5138f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5138f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5138f-123">See also</span></span>

- [<span data-ttu-id="5138f-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5138f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5138f-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5138f-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
