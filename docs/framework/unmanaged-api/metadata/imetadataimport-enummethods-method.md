---
title: "IMetaDataImport::EnumMethods Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d56c87d7073886d13e530501168801c6c69d9ce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="34b86-102">IMetaDataImport::EnumMethods Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34b86-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="34b86-103">Belirtilen türdeki yöntemleri temsil eden MethodDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="34b86-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34b86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34b86-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34b86-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34b86-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="34b86-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="34b86-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="34b86-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34b86-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="34b86-108">[in] Numaralandırılacak yöntemleriyle türünü temsil eden bir TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="34b86-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="34b86-109">[out] MethodDef belirteçleri depolama dizisi.</span><span class="sxs-lookup"><span data-stu-id="34b86-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="34b86-110">[in] En büyük boyutunu MethodDef `rMethods` dizi.</span><span class="sxs-lookup"><span data-stu-id="34b86-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="34b86-111">[out] Döndürülen MethodDef belirteçleri sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="34b86-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34b86-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34b86-112">Return Value</span></span>  
  
|<span data-ttu-id="34b86-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34b86-113">HRESULT</span></span>|<span data-ttu-id="34b86-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34b86-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="34b86-115">`EnumMethods`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="34b86-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="34b86-116">Numaralandırılacak hiçbir MethodDef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="34b86-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="34b86-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="34b86-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34b86-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34b86-118">Requirements</span></span>  
 <span data-ttu-id="34b86-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34b86-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34b86-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="34b86-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34b86-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="34b86-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="34b86-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34b86-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b86-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34b86-123">See Also</span></span>  
 [<span data-ttu-id="34b86-124">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="34b86-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="34b86-125">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="34b86-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
