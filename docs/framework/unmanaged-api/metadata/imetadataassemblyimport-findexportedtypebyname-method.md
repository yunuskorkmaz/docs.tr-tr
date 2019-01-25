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
ms.openlocfilehash: 1b2b7559c203e5d357dd6921ea6862fbb5ec90a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576193"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="0732d-102">IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0732d-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="0732d-103">Bir işaretçi verilen bir tür için adı ve türü kapsayan verilen alır.</span><span class="sxs-lookup"><span data-stu-id="0732d-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0732d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0732d-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0732d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0732d-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="0732d-106">[in] Dışarı aktarılan tür adı.</span><span class="sxs-lookup"><span data-stu-id="0732d-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="0732d-107">[in] Dışarı aktarılan tür kapsayan sınıfı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0732d-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="0732d-108">Bu değer `mdExportedTypeNil` istenen dışarı aktardıysanız türü iç içe geçmiş bir tür değil.</span><span class="sxs-lookup"><span data-stu-id="0732d-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="0732d-109">[out] Bir işaretçi `mdExportedType` dışarı aktarılan türünü temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="0732d-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0732d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0732d-110">Remarks</span></span>  
 <span data-ttu-id="0732d-111">`FindExportedTypeByName` Yöntemi başvurularını çözümlemek için ortak dil çalışma zamanı tarafından kullanılan standart kurallar kullanır.</span><span class="sxs-lookup"><span data-stu-id="0732d-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0732d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0732d-112">Requirements</span></span>  
 <span data-ttu-id="0732d-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0732d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0732d-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0732d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0732d-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="0732d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0732d-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0732d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0732d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0732d-117">See also</span></span>
- [<span data-ttu-id="0732d-118">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0732d-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="0732d-119">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="0732d-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
