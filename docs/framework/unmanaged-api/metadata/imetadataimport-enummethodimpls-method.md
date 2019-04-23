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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09bd9f4029f5e4609ab1ef6f49a4364e83f1edfb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184583"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="7a6f6-102">IMetaDataImport::EnumMethodImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a6f6-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="7a6f6-103">Belirtilen türün yöntemlerini temsil eden MethodBody ve MethodDeclaration belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a6f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a6f6-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a6f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a6f6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7a6f6-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7a6f6-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="7a6f6-108">[in] Numaralandırmak için yöntem uygulamaları simge türü için bir TypeDef.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="7a6f6-109">[out] MethodBody simgeleri depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="7a6f6-110">[out] MethodDeclaration simgeleri depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7a6f6-111">[in] En büyük boyutunu `rMethodBody` ve `rMethodDecl` dizileri.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7a6f6-112">[in] Döndürülen yöntemleri gerçek sayısını `rMethodBody` ve `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a6f6-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a6f6-113">Return Value</span></span>  
  
|<span data-ttu-id="7a6f6-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a6f6-114">HRESULT</span></span>|<span data-ttu-id="7a6f6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a6f6-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7a6f6-116">`EnumMethodImpls` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7a6f6-117">Numaralandırılacak hiçbir yöntemi belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="7a6f6-118">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a6f6-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a6f6-119">Requirements</span></span>  
 <span data-ttu-id="7a6f6-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a6f6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a6f6-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7a6f6-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a6f6-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7a6f6-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a6f6-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a6f6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6f6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a6f6-124">See also</span></span>

- [<span data-ttu-id="7a6f6-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a6f6-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7a6f6-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a6f6-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
