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
ms.openlocfilehash: a044924810016eea60682b8765aeee448b552f0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501202"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="8b694-102">IMetaDataTables::GetColumnInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b694-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="8b694-103">Belirtilen tabloda belirtilen sütunla ilgili verileri alır.</span><span class="sxs-lookup"><span data-stu-id="8b694-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b694-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8b694-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8b694-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b694-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="8b694-106">'ndaki İstenen tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="8b694-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="8b694-107">'ndaki İstenen sütunun dizini.</span><span class="sxs-lookup"><span data-stu-id="8b694-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="8b694-108">dışı Satırdaki sütunun uzaklığa yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8b694-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="8b694-109">dışı Sütunun bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8b694-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="8b694-110">dışı Sütundaki değerlerin türüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8b694-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="8b694-111">dışı Sütun adı işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8b694-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="8b694-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b694-112">Remarks</span></span>

<span data-ttu-id="8b694-113">Döndürülen sütun türü bir değer aralığı içinde yer alıyorsa:</span><span class="sxs-lookup"><span data-stu-id="8b694-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="8b694-114">pType</span><span class="sxs-lookup"><span data-stu-id="8b694-114">pType</span></span>                    | <span data-ttu-id="8b694-115">Description</span><span class="sxs-lookup"><span data-stu-id="8b694-115">Description</span></span>   | <span data-ttu-id="8b694-116">Yardımcı işlevi</span><span class="sxs-lookup"><span data-stu-id="8b694-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="8b694-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="8b694-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="8b694-118">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="8b694-118">(0..63)</span></span>   | <span data-ttu-id="8b694-119">Rid</span><span class="sxs-lookup"><span data-stu-id="8b694-119">Rid</span></span>           | <span data-ttu-id="8b694-120">**Isrbıtype türü**</span><span class="sxs-lookup"><span data-stu-id="8b694-120">**IsRidType**</span></span><br><span data-ttu-id="8b694-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="8b694-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="8b694-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="8b694-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="8b694-123">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="8b694-123">(64..95)</span></span> | <span data-ttu-id="8b694-124">Kodlanmış belirteç</span><span class="sxs-lookup"><span data-stu-id="8b694-124">Coded token</span></span> | <span data-ttu-id="8b694-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="8b694-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="8b694-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="8b694-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="8b694-127">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="8b694-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="8b694-128">Int16</span><span class="sxs-lookup"><span data-stu-id="8b694-128">Int16</span></span>         | <span data-ttu-id="8b694-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="8b694-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="8b694-130">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="8b694-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="8b694-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="8b694-131">UInt16</span></span>        | <span data-ttu-id="8b694-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="8b694-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="8b694-133">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="8b694-133">`iLONG` (98)</span></span>             | <span data-ttu-id="8b694-134">Int32</span><span class="sxs-lookup"><span data-stu-id="8b694-134">Int32</span></span>         | <span data-ttu-id="8b694-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="8b694-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="8b694-136">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="8b694-136">`iULONG` (99)</span></span>            | <span data-ttu-id="8b694-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="8b694-137">UInt32</span></span>        | <span data-ttu-id="8b694-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="8b694-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="8b694-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="8b694-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="8b694-140">Bayt</span><span class="sxs-lookup"><span data-stu-id="8b694-140">Byte</span></span>          | <span data-ttu-id="8b694-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="8b694-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="8b694-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="8b694-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="8b694-143">Dize</span><span class="sxs-lookup"><span data-stu-id="8b694-143">String</span></span>        | <span data-ttu-id="8b694-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="8b694-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="8b694-145">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="8b694-145">`iGUID` (102)</span></span>            | <span data-ttu-id="8b694-146">Guid</span><span class="sxs-lookup"><span data-stu-id="8b694-146">Guid</span></span>          | <span data-ttu-id="8b694-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="8b694-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="8b694-148">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="8b694-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="8b694-149">Blob</span><span class="sxs-lookup"><span data-stu-id="8b694-149">Blob</span></span>          | <span data-ttu-id="8b694-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="8b694-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="8b694-151">*Yığında* depolanan değerler (yani, `IsHeapType == true` ) kullanılarak okunabilir:</span><span class="sxs-lookup"><span data-stu-id="8b694-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="8b694-152">`iSTRING`: **IMetaDataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="8b694-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="8b694-153">`iGUID`: **IMetaDataTables. GetGUID**</span><span class="sxs-lookup"><span data-stu-id="8b694-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="8b694-154">`iBLOB`: **IMetaDataTables. GetBlob**</span><span class="sxs-lookup"><span data-stu-id="8b694-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b694-155">Yukarıdaki tabloda tanımlanan sabitleri kullanmak için `#define _DEFINE_META_DATA_META_CONSTANTS` *Cor. h* üstbilgi dosyası tarafından sunulan yönergeyi dahil edin.</span><span class="sxs-lookup"><span data-stu-id="8b694-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b694-156">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b694-156">Requirements</span></span>  
 <span data-ttu-id="8b694-157">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b694-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b694-158">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8b694-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b694-159">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8b694-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b694-160">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b694-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b694-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b694-161">See also</span></span>

- [<span data-ttu-id="8b694-162">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b694-162">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="8b694-163">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b694-163">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
