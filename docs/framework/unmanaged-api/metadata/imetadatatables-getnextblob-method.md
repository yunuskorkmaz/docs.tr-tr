---
title: IMetaDataTables::GetNextBlob Metodu
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
ms.openlocfilehash: e43485caa0c1dbf989ae12de77ee4e160652942e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502682"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="15c0d-102">IMetaDataTables::GetNextBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="15c0d-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="15c0d-103">Tablodaki sonraki ikili büyük nesne (BLOB) dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="15c0d-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15c0d-104">Syntax</span></span>  
  
```  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15c0d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15c0d-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="15c0d-106">[in] BLOB sütundan döndürülen dizini.</span><span class="sxs-lookup"><span data-stu-id="15c0d-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="15c0d-107">[out] Sonraki BLOB dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="15c0d-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15c0d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15c0d-108">Requirements</span></span>  
 <span data-ttu-id="15c0d-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15c0d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15c0d-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="15c0d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15c0d-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="15c0d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15c0d-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15c0d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c0d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15c0d-113">See also</span></span>
- [<span data-ttu-id="15c0d-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15c0d-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="15c0d-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15c0d-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
