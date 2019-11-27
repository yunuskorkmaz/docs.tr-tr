---
title: IMetaDataEmit::SetModuleProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 2d3c820975488fa722e7af6070611ba7e9686ce8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445450"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="98210-102">IMetaDataEmit::SetModuleProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98210-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="98210-103">Imetadatayayma için önceki bir çağrı tarafından tanımlanan bir modüle yapılan başvuruları güncelleştirir [::D efineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="98210-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98210-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98210-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98210-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98210-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="98210-106">'ndaki Unicode 'daki modül adı.</span><span class="sxs-lookup"><span data-stu-id="98210-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="98210-107">Bu, yalnızca dosya adıdır ve tam yol adı değildir.</span><span class="sxs-lookup"><span data-stu-id="98210-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98210-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98210-108">Requirements</span></span>  
 <span data-ttu-id="98210-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98210-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98210-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="98210-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98210-111">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="98210-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98210-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98210-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98210-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98210-113">See also</span></span>

- [<span data-ttu-id="98210-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98210-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="98210-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98210-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
