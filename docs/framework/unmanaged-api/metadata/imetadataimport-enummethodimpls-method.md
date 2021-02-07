---
description: ': IMetaDataImport:: EnumMethodImpls yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 3ae5795bdde36ad07c447370553e24e1ceacf493
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670703"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="8d5dc-103">IMetaDataImport::EnumMethodImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d5dc-103">IMetaDataImport::EnumMethodImpls Method</span></span>

<span data-ttu-id="8d5dc-104">Belirtilen türdeki yöntemleri temsil eden MethodBody ve MethodDeclaration belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-104">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d5dc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d5dc-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8d5dc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d5dc-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="8d5dc-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8d5dc-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-108">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="8d5dc-109">'ndaki Yöntem uygulamaları Numaralandırılacak tür için bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-109">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="8d5dc-110">dışı MethodBody belirteçlerini depolayacak dizi.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-110">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="8d5dc-111">dışı MethodDeclaration belirteçlerini depolayacak dizi.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-111">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8d5dc-112">'ndaki Ve dizilerinin en büyük boyutu `rMethodBody` `rMethodDecl` .</span><span class="sxs-lookup"><span data-stu-id="8d5dc-112">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8d5dc-113">'ndaki Ve ' de döndürülen gerçek Yöntem sayısı `rMethodBody` `rMethodDecl` .</span><span class="sxs-lookup"><span data-stu-id="8d5dc-113">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d5dc-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8d5dc-114">Return Value</span></span>  
  
|<span data-ttu-id="8d5dc-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d5dc-115">HRESULT</span></span>|<span data-ttu-id="8d5dc-116">Description</span><span class="sxs-lookup"><span data-stu-id="8d5dc-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8d5dc-117">`EnumMethodImpls` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-117">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8d5dc-118">Numaralandırılacak hiçbir yöntem belirteci yok.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-118">There are no method tokens to enumerate.</span></span> <span data-ttu-id="8d5dc-119">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d5dc-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d5dc-120">Requirements</span></span>  

 <span data-ttu-id="8d5dc-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d5dc-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d5dc-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8d5dc-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d5dc-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8d5dc-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d5dc-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d5dc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d5dc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d5dc-125">See also</span></span>

- [<span data-ttu-id="8d5dc-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d5dc-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8d5dc-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d5dc-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
