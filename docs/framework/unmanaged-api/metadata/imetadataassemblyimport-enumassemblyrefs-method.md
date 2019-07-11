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
ms.openlocfilehash: 5c7b512de76b5ada882b1d81c2968b4ead5c8c20
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775936"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="d785a-102">IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d785a-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="d785a-103">Numaralandırır `mdAssemblyRef` derleme bildiriminde tanımlanan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d785a-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d785a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d785a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d785a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d785a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d785a-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d785a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d785a-107">Bu boş olmalıdır ne zaman değer `EnumAssemblyRefs` yöntemi ilk kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d785a-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="d785a-108">[out] Numaralandırmasını `mdAssemblyRef` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d785a-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d785a-109">[in] Yerleştirilebilir belirteçleri sayısı `rAssemblyRefs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="d785a-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d785a-110">[out] Belirteçleri sayısı gerçekte yerleştirilen `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="d785a-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d785a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d785a-111">Return Value</span></span>  
  
|<span data-ttu-id="d785a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d785a-112">HRESULT</span></span>|<span data-ttu-id="d785a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d785a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d785a-114">`EnumAssemblyRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d785a-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d785a-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="d785a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d785a-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d785a-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d785a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d785a-117">Requirements</span></span>  
 <span data-ttu-id="d785a-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d785a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d785a-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d785a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d785a-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="d785a-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d785a-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d785a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d785a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d785a-122">See also</span></span>

- [<span data-ttu-id="d785a-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d785a-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
