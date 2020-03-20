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
ms.openlocfilehash: edfe5de9c9d7ef9607a2eea5146194bbd4393a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175999"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="202a2-102">IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="202a2-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="202a2-103">Adı ve çevreleyen türü verilen dışa aktarılan bir türü işaretçialır.</span><span class="sxs-lookup"><span data-stu-id="202a2-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="202a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="202a2-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="202a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="202a2-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="202a2-106">[içinde] Dışa aktarılan türün adı.</span><span class="sxs-lookup"><span data-stu-id="202a2-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="202a2-107">[içinde] Dışa aktarılan türdeki enilgili sınıfın meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="202a2-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="202a2-108">İstenilen dışa aktarılan tür iç içe bir tür değilse, bu değerdir. `mdExportedTypeNil`</span><span class="sxs-lookup"><span data-stu-id="202a2-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="202a2-109">[çıkış] Dışa `mdExportedType` aktarılan türü temsil eden belirteç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="202a2-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="202a2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="202a2-110">Remarks</span></span>  
 <span data-ttu-id="202a2-111">Yöntem, `FindExportedTypeByName` başvuruları çözmek için ortak dil çalışma zamanı tarafından kullanılan standart kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="202a2-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="202a2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="202a2-112">Requirements</span></span>  
 <span data-ttu-id="202a2-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="202a2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="202a2-114">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="202a2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="202a2-115">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="202a2-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="202a2-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="202a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202a2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="202a2-117">See also</span></span>

- [<span data-ttu-id="202a2-118">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="202a2-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="202a2-119">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="202a2-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
