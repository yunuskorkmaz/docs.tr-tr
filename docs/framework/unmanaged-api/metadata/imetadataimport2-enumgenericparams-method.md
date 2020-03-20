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
ms.openlocfilehash: 55709e79cd8bdb36fe1e32ee8a699fccb1b1bbc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175310"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="4426a-102">IMetaDataImport2::EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4426a-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="4426a-103">Belirtilen TypeDef veya MethodDef belirteciyle ilişkili genel parametre belirteçleri dizisi için bir sayısallaştırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="4426a-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4426a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4426a-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4426a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4426a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4426a-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4426a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="4426a-107">[içinde] Genel parametreleri numaralandırılacak Olan TypeDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="4426a-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="4426a-108">[çıkış] Sayısala' da genel parametreler dizisi.</span><span class="sxs-lookup"><span data-stu-id="4426a-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4426a-109">[içinde] Yerleştirilecek istenen maksimum belirteç `rGenericParams`sayısı.</span><span class="sxs-lookup"><span data-stu-id="4426a-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="4426a-110">[çıkış] Yerleştirilen belirteçlerin döndürülen `rGenericParams`sayısı.</span><span class="sxs-lookup"><span data-stu-id="4426a-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4426a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4426a-111">Return Value</span></span>  
  
|<span data-ttu-id="4426a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4426a-112">HRESULT</span></span>|<span data-ttu-id="4426a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4426a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4426a-114">`EnumGenericParams`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4426a-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4426a-115">`phEnum`üye öğesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4426a-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="4426a-116">Bu durumda, `pcGenericParams` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4426a-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4426a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4426a-117">Requirements</span></span>  
 <span data-ttu-id="4426a-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4426a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4426a-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4426a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4426a-120">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4426a-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4426a-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4426a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4426a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4426a-122">See also</span></span>

- [<span data-ttu-id="4426a-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4426a-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="4426a-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4426a-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
