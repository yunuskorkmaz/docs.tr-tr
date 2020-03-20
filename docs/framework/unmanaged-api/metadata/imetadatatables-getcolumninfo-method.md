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
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177129"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="4720f-102">IMetaDataTables::GetColumnInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4720f-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="4720f-103">Belirtilen tabloda belirtilen sütun hakkında veri alır.</span><span class="sxs-lookup"><span data-stu-id="4720f-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4720f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4720f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4720f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4720f-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="4720f-106">[içinde] İstenilen tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="4720f-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="4720f-107">[içinde] İstenilen sütunun dizini.</span><span class="sxs-lookup"><span data-stu-id="4720f-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="4720f-108">[çıkış] Satırdaki sütunun mahsup için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4720f-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="4720f-109">[çıkış] Sütunun boyutuna, baytlarda bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4720f-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="4720f-110">[çıkış] Sütundaki değerlerin türüne işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4720f-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="4720f-111">[çıkış] Sütun adına işaretçi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4720f-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="4720f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4720f-112">Remarks</span></span>

<span data-ttu-id="4720f-113">Döndürülen sütun türü bir değer aralığına girer:</span><span class="sxs-lookup"><span data-stu-id="4720f-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="4720f-114">pTipi</span><span class="sxs-lookup"><span data-stu-id="4720f-114">pType</span></span>                    | <span data-ttu-id="4720f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4720f-115">Description</span></span>   | <span data-ttu-id="4720f-116">Yardımcı işlevi</span><span class="sxs-lookup"><span data-stu-id="4720f-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="4720f-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="4720f-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="4720f-118">(0..63)</span><span class="sxs-lookup"><span data-stu-id="4720f-118">(0..63)</span></span>   | <span data-ttu-id="4720f-119">Kurtulmak</span><span class="sxs-lookup"><span data-stu-id="4720f-119">Rid</span></span>           | <span data-ttu-id="4720f-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="4720f-120">**IsRidType**</span></span><br><span data-ttu-id="4720f-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="4720f-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="4720f-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="4720f-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="4720f-123">(64..95)</span><span class="sxs-lookup"><span data-stu-id="4720f-123">(64..95)</span></span> | <span data-ttu-id="4720f-124">Kodlanmış belirteç</span><span class="sxs-lookup"><span data-stu-id="4720f-124">Coded token</span></span> | <span data-ttu-id="4720f-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="4720f-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="4720f-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="4720f-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="4720f-127">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="4720f-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="4720f-128">Int16</span><span class="sxs-lookup"><span data-stu-id="4720f-128">Int16</span></span>         | <span data-ttu-id="4720f-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="4720f-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="4720f-130">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="4720f-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="4720f-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="4720f-131">UInt16</span></span>        | <span data-ttu-id="4720f-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="4720f-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="4720f-133">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="4720f-133">`iLONG` (98)</span></span>             | <span data-ttu-id="4720f-134">Int32</span><span class="sxs-lookup"><span data-stu-id="4720f-134">Int32</span></span>         | <span data-ttu-id="4720f-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="4720f-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="4720f-136">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="4720f-136">`iULONG` (99)</span></span>            | <span data-ttu-id="4720f-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="4720f-137">UInt32</span></span>        | <span data-ttu-id="4720f-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="4720f-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="4720f-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="4720f-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="4720f-140">Bayt</span><span class="sxs-lookup"><span data-stu-id="4720f-140">Byte</span></span>          | <span data-ttu-id="4720f-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="4720f-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="4720f-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="4720f-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="4720f-143">Dize</span><span class="sxs-lookup"><span data-stu-id="4720f-143">String</span></span>        | <span data-ttu-id="4720f-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="4720f-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="4720f-145">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="4720f-145">`iGUID` (102)</span></span>            | <span data-ttu-id="4720f-146">Guid</span><span class="sxs-lookup"><span data-stu-id="4720f-146">Guid</span></span>          | <span data-ttu-id="4720f-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="4720f-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="4720f-148">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="4720f-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="4720f-149">Blob</span><span class="sxs-lookup"><span data-stu-id="4720f-149">Blob</span></span>          | <span data-ttu-id="4720f-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="4720f-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="4720f-151">*Yığında* depolanan değerler (diğer bir `IsHeapType == true`deyişle), aşağıdakiler kullanılarak okunabilir:</span><span class="sxs-lookup"><span data-stu-id="4720f-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="4720f-152">`iSTRING`: **IMetadataTables.GetString**</span><span class="sxs-lookup"><span data-stu-id="4720f-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="4720f-153">`iGUID`: **IMetadataTables.GetGUID**</span><span class="sxs-lookup"><span data-stu-id="4720f-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="4720f-154">`iBLOB`: **IMetadataTables.GetBlob**</span><span class="sxs-lookup"><span data-stu-id="4720f-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4720f-155">Yukarıdaki tabloda tanımlanan sabitleri kullanmak için `#define _DEFINE_META_DATA_META_CONSTANTS` *cor.h* üstbilgi dosyası tarafından sağlanan yönergeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4720f-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="4720f-156">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4720f-156">Requirements</span></span>  
 <span data-ttu-id="4720f-157">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4720f-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4720f-158">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4720f-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4720f-159">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4720f-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4720f-160">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4720f-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4720f-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4720f-161">See also</span></span>

- [<span data-ttu-id="4720f-162">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4720f-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="4720f-163">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4720f-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
