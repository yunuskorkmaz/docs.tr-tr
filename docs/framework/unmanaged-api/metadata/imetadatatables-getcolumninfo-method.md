---
title: IMetaDataTables::GetColumnInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 245933b23028e2baf8a09ca07595f394b65c0ec3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698303"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="849a7-102">IMetaDataTables::GetColumnInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="849a7-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="849a7-103">Belirtilen tabloda belirtilen sütuna ilişkin verileri alır.</span><span class="sxs-lookup"><span data-stu-id="849a7-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="849a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="849a7-104">Syntax</span></span>  
  
```  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="849a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="849a7-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="849a7-106">[in] İstediğiniz tabloyu dizini.</span><span class="sxs-lookup"><span data-stu-id="849a7-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="849a7-107">[in] İstenen sütun dizini.</span><span class="sxs-lookup"><span data-stu-id="849a7-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="849a7-108">[out] Satırdaki sütun uzaklığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="849a7-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="849a7-109">[out] Sütunun bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="849a7-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="849a7-110">[out] Sütundaki değerleri türü bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="849a7-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="849a7-111">[out] Sütun adı için bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="849a7-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="849a7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="849a7-112">Requirements</span></span>  
 <span data-ttu-id="849a7-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="849a7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="849a7-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="849a7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="849a7-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="849a7-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="849a7-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="849a7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="849a7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="849a7-117">See also</span></span>
- [<span data-ttu-id="849a7-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="849a7-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="849a7-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="849a7-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
