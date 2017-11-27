---
title: "IMetaDataAssemblyImport::EnumManifestResources Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumManifestResources
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25d8b63e2f40566164274715e562960eafbb83e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="29f07-102">IMetaDataAssemblyImport::EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29f07-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="29f07-103">Bir işaretçi geçerli derleme bildiriminde başvurulan kaynaklar için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="29f07-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29f07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29f07-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="29f07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29f07-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="29f07-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="29f07-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="29f07-107">Bu bir null olmalıdır değeri `EnumManifestResources` yöntemi ilk kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="29f07-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="29f07-108">[out] Depolamak için kullanılan dizi `mdManifestResource` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="29f07-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="29f07-109">[in] En fazla sayısını `mdManifestResource` yerleştirilebilir belirteçleri `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="29f07-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="29f07-110">[out] Sayısı `mdManifestResource` belirteçleri gerçekten yerleştirilen `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="29f07-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29f07-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="29f07-111">Return Value</span></span>  
  
|<span data-ttu-id="29f07-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29f07-112">HRESULT</span></span>|<span data-ttu-id="29f07-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29f07-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="29f07-114">`EnumManifestResources`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="29f07-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="29f07-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="29f07-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="29f07-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="29f07-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29f07-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29f07-117">Requirements</span></span>  
 <span data-ttu-id="29f07-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29f07-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29f07-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29f07-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29f07-120">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="29f07-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29f07-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29f07-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f07-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29f07-122">See Also</span></span>  
 [<span data-ttu-id="29f07-123">Imetadataassemblyımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="29f07-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
