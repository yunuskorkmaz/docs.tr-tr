---
title: "IMetaDataAssemblyImport::EnumFiles Yöntemi"
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
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5ce0682f6f7719c902183778578d75dd19d56867
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="c43af-102">IMetaDataAssemblyImport::EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c43af-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="c43af-103">Geçerli derleme bildiriminde başvurulan dosyaları sıralar.</span><span class="sxs-lookup"><span data-stu-id="c43af-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c43af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c43af-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c43af-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c43af-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c43af-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c43af-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c43af-107">Bu, bu yöntem ilk çağrısı için boş bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c43af-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="c43af-108">[out] Depolamak için kullanılan dizi `mdFile` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="c43af-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c43af-109">[in] En fazla sayısını `mdFile` yerleştirilebilir belirteçleri `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="c43af-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c43af-110">[out] Sayısı `mdFile` belirteçleri gerçekten yerleştirilen `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="c43af-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c43af-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c43af-111">Return Value</span></span>  
  
|<span data-ttu-id="c43af-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c43af-112">HRESULT</span></span>|<span data-ttu-id="c43af-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c43af-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c43af-114">`EnumFiles`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c43af-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c43af-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="c43af-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c43af-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c43af-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c43af-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c43af-117">Requirements</span></span>  
 <span data-ttu-id="c43af-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c43af-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c43af-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c43af-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c43af-120">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c43af-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c43af-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c43af-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c43af-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c43af-122">See Also</span></span>  
 [<span data-ttu-id="c43af-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c43af-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
