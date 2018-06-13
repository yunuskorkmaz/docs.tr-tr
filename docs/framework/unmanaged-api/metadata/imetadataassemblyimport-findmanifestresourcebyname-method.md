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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9afc2ecc34131f62f1f8e8e86ca73f8b8b0126b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443518"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="1c58d-102">IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c58d-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="1c58d-103">Bir işaretçi bildirim kaynağı için belirtilen adla alır.</span><span class="sxs-lookup"><span data-stu-id="1c58d-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c58d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c58d-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c58d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c58d-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="1c58d-106">[in] Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="1c58d-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="1c58d-107">[out] Depolamak için kullanılan dizi `mdManifestResource` meta veri simgesi, her biri bir bildirim kaynağı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1c58d-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c58d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c58d-108">Remarks</span></span>  
 <span data-ttu-id="1c58d-109">`FindManifestResourceByName` Yöntemi başvurularını çözümlemek için ortak dil çalışma zamanı tarafından kullanılan standart kurallar kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c58d-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c58d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c58d-110">Requirements</span></span>  
 <span data-ttu-id="1c58d-111">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c58d-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c58d-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1c58d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c58d-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1c58d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c58d-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c58d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c58d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c58d-115">See Also</span></span>  
 [<span data-ttu-id="1c58d-116">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c58d-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="1c58d-117">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="1c58d-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
