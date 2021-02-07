---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataTables:: GetStringHeapSize Yöntemi'
title: IMetaDataTables::GetStringHeapSize Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
ms.openlocfilehash: 0ec9f4e2768cc78163db67bc9099fc9cafae8c8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687785"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="49879-103">IMetaDataTables::GetStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49879-103">IMetaDataTables::GetStringHeapSize Method</span></span>

<span data-ttu-id="49879-104">Dize yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="49879-104">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49879-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49879-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49879-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49879-106">Parameters</span></span>  

 `pcbStrings`  
 <span data-ttu-id="49879-107">dışı Dize yığınının bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49879-107">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49879-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49879-108">Requirements</span></span>  

 <span data-ttu-id="49879-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49879-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49879-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="49879-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49879-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="49879-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49879-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49879-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49879-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49879-113">See also</span></span>

- [<span data-ttu-id="49879-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49879-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="49879-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49879-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
