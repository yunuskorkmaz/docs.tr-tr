---
title: IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
ms.openlocfilehash: ae9097725aecd21e910e49a78d81951df39e9b2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177773"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="d3493-102">IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3493-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="d3493-103">Belirtilen ada sahip bildirim kaynağına işaretçi sayar.</span><span class="sxs-lookup"><span data-stu-id="d3493-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3493-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3493-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d3493-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3493-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="d3493-106">[içinde] Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="d3493-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="d3493-107">[çıkış] Her biri bir `mdManifestResource` bildirim kaynağını temsil eden meta veri belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="d3493-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3493-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3493-108">Remarks</span></span>  
 <span data-ttu-id="d3493-109">Yöntem, `FindManifestResourceByName` başvuruları çözmek için ortak dil çalışma zamanı tarafından kullanılan standart kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3493-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3493-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3493-110">Requirements</span></span>  
 <span data-ttu-id="d3493-111">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3493-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3493-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d3493-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3493-113">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d3493-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3493-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3493-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3493-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3493-115">See also</span></span>

- [<span data-ttu-id="d3493-116">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3493-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="d3493-117">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="d3493-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
