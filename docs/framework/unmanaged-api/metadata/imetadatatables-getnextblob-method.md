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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e60ce044fc0272fbc9c4a641224bd70ad9faeeae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488129"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="9abf0-102">IMetaDataTables::GetNextBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9abf0-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="9abf0-103">Tablodaki sonraki ikili büyük nesne (BLOB) dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="9abf0-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abf0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9abf0-104">Syntax</span></span>  
  
```  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9abf0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9abf0-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="9abf0-106">[in] BLOB sütundan döndürülen dizini.</span><span class="sxs-lookup"><span data-stu-id="9abf0-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="9abf0-107">[out] Sonraki BLOB dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9abf0-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9abf0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9abf0-108">Requirements</span></span>  
 <span data-ttu-id="9abf0-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9abf0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9abf0-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9abf0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9abf0-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="9abf0-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9abf0-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9abf0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abf0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9abf0-113">See also</span></span>
- [<span data-ttu-id="9abf0-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9abf0-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="9abf0-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9abf0-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
