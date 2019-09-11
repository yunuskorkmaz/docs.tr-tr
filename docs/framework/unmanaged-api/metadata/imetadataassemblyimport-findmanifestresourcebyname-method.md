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
ms.openlocfilehash: aaaae5bda88d1fbc9949a080c5765127fd112bde
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855959"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="99183-102">IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99183-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="99183-103">Belirtilen ada sahip bildirim kaynağına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="99183-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99183-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99183-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="99183-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99183-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="99183-106">'ndaki Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="99183-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="99183-107">dışı Her biri bir bildirim kaynağını temsil `mdManifestResource` eden meta veri belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="99183-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99183-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99183-108">Remarks</span></span>  
 <span data-ttu-id="99183-109">Yöntemi `FindManifestResourceByName` , başvuruları çözümlemek için ortak dil çalışma zamanı tarafından çalıştırılan standart kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="99183-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99183-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99183-110">Requirements</span></span>  
 <span data-ttu-id="99183-111">**Platformunun** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99183-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99183-112">**Üst bilgi** Cor. h</span><span class="sxs-lookup"><span data-stu-id="99183-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99183-113">**Kitaplığı** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="99183-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99183-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99183-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99183-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99183-115">See also</span></span>

- [<span data-ttu-id="99183-116">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99183-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="99183-117">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="99183-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
