---
title: "IMetaDataImport::EnumTypeDefs Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeDefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a07d9ff237e6d3838fffb068e3a9ebf9febf66fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="3dfa4-102">IMetaDataImport::EnumTypeDefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3dfa4-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="3dfa4-103">Geçerli kapsamdaki tüm türleri temsil eden TypeDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dfa4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3dfa4-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3dfa4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3dfa4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3dfa4-106">[out] Yeni Numaralandırıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="3dfa4-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="3dfa4-108">[in] TypeDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3dfa4-109">[in] En büyük boyutunu `rTypeDefs` dizi.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="3dfa4-110">[out] Döndürülen TypeDef belirteçleri sayısı `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dfa4-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3dfa4-111">Return Value</span></span>  
  
|<span data-ttu-id="3dfa4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3dfa4-112">HRESULT</span></span>|<span data-ttu-id="3dfa4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3dfa4-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3dfa4-114">`EnumTypeDefs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3dfa4-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3dfa4-116">Bu durumda, `pcTypeDefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3dfa4-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dfa4-117">Remarks</span></span>  
 <span data-ttu-id="3dfa4-118">TypeDef belirteci genişletilebilirlik mekanizması eklenen herhangi bir tür yanı sıra, bir sınıf veya arabirim gibi bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dfa4-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3dfa4-119">Requirements</span></span>  
 <span data-ttu-id="3dfa4-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dfa4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dfa4-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3dfa4-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3dfa4-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3dfa4-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3dfa4-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dfa4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dfa4-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3dfa4-124">See Also</span></span>  
 [<span data-ttu-id="3dfa4-125">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dfa4-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3dfa4-126">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dfa4-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
