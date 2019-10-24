---
title: IMetaDataTables::GetColumnInfo Yöntemi
ms.date: 10/10/2019
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
ms.openlocfilehash: dd67d9faafedf4fb92c69618d4464ebb2ce47dcc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774252"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="2ae54-102">IMetaDataTables::GetColumnInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ae54-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="2ae54-103">Belirtilen tabloda belirtilen sütunla ilgili verileri alır.</span><span class="sxs-lookup"><span data-stu-id="2ae54-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae54-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ae54-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ae54-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ae54-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="2ae54-106">'ndaki İstenen tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="2ae54-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="2ae54-107">'ndaki İstenen sütunun dizini.</span><span class="sxs-lookup"><span data-stu-id="2ae54-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="2ae54-108">dışı Satırdaki sütunun uzaklığa yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2ae54-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="2ae54-109">dışı Sütunun bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2ae54-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="2ae54-110">dışı Sütundaki değerlerin türüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2ae54-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="2ae54-111">dışı Sütun adı işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2ae54-111">[out] A pointer to a pointer to the column name.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="2ae54-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ae54-112">Remarks</span></span>

<span data-ttu-id="2ae54-113">Döndürülen sütun türü bir değer aralığı içinde yer alıyorsa:</span><span class="sxs-lookup"><span data-stu-id="2ae54-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="2ae54-114">pType</span><span class="sxs-lookup"><span data-stu-id="2ae54-114">pType</span></span>                    | <span data-ttu-id="2ae54-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ae54-115">Description</span></span>   | <span data-ttu-id="2ae54-116">Yardımcı işlevi</span><span class="sxs-lookup"><span data-stu-id="2ae54-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="2ae54-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="2ae54-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="2ae54-118">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="2ae54-118">(0..63)</span></span>   | <span data-ttu-id="2ae54-119">Rid</span><span class="sxs-lookup"><span data-stu-id="2ae54-119">Rid</span></span>           | <span data-ttu-id="2ae54-120">**Isrbıtype türü**</span><span class="sxs-lookup"><span data-stu-id="2ae54-120">**IsRidType**</span></span><br><span data-ttu-id="2ae54-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="2ae54-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="2ae54-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="2ae54-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="2ae54-123">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="2ae54-123">(64..95)</span></span> | <span data-ttu-id="2ae54-124">Kodlanmış belirteç</span><span class="sxs-lookup"><span data-stu-id="2ae54-124">Coded token</span></span> | <span data-ttu-id="2ae54-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="2ae54-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="2ae54-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="2ae54-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="2ae54-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="2ae54-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="2ae54-128">Int16</span><span class="sxs-lookup"><span data-stu-id="2ae54-128">Int16</span></span>         | <span data-ttu-id="2ae54-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="2ae54-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="2ae54-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="2ae54-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="2ae54-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="2ae54-131">UInt16</span></span>        | <span data-ttu-id="2ae54-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="2ae54-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="2ae54-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="2ae54-133">`iLONG` (98)</span></span>             | <span data-ttu-id="2ae54-134">Int32</span><span class="sxs-lookup"><span data-stu-id="2ae54-134">Int32</span></span>         | <span data-ttu-id="2ae54-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="2ae54-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="2ae54-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="2ae54-136">`iULONG` (99)</span></span>            | <span data-ttu-id="2ae54-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="2ae54-137">UInt32</span></span>        | <span data-ttu-id="2ae54-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="2ae54-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="2ae54-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="2ae54-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="2ae54-140">Bayt</span><span class="sxs-lookup"><span data-stu-id="2ae54-140">Byte</span></span>          | <span data-ttu-id="2ae54-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="2ae54-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="2ae54-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="2ae54-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="2ae54-143">Dize</span><span class="sxs-lookup"><span data-stu-id="2ae54-143">String</span></span>        | <span data-ttu-id="2ae54-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="2ae54-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="2ae54-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="2ae54-145">`iGUID` (102)</span></span>            | <span data-ttu-id="2ae54-146">Guid</span><span class="sxs-lookup"><span data-stu-id="2ae54-146">Guid</span></span>          | <span data-ttu-id="2ae54-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="2ae54-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="2ae54-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="2ae54-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="2ae54-149">Bun</span><span class="sxs-lookup"><span data-stu-id="2ae54-149">Blob</span></span>          | <span data-ttu-id="2ae54-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="2ae54-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="2ae54-151">*Yığında* depolanan değerler (yani, `IsHeapType == true`) kullanılarak okunabilir:</span><span class="sxs-lookup"><span data-stu-id="2ae54-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="2ae54-152">`iSTRING`: **IMetaDataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="2ae54-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="2ae54-153">`iGUID`: **IMetaDataTables. GetGUID**</span><span class="sxs-lookup"><span data-stu-id="2ae54-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="2ae54-154">`iBLOB`: **IMetaDataTables. GetBlob**</span><span class="sxs-lookup"><span data-stu-id="2ae54-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ae54-155">Yukarıdaki tabloda tanımlanan sabitleri kullanmak için *Cor. h* üstbilgi dosyası tarafından sunulan yönerge `#define _DEFINE_META_DATA_META_CONSTANTS` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2ae54-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ae54-156">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ae54-156">Requirements</span></span>  
 <span data-ttu-id="2ae54-157">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ae54-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ae54-158">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2ae54-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ae54-159">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2ae54-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ae54-160">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ae54-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae54-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ae54-161">See also</span></span>

- [<span data-ttu-id="2ae54-162">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ae54-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="2ae54-163">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ae54-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
