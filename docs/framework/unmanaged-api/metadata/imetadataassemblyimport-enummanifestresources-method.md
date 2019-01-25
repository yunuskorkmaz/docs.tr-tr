---
title: IMetaDataAssemblyImport::EnumManifestResources Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cffafe9c8eac03d31c2b0b45dd65ed2c5b28861
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722652"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="275ed-102">IMetaDataAssemblyImport::EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="275ed-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="275ed-103">Bir işaretçi geçerli derleme bildiriminde atıf yapılan kaynakları için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="275ed-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="275ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="275ed-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="275ed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="275ed-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="275ed-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="275ed-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="275ed-107">Bu boş olmalıdır ne zaman değer `EnumManifestResources` yöntemi ilk kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="275ed-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="275ed-108">[out] Depolamak için kullanılan bir dizi `mdManifestResource` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="275ed-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="275ed-109">[in] En fazla `mdManifestResource` yerleştirilebilir belirteçleri `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="275ed-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="275ed-110">[out] Sayısını `mdManifestResource` belirteçleri gerçekten yerleştirilen `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="275ed-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="275ed-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="275ed-111">Return Value</span></span>  
  
|<span data-ttu-id="275ed-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="275ed-112">HRESULT</span></span>|<span data-ttu-id="275ed-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="275ed-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="275ed-114">`EnumManifestResources` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="275ed-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="275ed-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="275ed-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="275ed-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="275ed-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="275ed-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="275ed-117">Requirements</span></span>  
 <span data-ttu-id="275ed-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="275ed-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="275ed-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="275ed-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="275ed-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="275ed-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="275ed-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="275ed-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="275ed-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="275ed-122">See also</span></span>
- [<span data-ttu-id="275ed-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="275ed-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
