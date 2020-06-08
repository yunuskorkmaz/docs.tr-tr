---
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
ms.openlocfilehash: 71a75defa72e4fe3594b4d0ceff45273b3a35395
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490360"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="cda23-102">IMetaDataTables::GetGuidHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cda23-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="cda23-103">GUID yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="cda23-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda23-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cda23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cda23-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cda23-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="cda23-106">dışı GUID yığınının bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cda23-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cda23-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cda23-107">Requirements</span></span>  
 <span data-ttu-id="cda23-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cda23-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda23-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cda23-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cda23-110">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cda23-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cda23-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cda23-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda23-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cda23-112">See also</span></span>

- [<span data-ttu-id="cda23-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cda23-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="cda23-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cda23-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
