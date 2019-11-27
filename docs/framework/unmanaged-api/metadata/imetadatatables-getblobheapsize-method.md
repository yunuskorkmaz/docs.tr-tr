---
title: IMetaDataTables::GetBlobHeapSize Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
ms.openlocfilehash: 715456317b880de89b6abdf1fa82acd040d17ced
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442045"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="3e666-102">IMetaDataTables::GetBlobHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e666-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="3e666-103">İkili büyük nesne (BLOB) yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="3e666-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e666-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e666-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="3e666-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e666-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="3e666-106">dışı BLOB yığınının bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3e666-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e666-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e666-107">Requirements</span></span>  
 <span data-ttu-id="3e666-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e666-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e666-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3e666-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e666-110">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3e666-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e666-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e666-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e666-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e666-112">See also</span></span>

- [<span data-ttu-id="3e666-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e666-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="3e666-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e666-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
