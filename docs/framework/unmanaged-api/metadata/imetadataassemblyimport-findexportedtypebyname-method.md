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
ms.openlocfilehash: 048c7234fcb2592ea0dade135a32341a6e0f404f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444925"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="dd936-102">IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd936-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="dd936-103">Bir işaretçi verilen bir tür için adı ve türü kapsayan verilen alır.</span><span class="sxs-lookup"><span data-stu-id="dd936-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd936-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd936-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd936-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd936-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="dd936-106">[in] Dışarı aktarılan türünün adı.</span><span class="sxs-lookup"><span data-stu-id="dd936-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="dd936-107">[in] Dışarı aktarılan tür kapsayan sınıfı için meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="dd936-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="dd936-108">Bu değer `mdExportedTypeNil` istenen veriliyorsa türü bir iç içe geçmiş tür değil.</span><span class="sxs-lookup"><span data-stu-id="dd936-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="dd936-109">[out] Bir işaretçi `mdExportedType` dışarı aktarılan tür temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="dd936-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd936-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd936-110">Remarks</span></span>  
 <span data-ttu-id="dd936-111">`FindExportedTypeByName` Yöntemi başvurularını çözümlemek için ortak dil çalışma zamanı tarafından kullanılan standart kurallar kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd936-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd936-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd936-112">Requirements</span></span>  
 <span data-ttu-id="dd936-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd936-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd936-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd936-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd936-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dd936-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd936-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd936-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd936-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd936-117">See Also</span></span>  
 [<span data-ttu-id="dd936-118">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd936-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="dd936-119">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="dd936-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
