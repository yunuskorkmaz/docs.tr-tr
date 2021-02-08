---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: FindManifestResourceByName Yöntemi'
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
ms.openlocfilehash: 1d1312277675a1f2bf213221ab8d9d2a584733a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784177"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="6d072-103">IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d072-103">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>

<span data-ttu-id="6d072-104">Belirtilen ada sahip bildirim kaynağına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6d072-104">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d072-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d072-105">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="6d072-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d072-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="6d072-107">'ndaki Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="6d072-107">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="6d072-108">dışı `mdManifestResource` Her biri bir bildirim kaynağını temsil eden meta veri belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="6d072-108">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d072-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d072-109">Remarks</span></span>  

 <span data-ttu-id="6d072-110">`FindManifestResourceByName`Yöntemi, başvuruları çözümlemek için ortak dil çalışma zamanı tarafından çalıştırılan standart kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6d072-110">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d072-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d072-111">Requirements</span></span>  

 <span data-ttu-id="6d072-112">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d072-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d072-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6d072-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d072-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6d072-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d072-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d072-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d072-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d072-116">See also</span></span>

- [<span data-ttu-id="6d072-117">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d072-117">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="6d072-118">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="6d072-118">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
