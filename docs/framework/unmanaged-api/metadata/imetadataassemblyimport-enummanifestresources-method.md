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
ms.openlocfilehash: 560a6adf85fab7f421b86cba52224d5b1bfe1089
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006265"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="484e9-102">IMetaDataAssemblyImport::EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="484e9-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="484e9-103">Geçerli derleme bildiriminde başvurulan kaynaklar için bir Numaralandırıcı işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="484e9-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="484e9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="484e9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="484e9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="484e9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="484e9-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="484e9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="484e9-107">Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır `EnumManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="484e9-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="484e9-108">dışı Meta veri belirteçlerini depolamak için kullanılan dizi `mdManifestResource` .</span><span class="sxs-lookup"><span data-stu-id="484e9-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="484e9-109">'ndaki `mdManifestResource`İçine yerleştirilebilecek en fazla belirteç sayısı `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="484e9-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="484e9-110">dışı `mdManifestResource`Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="484e9-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="484e9-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="484e9-111">Return Value</span></span>  
  
|<span data-ttu-id="484e9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="484e9-112">HRESULT</span></span>|<span data-ttu-id="484e9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="484e9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="484e9-114">`EnumManifestResources`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="484e9-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="484e9-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="484e9-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="484e9-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="484e9-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="484e9-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="484e9-117">Requirements</span></span>  
 <span data-ttu-id="484e9-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="484e9-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="484e9-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="484e9-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="484e9-120">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="484e9-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="484e9-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="484e9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="484e9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="484e9-122">See also</span></span>

- [<span data-ttu-id="484e9-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="484e9-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
