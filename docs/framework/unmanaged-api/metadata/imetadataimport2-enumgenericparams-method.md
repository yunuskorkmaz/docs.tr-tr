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
ms.openlocfilehash: 7edd2eeafcce6a22c3256d0684a9c4f961b34002
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157644"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="14324-102">IMetaDataImport2::EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14324-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="14324-103">Bir numaralandırıcı genel parametre belirteçleri belirtilen TypeDef veya MethodDef ilişkili bir dizisi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="14324-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14324-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14324-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14324-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14324-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="14324-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="14324-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="14324-107">[in] Numaralandırılacak genel parametreleri olan TypeDef veya MethodDef belirteç.</span><span class="sxs-lookup"><span data-stu-id="14324-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="14324-108">[out] Numaralandırılacak genel parametreler dizisi.</span><span class="sxs-lookup"><span data-stu-id="14324-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="14324-109">[in] İstenen sayısı yerleştirmek için belirteçleri `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="14324-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="14324-110">[out] Döndürülen belirteç sayısı yerleştirilen `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="14324-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14324-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="14324-111">Return Value</span></span>  
  
|<span data-ttu-id="14324-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14324-112">HRESULT</span></span>|<span data-ttu-id="14324-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14324-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams` <span data-ttu-id="14324-114">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="14324-114">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="14324-115">üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="14324-115">has no member elements.</span></span> <span data-ttu-id="14324-116">Bu durumda, `pcGenericParams` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="14324-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14324-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14324-117">Requirements</span></span>  
 <span data-ttu-id="14324-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14324-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14324-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="14324-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14324-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="14324-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="14324-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="14324-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="14324-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14324-122">See also</span></span>

- [<span data-ttu-id="14324-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14324-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="14324-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14324-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
