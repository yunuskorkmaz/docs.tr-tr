---
description: ': IMetaDataImport:: EnumProperties metodu hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumProperties Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
ms.openlocfilehash: 7503dd14668e8ea4ccf8939e67b91a41db187105
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799362"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="753c9-103">IMetaDataImport::EnumProperties Yöntemi</span><span class="sxs-lookup"><span data-stu-id="753c9-103">IMetaDataImport::EnumProperties Method</span></span>

<span data-ttu-id="753c9-104">Belirtilen TypeDef belirtecinin başvurduğu türün özelliklerini temsil eden PropertyDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="753c9-104">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="753c9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="753c9-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="753c9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="753c9-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="753c9-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="753c9-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="753c9-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="753c9-108">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="753c9-109">'ndaki Numaralandırılacak özellikleri olan türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="753c9-109">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="753c9-110">dışı PropertyDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="753c9-110">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="753c9-111">'ndaki Dizinin en büyük boyutu `rProperties` .</span><span class="sxs-lookup"><span data-stu-id="753c9-111">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="753c9-112">dışı İçinde döndürülen PropertyDef belirteçleri sayısı `rProperties` .</span><span class="sxs-lookup"><span data-stu-id="753c9-112">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="753c9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="753c9-113">Return Value</span></span>  
  
|<span data-ttu-id="753c9-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="753c9-114">HRESULT</span></span>|<span data-ttu-id="753c9-115">Description</span><span class="sxs-lookup"><span data-stu-id="753c9-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="753c9-116">`EnumProperties` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="753c9-116">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="753c9-117">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="753c9-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="753c9-118">Bu durumda, `pcProperties` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="753c9-118">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="753c9-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="753c9-119">Requirements</span></span>  

 <span data-ttu-id="753c9-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="753c9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="753c9-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="753c9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="753c9-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="753c9-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="753c9-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="753c9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753c9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="753c9-124">See also</span></span>

- [<span data-ttu-id="753c9-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="753c9-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="753c9-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="753c9-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
