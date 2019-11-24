---
title: IMetaDataTables::GetColumn Yöntemi
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: 376b9ff09ad38ca43d57fcf064458e0331da8aad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442003"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="ab05e-102">IMetaDataTables::GetColumn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab05e-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="ab05e-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span><span class="sxs-lookup"><span data-stu-id="ab05e-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab05e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab05e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab05e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab05e-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="ab05e-106">[in] The index of the table.</span><span class="sxs-lookup"><span data-stu-id="ab05e-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="ab05e-107">[in] The index of the column in the table.</span><span class="sxs-lookup"><span data-stu-id="ab05e-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="ab05e-108">[in] The index of the row in the table.</span><span class="sxs-lookup"><span data-stu-id="ab05e-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="ab05e-109">[out] A pointer to the value in the cell.</span><span class="sxs-lookup"><span data-stu-id="ab05e-109">[out] A pointer to the value in the cell.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="ab05e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab05e-110">Remarks</span></span>

<span data-ttu-id="ab05e-111">The interpretion of the value returned through `pVal` depends on the column's type.</span><span class="sxs-lookup"><span data-stu-id="ab05e-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="ab05e-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="ab05e-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="ab05e-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span><span class="sxs-lookup"><span data-stu-id="ab05e-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="ab05e-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span><span class="sxs-lookup"><span data-stu-id="ab05e-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span> 
- <span data-ttu-id="ab05e-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span><span class="sxs-lookup"><span data-stu-id="ab05e-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="ab05e-116">Column type</span><span class="sxs-lookup"><span data-stu-id="ab05e-116">Column type</span></span>              | <span data-ttu-id="ab05e-117">pVal contains</span><span class="sxs-lookup"><span data-stu-id="ab05e-117">pVal contains</span></span> | <span data-ttu-id="ab05e-118">Yorum</span><span class="sxs-lookup"><span data-stu-id="ab05e-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="ab05e-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="ab05e-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="ab05e-120">(0..63)</span><span class="sxs-lookup"><span data-stu-id="ab05e-120">(0..63)</span></span>  | <span data-ttu-id="ab05e-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="ab05e-121">mdToken</span></span>     | <span data-ttu-id="ab05e-122">*pVal* will contain a full Token.</span><span class="sxs-lookup"><span data-stu-id="ab05e-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="ab05e-123">The function automatically converts the Rid into a full token.</span><span class="sxs-lookup"><span data-stu-id="ab05e-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="ab05e-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="ab05e-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="ab05e-125">(64..95)</span><span class="sxs-lookup"><span data-stu-id="ab05e-125">(64..95)</span></span> | <span data-ttu-id="ab05e-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="ab05e-126">mdToken</span></span> | <span data-ttu-id="ab05e-127">Upon return, *pVal* will contain a full Token.</span><span class="sxs-lookup"><span data-stu-id="ab05e-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="ab05e-128">The function automatically decompresses the CodedToken into a full token.</span><span class="sxs-lookup"><span data-stu-id="ab05e-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="ab05e-129">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="ab05e-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="ab05e-130">Int16</span><span class="sxs-lookup"><span data-stu-id="ab05e-130">Int16</span></span>         | <span data-ttu-id="ab05e-131">Automatically sign-extended to 32-bit.</span><span class="sxs-lookup"><span data-stu-id="ab05e-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="ab05e-132">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="ab05e-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="ab05e-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="ab05e-133">UInt16</span></span>        | <span data-ttu-id="ab05e-134">Automatically sign-extended to 32-bit.</span><span class="sxs-lookup"><span data-stu-id="ab05e-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="ab05e-135">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="ab05e-135">`iLONG` (98)</span></span>             | <span data-ttu-id="ab05e-136">Int32</span><span class="sxs-lookup"><span data-stu-id="ab05e-136">Int32</span></span>         |                                        | 
| <span data-ttu-id="ab05e-137">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="ab05e-137">`iULONG` (99)</span></span>            | <span data-ttu-id="ab05e-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="ab05e-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="ab05e-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="ab05e-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="ab05e-140">Bayt</span><span class="sxs-lookup"><span data-stu-id="ab05e-140">Byte</span></span>          | <span data-ttu-id="ab05e-141">Automatically sign-extended to 32-bit.</span><span class="sxs-lookup"><span data-stu-id="ab05e-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="ab05e-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="ab05e-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="ab05e-143">String heap index</span><span class="sxs-lookup"><span data-stu-id="ab05e-143">String heap index</span></span> | <span data-ttu-id="ab05e-144">*pVal* is an index into the String heap.</span><span class="sxs-lookup"><span data-stu-id="ab05e-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="ab05e-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span><span class="sxs-lookup"><span data-stu-id="ab05e-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="ab05e-146">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="ab05e-146">`iGUID` (102)</span></span>            | <span data-ttu-id="ab05e-147">Guid heap index</span><span class="sxs-lookup"><span data-stu-id="ab05e-147">Guid heap index</span></span> | <span data-ttu-id="ab05e-148">*pVal* is an index into the Guid heap.</span><span class="sxs-lookup"><span data-stu-id="ab05e-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="ab05e-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span><span class="sxs-lookup"><span data-stu-id="ab05e-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="ab05e-150">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="ab05e-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="ab05e-151">Blob heap index</span><span class="sxs-lookup"><span data-stu-id="ab05e-151">Blob heap index</span></span> | <span data-ttu-id="ab05e-152">*pVal* is an index into the Blob heap.</span><span class="sxs-lookup"><span data-stu-id="ab05e-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="ab05e-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span><span class="sxs-lookup"><span data-stu-id="ab05e-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="ab05e-154">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab05e-154">Requirements</span></span>  
 <span data-ttu-id="ab05e-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab05e-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab05e-156">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab05e-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab05e-157">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab05e-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab05e-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab05e-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab05e-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab05e-159">See also</span></span>

- [<span data-ttu-id="ab05e-160">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab05e-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ab05e-161">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab05e-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
