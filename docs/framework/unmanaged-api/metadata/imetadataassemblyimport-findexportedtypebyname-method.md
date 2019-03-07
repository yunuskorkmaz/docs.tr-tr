---
title: IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7575659441b2eae37365c10050bca53e0cfdef6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473922"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="d26fa-102">IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d26fa-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="d26fa-103">Bir işaretçi verilen bir tür için adı ve türü kapsayan verilen alır.</span><span class="sxs-lookup"><span data-stu-id="d26fa-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d26fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d26fa-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d26fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d26fa-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="d26fa-106">[in] Dışarı aktarılan tür adı.</span><span class="sxs-lookup"><span data-stu-id="d26fa-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="d26fa-107">[in] Dışarı aktarılan tür kapsayan sınıfı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d26fa-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="d26fa-108">Bu değer `mdExportedTypeNil` istenen dışarı aktardıysanız türü iç içe geçmiş bir tür değil.</span><span class="sxs-lookup"><span data-stu-id="d26fa-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="d26fa-109">[out] Bir işaretçi `mdExportedType` dışarı aktarılan türünü temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="d26fa-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d26fa-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d26fa-110">Remarks</span></span>  
 <span data-ttu-id="d26fa-111">`FindExportedTypeByName` Yöntemi başvurularını çözümlemek için ortak dil çalışma zamanı tarafından kullanılan standart kurallar kullanır.</span><span class="sxs-lookup"><span data-stu-id="d26fa-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d26fa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d26fa-112">Requirements</span></span>  
 <span data-ttu-id="d26fa-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d26fa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d26fa-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d26fa-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d26fa-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="d26fa-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d26fa-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d26fa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26fa-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d26fa-117">See also</span></span>
- [<span data-ttu-id="d26fa-118">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d26fa-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="d26fa-119">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="d26fa-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
