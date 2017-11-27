---
title: "IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumAssemblyRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 24a289ed42a99cd26c7829d9a5789ac3027026c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="1cc3b-102">IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1cc3b-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="1cc3b-103">Sıralar `mdAssemblyRef` derleme bildiriminde tanımlanan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cc3b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cc3b-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cc3b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1cc3b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1cc3b-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1cc3b-107">Bu bir null olmalıdır değeri `EnumAssemblyRefs` yöntemi ilk kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="1cc3b-108">[out] Numaralandırması `mdAssemblyRef` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1cc3b-109">[in] Yerleştirilebilir belirteçleri en fazla `rAssemblyRefs` dizi.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="1cc3b-110">[out] Belirteçleri sayısı gerçekte yerleştirilen `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cc3b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1cc3b-111">Return Value</span></span>  
  
|<span data-ttu-id="1cc3b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1cc3b-112">HRESULT</span></span>|<span data-ttu-id="1cc3b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1cc3b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1cc3b-114">`EnumAssemblyRefs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1cc3b-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="1cc3b-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1cc3b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1cc3b-117">Requirements</span></span>  
 <span data-ttu-id="1cc3b-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cc3b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cc3b-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1cc3b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1cc3b-120">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1cc3b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1cc3b-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cc3b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc3b-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1cc3b-122">See Also</span></span>  
 [<span data-ttu-id="1cc3b-123">Imetadataassemblyımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cc3b-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
