---
title: IMetaDataImport2::EnumGenericParams Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ecd1c714f41c76833ef6a0a4b7be87e338ca1a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448836"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="3628d-102">IMetaDataImport2::EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3628d-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="3628d-103">Bir numaralandırıcı genel parametresini belirteçleri belirtilen TypeDef veya MethodDef ilişkili bir dizi belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="3628d-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3628d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3628d-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3628d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3628d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3628d-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3628d-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="3628d-107">[in] Numaralandırılacak genel parametreleri olan TypeDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="3628d-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="3628d-108">[out] Numaralandırılacak genel parametreleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="3628d-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3628d-109">[in] İstenen sayısı yerleştirmek için belirteçleri `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="3628d-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="3628d-110">[out] Sıraya alınan belirteçleri döndürülen sayısıdır `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="3628d-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3628d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3628d-111">Return Value</span></span>  
  
|<span data-ttu-id="3628d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3628d-112">HRESULT</span></span>|<span data-ttu-id="3628d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3628d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3628d-114">`EnumGenericParams` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3628d-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3628d-115">`phEnum` hiç üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="3628d-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="3628d-116">Bu durumda, `pcGenericParams` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3628d-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3628d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3628d-117">Requirements</span></span>  
 <span data-ttu-id="3628d-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3628d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3628d-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3628d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3628d-120">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3628d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3628d-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3628d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3628d-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3628d-122">See Also</span></span>  
 [<span data-ttu-id="3628d-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3628d-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="3628d-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3628d-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
