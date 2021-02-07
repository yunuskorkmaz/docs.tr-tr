---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataTables:: GetGuidHeapSize yöntemi'
title: IMetaDataTables::GetGuidHeapSize Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
ms.openlocfilehash: bbf2fd7e083c5a0a42ad69ab685b3e1aa8321d68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688149"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="86dc2-103">IMetaDataTables::GetGuidHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86dc2-103">IMetaDataTables::GetGuidHeapSize Method</span></span>

<span data-ttu-id="86dc2-104">GUID yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="86dc2-104">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86dc2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86dc2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86dc2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86dc2-106">Parameters</span></span>  

 `pcbGuids`  
 <span data-ttu-id="86dc2-107">dışı GUID yığınının bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="86dc2-107">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86dc2-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86dc2-108">Requirements</span></span>  

 <span data-ttu-id="86dc2-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86dc2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86dc2-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="86dc2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86dc2-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="86dc2-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86dc2-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86dc2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86dc2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86dc2-113">See also</span></span>

- [<span data-ttu-id="86dc2-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86dc2-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="86dc2-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86dc2-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
