---
title: IMetaDataTables::GetColumn Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90ce56b3959c4768ef9cb6a9c551d53c5300a39e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049784"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="6a3e8-102">IMetaDataTables::GetColumn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a3e8-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="6a3e8-103">Belirtilen sütun ve satır tablodaki hücre bulunan değere bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6a3e8-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a3e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a3e8-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a3e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a3e8-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="6a3e8-106">[in] Tablo dizini.</span><span class="sxs-lookup"><span data-stu-id="6a3e8-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="6a3e8-107">[in] Tablodaki sütun dizini.</span><span class="sxs-lookup"><span data-stu-id="6a3e8-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="6a3e8-108">[in] Tablodaki satır dizini.</span><span class="sxs-lookup"><span data-stu-id="6a3e8-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="6a3e8-109">[out] Hücrenin değerini bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6a3e8-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a3e8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a3e8-110">Requirements</span></span>  
 <span data-ttu-id="6a3e8-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a3e8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a3e8-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6a3e8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a3e8-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6a3e8-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a3e8-114">**.NET framework sürümleri** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a3e8-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a3e8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a3e8-115">See also</span></span>

- [<span data-ttu-id="6a3e8-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a3e8-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="6a3e8-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a3e8-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
