---
description: ': IMetaDataTables:: GetColumnInfo Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 21980567c5f9b364362f7e3ff02ee3a5e60b01ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688240"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="c7931-103">IMetaDataTables::GetColumnInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7931-103">IMetaDataTables::GetColumnInfo Method</span></span>

<span data-ttu-id="c7931-104">Belirtilen tabloda belirtilen sütunla ilgili verileri alır.</span><span class="sxs-lookup"><span data-stu-id="c7931-104">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7931-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7931-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c7931-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7931-106">Parameters</span></span>

=======

 `ixTbl`  
 <span data-ttu-id="c7931-107">'ndaki İstenen tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="c7931-107">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="c7931-108">'ndaki İstenen sütunun dizini.</span><span class="sxs-lookup"><span data-stu-id="c7931-108">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="c7931-109">dışı Satırdaki sütunun uzaklığa yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7931-109">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="c7931-110">dışı Sütunun bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7931-110">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="c7931-111">dışı Sütundaki değerlerin türüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7931-111">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="c7931-112">dışı Sütun adı işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c7931-112">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="c7931-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7931-113">Remarks</span></span>

<span data-ttu-id="c7931-114">Döndürülen sütun türü bir değer aralığı içinde yer alıyorsa:</span><span class="sxs-lookup"><span data-stu-id="c7931-114">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="c7931-115">pType</span><span class="sxs-lookup"><span data-stu-id="c7931-115">pType</span></span>                    | <span data-ttu-id="c7931-116">Description</span><span class="sxs-lookup"><span data-stu-id="c7931-116">Description</span></span>   | <span data-ttu-id="c7931-117">Yardımcı işlevi</span><span class="sxs-lookup"><span data-stu-id="c7931-117">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="c7931-118">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="c7931-118">`0`..`iRidMax`</span></span><br><span data-ttu-id="c7931-119">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="c7931-119">(0..63)</span></span>   | <span data-ttu-id="c7931-120">Rid</span><span class="sxs-lookup"><span data-stu-id="c7931-120">Rid</span></span>           | <span data-ttu-id="c7931-121">**Isrbıtype türü**</span><span class="sxs-lookup"><span data-stu-id="c7931-121">**IsRidType**</span></span><br><span data-ttu-id="c7931-122">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="c7931-122">**IsRidOrToken**</span></span> |
| <span data-ttu-id="c7931-123">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="c7931-123">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="c7931-124">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="c7931-124">(64..95)</span></span> | <span data-ttu-id="c7931-125">Kodlanmış belirteç</span><span class="sxs-lookup"><span data-stu-id="c7931-125">Coded token</span></span> | <span data-ttu-id="c7931-126">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="c7931-126">**IsCodedTokenType**</span></span> <br><span data-ttu-id="c7931-127">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="c7931-127">**IsRidOrToken**</span></span> |
| <span data-ttu-id="c7931-128">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="c7931-128">`iSHORT` (96)</span></span>            | <span data-ttu-id="c7931-129">Int16</span><span class="sxs-lookup"><span data-stu-id="c7931-129">Int16</span></span>         | <span data-ttu-id="c7931-130">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c7931-130">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c7931-131">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="c7931-131">`iUSHORT` (97)</span></span>           | <span data-ttu-id="c7931-132">UInt16</span><span class="sxs-lookup"><span data-stu-id="c7931-132">UInt16</span></span>        | <span data-ttu-id="c7931-133">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c7931-133">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c7931-134">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="c7931-134">`iLONG` (98)</span></span>             | <span data-ttu-id="c7931-135">Int32</span><span class="sxs-lookup"><span data-stu-id="c7931-135">Int32</span></span>         | <span data-ttu-id="c7931-136">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c7931-136">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c7931-137">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="c7931-137">`iULONG` (99)</span></span>            | <span data-ttu-id="c7931-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="c7931-138">UInt32</span></span>        | <span data-ttu-id="c7931-139">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c7931-139">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c7931-140">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="c7931-140">`iBYTE` (100)</span></span>            | <span data-ttu-id="c7931-141">Bayt</span><span class="sxs-lookup"><span data-stu-id="c7931-141">Byte</span></span>          | <span data-ttu-id="c7931-142">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c7931-142">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c7931-143">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="c7931-143">`iSTRING` (101)</span></span>          | <span data-ttu-id="c7931-144">Dize</span><span class="sxs-lookup"><span data-stu-id="c7931-144">String</span></span>        | <span data-ttu-id="c7931-145">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="c7931-145">**IsHeapType**</span></span>                    |
| <span data-ttu-id="c7931-146">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="c7931-146">`iGUID` (102)</span></span>            | <span data-ttu-id="c7931-147">Guid</span><span class="sxs-lookup"><span data-stu-id="c7931-147">Guid</span></span>          | <span data-ttu-id="c7931-148">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="c7931-148">**IsHeapType**</span></span>                    |
| <span data-ttu-id="c7931-149">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="c7931-149">`iBLOB` (103)</span></span>            | <span data-ttu-id="c7931-150">Blob</span><span class="sxs-lookup"><span data-stu-id="c7931-150">Blob</span></span>          | <span data-ttu-id="c7931-151">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="c7931-151">**IsHeapType**</span></span>                    |

<span data-ttu-id="c7931-152">*Yığında* depolanan değerler (yani, `IsHeapType == true` ) kullanılarak okunabilir:</span><span class="sxs-lookup"><span data-stu-id="c7931-152">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="c7931-153">`iSTRING`: **IMetaDataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="c7931-153">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="c7931-154">`iGUID`: **IMetaDataTables. GetGUID**</span><span class="sxs-lookup"><span data-stu-id="c7931-154">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="c7931-155">`iBLOB`: **IMetaDataTables. GetBlob**</span><span class="sxs-lookup"><span data-stu-id="c7931-155">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7931-156">Yukarıdaki tabloda tanımlanan sabitleri kullanmak için `#define _DEFINE_META_DATA_META_CONSTANTS` *Cor. h* üstbilgi dosyası tarafından sunulan yönergeyi dahil edin.</span><span class="sxs-lookup"><span data-stu-id="c7931-156">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7931-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7931-157">Requirements</span></span>  

 <span data-ttu-id="c7931-158">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7931-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7931-159">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c7931-159">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7931-160">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c7931-160">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7931-161">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7931-161">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7931-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7931-162">See also</span></span>

- [<span data-ttu-id="c7931-163">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7931-163">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="c7931-164">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7931-164">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
