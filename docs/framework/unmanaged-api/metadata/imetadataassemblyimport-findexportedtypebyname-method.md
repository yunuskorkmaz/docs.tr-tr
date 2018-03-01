---
title: "IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 010e6c29541e4b55353db4359c018935c5e1ef2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="74e1f-102">IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74e1f-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="74e1f-103">Bir işaretçi verilen bir tür için adı ve türü kapsayan verilen alır.</span><span class="sxs-lookup"><span data-stu-id="74e1f-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74e1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74e1f-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74e1f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74e1f-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="74e1f-106">[in] Dışarı aktarılan türünün adı.</span><span class="sxs-lookup"><span data-stu-id="74e1f-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="74e1f-107">[in] Dışarı aktarılan tür kapsayan sınıfı için meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="74e1f-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="74e1f-108">Bu değer `mdExportedTypeNil` istenen veriliyorsa türü bir iç içe geçmiş tür değil.</span><span class="sxs-lookup"><span data-stu-id="74e1f-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="74e1f-109">[out] Bir işaretçi `mdExportedType` dışarı aktarılan tür temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="74e1f-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74e1f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74e1f-110">Remarks</span></span>  
 <span data-ttu-id="74e1f-111">`FindExportedTypeByName` Yöntemi başvurularını çözümlemek için ortak dil çalışma zamanı tarafından kullanılan standart kurallar kullanır.</span><span class="sxs-lookup"><span data-stu-id="74e1f-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74e1f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74e1f-112">Requirements</span></span>  
 <span data-ttu-id="74e1f-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74e1f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74e1f-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74e1f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74e1f-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="74e1f-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74e1f-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74e1f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e1f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74e1f-117">See Also</span></span>  
 [<span data-ttu-id="74e1f-118">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74e1f-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="74e1f-119">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="74e1f-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
