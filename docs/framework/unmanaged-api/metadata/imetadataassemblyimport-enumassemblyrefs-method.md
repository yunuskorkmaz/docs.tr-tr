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
ms.openlocfilehash: ba85ec920777189940a05864d19e4c24a65b4564
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499500"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="80929-102">IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80929-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="80929-103">Numaralandırır `mdAssemblyRef` derleme bildiriminde tanımlanan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="80929-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80929-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80929-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80929-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80929-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="80929-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80929-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="80929-107">Bu boş olmalıdır ne zaman değer `EnumAssemblyRefs` yöntemi ilk kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="80929-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="80929-108">[out] Numaralandırmasını `mdAssemblyRef` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="80929-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="80929-109">[in] Yerleştirilebilir belirteçleri sayısı `rAssemblyRefs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="80929-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="80929-110">[out] Belirteçleri sayısı gerçekte yerleştirilen `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="80929-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80929-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="80929-111">Return Value</span></span>  
  
|<span data-ttu-id="80929-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80929-112">HRESULT</span></span>|<span data-ttu-id="80929-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80929-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="80929-114">`EnumAssemblyRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="80929-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="80929-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="80929-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="80929-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="80929-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80929-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80929-117">Requirements</span></span>  
 <span data-ttu-id="80929-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80929-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80929-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="80929-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80929-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="80929-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80929-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80929-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80929-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80929-122">See also</span></span>
- [<span data-ttu-id="80929-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80929-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
