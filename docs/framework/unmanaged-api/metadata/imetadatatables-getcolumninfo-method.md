---
title: IMetaDataTables::GetColumnInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumnInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 939085294666a233341f65a8f5736d9dce201470
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="b6580-102">IMetaDataTables::GetColumnInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="b6580-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="b6580-103">Belirtilen tabloda belirtilen sütun hakkındaki verileri alır.</span><span class="sxs-lookup"><span data-stu-id="b6580-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6580-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6580-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b6580-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6580-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="b6580-106">[in] İstenen Tablo dizini.</span><span class="sxs-lookup"><span data-stu-id="b6580-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="b6580-107">[in] İstenen sütun dizini.</span><span class="sxs-lookup"><span data-stu-id="b6580-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="b6580-108">[out] Satır sütununda uzaklığını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6580-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="b6580-109">[out] Bir işaretçi sütunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b6580-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="b6580-110">[out] Sütundaki değerlerin türü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6580-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="b6580-111">[out] Sütun adı için bir işaretçi bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6580-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6580-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6580-112">Requirements</span></span>  
 <span data-ttu-id="b6580-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6580-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6580-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6580-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6580-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b6580-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6580-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6580-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6580-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6580-117">See Also</span></span>  
 [<span data-ttu-id="b6580-118">Imetadatatables arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6580-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="b6580-119">Imetadatatables2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6580-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
