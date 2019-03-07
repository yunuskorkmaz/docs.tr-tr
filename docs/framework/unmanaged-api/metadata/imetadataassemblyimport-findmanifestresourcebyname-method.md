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
ms.openlocfilehash: 8d736a93e7ba6451f1d4755a86749565b9ea071b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491525"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="c3dd6-102">IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3dd6-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="c3dd6-103">Bir işaretçi, belirtilen ada sahip bildirim kaynağı alır.</span><span class="sxs-lookup"><span data-stu-id="c3dd6-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3dd6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3dd6-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="c3dd6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3dd6-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="c3dd6-106">[in] Kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="c3dd6-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="c3dd6-107">[out] Depolamak için kullanılan bir dizi `mdManifestResource` meta veri belirteçleri, her biri bildirim kaynağını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3dd6-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3dd6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3dd6-108">Remarks</span></span>  
 <span data-ttu-id="c3dd6-109">`FindManifestResourceByName` Yöntemi başvurularını çözümlemek için ortak dil çalışma zamanı tarafından kullanılan standart kurallar kullanır.</span><span class="sxs-lookup"><span data-stu-id="c3dd6-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3dd6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3dd6-110">Requirements</span></span>  
 <span data-ttu-id="c3dd6-111">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3dd6-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3dd6-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c3dd6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3dd6-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="c3dd6-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3dd6-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3dd6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3dd6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3dd6-115">See also</span></span>
- [<span data-ttu-id="c3dd6-116">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3dd6-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="c3dd6-117">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="c3dd6-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
