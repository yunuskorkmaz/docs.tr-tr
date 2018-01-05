---
title: "IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindManifestResourceByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d6cc738c227157b45e242fb46a672d28d6ce778
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="72498-102">IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72498-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="72498-103">Bir işaretçi bildirim kaynağı için belirtilen adla alır.</span><span class="sxs-lookup"><span data-stu-id="72498-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72498-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72498-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="72498-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72498-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="72498-106">[in] Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="72498-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="72498-107">[out] Depolamak için kullanılan dizi `mdManifestResource` meta veri simgesi, her biri bir bildirim kaynağı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="72498-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72498-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72498-108">Remarks</span></span>  
 <span data-ttu-id="72498-109">`FindManifestResourceByName` Yöntemi başvurularını çözümlemek için ortak dil çalışma zamanı tarafından kullanılan standart kurallar kullanır.</span><span class="sxs-lookup"><span data-stu-id="72498-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72498-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72498-110">Requirements</span></span>  
 <span data-ttu-id="72498-111">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72498-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72498-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="72498-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72498-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="72498-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72498-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72498-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72498-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72498-115">See Also</span></span>  
 [<span data-ttu-id="72498-116">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72498-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="72498-117">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="72498-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
