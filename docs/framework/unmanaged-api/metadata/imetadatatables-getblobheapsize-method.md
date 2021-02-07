---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataTables:: GetBlobHeapSize yöntemi'
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
ms.openlocfilehash: f6d5c7aeb5e1cc1f307d53d8f3e3cc99daa72311
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688318"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="d4974-103">IMetaDataTables::GetBlobHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4974-103">IMetaDataTables::GetBlobHeapSize Method</span></span>

<span data-ttu-id="d4974-104">İkili büyük nesne (BLOB) yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="d4974-104">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4974-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4974-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d4974-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4974-106">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="d4974-107">dışı BLOB yığınının bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4974-107">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4974-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4974-108">Requirements</span></span>  

 <span data-ttu-id="d4974-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4974-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4974-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d4974-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4974-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d4974-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4974-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4974-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4974-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4974-113">See also</span></span>

- [<span data-ttu-id="d4974-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4974-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="d4974-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4974-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
