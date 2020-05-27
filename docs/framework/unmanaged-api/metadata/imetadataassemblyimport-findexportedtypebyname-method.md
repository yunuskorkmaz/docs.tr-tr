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
ms.openlocfilehash: ac6de9a16fad6ba9d14f3960ddd28c42c111f254
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009398"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="f4a32-102">IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4a32-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="f4a32-103">Adı ve kapsayan türü verilen, verilen bir türe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f4a32-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4a32-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f4a32-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4a32-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4a32-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f4a32-106">'ndaki İçe aktarılmış türün adı.</span><span class="sxs-lookup"><span data-stu-id="f4a32-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="f4a32-107">'ndaki İçe aktarılmış türün kapsayan sınıfına ait meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f4a32-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="f4a32-108">Bu değer, `mdExportedTypeNil` istenen dışarıya alınan türün iç içe bir tür olmaması durumunda olur.</span><span class="sxs-lookup"><span data-stu-id="f4a32-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="f4a32-109">dışı Bir belirteç için, `mdExportedType` dışarıya eklenen türü temsil eden bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f4a32-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4a32-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4a32-110">Remarks</span></span>  
 <span data-ttu-id="f4a32-111">`FindExportedTypeByName`Yöntemi, başvuruları çözümlemek için ortak dil çalışma zamanı tarafından çalıştırılan standart kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4a32-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4a32-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4a32-112">Requirements</span></span>  
 <span data-ttu-id="f4a32-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4a32-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4a32-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f4a32-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4a32-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f4a32-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4a32-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4a32-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4a32-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4a32-117">See also</span></span>

- [<span data-ttu-id="f4a32-118">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4a32-118">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="f4a32-119">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="f4a32-119">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
