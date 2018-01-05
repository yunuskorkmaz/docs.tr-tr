---
title: IMetaDataTables::GetColumn Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumn
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 162162b972ab0e1f3de55d56c18372f2475c9846
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="b19ac-102">IMetaDataTables::GetColumn Metodu</span><span class="sxs-lookup"><span data-stu-id="b19ac-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="b19ac-103">Verilen tablo satır ve belirtilen sütunun hücre içinde yer alan değeri için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="b19ac-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b19ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b19ac-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b19ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b19ac-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="b19ac-106">[in] Tablo dizini.</span><span class="sxs-lookup"><span data-stu-id="b19ac-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="b19ac-107">[in] Tablodaki sütun dizini.</span><span class="sxs-lookup"><span data-stu-id="b19ac-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="b19ac-108">[in] Tablodaki satır dizini.</span><span class="sxs-lookup"><span data-stu-id="b19ac-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="b19ac-109">[out] Hücrenin değerini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b19ac-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b19ac-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b19ac-110">Requirements</span></span>  
 <span data-ttu-id="b19ac-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b19ac-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b19ac-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b19ac-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b19ac-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b19ac-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b19ac-114">**.NET framework sürümleri**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b19ac-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19ac-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b19ac-115">See Also</span></span>  
 [<span data-ttu-id="b19ac-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b19ac-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="b19ac-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b19ac-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
