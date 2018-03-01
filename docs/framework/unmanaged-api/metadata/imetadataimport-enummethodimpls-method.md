---
title: "IMetaDataImport::EnumMethodImpls Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e3350fb4513604a0edc47cbf47e257648ff0d75a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="f100d-102">IMetaDataImport::EnumMethodImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f100d-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="f100d-103">Belirtilen türdeki yöntemleri temsil eden MethodBody ve MethodDeclaration belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="f100d-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f100d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f100d-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f100d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f100d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f100d-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f100d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f100d-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f100d-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="f100d-108">[in] Bir TypeDef numaralandırmak için yöntem uygulamalarını türü için simge.</span><span class="sxs-lookup"><span data-stu-id="f100d-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="f100d-109">[out] MethodBody belirteçleri depolama dizisi.</span><span class="sxs-lookup"><span data-stu-id="f100d-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="f100d-110">[out] MethodDeclaration belirteçleri depolama dizisi.</span><span class="sxs-lookup"><span data-stu-id="f100d-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f100d-111">[in] En büyük boyutunu `rMethodBody` ve `rMethodDecl` dizileri.</span><span class="sxs-lookup"><span data-stu-id="f100d-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f100d-112">[in] Döndürülen yöntemleri gerçek sayısını `rMethodBody` ve `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="f100d-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f100d-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f100d-113">Return Value</span></span>  
  
|<span data-ttu-id="f100d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f100d-114">HRESULT</span></span>|<span data-ttu-id="f100d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f100d-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f100d-116">`EnumMethodImpls`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f100d-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f100d-117">Numaralandırılacak hiçbir yöntemi belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f100d-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="f100d-118">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="f100d-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f100d-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f100d-119">Requirements</span></span>  
 <span data-ttu-id="f100d-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f100d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f100d-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f100d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f100d-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f100d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f100d-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f100d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f100d-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f100d-124">See Also</span></span>  
 [<span data-ttu-id="f100d-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f100d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f100d-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f100d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
