---
title: IMetaDataImport::EnumMethodImpls Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
ms.openlocfilehash: b8fabea78f85448e39fc6d31f0a7969458343877
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492028"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="7f010-102">IMetaDataImport::EnumMethodImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f010-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="7f010-103">Belirtilen türdeki yöntemleri temsil eden MethodBody ve MethodDeclaration belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7f010-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f010-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7f010-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdToken     rMethodBody[],
   [out]     mdToken     rMethodDecl[],
   [in]      ULONG       cMax,
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f010-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f010-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7f010-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7f010-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7f010-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f010-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="7f010-108">'ndaki Yöntem uygulamaları Numaralandırılacak tür için bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="7f010-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="7f010-109">dışı MethodBody belirteçlerini depolayacak dizi.</span><span class="sxs-lookup"><span data-stu-id="7f010-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="7f010-110">dışı MethodDeclaration belirteçlerini depolayacak dizi.</span><span class="sxs-lookup"><span data-stu-id="7f010-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7f010-111">'ndaki Ve dizilerinin en büyük boyutu `rMethodBody` `rMethodDecl` .</span><span class="sxs-lookup"><span data-stu-id="7f010-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7f010-112">'ndaki Ve ' de döndürülen gerçek Yöntem sayısı `rMethodBody` `rMethodDecl` .</span><span class="sxs-lookup"><span data-stu-id="7f010-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f010-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f010-113">Return Value</span></span>  
  
|<span data-ttu-id="7f010-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f010-114">HRESULT</span></span>|<span data-ttu-id="7f010-115">Description</span><span class="sxs-lookup"><span data-stu-id="7f010-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7f010-116">`EnumMethodImpls`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7f010-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7f010-117">Numaralandırılacak hiçbir yöntem belirteci yok.</span><span class="sxs-lookup"><span data-stu-id="7f010-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="7f010-118">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="7f010-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f010-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f010-119">Requirements</span></span>  
 <span data-ttu-id="7f010-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f010-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f010-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7f010-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f010-122">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7f010-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f010-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f010-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f010-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f010-124">See also</span></span>

- [<span data-ttu-id="7f010-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f010-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7f010-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f010-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
