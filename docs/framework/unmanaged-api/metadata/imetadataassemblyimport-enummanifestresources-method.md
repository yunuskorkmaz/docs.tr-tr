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
ms.openlocfilehash: 22141cf46a965c0624c076bd1d86d2624e5a09f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176025"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="2cf9d-102">IMetaDataAssemblyImport::EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2cf9d-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="2cf9d-103">Geçerli derleme bildiriminde başvurulan kaynaklar için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cf9d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2cf9d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2cf9d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2cf9d-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2cf9d-107">`EnumManifestResources` Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="2cf9d-108">[çıkış] `mdManifestResource` Meta veri belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2cf9d-109">[içinde] Yerleştirilebilen `mdManifestResource` en fazla belirteç `rManifestResources`sayısı.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2cf9d-110">[çıkış] Yerleştirilen belirteçlerin `mdManifestResource` `rManifestResources`sayısı.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cf9d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2cf9d-111">Return Value</span></span>  
  
|<span data-ttu-id="2cf9d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2cf9d-112">HRESULT</span></span>|<span data-ttu-id="2cf9d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cf9d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2cf9d-114">`EnumManifestResources`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2cf9d-115">Sayısala rendelemek için hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2cf9d-116">Bu durumda, `pcTokens` sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2cf9d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2cf9d-117">Requirements</span></span>  
 <span data-ttu-id="2cf9d-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cf9d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cf9d-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2cf9d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2cf9d-120">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2cf9d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2cf9d-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cf9d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf9d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cf9d-122">See also</span></span>

- [<span data-ttu-id="2cf9d-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cf9d-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
