---
title: IMetaDataTables::GetColumnInfo Yöntemi
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
ms.openlocfilehash: 6156499368fb743b69c03f38b40ad3c5bcabce6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992413"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="502e0-102">IMetaDataTables::GetColumnInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="502e0-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="502e0-103">Belirtilen tabloda belirtilen sütuna ilişkin verileri alır.</span><span class="sxs-lookup"><span data-stu-id="502e0-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="502e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="502e0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="502e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="502e0-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="502e0-106">[in] İstediğiniz tabloyu dizini.</span><span class="sxs-lookup"><span data-stu-id="502e0-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="502e0-107">[in] İstenen sütun dizini.</span><span class="sxs-lookup"><span data-stu-id="502e0-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="502e0-108">[out] Satırdaki sütun uzaklığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="502e0-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="502e0-109">[out] Sütunun bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="502e0-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="502e0-110">[out] Sütundaki değerleri türü bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="502e0-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="502e0-111">[out] Sütun adı için bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="502e0-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="502e0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="502e0-112">Requirements</span></span>  
 <span data-ttu-id="502e0-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="502e0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="502e0-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="502e0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="502e0-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="502e0-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="502e0-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="502e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="502e0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="502e0-117">See also</span></span>

- [<span data-ttu-id="502e0-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="502e0-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="502e0-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="502e0-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
