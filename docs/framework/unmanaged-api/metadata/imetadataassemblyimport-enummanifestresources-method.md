---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: EnumManifestResources yöntemi'
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
ms.openlocfilehash: ff819ebb575626af6049558656637e7fabcbc322
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677989"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="50666-103">IMetaDataAssemblyImport::EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50666-103">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>

<span data-ttu-id="50666-104">Geçerli derleme bildiriminde başvurulan kaynaklar için bir Numaralandırıcı işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="50666-104">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50666-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50666-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="50666-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50666-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="50666-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="50666-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="50666-108">Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır `EnumManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="50666-108">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="50666-109">dışı Meta veri belirteçlerini depolamak için kullanılan dizi `mdManifestResource` .</span><span class="sxs-lookup"><span data-stu-id="50666-109">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="50666-110">'ndaki `mdManifestResource` İçine yerleştirilebilecek en fazla belirteç sayısı `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="50666-110">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="50666-111">dışı `mdManifestResource` Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="50666-111">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50666-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="50666-112">Return Value</span></span>  
  
|<span data-ttu-id="50666-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50666-113">HRESULT</span></span>|<span data-ttu-id="50666-114">Description</span><span class="sxs-lookup"><span data-stu-id="50666-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="50666-115">`EnumManifestResources` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="50666-115">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="50666-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="50666-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="50666-117">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="50666-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50666-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50666-118">Requirements</span></span>  

 <span data-ttu-id="50666-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50666-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50666-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="50666-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50666-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="50666-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50666-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50666-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50666-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50666-123">See also</span></span>

- [<span data-ttu-id="50666-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50666-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
