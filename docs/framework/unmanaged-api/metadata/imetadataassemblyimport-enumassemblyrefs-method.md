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
ms.openlocfilehash: 91e253669b9f51e7c1d600ba11f13a9ce67fb58a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072486"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="d8e1a-102">IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8e1a-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="d8e1a-103">Numaralandırır `mdAssemblyRef` derleme bildiriminde tanımlanan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8e1a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8e1a-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8e1a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8e1a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d8e1a-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d8e1a-107">Bu boş olmalıdır ne zaman değer `EnumAssemblyRefs` yöntemi ilk kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="d8e1a-108">[out] Numaralandırmasını `mdAssemblyRef` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d8e1a-109">[in] Yerleştirilebilir belirteçleri sayısı `rAssemblyRefs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d8e1a-110">[out] Belirteçleri sayısı gerçekte yerleştirilen `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8e1a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d8e1a-111">Return Value</span></span>  
  
|<span data-ttu-id="d8e1a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8e1a-112">HRESULT</span></span>|<span data-ttu-id="d8e1a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8e1a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumAssemblyRefs` <span data-ttu-id="d8e1a-114">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d8e1a-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d8e1a-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8e1a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8e1a-117">Requirements</span></span>  
 <span data-ttu-id="d8e1a-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8e1a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8e1a-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d8e1a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8e1a-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="d8e1a-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d8e1a-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d8e1a-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d8e1a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8e1a-122">See also</span></span>

- [<span data-ttu-id="d8e1a-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8e1a-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
