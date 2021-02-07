---
description: 'Daha fazla bilgi edinin: IMetaDataImport2:: EnumGenericParams yöntemi'
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
ms.openlocfilehash: 9d4e9d163da07ec4a3af1aa628b8b6ec4b2338fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720962"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="46afb-103">IMetaDataImport2::EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46afb-103">IMetaDataImport2::EnumGenericParams Method</span></span>

<span data-ttu-id="46afb-104">Belirtilen TypeDef veya MethodDef belirteciyle ilişkili bir genel parametre belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="46afb-104">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46afb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46afb-105">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46afb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46afb-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="46afb-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="46afb-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="46afb-108">'ndaki Genel parametreleri numaralandırılmış olan TypeDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="46afb-108">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="46afb-109">dışı Numaralandırılacak genel parametrelerin dizisi.</span><span class="sxs-lookup"><span data-stu-id="46afb-109">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="46afb-110">'ndaki İstenen en fazla belirteç sayısı, içine yerleştirilecek `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="46afb-110">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="46afb-111">dışı Döndürülen belirteç sayısı döndürüldü `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="46afb-111">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46afb-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="46afb-112">Return Value</span></span>  
  
|<span data-ttu-id="46afb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46afb-113">HRESULT</span></span>|<span data-ttu-id="46afb-114">Description</span><span class="sxs-lookup"><span data-stu-id="46afb-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="46afb-115">`EnumGenericParams` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="46afb-115">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="46afb-116">`phEnum` Üye öğesi yok.</span><span class="sxs-lookup"><span data-stu-id="46afb-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="46afb-117">Bu durumda, `pcGenericParams` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="46afb-117">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46afb-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46afb-118">Requirements</span></span>  

 <span data-ttu-id="46afb-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46afb-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46afb-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="46afb-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46afb-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="46afb-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46afb-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46afb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46afb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46afb-123">See also</span></span>

- [<span data-ttu-id="46afb-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46afb-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="46afb-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46afb-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
