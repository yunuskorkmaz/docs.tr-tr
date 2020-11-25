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
ms.openlocfilehash: 6b1a8e66eea6caec9dfc8d99e343c987cefa1b0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702764"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="963ad-102">IMetaDataImport2::EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="963ad-102">IMetaDataImport2::EnumGenericParams Method</span></span>

<span data-ttu-id="963ad-103">Belirtilen TypeDef veya MethodDef belirteciyle ilişkili bir genel parametre belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="963ad-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="963ad-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="963ad-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="963ad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="963ad-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="963ad-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="963ad-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="963ad-107">'ndaki Genel parametreleri numaralandırılmış olan TypeDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="963ad-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="963ad-108">dışı Numaralandırılacak genel parametrelerin dizisi.</span><span class="sxs-lookup"><span data-stu-id="963ad-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="963ad-109">'ndaki İstenen en fazla belirteç sayısı, içine yerleştirilecek `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="963ad-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="963ad-110">dışı Döndürülen belirteç sayısı döndürüldü `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="963ad-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="963ad-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="963ad-111">Return Value</span></span>  
  
|<span data-ttu-id="963ad-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="963ad-112">HRESULT</span></span>|<span data-ttu-id="963ad-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="963ad-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="963ad-114">`EnumGenericParams` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="963ad-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="963ad-115">`phEnum` Üye öğesi yok.</span><span class="sxs-lookup"><span data-stu-id="963ad-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="963ad-116">Bu durumda, `pcGenericParams` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="963ad-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="963ad-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="963ad-117">Requirements</span></span>  

 <span data-ttu-id="963ad-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="963ad-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="963ad-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="963ad-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="963ad-120">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="963ad-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="963ad-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="963ad-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963ad-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="963ad-122">See also</span></span>

- [<span data-ttu-id="963ad-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="963ad-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="963ad-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="963ad-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
