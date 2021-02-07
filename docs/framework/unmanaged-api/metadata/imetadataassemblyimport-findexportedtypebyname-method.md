---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: FindExportedTypeByName yöntemi'
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
ms.openlocfilehash: 4a2dc2b65b7f7fe6d5f2e120c635214d457991bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677996"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="e826b-103">IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e826b-103">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>

<span data-ttu-id="e826b-104">Adı ve kapsayan türü verilen, verilen bir türe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="e826b-104">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e826b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e826b-105">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e826b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e826b-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="e826b-107">'ndaki İçe aktarılmış türün adı.</span><span class="sxs-lookup"><span data-stu-id="e826b-107">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="e826b-108">'ndaki İçe aktarılmış türün kapsayan sınıfına ait meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="e826b-108">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="e826b-109">Bu değer, `mdExportedTypeNil` istenen dışarıya alınan türün iç içe bir tür olmaması durumunda olur.</span><span class="sxs-lookup"><span data-stu-id="e826b-109">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="e826b-110">dışı Bir belirteç için, `mdExportedType` dışarıya eklenen türü temsil eden bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e826b-110">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e826b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e826b-111">Remarks</span></span>  

 <span data-ttu-id="e826b-112">`FindExportedTypeByName`Yöntemi, başvuruları çözümlemek için ortak dil çalışma zamanı tarafından çalıştırılan standart kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="e826b-112">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e826b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e826b-113">Requirements</span></span>  

 <span data-ttu-id="e826b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e826b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e826b-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e826b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e826b-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e826b-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e826b-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e826b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e826b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e826b-118">See also</span></span>

- [<span data-ttu-id="e826b-119">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e826b-119">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e826b-120">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="e826b-120">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
