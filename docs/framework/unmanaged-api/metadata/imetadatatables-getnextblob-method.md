---
title: IMetaDataTables::GetNextBlob Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: ba694f485d5a51870a1283b6ccbcb7b042a14501
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685649"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="fd6ba-102">IMetaDataTables::GetNextBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd6ba-102">IMetaDataTables::GetNextBlob Method</span></span>

<span data-ttu-id="fd6ba-103">Tablodaki bir sonraki ikili büyük nesne (BLOB) dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="fd6ba-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd6ba-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fd6ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd6ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd6ba-105">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="fd6ba-106">'ndaki Blob bir sütundan döndürülen dizin.</span><span class="sxs-lookup"><span data-stu-id="fd6ba-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="fd6ba-107">dışı Sonraki BLOBUN dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fd6ba-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd6ba-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd6ba-108">Requirements</span></span>  

 <span data-ttu-id="fd6ba-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd6ba-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd6ba-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fd6ba-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd6ba-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="fd6ba-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd6ba-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd6ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6ba-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd6ba-113">See also</span></span>

- [<span data-ttu-id="fd6ba-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd6ba-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="fd6ba-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd6ba-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
