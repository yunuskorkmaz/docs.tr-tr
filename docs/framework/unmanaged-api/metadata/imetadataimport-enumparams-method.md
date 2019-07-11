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
ms.openlocfilehash: d64a39dcdb6e3b26ff38106673719e475315f5dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782117"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="21c48-102">IMetaDataImport::EnumParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21c48-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="21c48-103">Belirtilen MethodDef belirteci tarafından başvurulan yönteminin parametreleri temsil eden ParamDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="21c48-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c48-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21c48-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21c48-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21c48-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="21c48-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21c48-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="21c48-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21c48-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="21c48-108">[in] Numaralandırılacak parametrelere sahip bir yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="21c48-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="21c48-109">[out] Dizi ParamDef simgeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21c48-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="21c48-110">[in] En büyük boyutunu `rParams` dizisi.</span><span class="sxs-lookup"><span data-stu-id="21c48-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="21c48-111">[out] Döndürülen ParamDef belirteçleri sayısı `rParams`.</span><span class="sxs-lookup"><span data-stu-id="21c48-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21c48-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21c48-112">Return Value</span></span>  
  
|<span data-ttu-id="21c48-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21c48-113">HRESULT</span></span>|<span data-ttu-id="21c48-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21c48-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="21c48-115">`EnumParams` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="21c48-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="21c48-116">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="21c48-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="21c48-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="21c48-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21c48-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21c48-118">Requirements</span></span>  
 <span data-ttu-id="21c48-119">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21c48-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21c48-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="21c48-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21c48-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="21c48-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21c48-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21c48-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c48-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21c48-123">See also</span></span>

- [<span data-ttu-id="21c48-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21c48-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="21c48-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21c48-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
