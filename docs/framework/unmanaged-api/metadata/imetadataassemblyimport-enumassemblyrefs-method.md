---
title: IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a56d874e5e7ef491c24b0aef2ace700087de677
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447417"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="5cdbe-102">IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cdbe-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="5cdbe-103">Sıralar `mdAssemblyRef` derleme bildiriminde tanımlanan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cdbe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cdbe-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cdbe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cdbe-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5cdbe-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5cdbe-107">Bu bir null olmalıdır değeri `EnumAssemblyRefs` yöntemi ilk kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="5cdbe-108">[out] Numaralandırması `mdAssemblyRef` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5cdbe-109">[in] Yerleştirilebilir belirteçleri en fazla `rAssemblyRefs` dizi.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5cdbe-110">[out] Belirteçleri sayısı gerçekte yerleştirilen `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cdbe-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5cdbe-111">Return Value</span></span>  
  
|<span data-ttu-id="5cdbe-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cdbe-112">HRESULT</span></span>|<span data-ttu-id="5cdbe-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cdbe-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5cdbe-114">`EnumAssemblyRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5cdbe-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="5cdbe-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cdbe-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cdbe-117">Requirements</span></span>  
 <span data-ttu-id="5cdbe-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cdbe-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cdbe-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5cdbe-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cdbe-120">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5cdbe-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5cdbe-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cdbe-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdbe-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cdbe-122">See Also</span></span>  
 [<span data-ttu-id="5cdbe-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5cdbe-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
