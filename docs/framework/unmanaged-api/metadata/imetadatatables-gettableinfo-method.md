---
description: ': IMetaDataTables:: GetTableInfo metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3929f91c15b5c1fc22ac3ad4b17cbaa38a08533a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687655"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="333bd-103">IMetaDataTables::GetTableInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="333bd-103">IMetaDataTables::GetTableInfo Method</span></span>

<span data-ttu-id="333bd-104">Belirtilen tablonun adını, satır boyutunu, satır sayısını, sütun sayısını ve anahtar sütun dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="333bd-104">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="333bd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="333bd-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="333bd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="333bd-106">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="333bd-107">'ndaki Özelliklerini döndürülecek tablonun tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="333bd-107">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="333bd-108">dışı Bir tablo satırının bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="333bd-108">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="333bd-109">dışı Tablodaki satır sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="333bd-109">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="333bd-110">dışı Tablodaki sütun sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="333bd-110">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="333bd-111">dışı Anahtar sütununun dizinine yönelik bir işaretçi veya tabloda anahtar sütunu yoksa-1.</span><span class="sxs-lookup"><span data-stu-id="333bd-111">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="333bd-112">dışı Tablo adı işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="333bd-112">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="333bd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="333bd-113">Requirements</span></span>  

 <span data-ttu-id="333bd-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="333bd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="333bd-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="333bd-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="333bd-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="333bd-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="333bd-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="333bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="333bd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="333bd-118">See also</span></span>

- [<span data-ttu-id="333bd-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="333bd-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="333bd-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="333bd-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
