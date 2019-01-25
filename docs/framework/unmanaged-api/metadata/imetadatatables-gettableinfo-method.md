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
ms.openlocfilehash: 9bf3e5d427698673576f71e290fde54275b75317
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683462"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="d5a4e-102">IMetaDataTables::GetTableInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="d5a4e-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="d5a4e-103">Ad, satır boyutu, satır sayısı, sütun sayısı ve belirtilen tablonun anahtar sütunu dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="d5a4e-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a4e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5a4e-104">Syntax</span></span>  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5a4e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5a4e-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="d5a4e-106">[in] Tablonun tanımlayıcısını döndürülecek özellikleri.</span><span class="sxs-lookup"><span data-stu-id="d5a4e-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="d5a4e-107">[out] Baytlarında tablo satırı boyutunu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5a4e-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="d5a4e-108">[out] Tablodaki satır sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5a4e-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="d5a4e-109">[out] Tablodaki sütun sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5a4e-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="d5a4e-110">[out] Anahtar sütunun veya tablonun anahtar sütunu yok varsa -1 dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5a4e-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="d5a4e-111">[out] Tablo adı için bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d5a4e-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5a4e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5a4e-112">Requirements</span></span>  
 <span data-ttu-id="d5a4e-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a4e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5a4e-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d5a4e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5a4e-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="d5a4e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5a4e-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5a4e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a4e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5a4e-117">See also</span></span>
- [<span data-ttu-id="d5a4e-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5a4e-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d5a4e-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5a4e-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
