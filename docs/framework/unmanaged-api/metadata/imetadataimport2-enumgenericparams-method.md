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
ms.openlocfilehash: 093e3edf0a3c06222ebc56a4876fca08d1b7578f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490737"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="87436-102">IMetaDataImport2::EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87436-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="87436-103">Belirtilen TypeDef veya MethodDef belirteciyle ilişkili bir genel parametre belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="87436-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87436-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="87436-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87436-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87436-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="87436-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="87436-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="87436-107">'ndaki Genel parametreleri numaralandırılmış olan TypeDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="87436-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="87436-108">dışı Numaralandırılacak genel parametrelerin dizisi.</span><span class="sxs-lookup"><span data-stu-id="87436-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="87436-109">'ndaki İstenen en fazla belirteç sayısı, içine yerleştirilecek `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="87436-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="87436-110">dışı Döndürülen belirteç sayısı döndürüldü `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="87436-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87436-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="87436-111">Return Value</span></span>  
  
|<span data-ttu-id="87436-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87436-112">HRESULT</span></span>|<span data-ttu-id="87436-113">Description</span><span class="sxs-lookup"><span data-stu-id="87436-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="87436-114">`EnumGenericParams`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="87436-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="87436-115">`phEnum`Üye öğesi yok.</span><span class="sxs-lookup"><span data-stu-id="87436-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="87436-116">Bu durumda, `pcGenericParams` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="87436-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87436-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87436-117">Requirements</span></span>  
 <span data-ttu-id="87436-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87436-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87436-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="87436-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87436-120">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="87436-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87436-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87436-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87436-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87436-122">See also</span></span>

- [<span data-ttu-id="87436-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87436-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="87436-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87436-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
