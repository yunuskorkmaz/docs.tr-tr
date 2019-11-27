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
ms.openlocfilehash: 2748460826deb422a3851713db11343209fe449a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449557"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="d6090-102">IMetaDataAssemblyImport::EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6090-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="d6090-103">Geçerli derleme bildiriminde başvurulan kaynaklar için bir Numaralandırıcı işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d6090-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6090-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6090-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="d6090-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6090-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d6090-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d6090-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d6090-107">`EnumManifestResources` yöntemi ilk kez çağrıldığında bu null bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6090-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="d6090-108">dışı `mdManifestResource` meta veri belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="d6090-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d6090-109">'ndaki `rManifestResources`yerleştirilebilecek en fazla `mdManifestResource` belirteci sayısı.</span><span class="sxs-lookup"><span data-stu-id="d6090-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d6090-110">dışı Gerçekte `rManifestResources`yer `mdManifestResource` belirteçlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="d6090-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6090-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d6090-111">Return Value</span></span>  
  
|<span data-ttu-id="d6090-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6090-112">HRESULT</span></span>|<span data-ttu-id="d6090-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6090-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d6090-114">`EnumManifestResources` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d6090-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d6090-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="d6090-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d6090-116">Bu durumda `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d6090-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6090-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6090-117">Requirements</span></span>  
 <span data-ttu-id="d6090-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6090-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6090-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d6090-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6090-120">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d6090-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6090-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6090-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6090-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6090-122">See also</span></span>

- [<span data-ttu-id="d6090-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6090-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
