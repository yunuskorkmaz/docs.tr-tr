---
description: ': IMetaDataTables:: GetNextBlob yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 99126ab5c3891ee09346bb54096a4fce3ca44bc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688136"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="667cb-103">IMetaDataTables::GetNextBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="667cb-103">IMetaDataTables::GetNextBlob Method</span></span>

<span data-ttu-id="667cb-104">Tablodaki bir sonraki ikili büyük nesne (BLOB) dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="667cb-104">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="667cb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="667cb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="667cb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="667cb-106">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="667cb-107">'ndaki Blob bir sütundan döndürülen dizin.</span><span class="sxs-lookup"><span data-stu-id="667cb-107">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="667cb-108">dışı Sonraki BLOBUN dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="667cb-108">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="667cb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="667cb-109">Requirements</span></span>  

 <span data-ttu-id="667cb-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="667cb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="667cb-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="667cb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="667cb-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="667cb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="667cb-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="667cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="667cb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="667cb-114">See also</span></span>

- [<span data-ttu-id="667cb-115">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="667cb-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="667cb-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="667cb-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
