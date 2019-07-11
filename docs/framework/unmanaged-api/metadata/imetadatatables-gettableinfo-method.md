---
title: IMetaDataTables::GetTableInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4844834232e34ab5dacfa34e7aa5d204ee344612
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781354"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="9850d-102">IMetaDataTables::GetTableInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="9850d-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="9850d-103">Ad, satır boyutu, satır sayısı, sütun sayısı ve belirtilen tablonun anahtar sütunu dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="9850d-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9850d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9850d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9850d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9850d-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="9850d-106">[in] Tablonun tanımlayıcısını döndürülecek özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9850d-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="9850d-107">[out] Baytlarında tablo satırı boyutunu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9850d-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="9850d-108">[out] Tablodaki satır sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9850d-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="9850d-109">[out] Tablodaki sütun sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9850d-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="9850d-110">[out] Anahtar sütunun veya tablonun anahtar sütunu yok varsa -1 dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9850d-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="9850d-111">[out] Tablo adı için bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9850d-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9850d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9850d-112">Requirements</span></span>  
 <span data-ttu-id="9850d-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9850d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9850d-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9850d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9850d-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="9850d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9850d-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9850d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9850d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9850d-117">See also</span></span>

- [<span data-ttu-id="9850d-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9850d-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="9850d-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9850d-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
