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
ms.openlocfilehash: ea617668a72413f3387a35fe009b37fa15d03354
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449614"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="844ef-102">IMetaDataTables::GetTableInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="844ef-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="844ef-103">Ad, satır boyutu, satır sayısı, sütun sayısı ve belirtilen tablonun anahtar sütunu dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="844ef-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="844ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="844ef-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="844ef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="844ef-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="844ef-106">[in] Tablonun tanımlayıcısını döndürülecek özellikleri.</span><span class="sxs-lookup"><span data-stu-id="844ef-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="844ef-107">[out] Bir işaretçi bir tablo satırının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="844ef-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="844ef-108">[out] Tablodaki satır sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="844ef-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="844ef-109">[out] Tablodaki sütun sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="844ef-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="844ef-110">[out] Anahtar sütunu tablonun anahtar sütunu yok varsa -1 veya dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="844ef-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="844ef-111">[out] Tablo adı için bir işaretçi bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="844ef-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="844ef-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="844ef-112">Requirements</span></span>  
 <span data-ttu-id="844ef-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="844ef-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="844ef-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="844ef-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="844ef-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="844ef-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="844ef-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="844ef-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="844ef-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="844ef-117">See Also</span></span>  
 [<span data-ttu-id="844ef-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="844ef-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="844ef-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="844ef-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
